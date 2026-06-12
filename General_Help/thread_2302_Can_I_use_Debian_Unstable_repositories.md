---
title: "Can I use Debian Unstable repositories?"
date: 2004-10-27
forum: General Help
---

### Post by anund on 2004-10-27
OK, I'm really new to Ubuntu (have used it on a test machine for some days) and Debian.

As far as I can understand, the 'Universe' repository is Debian Sarge. Right? Is there any way I can use Debian Unstable (Sid) repositories?

I know this isn't supported, of course, but I'd just like to try some things out :)

Regards,
Anund Rannestad

---

### Post by shufla on 2004-10-27
Hello,

Not exactly. Follow to [www.ubuntu.com](www.ubuntu.com) and read what they said about universe. If you need more software, add multiverse repository.

So, you do not need debian unstable packages.

Best regards,
Lukasz Nowak

---

### Post by anund on 2004-10-27
Thanks for the reply.

But I'm not quite sure I understand this ;) Multiverse is said to be 'software that has not been determined to be Free Software', while Universe is said to be, well, 'additional, non-supported packages'.

So, is Universe Ubuntu's own pickings from Debian Testing/Unstable, or is it consistently Testing (Sarge) or Unstable (Sid)?

Specifically, I'd like to install KDE 3.3.1, which should be available under Debian Unstable. When I enabled Universe, I got KDE 3.2.2 (which is what Debian Testing holds). 

So, is it possible for me under Ubuntu to use Debian Unstable repositories? And if yes - how?

Regards,
Anund Rannestad

---

### Post by shufla on 2004-10-27
Hello,

This is answered in Ubuntu FAQ:

[http://www.ubuntulinux.org/support/documentation/faq/newer-versions](http://www.ubuntulinux.org/support/documentation/faq/newer-versions)
[http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-15.7453904394](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-15.7453904394)

So I do not recommend to use Debian packages in Ubuntu.

Best regards,
Lukasz Nowak

---

### Post by anund on 2004-10-27
Again, thanks for the reply. 

Well, that makes the point clear to me :) Will have to wait for Ubuntu's development branch, then. Or just switch to Debian Unstable.... 

Regards,
Anund Rannestad

---

### Post by shufla on 2004-10-27
Hello,

[QUOTE=anund]
Well, that makes the point clear to me :) Will have to wait for Ubuntu's development branch, then. Or just switch to Debian Unstable.... 
[/QUOTE]

...or backport from deb-sources ;) But I saw on devel lists, that Ubuntu developers do not like backports ;)

Best regards,
Lukasz Nowak

---

### Post by jdong on 2004-10-27
Universe consists of most of the packages in Debian testing/sid (mostly testing).


If you want to use Debian packages, I recommend that you grab the .src.deb and compile it to match your libs.

However, I've installed quite a few debian packages on my system, and nothing bad happened!!

---

### Post by regeya on 2004-10-27
I don't know about Ubuntu, since I've only recently installed it, but my past experience tells me that mixing Apt sources on vanilla Debian systems can cause problems, and often does.  It's just not immediately apparent.  And before you get angry at the Ubuntu developers for not supporting this completely, bear in mind that mixing Debian sources on Debian can cause problems, and nobody really liked to help you sort out why, say, you have XFree 4.3.0 but wants to "upgrade" portions to 4.1.0, or why uninstalling some insignificant package that nothing depends on can cause apt to decide to uninstall 67% of the packages on your system.  You've been warned!   [-X 

All I'll say on the subject is that you should learn how to mix sources and how to pin packages and releases to ensure that the latest Ubuntu release is the preferred release.  If you're smart enough to figure this out with some research, you can handle it.  If you need a detailed description of what to do, then no, I DO NOT recommend mixing in Debian Unstable sources.

Alternatively, you could build packages from Debian Unstable and any necessary deps.

I took the former approach to get a usable version of Scribus.  Works fine...so far.   ;-)

---

### Post by jdong on 2004-10-27
Whoa, if you're talking about adding an **entire apt repo** from Debian into sources.list, that's a **very very very** bad idea! It'll make you end up with a Debian system!!

Maybe if you specify **Apt::Default-Release "warty";** in apt.conf it'll like you a bit better, but that's just BAD BAD BAD.

Grabbing individual debs is ok.

---

### Post by mailmesuf on 2004-10-27
Yes you can, to a certain limit. I've installed several apps like wine, wesnoth, gnumeric or abiword, can't remember, which all worked fine and didn't give me any problems. But  you can't upgrade your system with a debian source in your apt-list. It messed up my system when i upgraded from the ubuntu preview, i had to reinstall ubuntu alltogether.

Use the debian source only for packages which aren't part of the system like libraries for example and only if they arent available on the ubuntu servers.

---

### Post by regeya on 2004-10-27
[QUOTE=mailmesuf]Yes you can, to a certain limit. I've installed several apps like wine, wesnoth, gnumeric or abiword, can't remember, which all worked fine and didn't give me any problems. But  you can't upgrade your system with a debian source in your apt-list. It messed up my system when i upgraded from the ubuntu preview, i had to reinstall ubuntu alltogether.

Use the debian source only for packages which aren't part of the system like libraries for example and only if they arent available on the ubuntu servers.[/QUOTE]

OK, some more explanation, since what you say isn't entirely true, dangit.  ](*,) 

[http://www.argon.org/~roderick/apt-pinning.html](http://www.argon.org/~roderick/apt-pinning.html)

Now let's never speak of these foul deeds again.  :grin:

---

