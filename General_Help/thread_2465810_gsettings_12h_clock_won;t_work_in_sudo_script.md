---
title: "gsettings 12h clock won;t work in sudo script"
date: 2021-08-11
forum: General Help
---

### Post by KeepItSimpleStupid on 2021-08-11
Create foo.sh with the line

gsettings set org.gnome.desktop.interface clock-format 12h

in it. If you happen to be 12h then replace 12h with 24h

do a chmod +x foo.sh

bash foo.sh                    works
sudo bash foo.sh           doesn't work

the line is supposed to change the time format from am/pm to 24hr and vice versa.

---

### Post by monkeybrain20122 on 2021-08-11
Why is it necessary to use sudo? and why don you need a shell script to do that instead of just running it in the terminal?

---

### Post by KeepItSimpleStupid on 2021-08-11
Me: it hurts when I touch here.
Doc: Don;t touch there.

it's a config script and it installs some software as well.

---

### Post by monkeybrain20122 on 2021-08-11
It is a super bad idea to use sudo to access your $HOME's settings. There is a reason why sudo exists. If you sudo everything might as well just get rid of it. It is not "convenient" for a reason and for the same reason you don't login as root. sudo is useful but should be invoked only sparingly and only when it is absolutely necessary. There is a lot of abuse of sudo even on many online blogs and tutorials, possibly coming from a Windows mindset that you just click anything and "run as administrator" or not run at all.

---

### Post by KeepItSimpleStupid on 2021-08-12
Me: it hurts when I touch here.
Doc: Don;t touch there.

it's a config script and it installs some software as well.  

I'm running off the live CD, so it's everything I need.

Some of the things my config script does:
Sets time zone to NY
tries to set AM/PM
disables trackpad tapping
Sets KB delay to 500msIt did an arp entry for my printer.  Linux had trouble finding it.  It was probably an Ethernet cable.
It used to install flashplayer and Pepperflash - now not needed
[Firefox either needs VLC to be installed or I can use google chrome] to play some videos.
Now I have to make a symbolic link to the root of the file system.  e.g. /mnt and my /nas (networked attached storage)
[I know, I could put it somewhere else]
installs NFS
creates the mount directories
It ups the volume to 150%
Reminds me to:
Firefox: enable drm, where to save, update (now can't disable updates)
Adds libavcodec
Reminds me to Manually add  media.libavcodec.allow-obsolete to Firefox
The URLs for two Firefox add-ons
Search URL fix (so they copy without the Google nonsesnse)

I had a script to install google-chrome, but that's not posible either.
I don;t know how to "drop out of warp" (to a normal user) so to speak to finish the install.

It does some of this stuff and then checks if there is an Internet connection before continuing.

It's used once after I boot the live CD,  I have a small USB drive and a 5 TB NAS, but Ubuntu is running from a dvd.  I need a new computer.  Laptop preferred.  Virtual machine, dual boot would be nice.  I was thinking about Alienware Area 51, but that's not possible.    It has to be business class.  Now Windows 11 stuff just showed up/.

I don;t know how to install printers with a script.  I don;t know how to add Firefox defaults with a script.  I don;t know how to add firefox add-ins with a script.

The other problem that occurred with 12.04 LTS and the live CD is eventually, the keyboard starts getting unresponsive and then the mouse freezes. Part of that is a firmware issue.  I had another Toshiba laptop that I could do a control-alt-t and kill the offending process and go on my merry way.

It happens faster if I'm running google-chrome.  It happens faster if running videos.

Is there some way to detect "memory leaks"?

What i can say is upgrading from 12.04 LTS to 20.04 has been disapointing.

Why is **OK** on one side of the screen and **CANCEL** on the other?

Adding a printer is really messy?
The network dialog is messy as well.
Image viewer - another yuk.
Just printing is a mess. papersize and duplex

I should set /etc/papersize to letter.

---

