---
title: "Lubuntu 18.04 LTS odd menu duplications"
date: 2018-11-10
forum: General Help
---

### Post by heliosstudios on 2018-11-10
Hello, I've installed Lubuntu 18.04 and several software titles (WINE/PlayOnLinux - not used yet, Keepass2, KiCAD, LibreOffice, Kdenlive, etc) on a Dell Latitude 3540.  Using the Oibaf video driver.  Windows veteran, Linux convert.  The main menu was showing the KiCAD icons under "Other", so I installed MenuLibre (would not see "Other" at all) then Alacarte (ditto.)  Resorting to PCmanFM, it could finally see these, so I created an "Electronics" menu with MenuLibre, and tried to move the KiCAD icons from "Other" to "Electronics."  Long story short, it didn't work, and now I am left with the following:

[https://i.stack.imgur.com/3nF8r.png](https://i.stack.imgur.com/3nF8r.png)

Now things are a real mess and I cannot remedy any of this duplication.  

Any hints or tricks would be greatly appreciated!

P.S. here is a list of the files in /home/me/.local/share/applications:
```
me@Lubuntu:~/.local/share/applications$ ls
alacarte.desktop                      menulibre-visual-studio-code.desktop
apport-gtk.desktop                    menulibre-wine-configuration.desktop
bitmap2component.desktop              mimeinfo.cache
code.desktop                          mtpaint.desktop
code-url-handler.desktop              opera.desktop
defaults.list                         pcbcalculator.desktop
eeschema.desktop                      pcbnew.desktop
fcitx-configtool.desktop              PlayOnLinux.desktop
fcitx.desktop                         python2.7.desktop
gerbview.desktop                      python3.6.desktop
gnome-language-selector.desktop       software-properties-drivers.desktop
keepass2.desktop                      software-properties-gtk.desktop
kicad.desktop                         sylpheed.desktop
leafpad.desktop                       synaptic.desktop
lightdm-gtk-greeter-settings.desktop  update-manager.desktop
lxrandr.desktop                       usb-creator-gtk.desktop
lxsession-default-apps.desktop        xscreensaver-properties.desktop
lxshortcut.desktop
```

And /usr/share/applications:
```
me@Lubuntu:/usr/share/applications$ ls
alacarte.desktop                      lxappearance.desktop
apport-gtk.desktop                    lxde-x-terminal-emulator.desktop
audacious.desktop                     lxde-x-www-browser.desktop
audacity.desktop                      lxhotkey-gtk.desktop
bitmap2component.desktop              lxinput.desktop
bleachbit.desktop                     lxrandr.desktop
bleachbit-root.desktop                lxsession-default-apps.desktop
blueman-adapters.desktop              lxshortcut.desktop
blueman-manager.desktop               lxtask.desktop
code.desktop                          lxterminal.desktop
code-url-handler.desktop              menulibre.desktop
defaults.list                         mimeinfo.cache
eeschema.desktop                      mono-runtime-common.desktop
evince.desktop                        mono-runtime-terminal.desktop
evince-previewer.desktop              mtpaint.desktop
fcitx-config-gtk2.desktop             network.desktop
fcitx-configtool.desktop              nm-applet.desktop
fcitx.desktop                         nm-connection-editor.desktop
fcitx-skin-installer.desktop          notification-daemon.desktop
file-roller.desktop                   obconf.desktop
firefox.desktop                       opera.desktop
galculator.desktop                    org.gnome.DiskUtility.desktop
gcr-prompter.desktop                  org.gnome.FileRoller.desktop
gcr-viewer.desktop                    org.gnome.Software.desktop
gdebi.desktop                         org.gnome.Software.Editor.desktop
geoclue-where-am-i.desktop            org.kde.kdenlive.desktop
gerbview.desktop                      pavucontrol.desktop
gimp.desktop                          pcbcalculator.desktop
gnome-disk-image-mounter.desktop      pcbnew.desktop
gnome-disk-image-writer.desktop       pcmanfm.desktop
gnome-language-selector.desktop       pcmanfm-desktop-pref.desktop
gnome-software-local-file.desktop     pidgin.desktop
gpicview.desktop                      PlayOnLinux.desktop
gucharmap.desktop                     python2.7.desktop
guvcview.desktop                      python3.6.desktop
hardinfo.desktop                      screensavers
hplj1020.desktop                      shares.desktop
htop.desktop                          simple-scan.desktop
im-config.desktop                     software-properties-drivers.desktop
io.github.GnomeMpv.desktop            software-properties-gtk.desktop
keepass2.desktop                      sylpheed.desktop
kicad.desktop                         synaptic.desktop
ktelnetservice5.desktop               system-config-printer.desktop
leafpad.desktop                       time.desktop
libreoffice6.1-base.desktop           transmission-gtk.desktop
libreoffice6.1-calc.desktop           update-manager.desktop
libreoffice6.1-draw.desktop           usb-creator-gtk.desktop
libreoffice6.1-impress.desktop        users.desktop
libreoffice6.1-math.desktop           vim.desktop
libreoffice6.1-startcenter.desktop    xfburn.desktop
libreoffice6.1-writer.desktop         xfce4-notifyd-config.desktop
libreoffice6.1-xsltfilter.desktop     xfce4-power-manager-settings.desktop
lightdm-gtk-greeter-settings.desktop  xpad.desktop
lubuntu-logout.desktop                xscreensaver-properties.desktop
lubuntu-screenlock.desktop
```

---

