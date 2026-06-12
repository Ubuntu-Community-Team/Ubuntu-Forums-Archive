---
title: "How do you install 32-bit libraries on 64-bit Ubuntu 13.10 for Scrivener free tools?"
date: 2013-11-14
forum: General Help
---

### Post by Jim_Granite on 2013-11-14
I don't know enough abpout installing on Ubuntu. I'm told from the Scrivener forums that I need to "[install the necessary 32-bit libraries]("https://www.literatureandlatte.com/forum/viewtopic.php?f=33&t=25247&start=0")".  [B]
But, what does THAT mean?[/B]  
[COLOR=#b22222]Can you help me figure out how to install the necessary 32-bit libraries (whatever that means) so that Scrivener works on Ubuntu 13.10?  [/COLOR]

The Linux installation instructions for installing Scrivener are here: 
- [A Mostly Complete Guide to Installing Scrivener on Linux]("https://www.literatureandlatte.com/forum/viewtopic.php?f=33&t=20489")  

Trying to follow those instructions, I obtained the [scrivener-1.6.1.1-beta.deb file]("https://www.literatureandlatte.com/forum/viewtopic.php?f=33&t=20489") 

Following their instructions, I ran these two commands successfully: 
$ sudo apt-get install gdebi 
$ /usr/bin/gdebi-gtk scrivener-1.6.1.1-beta.deb   

This created: /usr/bin/scrivener 

But, when I run Scrivener, I get a complaint that it's missing (lots of) ld.so files.  
==> libstdc++.so.6 => not found
==> libfontconfig.so.1 => not found
==> libfreetype.so.6 => not found
... lots of these types of errors ..

The Scrivener people aren't used to Linux so they can't help me further. 
**[COLOR=#800000]How do I figure out what to install in order to add the necessary 32-bit libraries?[/COLOR]**

Note: [Full details are here.]("https://www.literatureandlatte.com/forum/viewtopic.php?f=33&t=25247&start=0")

---

### Post by Jim_Granite on 2013-11-14
Here are more complete details:

I'm not sure what a LD_LIBRARY_PATH is, but, mine doesn't appear to be set:
$ echo $LD_LIBRARY_PATH
==> nothing

Notice that the desired shared object module do seem to exist:
$ sudo updatedb
$ locate libstdc++.so.6
==> /usr/lib/x86_64-linux-gnu/libstdc++.so.6
==> /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.18

An "strace" seems to show where Scrivener is looking for these files:
$ sudo strace scrivener >& /tmp/foo
$ grep "No such file or directory" /tmp/foo
==> ... lots of stuff ... 
==> open("/usr/share/scrivener/bin/../lib/libstdc++.so.6", ... stuff ... (No such file or directory) ...
==> ... lots of similar stuff ... 
Note: There are 190 files that Scrivener needs but it couldn't find, so I only show the first one here.

I thought I was being clever by linking the found libstdc with where Scrivener was looking:
$ cd /usr/share/scrivener/lib
$ sudo ln -s /usr/lib/x86_64-linux-gnu/libstdc++.so.6

But, that just resulted in a different failure of Scrivener:
$ scrivener
==> /usr/share/scrivener/bin/Scrivener: error while loading shared libraries: libstdc++.so.6: wrong ELF class: ELFCLASS64

So, I removed the link I had created and googled some more, and found this command:
$ ldd /usr/share/scrivener/bin/Scrivener | grep "not found"
==> libstdc++.so.6 => not found
==> libfontconfig.so.1 => not found
==> libfreetype.so.6 => not found
... lots of these types of errors ... 

What's the next step to installing Scrivener (which appears to be a 32-bit program)?

---

### Post by oldos2er on 2013-11-14
Moved to General Help.

You shouldn't need to install gdebi if double-clicking the *.deb file opens it in Software Center, which it should by default. Can you confirm you have the file /etc/dpkg/dpkg.cfg.d/multiarch ? ```
ls /etc/dpkg/dpkg.cfg.d/multiarch
```

---

### Post by Jim_Granite on 2013-11-23
[QUOTE=oldos2er;12848203]Can you confirm you have the file /etc/dpkg/dpkg.cfg.d/multiarch ?

I have no idea what this "multiarch" file does, but, my /etc/dpkg/dpkg.cfg.d/ is empty.
Should I install something?

EDIT: Googling, I find [this multi-arch explanation]("https://help.ubuntu.com/community/MultiArch") and this [multi-arch for Debian]("https://wiki.debian.org/Multiarch/HOWTO") page, which I will read.

---

### Post by edwbaker on 2014-04-14
```
  apt-get install lib32stdc++6 libgtk2.0-0:i386 libgstreamer-plugins-base0.10-0:i386 
```  Is what worked for me.

---

### Post by LunaticStrain on 2014-04-28
> **edwbaker said:**
> ```
  apt-get install lib32stdc++6 libgtk2.0-0:i386 libgstreamer-plugins-base0.10-0:i386 
```  Is what worked for me.

Thanks, this is also what worked for me. After that it loaded right up.

---

