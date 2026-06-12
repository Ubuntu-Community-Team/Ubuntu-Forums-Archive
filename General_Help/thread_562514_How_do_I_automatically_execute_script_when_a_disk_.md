---
title: "How do I automatically execute script when a disk mounts?"
date: 2007-09-28
forum: General Help
---

### Post by math_penguin on 2007-09-28
Hi I would like to find a way to automatically execute a script when a disk is mounted. Does anyone know if this is possible? 

Here is what I want to do. I use the unison to utility to keep several working copies my current projects around so that they all stay in sync. I have done this with remote servers in the past, but now I want to do it locally with my laptop, an external hard drive and a flash drive. What I am hoping is that I can find a way for Ubuntu to run a script when I turn on the hard drive or plug in the flash drive (i.e. every time the drive is mounted.) The point is that these drives are not always plugged into the laptop, and that I would like to synchronize different paths depending on whether it was the hard drive or the flash drive that was mounted.

Thanks for any help or pointers.

-MP

---

### Post by geraldm on 2007-09-29
It is possible, although I do not have specific examples of how to.  Upon device discovery
an event is sent to the udev daemon, and the /etc/udev/rules.d/*.rules scripts are used
to handle the event, and start any program that is specified in the various rules scripts.
Look at those scripts, and read the various man pages for udev and that should give enough
information for a test.  It would be easier to look for a HOWTO, as someone else has 
probably done this, and there should be an easier way than trial and whatever.

Do not try to execute any long program, but keep the program to a very short script
(which could start another program and background it) as the event processing is held
up until the end of the script.

Gerald

---

### Post by math_penguin on 2007-09-29
Thanks this is what I was looking for. I had no idea which system service would be handling such events. Now maybe I can look for a howto or figure it out for myself. In any case I will post my solution here.

---

### Post by math_penguin on 2007-09-29
Found a thread that has been discussing this and I posted a nice solution there. Check it out:

[http://ubuntuforums.org/showthread.php?t=558413](http://ubuntuforums.org/showthread.php?t=558413)

---

