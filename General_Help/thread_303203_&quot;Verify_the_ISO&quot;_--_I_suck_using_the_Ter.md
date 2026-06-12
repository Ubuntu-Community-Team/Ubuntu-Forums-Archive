---
title: "&quot;Verify the ISO&quot; -- I suck using the Terminal ..."
date: 2006-11-19
forum: General Help
---

### Post by newagelink on 2006-11-19
At [https://help.ubuntu.com/community/BurningIsoHowto:](https://help.ubuntu.com/community/BurningIsoHowto:)

"Verify the ISO file (highly recommended, but not required). [WWW] Instructions on OpenOffice.org."

So I go to OpenOffice.org -- [http://www.openoffice.org/dev_docs/using_md5sums.html:](http://www.openoffice.org/dev_docs/using_md5sums.html:)

"This is how you verify MD5 Checksums under Linux:

   1. In the shell of your preference, type the command "md5sum Archivname.tar.gz"
   2. Compare the calculated MD5 Checksum with the one listed for the corresponding OpenOffice.org archive on the MD5Sum page (linked to on the latest download page)."

```
daniel@daniel-laptop:~$ md5sum ubuntu-6.10-desktop-i386.iso
md5sum: ubuntu-6.10-desktop-i386.iso: No such file or directory
daniel@daniel-laptop:~$ cd desktop
bash: cd: desktop: No such file or directory
daniel@daniel-laptop:~$ md5sum ubuntu-6.10-desktop-i386.iso
md5sum: ubuntu-6.10-desktop-i386.iso: No such file or directory

```
The file I'm trying to verify is /home/daniel/Desktop/ubuntu-6.10-desktop-i386.iso

There's just so many shell commands to learn; I wish I had time to sit down and browse websites and read up on it.

Nevermind, it seems I just didn't read it carefully.
```
daniel@daniel-laptop:~$ cd daniel/Desktop
bash: cd: daniel/Desktop: No such file or directory
daniel@daniel-laptop:~$ cd Daniel
bash: cd: Daniel: No such file or directory
daniel@daniel-laptop:~$ cd Desktop
daniel@daniel-laptop:~/Desktop$ md5sum ubuntu-6.10-desktop-i386.iso
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso
daniel@daniel-laptop:~/Desktop$
```I'm depressed; I can't even successfully Change Directories when I want to. I guess practice makes perfect. :(

---

### Post by ReaderRat on 2006-11-19
It's okay, you're learning.
I usually burn an .iso to disc and then, if it boots, pick the selection in the start menu that checks the disc MD5sums on ALL files. This does take a lot of CD-Rs, but, that's okay with me.

Don't give up....Ubuntu is a lot of fun....once you get to know it....

---

### Post by newagelink on 2006-11-21
> **ReaderRat said:**
> This does take a lot of CD-Rs, but, that's okay with me....?
> **ReaderRat said:**
> Don't give up....Ubuntu is a lot of fun....once you get to know it....Yeah, and it runs so much more smoothly on my computer than Windows XP ever has.

I'm excited about 6.10 because the display is so clear -- it makes my laptop screen feel like one of those expensive ($250?) flatscreens. :) The perfect resolution by default when I booted from the Ubuntu 6.10 disc.

I'm wondering: Should I try to upgrade from my Ubuntu 6.06 partition, with [all the errors I've been getting]("http://ubuntuforums.org/showpost.php?p=1785256&postcount=96")? ](*,) Or should I try to create a ghost partition, erase this one, reinstall Ubuntu, then try to import data? That sounds even more complex, though. :(

---

