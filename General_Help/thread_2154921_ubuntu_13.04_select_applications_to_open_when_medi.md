---
title: "ubuntu 13.04 select applications to open when media player is detected ?"
date: 2013-06-16
forum: General Help
---

### Post by AgentZ86 on 2013-06-16
I want to be able to select which program opens when a media device is plugged in.

For example:
System Settings / Details / Removable Media / Music Player / Other Applications from the pulldown menu
I want to select an application that is not shown in this pulldown list ?

The applicating or program I want to select is a custom script.

Please advise

---

### Post by Shrek01 on 2013-06-17
System Settings -> Hardware -> Device Actions

and add your programs

---

### Post by stinkeye on 2013-06-17
Your post is tagged kubuntu but sounds like your using ubuntu.

Find your application's launcher in **/usr/share/applications**
Copy it to **~/.local/share/applications**
Drag the copied launcher from **~/.local/share/applications** and drop in a gedit window.
Look for an **Exec=** line and append with a space then **%U**

Eg
```
Exec=smplayer %U
```
Your app should now show up in "other application"

To revert just delete the launcher from ~/.local/share/applications

---

### Post by AgentZ86 on 2013-06-17
> **Shrek01 said:**
> System Settings -> Hardware -> Device Actions

and add your programs

Thanks, please reread my post I don't have the option I'm looking for in there
I need to add my script or program that I want

On 13.04 it's
System Settings / Details / Removable Media / Music Player / Other Applications
But there is not option to select custom or point to a different script or application except for what is listed there

---

### Post by AgentZ86 on 2013-06-17
> **stinkeye said:**
> Your post is tagged kubuntu but sounds like your using ubuntu.

Find your application's launcher in **/usr/share/applications**
Copy it to **~/.local/share/applications**
Drag the copied launcher from **~/.local/share/applications** and drop in a gedit window.
Look for an **Exec=** line and append with a space then **%U**

Eg
```
Exec=smplayer %U
```
Your app should now show up in "other application"

To revert just delete the launcher from ~/.local/share/applications

Yep I don't know why they retagged this as kubuntu I posted it as ubuntu.

Anyhow, I see the local/share/applications folder but I can't drag or write anything to that folder for some reason
So I copied my script to the applications folder with sudo cp
I see a symlink in that folder that says defaultlist which is a symlink to etc/gnome/list

I do not see a file called applications but only an applications folder

---

### Post by stinkeye on 2013-06-17
What's the application you want to use?

---

### Post by AgentZ86 on 2013-06-18
> **stinkeye said:**
> What's the application you want to use?

It's my own script I wrote that copies files to the media device automatically and is already executable but I wanted it to run on dection of the removable media device
I still want prompting like you would get but just wanted to add my own application or script to the list

I'm not sure I understand what you mean by applications's launcher.

I see the applications folder but no applications launcher, except for the default symlink I mentioned

---

### Post by stinkeye on 2013-06-18
> **AgentZ86 said:**
> It's my own script I wrote that copies files to the media device automatically and is already executable but I wanted it to run on dection of the removable media device
I still want prompting like you would get but just wanted to add my own application or script to the list

I'm not sure I understand what you mean by applications's launcher.

I see the applications folder but no applications launcher, except for the default symlink I mentioned
The files in **~/.local/share/applications** and **/usr/share/applications** are what I call launchers or .desktop files.
They are the same format in both locations except in /usr/share/applications they show the icon with no .desktop extension. (permission thing)

By default there is no **~/.local/share/applications** directory but when created, .desktop files placed in this directory will
override desktop files in **/usr/share/applications**

If it's a script you want in the list, make a .desktop file for it.
eg create the file in terminal with...
```
gedit ~/.local/share/applications/usb-copy.desktop
```
Paste in this....
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon=[COLOR="#EE82EE"]gnome-panel-launcher[/COLOR]
Name=usb-copy
Exec=[COLOR="#FF8C00"]/full/path/to/script[/COLOR] %U
Comment=usb copy script
```

[COLOR="#EE82EE"]Edit for the path to your own icon[/COLOR] if desired.
[COLOR="#FF8C00"]Edit using full path to your script[/COLOR]

Save the file and you should have a **usb-copy** that shows in the dash and other applications

---

### Post by AgentZ86 on 2013-06-20
Thanks for the replies.
This will help me with some other apps I want to write also until I learn how to make a daemon and use dbus in the future.

So when you say it will show in the dash and other applications great.
Will it be available in the list where you select which application starts when a removeable drive plugged in ?  

Thanks again

---

### Post by stinkeye on 2013-06-20
Yep.
Must use **%U** in the Exec line of the .desktop file as shown earlier.

---

### Post by AgentZ86 on 2013-06-20
cool I got it, and it's on the list but it does not start when I plugin any media device for some reason

The script is executable and is a pythons script. I'm fairly sure I have the full path correct and I used the entire path/file.py

---

### Post by AgentZ86 on 2013-06-20
> **stinkeye said:**
> Yep.
Must use **%U** in the Exec line of the .desktop file as shown earlier.

Yep I have that and I do see my item in the menu now
However it's not in the dash in fact the use-copy entry is there even though I edited the file again to get rid of that entry

And it does not autostart for some reason but I can click the file manually and it's executable for sure.
Wonder why it won't run

---

### Post by stinkeye on 2013-06-20
> **AgentZ86 said:**
> Yep I have that and I do see my item in the menu now
However it's not in the dash in fact the use-copy entry is there even though I edited the file again to get rid of that entry

And it does not autostart for some reason but I can click the file manually and it's executable for sure.
Wonder why it won't run
What's the Exec line in your .desktop file?

I tested with a bash script that sends to the notification bubble "MP3 player connected".
Works after choosing usb-copy as the application to use when I plug in my mp3 player or if I select "ask what to do" then choose usb-copy when media connected.

usb-copy also appears in nautilus as the application to use when opening to the music player.
Clicking on the usb-copy button(see pic), runs the bash script again.

The **~/.local/share/applications/usb-copy.desktop** file...
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon=gnome-panel-launcher
Name=usb-copy
Exec=/home/glen/scripts/desktop-test.sh %U
Comment=usb script
```

The **/home/glen/scripts/desktop-test.sh** script
```
#!/bin/bash

notify-send -i multimedia-player "Music Player connected"
# cp /home/glen/cptest.txt /media/glen/SANSA-CLIPP
```

Also worked to copy a test file when uncommenting the second command in the bash script.

---

### Post by AgentZ86 on 2013-06-21
[http://bpaste.net/show/khvCKc9wdJG9ju0f2ylE/](http://bpaste.net/show/khvCKc9wdJG9ju0f2ylE/)

Here is the script with the top liine which makes the script a clickable auto execute.
It's a python script not a bash script and it does work when clicking the file
So that could be part of my problem

As far as the name and comments go I assumed the name would be the name of the script or whatever I wanted. Does that part matter ? 

And my full path is 

> [Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon=gnome-panel-launcher
Name=usb_devices
Exec=/home/agent86/Documents/usb_devices %U
Comment=usb_devices

My script is no longer in any lists or applications anywhere for some reason. Not in the dash,applications menus, system settings etc.
I also duplicated exactly what you have here made it executable and can run the script which will copy files but is not found anywhere to select it to run for any reason or any menu 

Also I was not aware that you could use the full path of an mtp device in the same was as a usb devices. 
I could not find any such path for my sansa clip+ or Zen players
I would love to change my code to make it call the console to copy the files instead that would be much easier if I  new the path I could simply use the cp command as you did


My python script is just testing right now so it copies files to another folder currently and not really to the device itself until I can work out the mtp device topics some more.
Perhaps I should write a bash call instead this might make it easier to copy files to mtp since that is a problem with python with limited libraries for this.

Also when I simply use the console and type 
> cp /home/agent86/Documents/6_19_2013.flac /media/agent86/CREATIVE-ZEN
I get permissions issues says permission denied

Or this:
> cp /home/agent86/Documents/6_19_2013.flac /CREATIVE
Produces no errors or messages and returns to prompt but does not copy any files either.


In the mean time I do need to work out how to run an applications when the devices are detected too I'll play with your examples a little and see if I can figure out whats going on.
Thanks

---

### Post by stinkeye on 2013-06-21
Python and any sort of coding is beyond me except simple bash.
The reason I bought a sansa clip+ is it has the option of MTP or MSC in
settings > system settings > usb mode
It's set to **MSC**so I can use just like a flash drive and drag and drop files or copy to.
I believe the zen has the same option.

When set to MTP I can't even view the files on my sansa.
[ATTACH=CONFIG]244003[/ATTACH]


When set to MSC can browse like any other mounted drive.
[ATTACH=CONFIG]244004[/ATTACH]

---

### Post by AgentZ86 on 2013-06-22
> **stinkeye said:**
> Python and any sort of coding is beyond me except simple bash.
The reason I bought a sansa clip+ is it has the option of MTP or MSC in
settings > system settings > usb mode
It's set to **MSC**so I can use just like a flash drive and drag and drop files or copy to.
I believe the zen has the same option.

When set to MTP I can't even view the files on my sansa.
[ATTACH=CONFIG]244003[/ATTACH]


When set to MSC can browse like any other mounted drive.
[ATTACH=CONFIG]244004[/ATTACH]

Yeah I know about the msc mode.
Ok forget the media players for now I'll just use a usb flash drive to simulate this or I'll use the sansa clip + which I also have.
Shouldn't the usb device like a flash drive also activate the script ? 

I have created the exact script you have done and I still do not get the script item in any available application list on any part of ubuntu.

Strange because when I first did this with your instruction for usb-copy the item was there the very first time but is now gone
I see the files in the .desktop folder but no effect.
Now I can't create ANY items no matter what I call them. They are being created in the .deskop folder for sure.
But no application items in dash,system settings or right clicks to open etc etc.

I'll keep playing with it but I'm stumped

---

### Post by AgentZ86 on 2013-06-22
Ok I removed all the files and started over
Created a script with only this:
> #!/bin/bash

notify-send -i multimedia-player "Music Player connected"

It's executable and is in the lists.
I can manually run or click the script but it will not notify or run when anything is plugged in for some reason.
OUCH this is bugging me LOL

---

### Post by stinkeye on 2013-06-22
Doesn't work for me with a normal usb flash drive.
Only with the sanza when in MSC mode.

FYI this is my **~/.local/share/applications/mimeapps.list** file
It has an entry....[COLOR="#FF0000"]x-content/audio-player=usb-copy.desktop[/COLOR]
```
[Default Applications]
application/x-deb=gdebi.desktop
audio/x-vorbis+ogg=totem.desktop
audio/3gpp=totem.desktop
audio/ac3=totem.desktop
audio/AMR=totem.desktop
audio/AMR-WB=totem.desktop
audio/basic=totem.desktop
audio/flac=totem.desktop
audio/midi=totem.desktop
audio/mp2=totem.desktop
audio/mp4=totem.desktop
audio/mpeg=totem.desktop
audio/mpegurl=totem.desktop
audio/ogg=totem.desktop
audio/prs.sid=totem.desktop
audio/vnd.rn-realaudio=totem.desktop
audio/x-aiff=totem.desktop
audio/x-ape=totem.desktop
audio/x-flac=totem.desktop
audio/x-gsm=totem.desktop
audio/x-it=totem.desktop
audio/x-m4a=totem.desktop
audio/x-matroska=totem.desktop
audio/x-mod=totem.desktop
audio/x-mp3=totem.desktop
audio/x-mpeg=totem.desktop
audio/x-mpegurl=totem.desktop
audio/x-ms-asf=totem.desktop
audio/x-ms-asx=totem.desktop
audio/x-ms-wax=totem.desktop
audio/x-ms-wma=totem.desktop
audio/x-musepack=totem.desktop
audio/x-pn-aiff=totem.desktop
audio/x-pn-au=totem.desktop
audio/x-pn-realaudio=totem.desktop
audio/x-pn-realaudio-plugin=totem.desktop
audio/x-pn-wav=totem.desktop
audio/x-pn-windows-acm=totem.desktop
audio/x-realaudio=totem.desktop
audio/x-real-audio=totem.desktop
audio/x-s3m=totem.desktop
audio/x-sbc=totem.desktop
audio/x-scpls=totem.desktop
audio/x-speex=totem.desktop
audio/x-stm=totem.desktop
audio/x-tta=totem.desktop
audio/x-wav=totem.desktop
audio/x-wavpack=totem.desktop
audio/x-vorbis=totem.desktop
audio/x-xm=totem.desktop
x-scheme-handler/mailto=opera-browser.desktop
x-scheme-handler/http=opera-browser.desktop
text/html=opera-browser.desktop
text/xml=opera-browser.desktop
application/xhtml+xml=opera-browser.desktop
text/vnd.wap.wml=opera-browser.desktop
text/wml=opera-browser.desktop
application/x-mimearchive=opera-browser.desktop
application/mime=opera-browser.desktop
application/xml=opera-browser.desktop
application/rss+xml=opera-browser.desktop
application/rdf+xml=opera-browser.desktop
image/svg+xml=eog.desktop
application/x-opera-extension=opera-browser.desktop
x-scheme-handler/https=opera-browser.desktop
x-scheme-handler/ftp=opera-browser.desktop
video/ogg=opera-browser.desktop
image/webp=opera-browser.desktop
image/jpeg=eog.desktop
image/bmp=eog.desktop
image/gif=eog.desktop
image/png=eog.desktop
image/tiff=eog.desktop
image/x-bmp=eog.desktop
image/x-ico=eog.desktop
image/x-png=eog.desktop
image/x-pcx=eog.desktop
image/x-tga=gthumb.desktop
image/xpm=gthumb.desktop
image/jpg=eog.desktop
image/pjpeg=eog.desktop
image/x-gray=eog.desktop
image/x-icb=eog.desktop
image/x-portable-anymap=eog.desktop
image/x-portable-bitmap=eog.desktop
image/x-portable-graymap=eog.desktop
image/x-portable-pixmap=eog.desktop
image/x-xbitmap=eog.desktop
image/x-xpixmap=eog.desktop
image/svg+xml-compressed=eog.desktop
image/vnd.wap.wbmp=eog.desktop
inode/directory=nautilus.desktop
application/x-gnome-saved-search=nautilus.desktop
audio/vorbis=totem.desktop
audio/x-adpcm=totem.desktop
audio/x-mp2=totem.desktop
video/avi=totem.desktop
video/mp4=totem.desktop
video/flv=totem.desktop
video/x-ms-wmv=totem.desktop
video/x-ogm=totem.desktop
video/x-theora=totem.desktop
image/x-xcursor=gedit.desktop
video/x-sgi-movie=totem.desktop
video/mpeg=totem.desktop
[COLOR="#FF0000"]x-content/audio-player=usb-copy.desktop[/COLOR]

[Added Associations]
application/x-deb=gdebi.desktop;
application/x-sqlite3=gedit.desktop;
audio/ac3=totem.desktop;totem.desktop;
audio/mp4=totem.desktop;totem.desktop;
audio/mpeg=totem.desktop;rhythmbox.desktop;clementine.desktop;totem.desktop;
audio/mpegurl=totem.desktop;totem.desktop;
audio/ogg=gedit.desktop;opera-browser.desktop;
audio/vnd.rn-realaudio=totem.desktop;totem.desktop;
audio/x-flac=totem.desktop;rhythmbox.desktop;
audio/x-matroska=totem.desktop;totem.desktop;
audio/x-mp3=totem.desktop;totem.desktop;rhythmbox.desktop;
audio/x-mpeg=totem.desktop;rhythmbox.desktop;
audio/x-mpegurl=totem.desktop;totem.desktop;rhythmbox.desktop;
audio/x-ms-wma=totem.desktop;totem.desktop;
audio/x-pn-realaudio=totem.desktop;totem.desktop;
audio/x-scpls=totem.desktop;totem.desktop;rhythmbox.desktop;
audio/x-wav=totem.desktop;totem.desktop;
audio/x-vorbis=totem.desktop;totem.desktop;
text/html=opera-browser.desktop;
text/xml=opera-browser.desktop;
application/xhtml+xml=opera-browser.desktop;
text/vnd.wap.wml=opera-browser.desktop;
text/wml=opera-browser.desktop;
application/x-mimearchive=opera-browser.desktop;
application/mime=opera-browser.desktop;
application/xml=opera-browser.desktop;
application/rss+xml=opera-browser.desktop;
application/rdf+xml=opera-browser.desktop;
image/svg+xml=opera-browser.desktop;gthumb.desktop;eog.desktop;
application/x-opera-extension=opera-browser.desktop;
x-scheme-handler/https=opera-browser.desktop;
x-scheme-handler/ftp=opera-browser.desktop;
video/ogg=opera-browser.desktop;
video/webm=opera-browser.desktop;
image/webp=opera-browser.desktop;
image/bmp=gthumb.desktop;eog.desktop;
image/gif=gthumb.desktop;eog.desktop;
image/png=gthumb.desktop;eog.desktop;
image/tiff=gthumb.desktop;eog.desktop;
image/x-bmp=gthumb.desktop;eog.desktop;
image/x-ico=gthumb.desktop;eog.desktop;
image/x-png=gthumb.desktop;eog.desktop;
image/x-pcx=gthumb.desktop;eog.desktop;
image/x-tga=gthumb.desktop;
image/xpm=gthumb.desktop;
application/octet-stream=file-roller.desktop;gedit.desktop;
x-scheme-handler/mailto=thunderbird.desktop;opera-browser.desktop;
image/jpg=eog.desktop;
image/pjpeg=eog.desktop;
image/x-gray=eog.desktop;
image/x-icb=eog.desktop;
image/x-portable-anymap=eog.desktop;
image/x-portable-bitmap=eog.desktop;
image/x-portable-graymap=eog.desktop;
image/x-portable-pixmap=eog.desktop;
image/x-xbitmap=eog.desktop;
image/x-xpixmap=eog.desktop;
image/svg+xml-compressed=eog.desktop;
image/vnd.wap.wbmp=eog.desktop;
image/x-xcursor=gedit.desktop;shotwell.desktop;gthumb.desktop;gimp.desktop;
application/x-shellscript=gedit.desktop;file-roller.desktop;
application/x-font-ttf=gnome-font-viewer.desktop;file-roller.desktop;
text/x-python=gedit.desktop;
video/x-ms-wmv=totem.desktop;
text/plain=eog.desktop;truecrypt.desktop;
audio/x-vorbis+ogg=totem.desktop;totem.desktop;
video/x-ogm+ogg=totem.desktop;
video/avi=totem.desktop;
video/mp4=totem.desktop;
video/flv=totem.desktop;
video/quicktime=totem.desktop;
video/vnd.rn-realvideo=totem.desktop;
video/x-matroska=totem.desktop;
video/x-ms-asf=totem.desktop;
video/x-msvideo=totem.desktop;
video/x-ogm=totem.desktop;
video/x-theora=totem.desktop;
application/x-tar=nautilus.desktop;gedit.desktop;
video/x-sgi-movie=totem.desktop;
video/mpeg=totem.desktop;
x-content/audio-player=vlc.desktop;
```

What I have noticed is the **x-content/audio-player=usb-copy.desktop** line remains after 
changing the removable media settings back to "never prompt or start programs"
So when inserting the sanza clip nothing is run but can be run from the **usb-copy** button in nautilus.
[ATTACH=CONFIG]244027[/ATTACH]

---

### Post by AgentZ86 on 2013-06-22
I actually tried it with the sansa clipp plus and it works well

I had assumed that it would run with other devices also
Other mtp device like Zen seem to run rhythm box etc.

Anyhow thanks

---

### Post by AgentZ86 on 2013-06-23
One last think on this

The sansa clip path says home/user/sansa clip

However this directory is not accessible and when using the ls command I get this

No such file or directory

Strange I can cd /media/agent86
then ls and see the directories for my flash drive and sansa clip

But if I cd DE30-94A7 works perfectly for the flash drive

If I cd sansa clip it says no such file or directory

I can't really access the sansa disk and do not appear to know what the real rull path is.

This is a separate topic really but related to this media player
I have no idea why I can't asccess is in msc mode this way from the commandline
Please advise


P.S
My stupid python script when running it manually does access the sansa clip using path 
Dir4 = "/media/agent86/sansa clip/"

This is a variable I made in my python script but it copies files with shutil and works with this path but copies very slowly
I was going to change this and simply use a simply bash as you outlined here but I can't figure out the path for my sansa clip

---

### Post by stinkeye on 2013-06-23
Are you quoting the path because of the space used in **sansa clip** ?

---

### Post by AgentZ86 on 2013-06-23
> **stinkeye said:**
> Are you quoting the path because of the space used in **sansa clip** ?

yes, but also when I cd to the location of the /media/agent86 and then ls I can see the directories shown. One directory is the sansa clip with a space.
The other is the flash drive. I can cd to the flash but not to the sansa clip. So I basically cannot cd into that directory whatever that directory really is.

And here is the bash script I'm attempting to use to run the python script not really relevent but anyhow.

bash script:
> [http://bpaste.net/show/VPz9P4uxn4eSzv5mXO3l/](http://bpaste.net/show/VPz9P4uxn4eSzv5mXO3l/)

python script here:
> [http://bpaste.net/show/baQ0mcuxoqJAyG7Lj9Do/](http://bpaste.net/show/baQ0mcuxoqJAyG7Lj9Do/)

The python script runs when I run the bash script manually with either of these commands:
bash usb-copy.sh
or
sh usb-copy.sh

But when the usb device is plugged I get the notify part and the python script does not run.

I would be happy either way, either cp commands or the python script or both.
Thanks


P.S
The strangest thing is that the python script uses the same path. The one I expect it to use when I open the device and press ctrl+l to see the path bar.

---

### Post by stinkeye on 2013-06-23
Don't know????
Works here.
I did label the sansa clip I think, a couple of years back using mlabel.
[https://help.ubuntu.com/community/RenameUSBDrive#FAT16_and_FAT32](https://help.ubuntu.com/community/RenameUSBDrive#FAT16_and_FAT32)

---

### Post by AgentZ86 on 2013-06-25
I found out why, thanks

[http://ubuntuforums.org/showthread.php?t=2157446](http://ubuntuforums.org/showthread.php?t=2157446)

---

### Post by stinkeye on 2013-06-25
> **AgentZ86 said:**
> I found out why, thanks

[http://ubuntuforums.org/showthread.php?t=2157446](http://ubuntuforums.org/showthread.php?t=2157446)

Oh ok.
I thought you said you were quoting the path because of the space in the name?
Goodluck.

---

