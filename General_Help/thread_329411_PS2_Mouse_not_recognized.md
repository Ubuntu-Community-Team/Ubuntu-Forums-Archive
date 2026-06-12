---
title: "PS/2 Mouse not recognized"
date: 2007-01-01
forum: General Help
---

### Post by mikemaggio on 2007-01-01
I am new to Linux. I just loaded Ubuntu on a PC yesterday but the Ps/@ mouse I have will not work. This box does not have USB so I have to use this kind of mouse. Any suggestions on how to get it to work?

Thanks,
Mike

---

### Post by ahaslam on 2007-01-01
It should work, please post your xorg.conf (/etc/X11/).

Tony.

---

### Post by mikemaggio on 2007-01-02
Hi Tony:

I checked the directory and the file doesn't exist.  What should I do?

Mike

---

### Post by scrooge_74 on 2007-01-02
> **mikemaggio said:**
> Hi Tony:

I checked the directory and the file doesn't exist.  What should I do?

Mike

The file exist if not you are not going to have a Xserver running

The file is in /etc/X11/xorg.conf

there is a line you are going to have to change 
in this line 
 Option          "Device"                "/dev/input/mice"

i had an old computer which needed it to say 
 Option          "Device"                "/dev/input/psaux"

With that  option you  should get your ps2 mouse running

---

### Post by mikemaggio on 2007-01-02
Thanks, but it doesn't exist.  How do I get it to exist?

---

### Post by scrooge_74 on 2007-01-02
Let see, do you have a working graphical enviroment? Or when starting it gave you a bunch of errors and a message tellling you the Xserver can't load?

The file in question if you installed Linux for a desktop version and not for a server is going to be in /etc/X11

log into your system and then do
cd /etc/X11
then do
sudo nano /etc/X11/xorg.conf

---

### Post by mikemaggio on 2007-01-02
Yes, I have a working graphical environment. 

I ran the commands and received the message "New File." As I said, the file doesn't exist.

---

### Post by scrooge_74 on 2007-01-03
I really don't want you to miss understand me or thinK I am making fun of you, but if you have a working GUI then you have an Xserver running and then you have an xorg.conf file.

So you need to check what you are doing or read a little more because everybody here is going to tell you that xorg.conf is located in /etc/X11, every time I do cd /etc/X11 and then ls the file is going to be there

---

### Post by ~LoKe on 2007-01-03
Let's make things easier.  Open up a terminal and type this:
```
cat /etc/X11/xorg.conf
```
Just copy and paste that.

**EDIT:** Wait, which release are you using?  I think older releases use XF86.

```
cat /etc/X11/XF86Config-4
```
or
```
cat /etc/X11/XF86Config
```

---

### Post by mikemaggio on 2007-01-04
OK. That did it. The file is XF86Config-4. So what should the entry be for the PS/2 mouse?

---

### Post by scrooge_74 on 2007-01-04
look for:

there is a line you are going to have to change
in this line
Option "Device" "/dev/input/mice"

i had an old computer which needed it to say
Option "Device" "/dev/input/psaux"

---

### Post by mikemaggio on 2007-01-05
I tried that. Now I can't boot into the desktop, only into command line mode.

---

### Post by scrooge_74 on 2007-01-05
Check the error messages, it is probably telling you it can't find your mouse and that will be the reason you can't log in.

Change back what you did, but you are in the right track, I don't remember if the Xfree86 file has the other options for mouse in there, in xorg.conf they have other options with the # comment in front.

---

### Post by mikemaggio on 2007-01-08
I gave up on this and am converting the box to a server. No mouse needed there.

Thanks to everyone for your help.

---

