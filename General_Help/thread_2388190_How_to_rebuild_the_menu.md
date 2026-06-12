---
title: "How to rebuild the menu"
date: 2018-03-29
forum: General Help
---

### Post by two4two on 2018-03-29
Ubuntu Studio 16.04.03, it uses xfce desktop.  K3B was not installed by default so I used Synaptic Package Manager to install it.  Afrter it was installed I didn't see it in the video production section (or anywhere else) so I used "accessories --> menu editor" to try to add it.  I don't know what I did wrong, but now the audio production section has only K3b, and the video production section does not even appear.  When I go back to the menu editor the video production section header is there, and it is not marked as hidden, but there is nothing in it.  There are other things messed up too.  Rather than play with it for hours I'd just like to find a tool to rebuild it all automatically.  Is there a way to do this?  Again, Ubuntu Studio, 16.04.03 using xfce desktop.  I've read other threads but none for this exact situation.

---

### Post by again? on 2018-03-29
From what I can see xfce4 Menu Editor creates user files in:
[LIST]
[*]~/.local/share/desktop-directories for menu categories
[*]~/.local/share/applications for applications
[/LIST]

When hidden using the editor, files are created with a "NoDisply=true" setting.

I used the editor to hide the "Office" category and "Libreoffice Math" application.
Deleting the files will return to default settings from /usr/share/desktop-directories and /usr/share/applications
Be aware you may also have custom launchers in ~/.local/share/applications as you can see in my second screenshot where I have numerous custom launchers.

---

### Post by two4two on 2018-03-30
> **guber2 said:**
> From what I can see xfce4 Menu Editor creates user files in:

Deleting the files will return to default settings from /usr/share/desktop-directories and /usr/share/applications


Thanks guber2.  Well my education is begun.

I deleted the files from .local/share/desktop-directories and rebooted but the original menu list did not restore.  However, no the audio production section is gone from the menu too.  I think there must be a bug in that menu edit software.  What if I copy the entire directory from usr/share to .local/share?  I'm thinking all the menu items should come back, but what about the applications?

---

### Post by again? on 2018-03-30
What's your term output for 
```
ls ~/.local/share/applications  ~/.local/share/desktop-directories
```

There may be some other setting I don't know about.
I'm in Xubuntu 17.10 and there may be something peculiar to Ubuntu-studio settings.

Would be safer to create a new user and test in that account which will start with the default settings.
You may be able to figure out what you did.
[https://wiki.bluesabre.org/menulibre_usage](https://wiki.bluesabre.org/menulibre_usage)

---

### Post by again? on 2018-03-30
Bit of googling found that menulibre also creates configs at **~/.config/menus**
Try moving or deleting that directory.

---

### Post by two4two on 2018-03-30
OK, this will take some space, but here it is:

```
don@don-Stubuntu-16-04-03:~$ ls ~/.local/share/applications  ~/.local/share/desktop-directories
/home/me/.local/share/applications:
AcetoneISO.desktop                                       kid3-qt.desktop                       software-properties-gtk.desktop
aeolus.desktop                                           kmailservice5.desktop                 sooperlooper.desktop
agave.desktop                                            kodi.desktop                          subtitleeditor.desktop
apport-gtk.desktop                                       ktelnetservice5.desktop               synaptic.desktop
ardour.desktop                                           ladi-control-center.desktop           synfigstudio.desktop
audacity.desktop                                         ladi-player.desktop                   synthv1.desktop
blender.desktop                                          ladi-system-log.desktop               system-config-printer.desktop
blueman-adapters.desktop                                 ladi-system-tray.desktop              system-config-samba.desktop
blueman-manager.desktop                                  language-selector.desktop             Thunar-bulk-rename.desktop
brasero.desktop                                          libreoffice-calc.desktop              Thunar.desktop
brasero-nautilus.desktop                                 libreoffice-math.desktop              Thunar-folder-handler.desktop
calf.desktop                                             libreoffice-startcenter.desktop       thunar-settings.desktop
catfish.desktop                                          libreoffice-writer.desktop            thunar-volman-settings.desktop
chrome-aohghmighlieiainnegkcijnfilokake-Default.desktop  libreoffice-xsltfilter.desktop        thunderbird.desktop
chrome-apdfllckaahabafndbhieahigkjlhalf-Default.desktop  lightdm-gtk-greeter-settings.desktop  time.desktop
chrome-blpcfgokakmgnkcojhhkbfbldkacnbeo-Default.desktop  lmms.desktop                          torbrowser.desktop
chrome-pjkljhegncpnkpknbcohdijeoejaedia-Default.desktop  lv2rack.desktop                       torbrowser-settings.desktop
darktable.desktop                                        menulibre.desktop                     totem.desktop
deb-gview.desktop                                        meterbridge.desktop                   transmission-gtk.desktop
debian-uxterm.desktop                                    mimeapps.list                         ubuntustudio-contribute.desktop
debian-xterm.desktop                                     mimeinfo.cache                        ubuntustudio-controls.desktop
defaults.list                                            mono-runtime-common.desktop           ubuntustudio-forum.desktop
deluge.desktop                                           mono-runtime-terminal.desktop         ubuntustudio-help.desktop
devede_ng.desktop                                        mount-archive.desktop                 ubuntustudio-installer.desktop
display-im6.desktop                                      mousepad.desktop                      ubuntustudio-irc.desktop
display-im6.q16.desktop                                  mscore.desktop                        ubuntustudio-mail.desktop
drumkv1.desktop                                          mudita24.desktop                      ubuntustudio-website.desktop
echomixer.desktop                                        mugshot.desktop                       update-manager.desktop
entangle.desktop                                         mypaint.desktop                       users.desktop
envy24_control.desktop                                   nautilus-autorun-software.desktop     v4l2ucp.desktop
evince.desktop                                           nautilus-classic.desktop              vim.desktop
evince-previewer.desktop                                 nautilus-connect-server.desktop       vinagre.desktop
exo-file-manager.desktop                                 nautilus.desktop                      vinagre-file.desktop
exo-mail-reader.desktop                                  nautilus-folder-handler.desktop       vino-preferences.desktop
exo-preferred-applications.desktop                       nautilus-home.desktop                 vino-server.desktop
exo-terminal-emulator.desktop                            nerolinux.desktop                     virtualbox.desktop
exo-web-browser.desktop                                  nerolinuxexpress.desktop              vkeybd.desktop
ffado.org-ffadomixer.desktop                             network.desktop                       wine.desktop
file-roller.desktop                                      nm-applet.desktop                     wine-extension-chm.desktop
firefox.desktop                                          nm-connection-editor.desktop          wine-extension-gif.desktop
fluid.desktop                                            onboard.desktop                       wine-extension-hlp.desktop
fontforge.desktop                                        onboard-settings.desktop              wine-extension-htm.desktop
font-manager.desktop                                     openshot.desktop                      wine-extension-html.desktop
font-sampler.desktop                                     org.gnome.baobab.desktop              wine-extension-ini.desktop
foo-yc20.desktop                                         org.gnome.DiskUtility.desktop         wine-extension-jfif.desktop
gcm-calibrate.desktop                                    org.gnome.FileRoller.desktop          wine-extension-jpe.desktop
gcm-import.desktop                                       org.gnome.gedit.desktop               wine-extension-msp.desktop
gcm-picker.desktop                                       org.gnome.Nautilus.desktop            wine-extension-png.desktop
gcm-viewer.desktop                                       org.gnome.Software.desktop            wine-extension-rtf.desktop
gcr-prompter.desktop                                     org.gnome.Totem.desktop               wine-extension-txt.desktop
gcr-viewer.desktop                                       org.kde.Help.desktop                  wine-extension-url.desktop
gdebi.desktop                                            org.kde.kdenlive.desktop              wine-extension-vbs.desktop
gedit.desktop                                            panel-desktop-handler.desktop         wine-extension-wri.desktop
gigolo.desktop                                           panel-preferences.desktop             wine-extension-xml.desktop
gimp.desktop                                             parole.desktop                        winetricks.desktop
gisomount.desktop                                        patchage.desktop                      xfburn.desktop
gksu.desktop                                             pavucontrol.desktop                   xfcalendar.desktop
gladish.desktop                                          petri-foo.desktop                     xfce4-about.desktop
globaltime.desktop                                       phasex.desktop                        xfce4-accessibility-settings.desktop
gmidimonitor-alsa.desktop                                phatch.desktop                        xfce4-appfinder.desktop
gmidimonitor-jack.desktop                                phatch-inspector.desktop              xfce4-clipman.desktop
gmount-iso.desktop                                       pidgin.desktop                        xfce4-dict.desktop
gnome-calculator.desktop                                 pitivi.desktop                        xfce4-mime-settings.desktop
gnome-disk-image-mounter.desktop                         puredata.desktop                      xfce4-notes.desktop
gnome-disk-image-writer.desktop                          putty.desktop                         xfce4-notifyd-config.desktop
gnome-mines.desktop                                      python2.7.desktop                     xfce4-power-manager-settings.desktop
gnome-software-local-file.desktop                        python3.5.desktop                     xfce4-run.desktop
gnome-sudoku.desktop                                     qasconfig.desktop                     xfce4-screenshooter.desktop
gnome-system-log.desktop                                 qashctl.desktop                       xfce4-sensors.desktop
gnome-system-monitor.desktop                             qasmixer.desktop                      xfce4-session-logout.desktop
gnome-system-monitor-kde.desktop                         qjackctl.desktop                      xfce4-settings-editor.desktop
google-chrome.desktop                                    qmidiarp.desktop                      xfce4-taskmanager.desktop
grub-customizer.desktop                                  qmidinet.desktop                      xfce4-terminal.desktop
gtk-recordmydesktop.desktop                              qmidiroute.desktop                    xfce-backdrop-settings.desktop
gtk-theme-config.desktop                                 qsynth.desktop                        xfce-display-settings.desktop
gucharmap.desktop                                        qtractor.desktop                      xfce-keyboard-settings.desktop
guitarix.desktop                                         qv4l2.desktop                         xfce-mouse-settings.desktop
hdajackretask.desktop                                    rakarrack.desktop                     xfce-session-settings.desktop
hdspconf.desktop                                         rapid-photo-downloader.desktop        xfce-settings-manager.desktop
hdspmixer.desktop                                        rawtherapee.desktop                   xfce-ui-settings.desktop
hexter.desktop                                           remmina.desktop                       xfce-wm-settings.desktop
hplj1020.desktop                                         ristretto.desktop                     xfce-wmtweaks-settings.desktop
hydrogen.desktop                                         rmedigicontrol.desktop                xfce-workspaces-settings.desktop
idjc.desktop                                             samplv1.desktop                       xfce-xfcalendar-settings.desktop
im-config.desktop                                        scribus.desktop                       xfpanel-switch.desktop
inkscape.desktop                                         shares.desktop                        xjadeo.desktop
isomaster.desktop                                        simple-scan.desktop                   yelp.desktop
jack-keyboard.desktop                                    smplayer.desktop                      yoshimi.desktop
jack-rack.desktop                                        smplayer_enqueue.desktop              zita-at1.desktop
jamin.desktop                                            smtube.desktop                        zita-mu1.desktop
k3b.desktop                                              software-properties-drivers.desktop   zita-rev1.desktop
kde4                                                     software-properties-gnome.desktop     zynjacku.desktop

/home/me/.local/share/desktop-directories:
ActionGames.directory                     kde-internet.directory                  ubuntustudio-effects.directory
AdventureGames.directory                  kde-internet-terminal.directory         ubuntustudio-graphics.directory
ArcadeGames.directory                     kde-main.directory                      ubuntustudio-info.directory
AudioVideo.directory                      kde-more.directory                      ubuntustudio-mediaplayback.directory
BlocksGames.directory                     kde-multimedia.directory                ubuntustudio-midi.directory
BoardGames.directory                      kde-office.directory                    ubuntustudio-mixers.directory
CardGames.directory                       kde-science.directory                   ubuntustudio-noshow.directory
Debian.directory                          kde-settingsmenu.directory              ubuntustudio-photography.directory
Development.directory                     kde-system.directory                    ubuntustudio-synths.directory
Education.directory                       kde-system-terminal.directory           ubuntustudio-video-audio-tools.directory
Game.directory                            kde-toys.directory                      ubuntustudio-videoproduction.directory
GnomeScience.directory                    kde-unknown.directory                   Utility-Accessibility.directory
Graphics.directory                        kde-utilities-accessibility.directory   Utility.directory
Hardware.directory                        kde-utilities-desktop.directory         xfce-accessories.directory
kde-development.directory                 kde-utilities.directory                 xfce-development.directory
kde-development-translation.directory     kde-utilities-file.directory            xfce-education.directory
kde-development-webdevelopment.directory  kde-utilities-peripherals.directory     xfce-games.directory
kde-editors.directory                     kde-utilities-pim.directory             xfce-graphics.directory
kde-education.directory                   kde-utilities-xutils.directory          xfce-hardware.directory
kde-edu-languages.directory               KidsGames.directory                     xfce-multimedia.directory
kde-edu-mathematics.directory             LogicGames.directory                    xfce-network.directory
kde-edu-miscellaneous.directory           Network.directory                       xfce-office.directory
kde-edu-science.directory                 Office.directory                        xfce-other.directory
kde-edu-tools.directory                   Personal.directory                      xfce-personal.directory
kde-games-arcade.directory                RolePlayingGames.directory              xfce-screensavers.directory
kde-games-board.directory                 Settings.directory                      xfce-settings.directory
kde-games-card.directory                  Settings-System.directory               xfce-system.directory
kde-games.directory                       SimulationGames.directory               X-GNOME-Menu-Applications.directory
kde-games-kids.directory                  SportsGames.directory                   X-GNOME-Other.directory
kde-games-logic.directory                 StrategyGames.directory                 X-GNOME-Sundry.directory
kde-games-roguelikes.directory            System.directory                        X-GNOME-SystemSettings.directory
kde-games-strategy.directory              System-Tools.directory                  X-GNOME-Utilities.directory
kde-graphics.directory                    ubuntustudio-audioproduction.directory  X-GNOME-WebApplications.directory
kde-information.directory                 ubuntustudio-audio-utiliy.directory
```

---

### Post by again? on 2018-03-30
That's an awful lot of files, considering in a fresh user account those directories don't even exist.

Try moving these 3 directories to ~/Desktop
```
~/.local/share/desktop-directories
~/.local/share/applications
~/.config/menus
```
Log out and back in.
Any trouble just move back.

---

### Post by two4two on 2018-03-30
> **guber2 said:**
> That's an awful lot of files, considering in a fresh user account those directories don't even exist.

Try moving these 3 directories to ~/Desktop
```
~/.local/share/desktop-directories
~/.local/share/applications
~/.config/menus
```
Log out and back in.
Any trouble just move back.

Success!  Thanks a billion.:)

---

### Post by again? on 2018-03-30
Ok.
Just delete the files you moved to ~/Desktop when you're happy all is going well.

---

