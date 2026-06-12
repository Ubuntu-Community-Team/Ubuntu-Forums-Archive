---
title: "Help installing Cmaptools .bin"
date: 2008-03-16
forum: General Help
---

### Post by mr tim esquire on 2008-03-16
Im trying to install cmaptools but i keep getting this error no matter how i download the file!  Does anyone know how i could install this anyway?

```
tim@timlaptop:~$ ./LinuxCmapTools_v4.16_03-11-08.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
tar: Skipping to next header
tar: Error exit delayed from previous errors
The included VM could not be unarchived (TAR). Please try to download
the installer again and make sure that you download using 'binary'
mode.  Please do not attempt to install this currently downloaded copy.

```

---

### Post by fkrahe on 2008-03-17
Thats the same for me.

First I was proibited from ./'ing the file, even as root. 

Then I did
```
chmod a+x LinuxCmapTools_v4.16_03-11-08.bin
```

Finally I did
```
cd Desktop/
./LinuxCmapTools_v4.16_03-11-08.bin
```

And got the same message.

Using Ubuntu 7.04 on HP Pavilion dv6220br

---

### Post by mr tim esquire on 2008-03-18
Is anyone running Cmaptools through wine?

---

### Post by fkrahe on 2008-03-18
I tried that too, Mr tim!

Cmap inicialises itself and then vanishes - to never came back...

But give it a trie.

If it works for you, tell me.

I just cannot use. And my teacher says I have to use CMAPS, no other options...

I'm stuck.

---

### Post by mr tim esquire on 2008-03-19
im stuck too
i posted these problems to the cmap mailing list, in the mean time im having to find a windows machine, how frustrating!

---

### Post by fkrahe on 2008-03-23
Well, well, well...

It is said at [http://cmap.ihmc.us/download/free_client.php?myPlat=Win](http://cmap.ihmc.us/download/free_client.php?myPlat=Win)

-----------------------
Select a target platform for system requirements and download:
Windows
Mac OS
Linux (Intel) >>> INTEL
Solaris
----------------------
Are you Intel? I'm AMD... Maybe thats the problem

---

### Post by mr tim esquire on 2008-03-29
The linux bin works with fedora 7 and 8
I wonder what Ubuntu would need to get it going?

---

