---
title: "Re-create &quot;/dev/dsp&quot; for current system configuration"
date: 2007-06-03
forum: General Help
---

### Post by mkoehler on 2007-06-03
Good morning,

       A little background on the situation to begin:  I've been running ubuntu for a year or so now, flawlessly.   Anyway, the other day I was playing around with the concept of trying to install new alsa drivers in order to make my sound blaster audigy 2 zs notebook soundcard to work (which unfortunately I think is broken).  I decided to give it a shot, and through the process of removing and installing items, I succeeded in breaking gnome.  Obviously easily fixed, I reinstalled gnome and logged on.  However (even after restarting), I've lost my "/dev/dsp" location, which as you may guess, makes many audio applications go haywire.  I searched the internet for a way to recreate "/dev/dsp", but I couldn't come up with any results.  If anyone could offer assistance, it would be appreciated.

Thanks.

---

### Post by jimbob on 2007-06-03
dsp is of course in the /dev/directory, here is the way it should look:

 crw-rw---- 1 root audio 14, 3 2007-06-03 08:01 dsp

It looks like it is a character device (crw-) so why don't you just re-create it?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by jimbob on 2007-06-03
Take a look in /dev/.static/dev

You should see (4) dsp devices in there.  Copy the /dev/dsp one into the /dev directory and see if that helps anything.

If you want to regenerate all the audio devices run /dev/MAKEDEV -v audio

This must be done as superuser.  Back things up first just in case.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by mkoehler on 2007-06-03
> **jimbob said:**
> Take a look in /dev/.static/dev

You should see (4) dsp devices in there.  Copy the /dev/dsp one into the /dev directory and see if that helps anything.

If you want to regenerate all the audio devices run /dev/MAKEDEV -v audio

This must be done as superuser.  Back things up first just in case.

Thanks, thiis response provided a temporary fix.  By trying to copy the directory, and then running MAKEDEV, a "workable" dsp is created until the computer is restarted.  Is it possible to make these changes permanent, so they aren't erased when I restart my computer?  Thanks!

---

### Post by jimbob on 2007-06-04
I'm sure there is but at the moment it is beyond my scope.

I believe these devices should be created at boot time by udev - why your system fails to do so is the problem that must be researched.

If I have some time later this afternoon I'll google about and see what I can find.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

