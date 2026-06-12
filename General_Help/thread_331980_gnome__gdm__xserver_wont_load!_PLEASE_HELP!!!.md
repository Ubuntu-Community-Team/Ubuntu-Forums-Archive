---
title: "gnome / gdm / xserver wont load! PLEASE HELP!!!"
date: 2007-01-05
forum: General Help
---

### Post by $teve on 2007-01-05
I just bought a GeForce FX5500 card, put it in the computer booted edgy and got the message about XServer not being able to start. I ran dpkg-reconfigure xserver-xorg and changed the settings to suit the card HOWEVER now whenever I try to start Ubuntu I get a message about some Server authorization error and telling me that /var/lib/gdm does not exist???

One other thing is that I can also no longer access apt-get/aptitude as it reports an error message; something to do with /var/lib/apt/ being locked (or more to the point it doesnt exist)??? 

Also I found that /var/lib has gone missing/dissappeared??? I cant even run dpkg-reconfigure xserver-xorg anymore because of this. 

I am really stuck :( ! Please anyone I would really appreciate help on this one! Thanks.

---

### Post by $teve on 2007-01-08
an update for anyone who is having this problem; my solution was to copy the /var/lib and /var/cache folders from my live cd onto my HD. This is easiest to do by booting ubuntu from the live cd, mounting the HD partition containing ubuntu (HDB1 in my case) copying the said folders from the cd to the corrosponding directories on the HD, then re-boot the machine without the live cd and proceed with the installation of the graphics card. 

This may not have been the ideal solution as I then had to do a dist-upgrade as the files on the cd are for 6.06 and I am running 6.10, however this was the best i could do by myself, and it worked!!! 

My system is restored but is now using my new graphics card. I even have beryl/xgl working!

As for why those folders (/var/lib etc.) went missing in the first place :confused: maybe someone could shed light on that

---

### Post by konungursvia on 2007-01-14
> **$teve said:**
> an update for anyone who is having this problem; my solution was to copy the /var/lib and /var/cache folders from my live cd onto my HD. This is easiest to do by booting ubuntu from the live cd, mounting the HD partition containing ubuntu (HDB1 in my case) copying the said folders from the cd to the corrosponding directories on the HD, then re-boot the machine without the live cd and proceed with the installation of the graphics card. 

This may not have been the ideal solution as I then had to do a dist-upgrade as the files on the cd are for 6.06 and I am running 6.10, however this was the best i could do by myself, and it worked!!! 

My system is restored but is now using my new graphics card. I even have beryl/xgl working!

As for why those folders (/var/lib etc.) went missing in the first place :confused: maybe someone could shed light on that

How do I copy the directories from the CD in terminal mode? I can't seem to do it (my head is still full of old Sun Solaris Unix commands and I can't seem to do it.) Can you give a very simple dummies version of how to do that?

---

### Post by acorey on 2007-01-17
I'm not sure about edgy but I had the same problem with dapper.
Oddly, I was able to startx from safe mode /root, but not my user account. 
After a lot of messing about I installed wdm (wings display manager) with synaptic. During installation a wizard popped up asking what my default window manager should be. I selected wdm and all was well upon reboot.

My problems started after trying to install beryl by following a wiki (genius move on my part).

I know this doesn't solve anything really. I guess it is more of a work around.

Good Luck!

---

### Post by bodhi.zazen on 2007-01-17
> **konungursvia said:**
> How do I copy the directories from the CD in terminal mode? I can't seem to do it (my head is still full of old Sun Solaris Unix commands and I can't seem to do it.) Can you give a very simple dummies version of how to do that?

boot the live CD

Open a terminal

Enter the following (assuming Ubuntu is on /dev/hda1, you will need to adjust if your ubuntu root is on an alternate partition :p )

```
sudo mkdir /media/ubuntu
sudo mount /dev/hda1 /media/ubuntu
sudo cp -R /var/lib/* /media/ubuntu/var/lib
```

You may need to :

sudo mkdir /ubuntu/media/var/lib

---

