---
title: "mounting ISO file/ possibly reading wrong device?"
date: 2007-03-29
forum: General Help
---

### Post by bone2006 on 2007-03-29
I wanted to install linux MCE and give it a try.  I downloaded the ISO file and then ran the installation (deb) file I downloaded.

I followed these simple instructions to mount the ISO file

sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop

I checked and the ISO file was properly mounted and I saw the device under computer and I was able to navigate the the mounted ISO file. 

The problem I'm having is that when I run the install script it says it can't read the CDROM, is possible that the application is looking under the real CD/DVD device?  Anything I can do to change that?'

---

### Post by bone2006 on 2007-03-29
I used the exact same command but instead of mounting it to iso I typed in cdrom and now it seems to be working.

I guess I should mount all ISO images to cdrom folder?

---

### Post by bone2006 on 2007-03-29
by the way can somebody explain what these commands do?
Like what does sudo modprobe loop do?  The parameters that are being passed like -t and -o 
I think knowing what it does will help me memorize the commands instead of looking it up each time I need to mount something.

Thanks in advance

---

### Post by acormack on 2007-03-30
by the way can somebody explain what these commands do?



sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop

*Comments Below:*

**sudo** means run as root instead of the normal user

**modprobe** means insert an optional module into the running LINUX kernel (basically adds extra functionality to yur LINUX system)

**loop** is the name of the module (in this case the loopback driver allowing .iso files to be treated like file systems)

**mount** is the standard command for adding devices into the LINUX filesystem


Hope this helps.  

Always type man {program name} on the command line for detailed help

e.g.  man mount


Alec

---

