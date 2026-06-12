---
title: "Newbie's question: How to run downloads"
date: 2008-06-05
forum: General Help
---

### Post by NikolajFabriciusBjerre on 2008-06-05
Hi.

I'm new to Linux.
My problem is that when I download a program or a game for Linux,
I get a lot of files i don't know what to do with,
and I can't find a 'setup'-file like in windows.
I don't know how to use the terminal or anything,
so a big explanation would be nice.

I hope you can help me.

Thanks :)

---

### Post by 50words on 2008-06-05
> **NikolajFabriciusBjerre said:**
> Hi.

I'm new to Linux.
My problem is that when I download a program or a game for Linux,
I get a lot of files i don't know what to do with,
and I can't find a 'setup'-file like in windows.
I don't know how to use the terminal or anything,
so a big explanation would be nice.

I hope you can help me.

Thanks :)

Start with the programs in the repositories (Applications > Add/Remove in Ubuntu), which install without much effort on your part.

If there is something else you want to install, first look for a .deb package, which works like an .exe in Windows.

If something else, you will need to compile the program from source, which can be difficult. Look for a readme file to help you, and search for a howto online, and you can probably figure out how to install the software you want.

---

### Post by NikolajFabriciusBjerre on 2008-06-05
If I've understanded right:
When I download a program, I must look for a .deb file and if it's not there, I'm just goind into add/remove programs and then it should be there?

Thank you very much

---

### Post by drs305 on 2008-06-05
These two links should answer most of your questions about installing apps in ubuntu. 

How to install ANYTHING in Ubuntu!:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Ubuntu Guide: Hardy
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

Welcome to ubuntu!

---

### Post by _DD_ on 2008-06-05
> **NikolajFabriciusBjerre said:**
> If I've understanded right:
When I download a program, I must look for a .deb file and if it's not there, I'm just goind into add/remove programs and then it should be there?

Thank you very much

Kinda :)

There probably won't be a package in the files you downloaded - if you downloaded an archive with lots of files then its likely you downloaded the source.

If its a popular program then chances are it will be in add/remove programs so go there first.

If its not there then have a look through the download page on the site and you want to be looking for debian (.deb) packages, not the source code. Also keep your eye out for anything to do with "ubuntu repositories", as you can add these to your software sources list to enable you to download through the package manager.

If there's not a .deb available to download (either from the site or through any repositories) then don't panic! Google the name of the software with keywords like "ubuntu" and "package" - you may find someone has built one.

The last resort is to compile the program from source. If you get this far then give another shout and someone will walk you through your first compile!

Anyway, it might be worth knowing what program in particular you want to install, then we might be able to point you in the right direction for debs.

---

### Post by NikolajFabriciusBjerre on 2008-06-05
Thank you very much. That was just what i needed! :D

---

### Post by NikolajFabriciusBjerre on 2008-06-05
Thanks for the links. Now I've learned how to use the Synaptic - package thing. It works great. Linux is much smarter than windows!

---

