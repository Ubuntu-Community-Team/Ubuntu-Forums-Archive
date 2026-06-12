---
title: "Ubuntu 12.04 + MATE Guide"
date: 2013-08-17
forum: General Help
---

### Post by salatiel on 2013-08-17
Well, i've been trying to get ubuntu 12.04 to behave exactly like ubuntu 10.04 . No bloatware, spyware and a very clean interface. (I really hate UNITY  and gnome 3)
So after a few tries i decided to make a tutorial to help those that want to achieve this same goal.

After following this procedure you will get a very clean ubuntu 12.04 running ONLY mate (gnome 2 fork)

1) After the initial installation of ubuntu 12.04, instead of reboot, select  "Continue testing".
2) open a gnome-terminal
3) follow the script below 

PLEASE MAKE SURE THAT YOU MOUNT ALL PARTITION INSIDE OF /target if you use different partitions for /usr /var .... etc

DO IT AT YOUR OWN RISK !


```

sudo su -
mount /dev/sdXX /target  # replace XX by the partition you used as root
for i in proc sys dev ; do 
     mount --bind /$i /target/$i
done
chroot /target
sed -i s@enabled=1@enabled=0@g /etc/default/apport  # DISABLE APPORT
# ADD MATE/SMPLAYER and JAVA repositories
add-apt-repository "deb http://packages.mate-desktop.org/repo/ubuntu precise main"
apt-add-repository -y ppa:rvm/smplayer
apt-add-repository -y ppa:motumedia/mplayer-daily
apt-add-repository -y ppa:webupd8team/java
apt-get update
apt-get --yes --quiet --allow-unauthenticated install mate-archive-keyring
apt-get update

# REMOVE ALL BLOATWARE 

sudo apt-get --yes remove --purge zeitgeist activity-log-manager-common zeitgeist-core \
        zeitgeist-datahub python-zeitgeist rhythmbox-plugin-zeitgeist \
        geoclue geoclue-ubuntu-geoip geoip-database whoopsie  \
        evince gcalctool gnome-screenshot gedit file-roller gnome-keyring \
        eog gnome-system-monitor gnome-system-log \
        baobab gnome-terminal gnome-applets gnome-media empathy bash-completion \
        gnome-power-manager gnome-screensaver thunderbird gwibber \
        unity unity-2d unity-2d-places unity-2d-panel \
        unity-2d-spread unity-services \
        unity-asset-pool unity-lens-* unity-scope-* \
        liboverlay-scrollbar* appmenu-gtk nautilus \
        appmenu-gtk3 appmenu-qt firefox-globalmenu \
        thunderbird-globalmenu unity-2d-common unity-common libunity-misc4 libunity-core-5*

apt-get --yes autoremove

# INSTALL MATE and bring back synaptic - Install in this order , dont force install everything in one line
sudo apt-get --yes install mate-core
sudo apt-get --yes install mate-desktop-environment 
sudo apt-get --yes install mate-keyring mate-media-pulse mate-settings-daemon-pulse synaptic

# SET MATE DEFAULT


 /usr/lib/lightdm/lightdm-set-defaults -s mate
 xdg-mime default caja-folder-handler.desktop inode/directory
 xdg-mime default caja-folder-handler.desktop x-scheme-handler/ssh
 xdg-mime default caja-folder-handler.desktop x-scheme-handler/ftp
 xdg-mime default eom.desktop image/bmp
 xdg-mime default eom.desktop image/gif
 xdg-mime default eom.desktop image/jpeg
 xdg-mime default eom.desktop image/x-pcx
 xdg-mime default eom.desktop image/png
 xdg-mime default eom.desktop image/tiff
 xdg-mime default pluma.desktop text/plain
 xdg-mime default pluma.desktop text/x-log
 xdg-mime default pluma.desktop application/x-perl
 xdg-mime default pluma.desktop application/javascript
 xdg-mime default pluma.desktop application/rdf+xml
 xdg-mime default pluma.desktop application/x-wine-extension-ini
 xdg-mime default pluma.desktop application/x-wine-extension-vbs
 xdg-mime default pluma.desktop text/x-csrc
 xdg-mime default pluma.desktop application/x-wine-extension-inf
 xdg-mime default atril.desktop application/pdf
 update-alternatives --install "$(which x-terminal-emulator)" x-terminal-emulator "$(which mate-terminal)" 30
 update-alternatives --set x-terminal-emulator "$(which mate-terminal)"

 # LINK THE OLD APPS TO THE NEW ONES ( Help a lot those who like Alt+F2 :p )
 ln -s /usr/bin/mate-terminal /usr/bin/gnome-terminal
 ln -s /usr/bin/pluma /usr/bin/gedit
 ln -s /usr/bin/atril /usr/bin/evince
 ln -s /usr/bin/mate-calc /usr/bin/gcalctool
 ln -s /usr/bin/eom /usr/bin/eog

# FIX THE DELAYED SPLASH SCREEN
echo FRAMEBUFFER=y |  tee /etc/initramfs-tools/conf.d/splash
 update-initramfs -u


# INSTALL BACK SOME UTILITIES
 apt-get -y install system-config-printer-gnome gnome-system-tools gimp smplayer

# INSTALL JAVA AND COREFONTES - will need user intervention
 apt-get-y  install oracle-java7-installer ttf-mscorefonts-installer


# FIX THE  AUTOSTART OF A FEW APPLICATION AND THE DESKTOP SHARING ICONS
for i in /etc/xdg/autostart/bluetooth-applet.desktop /etc/xdg/autostart/vino-server.desktop \
                /usr/share/applications/vino-preferences.desktop   ; do  
        sed -i 's@OnlyShowIn=.*@OnlyShowIn=MATE;@g' $i
        sed -i '/AutostartCondition=GNOME/d' $i
 done

# FULL UPGRADE
apt-get -y upgrade
# CLEAN EVERYTHING
apt-get clean
sync

```


Now you umount everything and reboot. (Actually you can just reboot)

Hope it helps anyone.

---

