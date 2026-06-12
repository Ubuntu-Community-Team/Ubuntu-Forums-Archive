---
title: "utf8 and filesystem panics"
date: 2007-01-27
forum: General Help
---

### Post by kabanta on 2007-01-27
My Edgy install occasionally "panics" and sets itself to read-only:

[17179811.736000] FAT: Filesystem panic (dev sda6)
[17179811.736000]     File system has been set read-only

The culprit seems to be a combination of utf8 and operations on certain music files. I have the following in fstab: iocharset=utf8 -- and a peek at dmesg after startup shows this:

[17179760.944000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

I choose utf8 because i deal with a lot of files that use different character sets. Perhaps this is the wrong logic on my part?

And I am not really sure what is causing the problems with the music files. Perhaps it is DRM? Sometimes the "panic" kicks in when I try to do a backup of my hard-drive. In which case, my ENTIRE system freezes after throwing an I/O error about a particular file. At which point I have to do a hard reboot.

Any suggestions for avoiding this problem of filesystem panic? (Other than "stop playing music on your computer" :-))

---

