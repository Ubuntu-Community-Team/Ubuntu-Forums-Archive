---
title: "graphics failure, on restart"
date: 2015-09-08
forum: General Help
---

### Post by jaxom98 on 2015-09-08
System asus p5k mobo

---

### Post by QIII on 2015-09-08
Hello!

Onboard graphics?  Dedicated graphics?  Manufacturer and model of GPU? What release of Ubuntu are you using?

What is the nature of the behavior you are seeing?  Black screen?  Artifacts?  Black screen with blinking cursor?

---

### Post by Bucky Ball on 2015-09-09
See third link in my signature. As QIII alludes to, we can't give you much help with so little information. :)

---

### Post by jaxom98 on 2015-09-09
I hit the wrong key and somehow posted the first line.I then used edit to add the rest of the post which went missing.

---

### Post by jaxom98 on 2015-09-09
2nd try
desktop custom build bought used. owned for 7
 years
Mobo asusP5k
Gpu nvidea geforce 8800gts
ram Gskill 4Gb
hdd WD20EZRX  2Tb
OS dual boot both 64 bit win7 ult/ edubuntu 12.04

I was trying to set num lock to start automaticlly so that I don't have to engage num lock manually when inputting password. The first attempt failed so I made a 2nd attempt and was restarting when I ended up with a black screen with a window showing an error message.
"The system is running in low-graphics mode"
Your screen graphics card and input device settings cannot be detected correctly. You will need to configure these yourself.
clicked ok (curser shows as an "x" ,not the usual arrow.
2nd window
What would you like to do?
run in low graphics mode for just one sesssion
reconfigure graphics
troubleshoot errror
exit to console login
3rd window (reached via "troubleshoot error")
review xserver log file    (need a translator, I can't read it)
review startup errors 
edit configuration file      
archive configuration and logs (click ok) 
4th window
    relevant configuration and logs have been saved to: /var/log/failsafeX-backup-150909113748.tar
                                             bug reports can submitted at [http://www.launchpad.net.ubuntu/](http://www.launchpad.net.ubuntu/).
click ok and back to 3rd window

---

### Post by Bucky Ball on 2015-09-09
> **jaxom98 said:**
> 
I was trying to set num lock to start automaticlly so that I don't have to engage num lock manually when inputting password. The first attempt failed so I made a 2nd attempt and was restarting when I ended up with a black screen with a window showing an error message.

How were you trying to do this (what did you do) and how did it fail the first time? What did you do differently the second time?

Did you try 'Reconfigure graphics'? Did you boot into the system in low graphics then check what was going on with the driver? Did you enable the appropriate driver in 'Additional Drivers' (when booted in low graphics mode), if there is a driver there for your card?

Finally, what driver were you using successfully and how did you install it?

---

### Post by QIII on 2015-09-09
We're not picking at you jaxom98!  :)

It's simply that the more we know, the better prepared we are to help.

---

### Post by Bucky Ball on 2015-09-09
> **qiii said:**
> we're not picking at you jaxom98!  :)

it's simply that the more we know, the better prepared we are to help.

+1. :)

---

### Post by jaxom98 on 2015-09-09
I understand that I am not being picked on.
This is the first time I have lost most of a post.

System is dual boot
Win 7 needed a driver update as the resolution was low/pixillated/bad colours and following the graphics driver update win7 is now running correctly.
This post is being done on win7 desk top.

BUT edubuntu12.04 is not running. It seems to boot correctly,but instead of going to login it black screens with the error messages as posted above.
How do I get past the black screen to get the log to find out what happened?
how do I get the system running enough to get in and repair things?
The  attempt to get numlock working at login was follows:
sudo apt-get numlockx
gksudo gedit /etc/lightdm/lightdm.conf
greeter-setup-script=/user/bin/numlockx on

I then restarted and got the black screen. I get to 3rd error message window (see 2nd try post) and then just go in circles.

---

### Post by jaxom98 on 2015-09-13
I think I tracked the culprint down.Someone else had the same trouble. There is an incompatibility in the greeter script.
Since I couldn't logon I tried an upgrade off a disk. I am nw running 14.04 Lts. This has solved the graphics problem, how ever there are some settings that did not transfer. There was a warning that some setting would be lost.
Thank you everyone for your help.

---

### Post by Bucky Ball on 2015-09-13
Good news and thanks for sharing. :)

---

