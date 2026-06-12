---
title: "Black Screen every other boot"
date: 2007-12-22
forum: General Help
---

### Post by jadymitchell on 2007-12-22
This is sort of a weird problem.  On every second boot, my display will be black.  I can see hear that the system is running, so it's not a crash.  Basically, the splash screen will run, complete, then I get the black screen, but I can hear the ubuntu login music going and it's obvious that the OS is running.  I have to hold down the power button on my Thinkpad T22, force a reboot, and then I get a normal startup.

I though this was a splash screen problem ([http://ubuntuforums.org/showthread.php?t=579684&highlight=boot+problem&page=4](http://ubuntuforums.org/showthread.php?t=579684&highlight=boot+problem&page=4)), but none of these procedures fixes the problem.  It will still happen even when the splash is disabled.

Any suggestions?

---

### Post by jadymitchell on 2007-12-23
bump...

---

### Post by peter_k on 2007-12-26
I've had this as well; it's not necessarily every boot though; sometimes it works a bunch of times in a row, and then sometimes I get the black screen.  Are you seeing any of the following, which I'm seeing:

1. Does your login screen stay the same resolution, or change?  I run my desktop at 1280x1024, and sometimes the login looks like 1280x768, sometimes 1024x768 (or possibly lower, I'm not sure) - there doesn't seem to be a correlation between the gdm resolution and whether I get a black screen.

2. Does bootup seem to take a pretty long time (say as opposed to Feisty)? 

3. When you do get to the desktop OK, do you ever get a message that gnome-settings-daemon failed to load?

Just trying to see how similar our problems are. 

I find it frustrating, as I really like Gutsy except for this issue; it seems pretty polished in comparison to Feisty and other distros - if this could get fixed, it would be as near to perfect as I would want.

---

### Post by danwood76 on 2007-12-26
are there any errors or warnings in your Xorg.0.log or Xorg.0.log.old?

Open a terminal and run these two:
cat /var/log/Xorg.0.log | grep '(EE)'
cat /var/log/Xorg.0.log | grep '(WW)'

and 

cat /var/log/Xorg.0.log.old | grep '(EE)'
cat /var/log/Xorg.0.log.old | grep '(WW)'

post the results of each please, in a code tag.

regards,
Danny

-- edit --

Forgot to say run these right after it does the black boot then a clean boot.

---

### Post by jadymitchell on 2007-12-27
Thanks for the replies!  Peter, no I don't have any of those symptoms.  The boot is normal each time, it's just that when the splash screen is finished, the monitor goes blank.  You are right, however, in that sometimes I can go 4 or 5 boots without the problem; it's not every other boot as it first seemed.   Danwood, here are the log results (they are the same whether there's been a clean or a blank boot):

```

CLEAN

cat /var/log/Xorg.0.log | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"

cat /var/log/Xorg.0.log | grep '(WW)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29

cat /var/log/Xorg.0.log.old | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"

cat /var/log/Xorg.0.log.old | grep '(WW)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29

BLANK

 cat /var/log/Xorg.0.log | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"

$ cat /var/log/Xorg.0.log | grep '(WW)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29

 cat /var/log/Xorg.0.log.old | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29


```

---

### Post by danwood76 on 2007-12-27
> **jadymitchell said:**
> Thanks for the replies!  Peter, no I don't have any of those symptoms.  The boot is normal each time, it's just that when the splash screen is finished, the monitor goes blank.  You are right, however, in that sometimes I can go 4 or 5 boots without the problem; it's not every other boot as it first seemed.   Danwood, here are the log results (they are the same whether there's been a clean or a blank boot):

```

CLEAN

cat /var/log/Xorg.0.log | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"

cat /var/log/Xorg.0.log | grep '(WW)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29

cat /var/log/Xorg.0.log.old | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"

cat /var/log/Xorg.0.log.old | grep '(WW)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29

BLANK

 cat /var/log/Xorg.0.log | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"

$ cat /var/log/Xorg.0.log | grep '(WW)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29

 cat /var/log/Xorg.0.log.old | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29


```

It looks like you have a couple of small problems in your xorg.conf, but nothing that would give a blank  screen on startup.
Seems strange, I dont think xorg is giving the error on startup though which narrows it down.

---

### Post by jadymitchell on 2007-12-28
Problem persists, is there somewhere other than xorg where I can look for troubleshooting purposes?

---

### Post by clayts450 on 2007-12-28
Woah, jady - how very weird. My T22 has also started doing this (blank screen after Ubuntu bar fills up).

It's probably because I was messing around with a few settings in my xorg.conf file this afternoon to try and speed Gutsy up a little - I've probably broken something system critical.

Having said that, my T22 is one of these Thinkpads which suffers from the blink of death (the only way to get the machine to boot as far as grub is to 'bend the motherboard' a bit) - see the Thinkpads forum for loads on that issue

[http://forum.thinkpads.com/viewforum.php?f=28](http://forum.thinkpads.com/viewforum.php?f=28)

Anyway, I've done  a search and have a couple of things to try - I'll let you know how they go (if they work).

Failing that, maybe all T22s are destined

---

### Post by clayts450 on 2007-12-28
just to finish off my sentence....

Maybe all T22s are destined to self destruct on 28 Dec 2007...

---

### Post by clayts450 on 2007-12-28
I managed to get back to some form of normality by opening in single-user mode (recovery mode) and once booted up I typed in

sudo dpkg-reconfigure xserver-xorg

and went through and rechecked all my settings. For some incredibly bizarre reason the system seemed to have changed to 1980x1024 (or something) as the screen resolution which is clearly wrong for a T22. I changed it to 1024x768, the correct setting, left everything else unchanged and now everything is running fine again - indeed I am running Ubuntu as I type this :)

Dunno how long it will last - my T22 is on its last legs, but I'm determined that Ubuntu will give it a new lease of life : I've been happily using it all this week instead of Windows 98SE and am very happy.

Anyway - give that a whirl and see what happens - hopefully your fault isn't something hardware related.

---

### Post by teldatakyle on 2007-12-28
Ya i have the same problem on my Dell Inspiron 1000, every once in a while when i boot up i can get to the splash screen, but after that the screen goes blank. Sometimes i can get it to work after pressing the multiple moniter button on the laptop, but that does not seem to work anymore. I can't boot up at all im on a windows machine right now. Any suggestions?

---

### Post by danwood76 on 2007-12-29
> **jadymitchell said:**
> Problem persists, is there somewhere other than xorg where I can look for troubleshooting purposes?

If you go System > Administration > System Log it will open up all the most common log files which you can search for errors (ctrl + f).

if you find any errors post them here, remember as with anything on linux its case sensetive so Error is not the same as error.

hope you find something useful,
Danny

---

### Post by danwood76 on 2007-12-29
> **teldatakyle said:**
> Ya i have the same problem on my Dell Inspiron 1000, every once in a while when i boot up i can get to the splash screen, but after that the screen goes blank. Sometimes i can get it to work after pressing the multiple moniter button on the laptop, but that does not seem to work anymore. I can't boot up at all im on a windows machine right now. Any suggestions?

That sounds like its defaulting to the second monitor, im not too sure about dual monitor setups but I think you can specify which monitor it boots too.

You could try setting the screen up to dual monitor, mirrored screen when you manage to boot in. This can be don in the screens and settings control panel in System > Administrate

regards,
Danny

---

### Post by teldatakyle on 2007-12-29
Ya i can't boot into ubuntu at all. So I think im going to have to just re-install.

---

### Post by jadymitchell on 2008-01-04
I thought I made this go away by reconfiguring xorg, but it came back.  A really annoying problem....

---

### Post by Jeztastic on 2008-01-14
Has anyone found a solution to this, as I am having the same problem.

---

### Post by jadymitchell on 2008-01-14
Nope, I'm afraid not.  I still get it - more or less- every other boot.  I worry about the effects on my computer of having having to hold down the power button to force a restart when this happens.

---

### Post by Jeztastic on 2008-01-15
> **jadymitchell said:**
> Nope, I'm afraid not.  I still get it - more or less- every other boot.  I worry about the effects on my computer of having having to hold down the power button to force a restart when this happens.

Yes, me too. My computer has also started to hang when entering BIOS every now and then, so I am having to force restart there too. 

One way to avoid holding down power button is to boot into recovery mode first, then type "halt" or "restart". I'm not sure if this is better than holding down the power button, but I suspect it is.

I am going to update to the realtime kernel soon, I will let you know what effect this has. 

What kind of graphics card do you have, and with what drivers? I have only really had this problem since trying to improve graphics handling.

---

### Post by jadymitchell on 2008-01-15
I'm glad there's someone else working on this!  Here's what I have: 

*-display
                description: VGA compatible controller
                product: 86C270-294 Savage/IX-MV
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 13
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-1.0 vga bus_master cap_list
                configuration: latency=64 maxlatency=255 mingnt=4

---

### Post by rahimveron on 2008-01-18
I too have the same problem, blank screen at GDM randomly.

On a side note: How can i change my GDM resolution to 1024x768 as it is currently at 800x600

---

### Post by Jeztastic on 2008-01-18
I switched to KDE and this problem has stopped happening (so far). However, I do get an error message whenever I boot about Composite Manager crashing. I suspect there might be a relationship there. 

This works for me, as I really am liking KDE. However, I am checking out about the problem here. [http://ubuntuforums.org/showthread.php?t=176806]("http://ubuntuforums.org/showthread.php?t=176806")

---

