---
title: "Reading and editing .pdf files"
date: 2007-03-14
forum: General Help
---

### Post by stchman on 2007-03-14
Hello all.  I have been using Ubuntu for a few weeks now and love it.  I gave teh built in .pdf reader (evince) a chance and found it to be lacking.

When I was on windows I use Foxit to read .pdf files and it ROCKED.  Acrobat for Windows is bloated and takes forever to load.   Now that I am on Ubuntu I found that Acrobat reader for Ubuntu is the best way to read .pdf files.  Acrobat reader loads quick and its usage is very easy.  I have read on this forum from some that using Acrobat is nto a good thing since it is not open source.  I am not wanting to modify the source code so it is not a big issue to me.

My question is there a better peice of software for Ubuntu to read .pdf files?  Also is there a free peice of software that allows me to edit .pdf files?

Thanks

---

### Post by ahmatti on 2007-03-16
Hello!
I also use acrobat reader for browsing pdfs. I just find better than xpdf, or evince etc. For editing I just came across **flpsed** [http://www.ecademix.com/JohannesHofmann/flpsed.html](http://www.ecademix.com/JohannesHofmann/flpsed.html), which can be used to add text in pdfs.

And there is also **pdfedit** which can be [COLOR="Navy"]used to edit pdf files[/COLOR]. It works! I can edit and highlight text 

You can download the *.deb package for pdfedit here:

[http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/pdfedit_0.2.5-0+3v1ubuntu1_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/pdfedit_0.2.5-0+3v1ubuntu1_i386.deb)

I found it from this thread: [http://www.ubuntuforums.org/showthread.php?t=345257&page=2&highlight=edit+pdf](http://www.ubuntuforums.org/showthread.php?t=345257&page=2&highlight=edit+pdf). Thanks guys!

I see there is also a linux version of Foxit reader, but I haven't tried compiling it for Ubuntu.

---

### Post by aysiu on 2007-03-16
More info on the Linux version of Foxit:
[http://www.foxitsoftware.com/pdf/sdk/dll/index.html](http://www.foxitsoftware.com/pdf/sdk/dll/index.html)

Hm.

I just tried it. It doesn't need to be compiled or anything. It's a precompiled binary.

It launches just fine, but when I try to open any PDF, it crashes. This is the terminal output: ```
./ReaderLinux 
X Error: BadDevice, invalid or uninitialized input device 169
  Extension:    147 (XInputExtension)
  Minor opcode: 3 (X_OpenDevice)
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Extension:    147 (XInputExtension)
  Minor opcode: 3 (X_OpenDevice)
  Resource id:  0x0
Failed to open device
Segmentation fault (core dumped)
```

---

### Post by ahmatti on 2007-03-16
> **aysiu said:**
> 
It launches just fine, but when I try to open any PDF, it crashes. This is the terminal output: 

I get the same problem!

---

### Post by buuntuu! on 2007-03-16
> **stchman said:**
>   Also is there a free peice of software that allows me to edit .pdf files?


i've been looking for the same thing, browsing the forum, searching in the repos but i can't find anything useful... flpsed is fine, but does not allow to modify existing elements. is there nothing out there?... any suggestions?

---

### Post by Marsolin on 2007-03-16
> **buuntuu! said:**
> i've been looking for the same thing, browsing the forum, searching in the repos but i can't find anything useful... flpsed is fine, but does not allow to modify existing elements. is there nothing out there?... any suggestions?

[PDFedit]("http://linuxappfinder.com/package/pdfedit") that was mentioned above can do this. Linux.com just did an article on it this week.

---

### Post by rsambuca on 2007-03-16
Probably not exactly what you are looking for, but pdftk allows for certain modifications of pdf's.  It is in the repos, and the website is [[COLOR="Red"]here.[/COLOR]]("http://www.accesspdf.com/pdftk/")

---

