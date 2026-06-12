---
title: "Ridiculously Long String for Fresh Install"
date: 2013-11-14
forum: General Help
---

### Post by dannymichel on 2013-11-14
I've been fresh installing a lot lately, so i decided to copy some files to my windows hard drive and write a ridiculously long string to copy and paste when i've done a fresh install. Any way to improve this?
> xset m 1 1 && sudo apt-get install filezilla chromium-browser gpart gparted hfsplus hfsutils hfsprogs gptsync autogen git subversion libtool gimp inkscape scribus compiz-plugins compizconfig-settings-manager unity-tweak-tool kazam fonts-droid backintime-gnome synaptic xchat nautilus-dropbox && sudo mkdir /media/danny/Windows && sudo mount /dev/sda2 /media/danny/Windows && sudo cp -R /media/danny/Windows/Fonts/* /usr/share/fonts/ && sudo chmod -R 755 /usr/share/fonts && sudo chown -R danny:danny /usr/share/fonts && sudo chmod -R 755 /media/danny/Backup && sudo chown -R danny:danny /media/danny/Backup && sudo fc-cache -fv && sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade %% sudo gptsync /dev/sda && sudo gptsync /dev/sdb && sudo cp /media/danny/Windows/local.conf  /etc/fonts/ && sudo mkdir ~/public_html && sudo chown -R www-data ~/public_html && sudo chmod -R 755 ~/public_html && sudo cp /media/danny/Windows/hosts /etc/ && sudo apt-get install apache2 && sudo cp /media/danny/Windows/apache2.conf /etc/apache2/ && && sudo cp /media/danny/Windows/dev.dmichel.conf /etc/apache2/sites-available/ && sudo a2enmod rewrite && sudo /etc/init.d/apache2 restart && sudo a2dissite 000-default && sudo a2ensite dev.dmichel.net && sudo /etc/init.d/apache2 restart && sudo apt-get install mysql-server mysql-client && sudo cp /media/danny/Windows/my.cnf /etc/mysql/ && sudo apt-get install php5 php5-mysql libapache2-mod-php5 && sudo /etc/init.d/apache2 restart && sudo cp /media/danny/Windows/php.ini /etc/php5/apache2/ &&  sudo /etc/init.d/apache2 restart && sudo apt-get install phpmyadmin && sudo ln -s /usr/share/phpmyadmin ~/public_html/phpmyadmin && mv -i /etc/php5/conf.d/mcrypt.ini /etc/php5/mods-available/ && sudo php5enmod mcrypt && sudo /etc/init.d/apache2 restart && sudo sh -c 'echo "deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free" >> /etc/apt/sources.list'  && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59 && sudo apt-get update && sudo apt-get install spotify-client && cd ~/Downloads && wget [http://s.insynchq.com/builds/insync_1.0.24_amd64.deb](http://s.insynchq.com/builds/insync_1.0.24_amd64.deb) && sudo dpkg -i insync_1.0.24_amd64.deb && sudo add-apt-repository ppa:webupd8team/sublime-text-3 && sudo apt-get update && sudo apt-get install sublime-text-installer && wget [https://dl.google.com/linux/direct/google-talkplugin_current_amd64.deb](https://dl.google.com/linux/direct/google-talkplugin_current_amd64.deb) && sudo dpkg -i google-talkplugin_current_amd64.deb

---

### Post by Habitual on 2013-11-14
you may wish to save your sanity and try one of these methods:
[http://askubuntu.com/questions/9135/best-way-to-backup-all-settings-list-of-installed-packages-tweaks-etc](http://askubuntu.com/questions/9135/best-way-to-backup-all-settings-list-of-installed-packages-tweaks-etc)
or
[http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)
or
[http://askubuntu.com/questions/122505/how-do-i-create-completely-unattended-install-for-ubuntu](http://askubuntu.com/questions/122505/how-do-i-create-completely-unattended-install-for-ubuntu)

---

### Post by oldfred on 2013-11-14
I found I was doing a lot of the same things with many installs.
But I copied command from history into a bash file and then just execute the bash file.
I started off simple with just a few commands and it has grown as I learned how to do more things.

And I do as Habitual posted in using dpkg to list installed apps and in bash script run the reinstall from it.
List of apps must be in my same folder as script.

Lots of links on scripting in this thread
 [http://ubuntuforums.org/showthread.php?t=1893106](http://ubuntuforums.org/showthread.php?t=1893106)

 [http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)

You could even add your one liner as a bash script but better to make it mulple lines for ease of maintence.
If you copy to a NTFS partition it will lose ownership & permissions which you will have to reset to make it executeable.
Someone posted this, which I have modified for my use:
```

#!/usr/bin/env bash -x
# newinstall.sh
# -x adds debugging mode set +x or set -x

# Repositoires - Normally users have the first 4 enabled - main, universe, multiverse, restricted
# Check if we are on Ubuntu
if [ "$(lsb_release -is)" != "Ubuntu" ] ; then
    echo "This script is only intended to run on Ubuntu"
    exit 255
fi

# Check if we are root
if [ $UID -ne 0 ] ; then
    echo "Please run this as root!"
    exit 255
fi

# Get distro
distro=$(lsb_release -cs)

src=/etc/apt/sources.list
#save your original sources.list file.
echo "Backing Up The sources.list"
cp -i /etc/apt/sources.list /etc/apt/sources.list_backup

#this updates everything
apt-get update
apt-get upgrade
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade

#then add logic 
if [ $(uname -m) == 'x86_64' ]; then
# 64-bit
apt-get install w64codecs libdvdcss2
else
# 32-bit
apt-get install w32codecs libdvdcss2
fi

apt-get install dselect

apt-get update
apt-get dist-upgrade
# Finally, install all the packages from previous install
# must have saved ubuntu-files from previous install to this directory
dpkg --set-selections < ubuntu-files
#dselect
apt-get -y update
apt-get dselect-upgrade
```

      
 make it executable
chmod +x newinstall.sh

---

### Post by Habitual on 2013-11-14
good one, oldfred!
There's also such popular topics as 'preseeding' and "off-line repositories".

but save that for another day. :)

---

