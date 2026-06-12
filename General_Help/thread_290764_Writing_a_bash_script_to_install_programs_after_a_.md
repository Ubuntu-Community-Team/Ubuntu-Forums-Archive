---
title: "Writing a bash script to install programs after a fresh install"
date: 2006-11-01
forum: General Help
---

### Post by ThrobbingBrain66 on 2006-11-01
I got to thinking today that I could save a lot of time during a fresh install if I made a bash script of all the programs i need to install (gnomebaker, bluej, vlc, frostwire, just to name a few) and all the other tweaks/fixes I need to do (deleting the totem plugins from the firefox folder, for example).

Most of the programs I need are in the repos, but some are not. So I'll need to know how to pull them from both places.

The problem is that I don't know anything about bash scripting.

help?

---

### Post by matthewstory on 2006-11-01
this is easy enough.  For your purposes all you really need to know is that you can run any terminal command in a bash script.  So for the stuff in the repos just install with aptitude:

aptitude install <packages> -y

The -y will send yes to apt for all the "are you sure" so that you don't have to sit there and type yes every couple of minutes.

For stuff that's not in the repos use wget to download it:

wget <URL>

and then you'll have to run all the other stuff you'll need in the script, tar, make, make install, etc.

The first line of the script needs to be:

#!/bin/bash

and save the file as <filename>.sh

then you run it (with sudo of course) like so:

sudo ./<filename>.sh

assuming your PWD is the same as the directory that holds the file, otherwise:

sudo /path/to/<filename>.sh

If you need any more help just ask.

---

### Post by ianmacgregor on 2006-11-01
> **ThrobbingBrain66 said:**
> I got to thinking today that I could save a lot of time during a fresh install if I made a bash script of all the programs i need to install (gnomebaker, bluej, vlc, frostwire, just to name a few) and all the other tweaks/fixes I need to do (deleting the totem plugins from the firefox folder, for example).

Most of the programs I need are in the repos, but some are not. So I'll need to know how to pull them from both places.

The problem is that I don't know anything about bash scripting.

help?

Here is a copy of one of the master scripts that I run just after a fresh install.. saves a lot of work I pruned down the list of apps it installs to just two to give you an idea of the syntax - and my original script lists tons of apps:

```

#!/bin/bash
#
# This script is the first in a series of setup scripts for gnome

# Check for admin rights. If user is not an admin user, exit the script
if [ $UID != 0 ]
then
   echo "You need to be root to run this script! Exiting.."
   exit
fi

# Update the system sources and software
aptitude clean
aptitude update
aptitude upgrade
aptitude dist-upgrade
aptitude clean

# Install some desired software
# Any number of apps can be listed for install here, but
# they must be seperated by a space and the whole thing
# needs to be one single line
aptitude install firestarter numlockx

# Cleanup after install
aptitude clean

exit

```You can, however, change all instances of 'aptitude' to 'apt-get' and accomplish the same thing.

---

### Post by ThrobbingBrain66 on 2006-11-01
thanks for the help guys.  here is my script...id appreciate it if someone could proof-read it for me.  thanks

```
#!/bin/bash

## Replace system files
cp ~/Desktop/documents/backups/xorg.conf_beryl /etc/X11/xorg.conf

cp ~/Desktop/documents/backups/sources.list /etc/apt/sources.list

cp ~/Desktop/documents/backups/menu.lst /boot/grub/menu.lst

## Add repo keys
gpg --keyserver subkeys.pgp.net --recv 1135D466
gpg --export --armor 1135D466 | sudo apt-key add -

wget http://www.beerorkid.com/compiz/quinn.key.asc -O - |sudo apt-key add -

## Install applications
aptitude install firestarter gnomebaker localepurge deborphan libdvdread3 libdvdcss2 vlc beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes gaim-extendedprefs gaim-guifications
flashplugin-nonfree sun-java5-jre sun-java5-jdk sun-java5-plugin w32codecs mplayer-nogui mozilla-mplayer mplayer-fonts msttcorefonts firefox-themes-ubuntu gstreamer0.10-ffmpeg gstreamer-fluendo-mp3 gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly -y

wget http://www.exaile.org/files/exaile_0.2.4_i386.deb
dpkg -i exaile_0.2.4_i386.deb
rm exaile_0.2.4_i386.deb

wget http://www.bluej.org/download/files/bluej-213.jar
java -jar bluej-213.jar
rm bluej-213.jar

wget http://www.frostwire.com/download.php?file=http://mirror1.peercommons.net/frostwire/4.10.9/FrostWire-4.10.9-2.i586.deb
dpkg -i FrostWire-4.10.9-2.i586.deb
rm FrostWire-4.10.9-2.i586.deb

## CD burning fix
cp ~/Desktop/documents/backups/15-local.rules /etc/udev/rules.d

chmod 4755 /usr/bin/cdrecord
chmod 4755 /usr/bin/cdrecord.mmap
chmod 4755 /usr/bin/X11/cdrecord.mmap
chmod 4755 /usr/bin/cdrdao
chmod 4755 /usr/bin/X11/cdrdao

## Sun Java Default
update-java-alternatives -s java-1.5.0-sun

## Remove Firefox's Totem plugins
rm /usr/lib/firefox/plugins/libtotem*
```

EDIT: I do realize that I forgot EXIT at the end.  so if you find any other errors, please let me know.

---

### Post by LenzM on 2006-11-01
> **ThrobbingBrain66 said:**
> 
cp ~/Desktop/documents/backups/menu.lst /boot/grub/menu.lst


This is not a good idea as the old boot menu will not include the new install.  All of the old installations should be automatically determined when you do a clean install, so this isn't necessary either.

---

### Post by ThrobbingBrain66 on 2006-11-01
I'm not sure if I follow what you're saying, but I have a seperate /home partition, so copying my backup files from there shouldn't be an issue.  I've done this many times before, just not with a script

EDIT: i see what youre saying now, but ubuntu is my only operating system so the mount points etc never change

---

### Post by LenzM on 2006-11-01
The new kernel is added to the boot menu during a fresh install, so your new install won't be in the old file (and it won't boot into the new install).

---

### Post by ThrobbingBrain66 on 2006-11-01
ahh, good call. thanks...any other errors you noticed?

also, the only reason i wanted to do that was so i could change the default timeout from 2 seconds to 0...can i do that with this script some other way?

---

### Post by ciscosurfer on 2006-11-01
@ianmacgregor,

> **ianmacgregor said:**
> Here is a copy of one of the master scripts that I run just after a fresh install.. saves a lot of work I pruned down the list of apps it installs to just two to give you an idea of the syntax - and my original script lists tons of apps:

```

#!/bin/bash
#
# This script is the first in a series of setup scripts for gnome

# Check for admin rights. If user is not an admin user, exit the script
if [ $UID != 0 ]
then
   echo "You need to be root to run this script! Exiting.."
   exit
fi

# Update the system sources and software
aptitude clean
aptitude update
aptitude upgrade
aptitude dist-upgrade
aptitude clean

# Install some desired software
# Any number of apps can be listed for install here, but
# they must be seperated by a space and the whole thing
# needs to be one single line
aptitude install firestarter numlockx

# Cleanup after install
aptitude clean

exit

```You can, however, change all instances of 'aptitude' to 'apt-get' and accomplish the same thing.

I'd be very intereted in taking a look at your original script with everything listed.  Do you mind posting it here?  If not, can you PM me with it?

Thanks,
Curious (ciscosurfer) :D

---

### Post by LenzM on 2006-11-01
You might want to back up your old sources.list and xorg.conf
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bu
cp /etc/apt/sources.list /etc/X11/xorg.conf.bu

```
Other than that everything looks like it should work fine.

---

### Post by matthewstory on 2006-11-01
> **ThrobbingBrain66 said:**
> 

also, the only reason i wanted to do that was so i could change the default timeout from 2 seconds to 0...can i do that with this script some other way?

This is gnarly complicated but yes there is a way:

grepvar=^timeout
cp /boot/grub/menu.lst /boot/grub/menu.lst.orig
exec < /boot/grub/menu.lst
while read line
do
if echo $line | grep $grepvar &> /dev/null
then
echo "timeout    0" 1>> /boot/grub/menu.lst.new
else
echo $line 1>> /boot/grub/menu.lst.new
fi
done
mv /grub/boot/menu.lst.new /grub/boot/menu.lst

This should work, though I havn't tested it, so if you use it, i'd check your menu.lst file very very carefully before you reboot.  I did run the grep to test, and the only line that should give "true" back from the grep is the timeout     2 line.

Hope this helps.

---

### Post by po0f on 2006-11-01
ThrobbingBrain66,

This sed command should edit /boot/grub/menu.lst for you replacing the timeout value, AND create a backup in /boot/grub/menu.lst~!  (BTW, it's 3 on my box):
```
# sed -i~ -e 's/^timeout\s*3$/timeout 0/' /boot/grub/menu.lst
```

[EDIT] Stupid grammar...

---

### Post by ThrobbingBrain66 on 2006-11-01
Thanks everyone for your help.  This is turning out much easier than i thought it would be.

---

