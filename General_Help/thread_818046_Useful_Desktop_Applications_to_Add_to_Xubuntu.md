---
title: "Useful Desktop Applications to Add to Xubuntu"
date: 2008-06-04
forum: General Help
---

### Post by Tybion on 2008-06-04
This was originally submitted to the xubuntu-users mailing list, but I have added it here so that it is more easily found by other people not on the xubuntu-users mailing list.

I have been using Xubuntu in my home for a bit more than a year. I now have Xubuntu on all our PCs - my own and my 2 daughter's PCs. I chose the XFCE interface over GNOME and KDE for the usual reasons - it is simple and fast and will run nicely on any old PC or mini-laptop (eg. the Eee PC) when I eventually get to buy one. My thinking is that if I get familar with Xubuntu, I can use it EVERYWHERE, and not have to bother with Kubuntu or Ubuntu.

By design, though, the default Xubuntu install does not give you a fully-functioning desktop PC. You need to install a number of applications,  browser plugins and codecs. We have tested lots of applications to see which is the most suitable paint program, word processor, iPod manager, etc. for us.  I thought it might be useful to anyone new to Xubuntu to document the applications that we install. Note that I have scripted the install process as much as possible so that I don't have to re-do this manually on 3 PCs when I do a fresh install of the next version of Xubuntu.

GStreamer packages (codecs for different format video files) ..
gstreamer0.10-alsa
gstreamer0.10-ffmpeg
gstreamer0.10-gnomevfs
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-bad

More things for Web-browsing ..
REMOVE totem
flashplugin-nonfree
vlc
mozilla-plugin-vlc
Java run-time ..
sun-java6-bin
sun-java6-jre
sun-java6-plugin

xubuntu-restricted-extras (includes icedtea) ..
xubuntu-restricted-extras

Essential Simple GUI Program for looking at Hardware ..
gnome-device-manager

Xfce4 utilities (these might all be installed by default in hardy?) ..
xfce4-mixer
xfce4-mixer-alsa
xfce4-taskmanager
xfce4-cpugraph-plugin
xfce4-datetime-plugin
xfce4-netload-plugin
xfce4-systemload-plugin
xfce4-taskmanager
You then need to add these to the top panel and configure. Once you have configured these manually, you can copy all the config files in ~/.config/xfce4/panel/ to other PCs.

Ksnapshot - much more flexible than xfce4-screenshooter-plugin ..
ksnapshot
Add a launcher for this in the top panel, also.

a2ps - needed for Mousepad to print ..
a2ps

Load apps faster (?) ..
preload

OpenOffice ..
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-hyphenation
openoffice.org-impress
openoffice.org-style-human
openoffice.org-thesaurus-en-au
openoffice.org-writer
myspell-en-au

kolourpaint, gthumb and Gimp help files ..
kolourpaint - VERY similar to MS Paint - basic and easy to use
gthumb - Great little program for photos - brightening, cropping, removing red eye, etc.
gimp-help-en - With GIMP you need all the help you can get!
GIMP is a very scary program - but it is very good once you get used to it. The most important thing to understand is that it creates and removes LAYERS without you being aware. Make sure that you have the 'Layers Dialog' open so that you can see what layer is active - else you will get totally confused. I bought a book 'Beginning GIMP' by Akkana Peck - and this explained everything - heaps cheaper than buying a software license for PhotoShop.

Add a File Search in Thunar (good if this was done in the Xubuntu install) ....
gnome-utils
Now in Thunar, click Edit/Configure Custom Actions and add an item with the command -
gnome-search-tool --path=%f
Under the 'Appearance Conditions' tab, type * for 'File Pattern' and tick 'Directories'

Music Management ..

CD Player (this simple program will copy the sound tracks off an audio CD into .ogg files. You can then use GTKPod to translate these to .MP3s and copy to an iPod.) ..
goobox

And GTKPod (with packages that probably should be in the dependency list?) ..
gtkpod
  mp3gain
  lame
  flac
  vorbis-tools
We were ONLY using Banshee for a while, but then it didn't work with an iPod shuffle that we bought. GTKPod is more basic but seems to work more reliably with the hardware. GTKPod has less dependent packages, so it might be best to try GTKPod, and then only use Banshee if you want something fancier.

Banshee ..
banshee-1
podsleuth - required for iPod

For transferring photos from Cameras onto your PC ..
gtkam

Microsoft fonts ...
msttcorefonts

I use Samba for a shared folder area on our main PC, so we install the following on all PCs ..
smbfs
smbclient
pyneighborhood

For Bluetooth, I have also added the installation of -
gnome-bluetooth
bluez-gnome
We never got this working in Gutsy, but Hardy is nicely set up to recognise the Bluetooth hardware. A 'Bluetooth File Sharing' option is added under the 'Accessories' part of the menu. I created a Desktop icon that runs 'bluetooth-properties --singleton' to set Bluetooth transfer options.  We use this for transferring photos from a mobile phone to the PC.

Initially we installed VirtualBox for running a Windows XP session in. It runs very nicely and is very user-friendly. Although I still have it installed on a couple of PCs, we don't actually use it anymore - or very rarely.

I hope this is useful to some of you.

---

### Post by Bruce M. on 2008-07-12
Hi Tybion,

Wonderful stuff. Now for a couple of questions.

> **Tybion said:**
> This was originally submitted to the xubuntu-users mailing list, but I have added it here so that it is more easily found by other people not on the xubuntu-users mailing list.

Where do I find the mailing list?

> **Tybion said:**
> Note that I have scripted the install process as much as possible so that I don't have to re-do this manually on 3 PCs when I do a fresh install of the next version of Xubuntu.

Can you share the script?

> **Tybion said:**
> GStreamer packages (codecs for different format video files) ..
gstreamer0.10-alsa
gstreamer0.10-ffmpeg
gstreamer0.10-gnomevfs
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-bad

Will the above allow DVD's to play?

> **Tybion said:**
> More things for Web-browsing ..
REMOVE totem
flashplugin-nonfree
vlc
mozilla-plugin-vlc
Java run-time ..
sun-java6-bin
sun-java6-jre
sun-java6-plugin

Why remove totem?

> **Tybion said:**
> xubuntu-restricted-extras (includes icedtea) ..
xubuntu-restricted-extras

Why do xubuntu-restricted-extras twice?
What is icedtea?


> **Tybion said:**
> a2ps - needed for Mousepad to print ..
a2ps

I didn't know that mousepad couldn't print without these.
Interesting. Testing now ... how about that, blank pages...

> **Tybion said:**
> Load apps faster (?) ..
preload

Does this really work?

> **Tybion said:**
> OpenOffice ..
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-hyphenation
openoffice.org-impress
openoffice.org-style-human
openoffice.org-thesaurus-en-au
openoffice.org-writer
myspell-en-au

I don't use a wordprocessor more than 2 or 3 times a year so ABIWord is OK here. However I do a lot of text editing so I have added Gedit as I can't get Mousepad to edit multiple docs in the same window. My conky has 11 files to edit.

> **Tybion said:**
> Music Management ..

CD Player (this simple program will copy the sound tracks off an audio CD into .ogg files. You can then use GTKPod to translate these to .MP3s and copy to an iPod.) ..
goobox

Well, no wonder I could never find "CD Player" that I hear people talking about. **"goobox"** indeed!  :)

> **Tybion said:**
> I hope this is useful to some of you.

Perfect.
Have a nice day
Bruce

---

### Post by Tybion on 2008-07-12
Thanks, Bruce.

Just a 'couple' of questions? :)

> Where do I find the mailing list?
[https://lists.ubuntu.com/mailman/listinfo/xubuntu-users](https://lists.ubuntu.com/mailman/listinfo/xubuntu-users)

> Can you share the script?
Since I posted this thread I have created a Custom Install CD, so the scripting has changed a bit. I followed - [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization) - and updated the article when finished.  I have attached the script folder structure that is copied to the CD - setup.tar.gz - look at setup/install/settings.sh first.

I have also attached the common.seed file - this lists the extra packages that are installed.

I am happy to upload the .iso file if someone can give me an FTP server to copy it to.  (681 Megs - just small enough for a CD)

If you want to have a simple script that installs heaps of packages - do like so -

```
#!/bin/sh
INSTALL="sudo apt-get --yes install"
REMOVE="sudo apt-get --yes remove"
$INSTALL gstreamer0.10-alsa
$INSTALL gstreamer0.10-ffmpeg
```

> Will the above allow DVD's to play?
No - sorry, but I have a DVD player sitting on my TV. :)

> Why remove totem?
Maybe totem would be OK if I knew more about it?  Maybe I need to install extra packages to get it to work well?  But we found that VLC just worked, so I removed totem so that it wouldn't be the default app for anything.

> Why do xubuntu-restricted-extras twice?
Mistake :)

> What is icedtea?
I think it is basically an Open Source version of Java - but don't quote me.  I am not using it now, though - just using the SUN java stuff.

> Does preload really work?
Good question.  I really don't know if it makes any difference.  Anyone out there actually seen it make a noticeable difference?

---

### Post by Bruce M. on 2008-07-13
> **Tybion said:**
> Thanks, Bruce.

On the contrary, Thank you!

A while back a friend showed me a bash script files to reload all those files one has on their system that aren't part of the install.

```
#!/bin/bash

sudo aptitude install gedit gedit-plugins bluefish -y
```
My real one is actually quite long and got longer after reading your post.

Here's what I do:
[LIST=1]
[*]A clean install of Xubuntu.
[*] Get updates.
[*] Restore /home from backup.
[*] Run qinstall.sh
[/LIST]

Important to remember do not run any program until complete.

---

