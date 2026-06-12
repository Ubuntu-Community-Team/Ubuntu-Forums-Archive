---
title: "Need help with a bash script please please!!"
date: 2007-10-22
forum: General Help
---

### Post by gurukreff on 2007-10-22
Hi everybody..

Here's the thing... i installed ubuntu in a windows installation, using the option to use all the disk (format), confident that the windows to linux wizard that transfers your files would work... It didn't. It was because when i was going to reboot to boot from live CD (Gusty) i didn't want to wait and did a simple hardware reboot (pushed te button), that caused that the wizard couldn't mount the windows partition, so i lost my very important data.

I used the ubuntu rescue remix cd (a great tool) and used foremost to help me get my jpg files, the thing is that it recovered around 50k files, all without name, and i need a bash script that moves files over 100K in size to another folder so i can see wich ones i need (couldn't do this from nautilus, there are so many files that the thing freezes).

That's it, i would learn scripting so i would not bother anyone but it's something that i need to get done quickly, so plese IN THE NAME OF OPEN SOURCE COMMUNITY HELP!! IT WOULD BE GREATLY APRECIATED!!   :(

---

### Post by Old *ix Geek on 2007-10-22
The following will do exactly what you need, from a command line.
```
find . -maxdepth 1 -size +100000c -exec mv {} bigger \;
```
For a thorough explanation of each part of it, see **man find**.

Briefly, you're using the **find** command to search the current directory (**.**) only, looking for files that are 100,000 bytes or more, and moving them to a directory named **bigger**.  (Before running this, **mkdir bigger**.)

You may need to modify the above depending on your location and where you're moving the files.

For example, if your pictures are in **/home/yourname/pictures**, and you're running this from some other directory, replace the **.** with **~/pictures**.

If you want to move the files to **/tmp/pictures**, and you're in your home directory, change **bigger** to **/tmp/pictures**.  Etc.

---

### Post by gurukreff on 2007-10-22
> **Old *ix Geek said:**
> The following will do exactly what you need, from a command line.
```
find . -maxdepth 1 -size +100000c -exec mv {} bigger \;
```
For a thorough explanation of each part of it, see **man find**.

Briefly, you're using the **find** command to search the current directory (**.**) only, looking for files that are 100,000 bytes or more, and moving them to a directory named **bigger**.  (Before running this, **mkdir bigger**.)

You may need to modify the above depending on your location and where you're moving the files.

For example, if your pictures are in **/home/yourname/pictures**, and you're running this from some other directory, replace the **.** with **~/pictures**.

If you want to move the files to **/tmp/pictures**, and you're in your home directory, change **bigger** to **/tmp/pictures**.  Etc.

[B]
THANK YOU SO VERY MUCH!![/B]

I'll tell you, things went great, i was able to recover thousands of my brother's photos, mainly from a trip to NZ, but more importantly, photos from his workshops (he studies architecture), so i'm very grateful and i hope that this thread will be useful for people that are in that position.

If you have trouble of this kind, don't forget to visit the [ubuntu rescue remix website]("http://ubuntu-rescue-remix.org/") and give it a try, documentation is [right here]("http://http://help.ubuntu.com/community/DataRecovery"). 

In my case i was able to recover photos using **foremost** and the command line given just moments ago by Old *ix Geek, and also other kinds of files like docs, pdf, avi, etc...

Thank you again... And VIVA OPEN SOURCE!

---

### Post by gurukreff on 2007-10-22
I recovered lots of files and i've been busy naming them again, but there is a type of file that i wasn't able to recover, wich are the dwg files from CAD software. I used foremost and photorec but neither of them recovers that kind of file...

Anyone knows what may help (already googled... didn't seem to find anything relevant apart from lots of shareware for windows, wich would be my las resource =P)

Thanks in advance, and sorry to bother again :S

---

### Post by thinnoune on 2008-05-15
Hi everybody,

to recover dwg (CAD files) with foremost edit /etc/foremost.conf and add the next lines:
# DWG
# AUTOCAD R14
dwg     y       100000000       \101\103\061\060\061\062\000\000\000\000        
# AUTOCAD R13
dwg     y       100000000       \101\103\061\060\061\064\000\000\000\000

foremost will recognise the dwg extension 

I'm recovering files with that at the moment ;)

Enjoy ;)

---

