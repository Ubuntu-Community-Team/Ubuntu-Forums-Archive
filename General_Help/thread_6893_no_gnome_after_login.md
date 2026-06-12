---
title: "no gnome after login"
date: 2004-12-02
forum: General Help
---

### Post by mezrot on 2004-12-02
Have now done 2 installations of Ubuntu and same problem occurs.  I put in my login and password and after some text about free software and that I have mail, just this: myname@myname:~ $
I try what very little commands I know and can't get to a gui.  I've tried ls, startx, and some other things but a gui never comes up.  What to do? :confused:

---

### Post by electroglas on 2004-12-02
It sounds like you have a problem starting X automatically. It is probably a problem in your /etc/X11/XF86Config-4 file.

I booted on Knoppix and copied its XF86Config-4 file into the /etc/X11 directory. I did this from a Knoppix root terminal.


BTW - I am only a newbie, so you may want to wait for other answers...

---

### Post by Magneto on 2004-12-02
sudo gdm

can you post your system specifications please

what does control+F7 do?

if the screen is blank  press control+F1 to get back to your terminal

---

### Post by mezrot on 2004-12-02
System is Celeron366 with 128MB Ram and ATI3D Rage 2c onboard video, 3.2 GB hard disk, no idea about mobo.  
Ctrl+F7 does nothing.
I don't have a blank monitor but Ctrl+F1 didn't do anything either.

---

### Post by Magneto on 2004-12-02
can you attach or post the contents of /var/log/XFree86.0.log

---

### Post by mezrot on 2004-12-02
I have no idea how to do that or even where it is.

---

### Post by mezrot on 2004-12-02
Change my last reply...(I think)...
I did get to /var/log but when I did a dir command there was no entry for anything to do with XFree86.0.log.  I don't know for sure if I was in a root directory or just my user directory when I tried this.

---

### Post by Magneto on 2004-12-02
cd - change directory

ls  instead of dir 

ls -al  - will list all files in the current directory

pwd  - will tell you what directory you are in


cd /var/log

ls

nano -w XFree86.0.log

---

### Post by mezrot on 2004-12-02
Magneto, thnx for the inst.
Got to GNU Nano and there is nothing written there.

---

### Post by wallijonn on 2004-12-05
if you are at a # prompt, then

```

[COLOR=Red]cd /usr/X11R6/bin
sudo xf86config[/COLOR]

```

you will have to walk through a new XF86Config-4 configuration. 

Your mouse device is [COLOR=Green]/dev/input/mice[/COLOR]

Turn ON 3 button emulation even if you have 3 buttons on your mouse.

If you have an Intellimouse PS2 mouse the device is [COLOR=Green]ImPS2[/COLOR]. 

You should choose the 104 key keyboard. 

Take as many defaults as you can to try to get it into a workable X-Window state.

---

