---
title: "Diagnosis needed"
date: 2007-07-30
forum: General Help
---

### Post by toddpedlar on 2007-07-30
I have just purchased a new PC with Feisty Fawn installed; upon delivery and first bootup everything seemed fine - but on several occasions the computer seemed to freeze (could
have been the wireless Logitech Comfort Desktop failing to work, but I didn't investigate much).
On reboot, things came up fine; then it froze again, and the cycle was repeated.

On the next reboot, however, I was told there was a problem with one of the disk
partitions (/dev/sda7, not that that's important) and the boot sequence could not continue.
One of the options given was to run fsck manually to repair whatever problems there were.

Well that was a big mistake.  Next reboot, what comes up now is the following, after
the Ubuntu bootup screen has been spinning for 30 seconds or so.  The computer is
in a built in shell (ash), and I am told

/bin/sh: can't access tty; job control turned off

and the prompt is

(initramfs)

I'm stuck.  It seems there are a couple of possible hardware malfunctions here, but I
don't get what's happened.  I DON'T seem to be able to get into the setup program in 
order to switch the bootup drive to the CD, and do a reinstall and reformat (which is 
what I'm tempted to want to do)

Help?

Thanks,

Todd

---

### Post by ddrichardson on 2007-07-30
Where did you purchase it from and what support did they offer?

---

### Post by toddpedlar on 2007-07-30
They hadn't offered any support yet - i hadn't yet gotten through to them.  I had just
had the machine, along with two others, delivered on Friday.  

Anyway, I reinstalled the OS and all is well as far as I can tell.  I wonder if the 
fsck process overwrote critical space on the HDD... 

at any rate, case is closed (so far).

Todd

---

