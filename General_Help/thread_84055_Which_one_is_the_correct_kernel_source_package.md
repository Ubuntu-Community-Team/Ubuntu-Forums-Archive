---
title: "Which one is the correct kernel source package?"
date: 2005-10-30
forum: General Help
---

### Post by sk545 on 2005-10-30
Right now, i have this insalled:

```
~$ uname -a
Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux
```

Whats its corresponding kernel source package in apt?  The closest i saw is:

linux-source-2.6.12

Is that the right one?  How come its named differently (there is no -9-386 after it)?  I also saw the header files:

linux-headers-2.6.12-9                          
linux-headers-2.6.12-9-386
linux-kernel-headers 

Do i need to install those too?  I mean, what i am trying to do is configure the dazuko module, and it needs the correct linux source.  Plus, i would also like to have the source properly configured since many applications require the linux source to be present.  I think i have to do a 'ln -s <name of kernel> linux' in /usr/src directory.  But i don't know what to do the 'ln -s' to.

Thanks.

---

### Post by Xian on 2005-10-30
[QUOTE=sk545]Whats its corresponding kernel source package in apt?  The closest i saw is:

linux-source-2.6.12

Is that the right one?  How come its named differently (there is no -9-386 after it)?  I also saw the header files:

linux-headers-2.6.12-9                          
linux-headers-2.6.12-9-386
linux-kernel-headers [/quote]

linux-source-2.6.12 is the correct package. It is named differently because it (as the source) is not tied to a specific machine arch, and can be used to compile a kernel which can be used with any normal processor.

[QUOTE=sk545]Plus, i would also like to have the source properly configured since many applications require the linux source to be present.  I think i have to do a 'ln -s <name of kernel> linux' in /usr/src directory.  But i don't know what to do the 'ln -s' to.[/QUOTE]

First you need to untar the source kernel package. Easiest way is to open nautilus with admin rights then just navigate to the file, right-click on it and choose to extract at that location.

```
$ sudo nautilus
```

Then you will make the symlink:

```
$ cd /usr/src
$ sudo ln -s linux-source-2.6.12 linux
```

---

### Post by sk545 on 2005-10-30
> It is named differently because it (as the source) is not tied to a specific machine arch, and can be used to compile a kernel which can be used with any normal processor.
I see.  But i don't want to compile my own kernel.  I just want the source tree that was used to compile the default breezy kernel that i have installed right now.  I mean, that would've been already configured, right?  Is that what those kernel headers are for?  If so, which one should i link to? linux-headers-2.6.12-9 or linux-headers-2.6.12-9-386?  No idea what linux-kernel-headers is for....

confused...

---

### Post by realwhz on 2005-10-30
If you just need a source code tree to complete some kernel-dependent software's compilation or installation, the linux-header package is for you. linux-headers-2.6.12-9-386 is kernel header files for version 2.6.12 on 386, which depends on linux-headers-2.6.12-9 package in fact.

---

### Post by sk545 on 2005-10-30
Alright, thats making sense now.  Thx.

But, what is the package 'linux-kernel-headers' for?  I mean i have three of such kind:

linux-headers-2.6.12-9 
linux-headers-2.6.12-9-386
linux-kernel-headers

Is it just another dependency?

---

### Post by Xian on 2005-10-30
[QUOTE=sk545]But, what is the package 'linux-kernel-headers' for?  I mean i have three of such kind:[/QUOTE]
Just issue the following command.
It will download what you need with deps.

```
$ sudo apt-get install linux-headers-`uname -r`
```

---

### Post by sk545 on 2005-10-30
Alright, thanks.  Is there a difference between 386 and 686?  I am using a Athlon 64 3000+ cpu, and was wondering if it was better to use 686 or should i just stick to 386 since i have everything pretty much working on it right now.  I don't want to enable 64bit mode, and still use 32bit.

---

### Post by Xian on 2005-10-30
[QUOTE=sk545]Is there a difference between 386 and 686?[/QUOTE]
Yeah, the i686 is optimized for Pentium type-IV processors.
The i386 is compiled to run on almost any arch.

I'm unsure what 32bit arch kernel a x86_64 proc is best run on.

---

### Post by sk545 on 2005-10-30
is the athlon 64 3000+ considered a "pentium IV" type?

---

