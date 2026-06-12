---
title: "I've lost my panels!"
date: 2008-05-22
forum: General Help
---

### Post by mac9416 on 2008-05-22
I have had two installations go haywire. Three things have happened on both installs:
1) My desktop appearence changes. It seems to have switched to XCFE because I have the XCFE wallpaper and icons
2) I lost both of my panels: top and bottom. Boom! gone. I can launch apps using alt-f2 but I can't remember the commands for every program.
3) Everything seems very slow. I click alt-f2, go get a cup of coffee, and seconds after I get back the dialog finally pos up. Same when launching apps.

I am using a third install to tide me over and I have little hope of getting either back.

Can someone shed a little light on the situation?

---

### Post by Sam Lars on 2008-05-22
Do you have XFCE installed?
Try running
```
killall gnome-panel
```
in a terminal or the run dialog.  You could also try just running gnome-panel.
If you run 
```
top
```
in a terminal, does it give you any clue as to what is slowing the computer down?  Do you know if it's based on hard drive or processor usage?

---

### Post by HermanAB on 2008-05-22
Yup, that is a known bug which has been around for more than a year.  The easy way to fix things, is to create a new user account.  The best way to permanently fix things, is to install Gnome or KDE and forget about Xfce.  Xfce is nice when it works, but worse than Windows ME in terms of relibility...

---

### Post by Peedjay on 2008-05-22
Hello 
seems there are two of us! I've lost my panels to! Top nor bottom bar are visible anymore. Just out of the blue after an update a few days ago. I can only open the icons that are already there on my desktop. Creating a new launcher doesn't work, and ALT + F2 for opening a terminal neither. Other changes to desktop e.g. background are still possible.
I've tried already some things:
- reconfiguring xserver: blocks after a few steps with a postint warning that I'm working on a possibly-customised xconf
- reinstalling nautilus (as mentioned in another thread [http://ubuntuforums.org/showthread.php?t=734143):](http://ubuntuforums.org/showthread.php?t=734143):) most recent version installed so no progress here.

Does someone have an explanation/solution for this? Any help would be greatly appreciated.

Thanks
Peedjay

----------------------------------------------------------------
System: ASUS F3SV, 2GB RAM, HD 180 GB, dual boot:Vista-Ubuntu Hardy Heron

---

### Post by AlbertTatlocksCap on 2008-05-23
Ok - i had the same problem immediately after some updates

Here is what I did ..

Ok - I posted this possible solutin in another thread but heer it is again



Ok - I had the same problem after a fresh install install of 8.04 onto a scsi disk (apparently it seems to affect scsi and USB devices)

I used this to get around it for now

CTRL+ALT+F1 (or CTRL+ALT+F2 if that doesn't work)

Login in text mode

sudo rm /tmp/.X0-lock

startx

It should then start up OK

Then set Automatic login by:

System>Administration>Login Window>Security and then check Automatic Login

Ok - this means that you can only login with one username and it will be automatic so no login window for password - but it works and I suspect/hope there will be a fix in the near future

Hope it helps

---

### Post by Peedjay on 2008-05-24
Solved!

Looking elsewhere I found that reinstalling gnome could help.
```
sudo apt-get remove ubuntu-desktop && apt-get install ubuntu-desktop
```
This presented me the warning that ubuntu-desktop was not installed. 
So just running the second part of the code gave me my top & bottom bars back!

---

