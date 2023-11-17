# ansible-role-tmux

This role helps you to install and configure tmux with the TPM plugin manager, and some nice extras.

Heavily influced by the tmux configurations of both [@ThePrimeagen](https://github.com/dreamsofcode-io/) and [@dreamsofcode](https://github.com/dreamsofcode-io/).

## Requirements

Python packges:

- python3-jmespath

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    tmux_users: []

List of users to run the role on.

    tmux_tpm_location: https://github.com/tmux-plugins/tpm

Location of the TPM plugin manager on GitHub.

    tmux_enable_24bit_terminal: true

Enable 24bit terminal support for correct colours.

    tmux_enable_mouse: true

Enable mouse support

    tmux_prefix_key:

Change the prefix key, away from CTRL + b which is the default. I.e. `C-Space` for CTRL + Space.

    tmux_vim_style_panel_selection: true

Enable VIM style window/panel selection.

    tmux_statusbar_location: bottom

The location of the tmux statusbar.

    tmux_window_and_pane_renumbering: true

Enable renumbering of windows and panels, 0 becomes 1.

    tmux_vi_mode: true

Enable VI mode.

    tmux_vim_copy_mode: true

Enable VIM copy mode.

    tmux_custom_config: true

Enable support for custom configuration using ~/.tmux.conf.local.

    tmux_custom_keybindings: []

Add custom keybindings to ~/.tmux.conf

    tmux_plugins: []

The list of plugins to enable for tmux

## Variable examples

    tmux_custom_keybindings: |
      bind C-t new-window

This adds the keybinding `CTRL + t` to open a new window.

    tmux_plugins:
      tmux-sensible:
        name: "tmux-plugins/tmux-sensible"
        options:
      vim-tmux-navigator:
        name: "christoomey/vim-tmux-navigator"
        options:
      tmux-yank:
        name: "tmux-plugins/tmux-yank"
        options:
      catppuccin-tmux:
        name: "dreamsofcode-io/catppuccin-tmux"
        options: |
          set -g @catppuccin_flavour 'mocha'

This adds the following plugins to your tmux configuration: `tmux-sensible`, `vim-tmux-navigator`, `tmux-yank` and the theme `catppuccin-tmux`.

It is controlled by two options, `name` and `options`. `name` contains the GitHub repisotory name, while `options` contain any options you want to apply to your tmux configution to over the plugins default options.

## Dependencies

None

## Example Playbook

    ---
    - name: Run Ansible TMUX role
      hosts: all
      become: true
      gather_facts: true

      vars:
        tmux_users:
          - tolecnal

      roles:
        - role: tolecnal.tmux_npm

## License

MIT / BSD

## Author Information

Jostein Elvaker Haande - tolecnal - [https://tolecnal.net](tolecnal.net)
