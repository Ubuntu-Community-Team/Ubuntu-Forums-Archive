---
title: "Log in problem......"
date: 2008-03-13
forum: General Help
---

### Post by Rodhill on 2008-03-13
I am using Ubuntu 7.10 and last night I was using the terminal window to get some sounds working.After inputing what was required it asked me to re-boot but I forgot to close the terminal window. After I rebooted everything looked ok until it wouldn't load the desktop. Instead it asked me to login  and put my password in (on a black screen) after I did that it just showed the normal prompt what you would see in the terminal window.
What should I input at that point to get it to load up properly?:confused:

Thanks

Rod

---

### Post by justleen on 2008-03-13
you probably had a terminal open, and where logged in as root.

If you then (in the grapical env.) shutdown or reboot as a user, it will shut down X to the terminal, since root is still logged on. Users are not allowed to stop root sessions.


If this happens, you can simply type "reboot" at the (root)prompt to reboot, or "shutdown now -h" to shutdown,

---

### Post by Rodhill on 2008-03-13
Thanks justleen I'll try that:) 

Regards

---

### Post by Rodhill on 2008-03-14
Hi justleen, I've tried to reboot but no luck. When it re-boots it shows the Ubuntu logo with the bar loading and just as it gets about a centimeter from the end the screen goes black and just shows some information on it and the command prompt:( I don't know how to get back into the system from here) I tried to get into the option for reload with minimal configeration but I can't make the keyboard work!
Any other suggestions?

Regards

Rod

---

### Post by danwood76 on 2008-03-14
When you login and get the command prompt does the following bring up the x environment:
```

startx

```

it might be that youve messed up the xorg.conf file and so X doest load.

if the above doesnt get the graphical environment up try doing
```

sudo dpkg-reconfigure xserver-xorg

```
and follow the onscreen wizard to reconfigue the x server.

---

### Post by Rodhill on 2008-03-14
> **danwood76 said:**
> When you login and get the command prompt does the following bring up the x environment:
```

startx

```

it might be that youve messed up the xorg.conf file and so X doest load.

if the above doesnt get the graphical environment up try doing
```

sudo dpkg-reconfigure xserver-xorg

```
and follow the onscreen wizard to reconfigue the x server.

I tried to configure the xserver and when all questions are answered it goes back to where I started!

I also have tried typing 'startx' and some information came up that said:-
Fatal server error:
no screens found
x10: fatal 10 error 104 (Connection reset by peer) on x server ":0.0"
after 0 requsests (0 known processed) with 0 events remaining.

After that is goes back to
rod@rod-desktop:~$

So are there any clues here as to whats wrong??:confused::confused:

---

### Post by Rodhill on 2008-03-14
I've just re-booted the pc and it says (on a black screen):-
<init: trying to resume from /dev/disk/by-uuid/2ab4e53c-5d60-45b5-9c96-f452efcca640
<init: no resume image, doing normal boot...

Ubuntu 7.10 rod-desktop tty1

rod-desktop login:

I cant go from here :(

Any help?

Rod

---

### Post by melvis02 on 2008-03-14
So at this point are you able to use your keyboard at all?  If you can use it, I'd try logging in normally which should pull you to the text side, then try 'sudo /etc/init.d/gdm restart' and hope that the bulletproof-x xorg configuration window pops up and allows you to reconfigure your screen.

Otherwise if you're not able to use your keyboard, one thing you might try is SSHing into your computer from another computer (i.e. from another computer on the same network, ssh <user>@<IP Address>, mine would be something like ssh melvis02@192.168.1.106).  That might at least give you the ability to work with your system again.

If you think your xorg.conf file might have gotten messed up, you might want to check your /etc/X11 directory to see if you have any old copies in there.  A lot of times I mess something up, and am able to copy an old version.  Usually you'll see something like an xorg.conf.0, and you can do a sudo cp xorg.conf.0 xorg.conf to restore the old version.

Just some thoughts, let us know what happens.

--Trey

---

### Post by danwood76 on 2008-03-15
It sounds like you may be setting the wrong graphics driver or the graphics driver is corrupt.
When you reconfigure the xorg.conf select the vesa driver, this driver will work with all graohics hardware and should hopefully give you a graphical login.

whats graphics card do you have?

---

### Post by Rodhill on 2008-03-15
I can type in ok at the commands - although because the keyboard is wireless it wont work if I press escape while booting up to access the boot choices. If I leave it to go to the black screen I then get the command inputs and I can type ok.

I have gone through this

[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg
[/COLOR]
about 5 times and it registers my graphics card correctly and also my monitor. I have deliberately put lower values of resolution etc so that it works. and when I get to the end it reads this:

[COLOR="Red"]<init: trying to resume from /dev/disk/by-uuid/2ab4e53c-5d60-45b5-9c96-f452efcca640
<init: no resume image, doing normal boot...

Ubuntu 7.10 rod-desktop tty1

rod-desktop login:[/COLOR]

I cant believe because I didnt close the terminal when I rebooted I would have had this trouble:(

Melvis 02 I'll try what you suggested although I wouldnt understand linking in another PC thats beyond my expertise!

Danwood76 I have a GForce FX5200 which the reconfigeration programme registers correctly as does the monitor. When it gets to the end of:-

[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg
[/COLOR]
it goes to the black screen command point what should I type in after that?

Rod

P.S many thanks to all who are trying to help me:)

---

### Post by danwood76 on 2008-03-15
Ive just realised your in run level 1. (tty1)
Try pressing ctrl + alt + F7 to switch to run level 6 which should be your graphical desktop.

---

### Post by Rodhill on 2008-03-15
Thanks Danwood76 I'm at work at the moment so I'll try this tonight [-o< Thanks very much - it's got to be something simple enough. I'll let you know later.

Regards

Rod

---

### Post by Rodhill on 2008-03-16
I can get into tty6 but not tty7:confused: I've just reloaded in tty1 the xorg info and it says after restarting:-

*Starting GNOME Display manager...  [OK]
rod@rod-desktop:~$

[COLOR="Red"]now what do I enter?
[/COLOR]

---

### Post by Rodhill on 2008-03-16
I've fixed it!):P Don't ask what I did but I ran the xorg again (done it probably 20 times) and was able to select tty7.

Thanks for all help from me

Rod

---

