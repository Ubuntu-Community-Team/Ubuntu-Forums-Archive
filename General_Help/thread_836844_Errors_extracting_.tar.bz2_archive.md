---
title: "Errors extracting .tar.bz2 archive"
date: 2008-06-21
forum: General Help
---

### Post by vader347 on 2008-06-21
I downloaded [Wii-Linux]("http://downloads.sourceforge.net/gc-linux/debian-etch-4.0%2Bwhiite-0.1.tar.bz2") and when I extracted the archive it was telling me I didn't have permissions to extract certain files.  This is because there are root only files in the archive and displays a ton of cannot mknod <insert file here> permissions denied.  So I type sudo nautilus and extract the files.  When I try to copy the files to my sd card I gives a ton of errors telling me I can't make symbolic links.  
I tried to extract the archive on my windows xp computer put it was going very slow.

Is there anyway to tell ubuntu to ignore the files and just copy them to my sd card?

---

### Post by kevdog on 2008-06-21
sudo tar jxvf <filename>

Maybe that will work?

---

### Post by Twintop on 2008-06-28
Hi vader347,

I actually just got Wii-Linux working on my Wii last night/early this morning. What I had to do was use all command line tools and extract the contents of the .tar.bz2 file to /root/ then copy them over to the ext2 partition on the SD card. Also, if you're using the instructions from [wiibrew.org]("http://wiibrew.org/wiki/Homebrew_apps/Wii-Linux"), remember to change the /etc/passwd file to update root's login info.

---

