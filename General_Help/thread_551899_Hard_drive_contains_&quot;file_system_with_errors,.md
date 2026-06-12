---
title: "Hard drive contains &quot;file system with errors, check forced&quot;"
date: 2007-09-15
forum: General Help
---

### Post by chimerical_brio on 2007-09-15
I have two hard drives in my computer: I have my OS installed on one, which is device sda, and my home directory lives on sdb. It's worked perfectly until, on bootup, I was told that the file system on sdb1 has errors. Here's the message I got:

"/dev/sdb1 contains a file system with errors, check forced

i_blocks_hi for inode 15075883 (/henry/Media/Music/Gnutella/The Hives/The Hives -Barely Legal) is 512, should be zero

/dev/sdb1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (i.e., without -a or - options)
fsck died with exit status 4

*File system check failed.
A log is being saved in /var/log/fsk/checkfs if that location is writeable. Please repair the file system manually."

Then a maintenance shell is started, and I have no clue what to do. Nothing special is in /var/log/fsck/checkfs, just the error that's above. The one thing to note: when it shut down before this problem started, it got stuck at unmounting local file systems, so I had to turn it off manually. Any ideas?! Help, please!

As a side note, when logging into this maintenance shell, I'm told that apt-get is not installed. Also, my wireless adapter won't work either, even though I have ndiswrapper configured correctly. I have an ESSID specified in /etc/network/interfaces, but when I do "ifdown wlan0" and then "ifup wlan0", no ESSID shows up. Could these be related? HELP!

---

### Post by splintercellguy on 2007-09-15
At the maintenance shell, do what the prompt asks: type fsck, then Enter.

---

### Post by chimerical_brio on 2007-09-15
Wow, that was weird. I did fsck, did all the stuff asked of me for sdb1, and lo and behold...it worked!

But still, something went wrong, and I hate not knowing these things. So the question becomes, why did this happen? I haven't used that file (the song by the Hives, and there was another song) since I can remember. What would cause this?

---

### Post by splintercellguy on 2007-09-15
For some reason (perhaps an unclean shutdown) that particular portion of the filesystem was corrupted. When fsck performed its consistency check it detected this error.

---

