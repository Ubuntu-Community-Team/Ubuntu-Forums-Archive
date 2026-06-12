---
title: "auto start gnome without GDM?"
date: 2007-09-09
forum: General Help
---

### Post by markp1989 on 2007-09-09
Im trying to get my linux box to boot up as fast as possible, and i have managed to get it down to 23 seconds, however,  i cannot get gnome to auto start, and have to type "startx" at each boot.

so u was wondering if anyone knew if anyone knows of a way to start gnome on boot up without having to use GDM??

---

### Post by kerry_s on 2007-09-09
hmm, i haven't used ubuntu for a long while. it uses upstart so i can't remember what you have to change on that. i can help you with the auto starting after you log in.

**gedit ~.bash_profile**
```

if [ -z "$DISPLAY" ] && [ $(tty) = /dev/tty1 ]; then
while true
do
startx --
sleep 5
done
fi
 
```

in debian, i use rungetty in /etc/initab, upstart is different in ubuntu, so you'll have to find and try for your self. the line looks like this->
**1:2345:respawn:/sbin/rungetty tty1 --autologin user**

"user" is your login name
you also have to install rungetty, it's not there by default(sudo apt-get install rungetty)

---

### Post by markp1989 on 2007-09-09
> **kerry_s said:**
> hmm, i haven't used ubuntu for a long while. it uses upstart so i can't remember what you have to change on that. i can help you with the auto starting after you log in.

**gedit ~.bash_profile**
```

if [ -z "$DISPLAY" ] && [ $(tty) = /dev/tty1 ]; then
while true
do
startx --
sleep 5
done
fi
 
```

in debian, i use rungetty in /etc/initab, upstart is different in ubuntu, so you'll have to find and try for your self. the line looks like this->
**1:2345:respawn:/sbin/rungetty tty1 --autologin user**

"user" is your login name
you also have to install rungetty, it's not there by default(sudo apt-get install rungetty)


that worked exactly is i wanted, i just added that text u gave me to the ~/.profile file and it worked perfectly THANKYOU!!

---

### Post by kerry_s on 2007-09-09
if you can find where to put the rungetty line you won't have to login at all, it will just go straight to the gui at start up. that's how i have mine setup.

---

### Post by markp1989 on 2007-09-09
> **kerry_s said:**
> if you can find where to put the rungetty line you won't have to login at all, it will just go straight to the gui at start up. that's how i have mine setup.

thats what i have mine doing now but i dont use rungetty, were would i put the line if i wanted to use rungetty?

---

### Post by kerry_s on 2007-09-11
> **markp1989 said:**
> thats what i have mine doing now but i dont use rungetty, were would i put the line if i wanted to use rungetty?

for you it would be> /etc/event.d/tty1 <cause ubuntu uses upstart. i use debian so it's /etc/inittab for me.
what are you using?

i just switched to mingetty, half the size of rungetty and faster.
also i'm using a new bash_profile setting that seems faster to me.

```
if [ `tty` = "/dev/tty1" ]; then
startx
fi

```

---

### Post by markp1989 on 2007-09-11
> **kerry_s said:**
> for you it would be> /etc/event.d/tty1 <cause ubuntu uses upstart. i use debian so it's /etc/inittab for me.
what are you using?

i just switched to mingetty, half the size of rungetty and faster.
also i'm using a new bash_profile setting that seems faster to me.

```
if [ `tty` = "/dev/tty1" ]; then
startx
fi

```

To do my auto login im using a tutorial i found on the internet (see attachments), which seems to work ok, so i think il leave it as it is.

thankyou for all your help

---

### Post by kerry_s on 2007-09-11
ahh, i see your using the old school method, i remember that.
[http://ubuntuforums.org/showthread.php?t=303319](http://ubuntuforums.org/showthread.php?t=303319)

---

### Post by gladstone on 2007-11-05
> **kerry_s said:**
> for you it would be> /etc/event.d/tty1 <cause ubuntu uses upstart. i use debian so it's /etc/inittab for me.
what are you using?

i just switched to mingetty, half the size of rungetty and faster.
also i'm using a new bash_profile setting that seems faster to me.

```
if [ `tty` = "/dev/tty1" ]; then
startx
fi

```

Hey, I've been trying to use this in Xubuntu. I'm guessing it uses the same /etc/event.d/tty1 file? 

Mine contains:

```

# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 38400 tty1
```

And I've added:
```

# respawn
# exec /sbin/getty 38400 tty1

1:2345:respawn:/sbin/mingetty tty1 --autologin user
```

But at boot, I'm getting an error regarding the  mingetty line.

---

### Post by siafok on 2007-12-15
try:

> respawn
#exec /sbin/getty 38400 tty1
exec /sbin/mingetty tty1 --autologin olaf

---

### Post by siafok on 2007-12-15
but of course your user name instead of "olaf", sorry :)

---

### Post by gladstone on 2007-12-15
Thanks, I'm now able to start XFCE4 without GDM!

Next thing I'm looking at is when I try to start something with "gksudo", I get what looks like a permission error. I can run "sudo" from terminal fine.

For example, if I want to start synaptic from the system menu, I get this error:

> Failed to run /usr/sbin/synaptic as user root:
Unable to copy the user's Xauthorization file

First I did this (from [http://ubuntuforums.org/showthread.php?t=303319](http://ubuntuforums.org/showthread.php?t=303319)):

> Now we want to fix a bug with startx, so->

```
gksu (your editor) /usr/bin/startx
```
We want to change line 131 to read->

```
xserverauthfile=$XAUTHORITY
```
This fixes a bug that keeps creating a new .xserverauth.#### on every boot.

Then this solution through google:

```
sudo cp /root/.Xauthority ~/
sudo chown username:group ~/.Xauthority
```

Is that a safe/secure method? Other [sources]("http://www.ocf.berkeley.edu/help/X_Windows_Env_HTML/security.html") ([and]("http://forums.whirlpool.net.au/forum-replies.cfm?t=538206&r=8419687#r8419687")) say to "generate" an Xauthority file, though I'm not sure how to do that?

---

