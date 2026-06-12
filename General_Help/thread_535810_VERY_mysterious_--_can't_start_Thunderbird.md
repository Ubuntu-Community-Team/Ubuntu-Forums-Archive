---
title: "VERY mysterious -- can't start Thunderbird"
date: 2007-08-26
forum: General Help
---

### Post by TimK65 on 2007-08-26
Hello everyone,

I'm new here and fairly new to Ubuntu, but I've been running Linux for about nine years.

I don't like the fact that the Thunderbird package for Ubuntu just upgraded from 1.5.0.12 to 1.5.0.13 (both seriously aged), so I downloaded a binary tarball from mozilla.com and installed it into /usr/local.

For some reason, it won't run. The "thunderbird" command calls the "run-mozilla.sh" script, which in turn executes the "thunderbird-bin" binary, which is the actual program. The output of

/usr/local/binary/thunderbird/thunderbird

is:

/usr/local/binary/thunderbird/run-mozilla.sh: 424: /usr/local/binary/thunderbird/thunderbird-bin: not found

The output of

ls -l /usr/local/binary/thunderbird/thunderbird-bin

is:

-rwxr-xr-x 1 root root 13486280 2007-07-28 20:09 /usr/local/binary/thunderbird/thunderbird-bin

So I don't get why the run-mozilla.sh script can't find a file that is obviously there (and equally obviously executable by world).

Any ideas? About the only thing I can think of is that I'm running 64-bit Ubuntu, and I don't recall whether this is a 32-bit or 64-bit Thunderbird that I downloaded, but that shouldn't matter, should it?

Thanks,
Tim Kynerd

---

### Post by Spr0k3t on 2007-08-26
Definitely check to see if the binaries are 64bit if you are running a 64bit setup.  Last time I tried to run a 32bit binary the application gave similar error messages about the file (the one I was launching) could not be found.

---

### Post by OzzyFrank on 2007-08-27
I'm pretty sure the command needs to be "mozilla-thunderbird". Try that.

---

### Post by TimK65 on 2007-08-29
The Thunderbird executable is 32-bit. There is no 64-bit version available for download at mozilla.com.

There is no "mozilla-thunderbird" file in the extracted folder. (I think this is something that changed between Thunderbird 1.x and 2.0.)

Thanks anyway. Looks like I'm basically just screwed, which sucks.

---

### Post by jrusso2 on 2007-08-29
your should be able to start thunderbird with the command ./thunderbird

---

### Post by OzzyFrank on 2007-08-29
You're not screwed if you uninstall it and reinstall the one that the rest of us use. I had no idea it was as dated as you say, but it works and it seems having the latest in this case is just not worth it.

---

### Post by Irihapeti on 2007-08-30
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

Irihapeti

---

### Post by OzzyFrank on 2007-08-30
WOW! **Ubuntuzilla** worked a treat! I was happy enough with the old Thunderbird, but this made updating it to the current version really simple. Works fine, but I've yet to look for new features. Thanks for the link!

---

### Post by nanotube on 2007-08-30
one note for using ubuntuzilla for 64bit users: audio notifications for new mail won't work. haven't been able to get to the root of that problem yet. so if you really want audio notifications, then use the iuculano repository (the other automatic method suggested in the help.ubuntu wiki link posted above).

---

### Post by Irihapeti on 2007-08-30
Nanotube:

New mail audio notification doesn't work on my 32bit setup either. And now that you mention it, neither did Iuculano's version. As it's not an issue for me, I've not bothered to look into it.

BTW, I run dual boot, and I found a curious error when using Iuculano's version after I'd updated my Windows Thunderbird: I was getting a "can't identify trusted website" error when getting mail from my (SSL) providers. Doesn't happen with the official Mozilla version, which is why I'm using that in preference to the repository. I just mention this in case someone else has the same problem.

Irihapeti

---

### Post by TimK65 on 2007-08-30
Because I was experiencing other problems with my 64-bit installation, I resorted to the simple expedient of installing 32-bit Ubuntu on this partition. Thunderbird runs fine now (unsurprisingly).

The main feature I want from the new version of Thunderbird is the display, at the bottom of the window, of what % of my quota I'm currently using on whatever mail server I'm looking at. It's extremely helpful, and the 1.5.x series doesn't have it.

Best,
Tim

---

