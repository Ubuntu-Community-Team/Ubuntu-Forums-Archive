---
title: "Can I Disable System Beep For Shutdown Warnings?"
date: 2006-12-03
forum: General Help
---

### Post by ixus_123 on 2006-12-03
My computer is in my bedroom & makes & the fan makes a fair old bit of noise. Sometimes I want to go to sleep before the computer has finished performing tasks so I use the shutdown command to shut it down on a timer

```
~$ sudo shutdown -h +45

```

Where 45 is the minutes.  This is really useful for me but it gives out a warning in the terminal & lets you know with a system beep from the computer speaker.

Is there a way to disable this beep just for shutdown? I don't want to disable it permanently as I like to have it for my email, start up & any error messages it might try & send.

Thanks

---

### Post by ankle on 2008-01-14
Me too - any ideas?

---

### Post by sofamensch on 2008-02-27
Well i found this in another post
> Disabling the system beep from the "Sound Preferences" settings doesn't guaranty that the system beep will be disabled. It's up to each application to check the global settings and to honor them. As you can see not every application does it.

The best way that I found to disable the system beep is to remove the kernel module that creates it. This has the advantage to turn off the PC speaker completely thats the speaker creating the beeps. It will work for all applications.

Execute the follow command in a terminal and try to see if you hear a beep:
sudo rmmod pcspkr

In order to always disable the speaker after each system boot add the following lines to the file /etc/modprobe.d/blacklist:

# No more beeps
blacklist pcspkr

[http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/]("http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/")

This if for really disabling it. The Shutdown tool (Upstart Package) has a -q feature for quite, but that does not work for me. Please check it?

---

### Post by ankle on 2008-04-06
I hadn't noticed the -q option: thanks, that should help. I'm also using [GShutdown]("http://gshutdown.tuxfamily.org/") now, which shuts down via GDM, avoiding the beeps.

---

