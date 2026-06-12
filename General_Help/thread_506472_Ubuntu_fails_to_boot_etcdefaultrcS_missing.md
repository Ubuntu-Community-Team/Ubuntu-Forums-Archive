---
title: "Ubuntu fails to boot: /etc/default/rcS missing"
date: 2007-07-21
forum: General Help
---

### Post by manhinli on 2007-07-21
Hi everyone,

I have Ubuntu 7.04, and it was running quite well until it kept on popping up messages that I've used up 99-100% of my hard drive. I was really annoyed, and looked for programs to clean out my system.

I looked into "Add/Remove Apps" from the Ubuntu menu and found Kleensweep.

For the first run, I did select to backup to an archive to an external HDD that root DID have permission to do things in, and I only selected files that I thought were OK to clean out. Kleensweep bombed out at creating an archive, stating that there was an error during the archive process.

So the second time, I was in a hurry and was really annoyed as well, so I selected everything and didn't select the option to create an archive.

That was the most stupid thing I could have done.

5 hours later, I came back to shut down my computer. It just paused with a empty progress bar and after about 30 seconds this would appear:

```

.: Can't open /etc/default/rcS
error: 'etc/init.d/rc' exited outside the expected code flow.
init: rcS main process (XXXX) terminated with status 2

```

XXXX are some random numbers in the 2000 range

This error also appears everytime I start Ubuntu up.

I have tried to use the recovery mode and tried to run 'sudo apt-get coreutils', but it can't connect to the Internet.

I've screwed up the file with the boot script symlinks file.
Does anyone know of a way to recover it?

---

### Post by Daveth on 2007-07-21
well  if its any use this is mine

#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no

- you could try making a new one from it, though make a copy of your own, screwed as it may be! Alternatively, can you recover that file from the live cd?

---

### Post by manhinli on 2007-07-21
I'll try and see what copying does.

---

### Post by manhinli on 2007-07-21
With rcS copied over, the system does boot (to some extent), but stuff like basic networking and X server fail.

So, I'm planning on giving up and reinstall the system - and this time I won't screw up the init process.

---

### Post by trishacupra on 2007-09-11
Argh, did the same thing, got very similar errors.

Any other ideas other than reinstalling? I'd really rather not.

If I get it to boot up by trying to correct that file, any idea on how to get the Kleansweep archive (yeah, I did make one) to restore everything to it's proper place?

---

### Post by trishacupra on 2007-09-12
Well, I'm using the Live CD now to access my files. I have discovered that my Kleansweep archive has all the files I wiped in the folders they belong in, so I'm now copying them all back into the right spots - hundreds of them. Oh well, hope it works. 

I'll post the results - whether or not it works.

---

### Post by trishacupra on 2007-09-12
It worked. Phew, what a relief!

---

