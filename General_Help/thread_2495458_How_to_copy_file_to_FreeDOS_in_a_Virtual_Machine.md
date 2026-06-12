---
title: "How to copy file to FreeDOS in a Virtual Machine?"
date: 2024-02-20
forum: General Help
---

### Post by Acharn on 2024-02-20
I've been searching for three days and haven't found an answer. I'm running Ubuntu 22.04, I've created a VirtualBox and installed FreeDOS into it. I can boot FreeDOS in the VM, and I've downloaded the installation programs for a couple of DOS games, but I can't install them. When I click on IDE Primary Device 0 and then Choose Disk File, I'm taken to my home directory. When I click on the folders the downloaded files unzipped to, I don't see anything. I'm baffled as to why I can't find a tutorial even in the FreeDOS website. There are tutorials about how to create VMs and install FreeDOS, but I haven't found one on how to use it. Can anyone help me?

---

### Post by TheFu on 2024-02-20
Normally, people would use DosBox to run DOS games. This means you don't need a VM.  With DosBox, you can link a letter to a directory on Linux.  You don't want that to be your HOME, but a directory elsewhere.  I've used /opt/dosgames/

[https://itsfoss.com/ubuntu-dosbox/](https://itsfoss.com/ubuntu-dosbox/) has step by step.

DOS didn't have networking, so most of the normal methods we use with VMs to transfer files won't work without installing network drivers.  I remember networking under MS-Dos/PC-DOS. It was a pain and on a system with 640KB of RAM, it was easy for the network drivers to use 150KB making it hard to run the actual program you want.

---

### Post by Acharn on 2024-02-20
I've already installed DOSBox, because I want to run these games anyway, and I used to run them in DOSBox on Windows. But let's say I want to learn to use Wordperfect in DOS. How would I install the program in my VM? And if I can't, what is the VM good for? So I wanted to install these programs just to see how they work in FreeDOS.

---

### Post by TheFu on 2024-02-20
> **Acharn said:**
> I've already installed DOSBox, because I want to run these games anyway, and I used to run them in DOSBox on Windows. But let's say I want to learn to use Wordperfect in DOS. How would I install the program in my VM? And if I can't, what is the VM good for? So I wanted to install these programs just to see how they work in FreeDOS.

I own a copy of WordPerfect for DOS.  You aren't missing anything. ;)  AbiWord is better. [https://help.ubuntu.com/community/AbiWord](https://help.ubuntu.com/community/AbiWord)

Did you provide a fake network device to the VM and did you install the MS-DOS drivers for that network into the VM?

MS-DOS hasn't been supported for decades, so don't be surprised when modern hardware doesn't have DOS drivers.

---

### Post by Acharn on 2024-02-21
> **TheFu said:**
> I own a copy of WordPerfect for DOS.  You aren't missing anything. ;)  AbiWord is better. [https://help.ubuntu.com/community/AbiWord](https://help.ubuntu.com/community/AbiWord)

Did you provide a fake network device to the VM and did you install the MS-DOS drivers for that network into the VM?

MS-DOS hasn't been supported for decades, so don't be surprised when modern hardware doesn't have DOS drivers.

Well, it's actually FreeDOS, which is still being supported. I've given up on being able to install DOS to a USB stick. Now I just want to learn how to install files to it. And I use LibreOffice for the rare times when I need a word processor.

---

### Post by TheFu on 2024-02-21
FreeDOS is meant to be a clone of MS-DOS, so the tools and drivers created for MS-DOS are used, like for networking.  

I don't know what good this information is, but check out **mtools** to copy files, to/from MS-DOS formatted devices. 
[https://www.gnu.org/software/mtools/](https://www.gnu.org/software/mtools/)
```
sudo apt install mtools
```
[https://www.gnu.org/software/mtools/manual/mtools.html](https://www.gnu.org/software/mtools/manual/mtools.html) is the manpage for the tools.

I'm just guessing, but perhaps you could create a FAT16 formatted file and use mtools to copy data into it.  Then you could add that FAT16 device to the VM to get data/programs added?  Just an idea.  There has to be an easier way.  I'd be surprised if FreeDOS didn't have examples of how to get files into itself easier.

I googled for a solution. Great idea, right?   
[LIST]
[*][https://forums.virtualbox.org/viewtopic.php?t=59564](https://forums.virtualbox.org/viewtopic.php?t=59564)
[*][https://opensource.com/article/21/6/copy-files-linux-freedos](https://opensource.com/article/21/6/copy-files-linux-freedos)
[*][http://wiki.freedos.org/wiki/index.php/VirtualBox](http://wiki.freedos.org/wiki/index.php/VirtualBox)
[/LIST]

---

### Post by MAFoElffen on 2024-02-21
I use FreeDOS for things like updating BIOS on machines...

Having said that, what I usually do for the files I download, is to download them via something else, then make them available to FreedDOS by copying it to it.

The easiest way to do the same with a VM, is to create a virtual USB vDisk device, that can be shared between VM Guests, to download to on anther VM, then add it to the FreeDOS VM, to use with those files. Thne you don't have to worry about having to set it up for networking.

Or just temporarly mount the FreeDOS vDisk to another VM to copy the files directly to that media...

Just a thought.

---

### Post by Acharn on 2024-02-22
Thanks, TheFu. The link to wiki.freedos.org looks like what I need. I feel so dumb for not finding it. Chapter 6 explains how to mount a virtual hard drive on the host computer (for Windows, MAC, and Linux). I don't understand, though, why they then set it to R/O (read only), but it's a start. Otherwise, maybe using FTP will work. It seems awfully convoluted.

---

### Post by HermanAB on 2024-02-22
Howdy, I suspect that you need to make a floppy disk image with your data on it and enable it in the VM storage manager then restart it.

---

### Post by TheFu on 2024-02-22
> **Acharn said:**
> Thanks, TheFu. The link to wiki.freedos.org looks like what I need. I feel so dumb for not finding it. Chapter 6 explains how to mount a virtual hard drive on the host computer (for Windows, MAC, and Linux). I don't understand, though, why they then set it to R/O (read only), but it's a start. Otherwise, maybe using FTP will work. It seems awfully convoluted.

Not at all.  FTP is a very, very, simple protocol.  If there's any sort of networking available, it doesn't take much. Best to stick with simple, bad, protocols like plain FTP to get something working that try to invent something new that nobody else uses.
The full specifications for FTP: [https://datatracker.ietf.org/doc/html/rfc959](https://datatracker.ietf.org/doc/html/rfc959)

There are specifications for all public protocols.   SMTP, NNTP, IMAP, POP3, anything that is cross platform and not proprietary.  Implementing these things is what keeps Unix interoperable, unlike most MSFT tools.

---

