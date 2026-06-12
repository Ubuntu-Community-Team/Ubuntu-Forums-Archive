---
title: "gtk-query-settings"
date: 2017-10-14
forum: General Help
---

### Post by mattdawolf on 2017-10-14
What file does it pull its config from? I've changed all the config  files I could find but I must be missing something. Does Trinity have its own separate gtk files? 

```

mattdawolf@mattdawolfsden:~$ gtk-query-settings
              gtk-double-click-time: 400
          gtk-double-click-distance: 5
                   gtk-cursor-blink: TRUE
              gtk-cursor-blink-time: 1200
           gtk-cursor-blink-timeout: 10
                   gtk-split-cursor: TRUE
                     gtk-theme-name: "Default"
                gtk-icon-theme-name: "tdegtk-icon-theme"
!           gtk-fallback-icon-theme: "tdegtk-fallback-icon-theme"
                 gtk-key-theme-name: NULL
                 gtk-menu-bar-accel: "F10"
             gtk-dnd-drag-threshold: 8
                     ** gtk-font-name: "Sans 10"**
!                    gtk-icon-sizes: "panel-menu-bar=24,24"
                        gtk-modules: NULL
                  gtk-xft-antialias: 1
                    gtk-xft-hinting: 1
                  gtk-xft-hintstyle: "hintfull"
                       gtk-xft-rgba: "none"
                        gtk-xft-dpi: 122880
              gtk-cursor-theme-name: NULL
              gtk-cursor-theme-size: 0
       gtk-alternative-button-order: FALSE
        gtk-alternative-sort-arrows: FALSE
!        gtk-show-input-method-menu: FALSE
!             gtk-show-unicode-menu: FALSE
!               gtk-timeout-initial: 500
!                gtk-timeout-repeat: 50
!                gtk-timeout-expand: 500
!                  gtk-color-scheme: ""
              gtk-enable-animations: TRUE
!              gtk-touchscreen-mode: FALSE
!               gtk-tooltip-timeout: 500
!        gtk-tooltip-browse-timeout: 60
!   gtk-tooltip-browse-mode-timeout: 500
!            gtk-keynav-cursor-only: FALSE
!            gtk-keynav-wrap-around: TRUE
                     gtk-error-bell: TRUE
!                        color-hash: ((GHashTable*) 0x5574c361cde0)
!          gtk-file-chooser-backend: NULL
                 gtk-print-backends: "file,cups,cloudprint"
          gtk-print-preview-command: "evince --unlink-tempfile --preview --print-settings %s %f"
               gtk-enable-mnemonics: TRUE
                  gtk-enable-accels: TRUE
!            gtk-recent-files-limit: 50
                      gtk-im-module: NULL
           gtk-recent-files-max-age: 30
           gtk-fontconfig-timestamp: 0
               gtk-sound-theme-name: "ubuntu"
   gtk-enable-input-feedback-sounds: TRUE
            gtk-enable-event-sounds: TRUE
!               gtk-enable-tooltips: TRUE
!                 gtk-toolbar-style: GTK_TOOLBAR_BOTH_HORIZ
!             gtk-toolbar-icon-size: GTK_ICON_SIZE_LARGE_TOOLBAR
!                gtk-auto-mnemonics: TRUE
    gtk-primary-button-warps-slider: TRUE
!                 gtk-visible-focus: GTK_POLICY_AUTOMATIC
  gtk-application-prefer-dark-theme: FALSE
!                 gtk-button-images: FALSE
          gtk-entry-select-on-focus: TRUE
    gtk-entry-password-hint-timeout: 0
!                   gtk-menu-images: FALSE
!          gtk-menu-bar-popup-delay: 0
!     gtk-scrolled-window-placement: GTK_CORNER_TOP_LEFT
!             gtk-can-change-accels: FALSE
!              gtk-menu-popup-delay: 225
!            gtk-menu-popdown-delay: 1000
          gtk-label-select-on-focus: TRUE
!                 gtk-color-palette: "black:white:gray50:red:purple:blue:light blue:green:yellow:orange:lavender:brown:goldenrod4:dodger blue:pink:light green:gray10:gray30:gray75:gray90"
!              gtk-im-preedit-style: GTK_IM_PREEDIT_CALLBACK
!               gtk-im-status-style: GTK_IM_STATUS_CALLBACK
           gtk-shell-shows-app-menu: FALSE
            gtk-shell-shows-menubar: FALSE
            gtk-shell-shows-desktop: TRUE
              gtk-decoration-layout: "menu:minimize,maximize,close"
          gtk-titlebar-double-click: "toggle-maximize"
          gtk-titlebar-middle-click: "none"
           gtk-titlebar-right-click: "menu"
             gtk-dialogs-use-header: FALSE
           gtk-enable-primary-paste: TRUE
           gtk-recent-files-enabled: TRUE
                gtk-long-press-time: 500
               gtk-keynav-use-caret: FALSE

```

---

### Post by again? on 2017-10-14
No idea what trinity is but in my ubuntu 17.04 install I can override settings using
~/.config/gtk-3.0/settings.ini
eg my file
```
[Settings]
gtk-application-prefer-dark-theme=0
gtk-primary-button-warps-slider=0
```

[https://developer.gnome.org/gtk3/stable/GtkSettings.html]("https://developer.gnome.org/gtk3/stable/GtkSettings.html")

---

