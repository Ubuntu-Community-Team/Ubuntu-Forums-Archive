---
title: "Windows Virtual PC- Video Res."
date: 2006-08-13
forum: General Help
---

### Post by chris062689 on 2006-08-13
I booted up Xubuntu in my Virtual PC today, and come to find out.. this happens. ](*,) 

[IMG]http://img225.imageshack.us/img225/6294/glitchly6.png[/IMG]

Makes it kind of hard to work with, doesn't it?  ;)
I've tried adjusting settings, seems nothing I've tried will work.

Has this happened to anyone else in the past?  What can I do to make it select the right resultion?

---

### Post by Jud on 2006-08-13
I'm installing Ubuntu for this first time on Virtual PC tonight.  The same thing happened to me with the Alternate version.  I downloaded the Desktop version and followed the recommendations in this guide: [https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004]("https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004").  Unfortunately now I'm stuck on getting the sound set up correctly in VPC.  One good thing to note is you can play blackjack while its installing. :)

Good luck and hope this helps.

---

### Post by Jud on 2006-08-13
Link appears to not be working right now.

Here's what I did:
Set Virtual PC's RAM to 256MB
Mount Desktop version ISO
Run in safe graphics mode (it takes a while to load)
Double click install, proceed to play blackjack for about 20 minutes
Reboot the VPC
Hit ESC when GROB comes up
Run in recovery mode
cd /etc/X11
pico xorg.conf
scroll down to Section "Screen"
change DefaultDepth to 16
Ctrl-X, yes
logout

---

### Post by mrmagee2759 on 2006-11-05
[FONT="Tahoma"][FONT="Trebuchet MS"]if you want to use the alternate install disk then all you have to do is reset, go to the initial screen and look at the bottom of the screen where it says VGA. Push the corrosponding button and select 600x800x16. The virtual pc window should resize and you can go through the install process.


I was faced with another problem. On one of the steps it says that it failed to mount the cdrom drive. It says I should reinsert the cd but im working off an iso image and it should work. If anyone can help me it would be great.[/FONT][/FONT]

---

### Post by mrmagee2759 on 2006-11-05
[COLOR="Lime"]Oh wait, this was in UBUNTU not XUBUNTU but it may be the same[/COLOR]

---

