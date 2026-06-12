---
title: "software ?'s"
date: 2008-05-03
forum: General Help
---

### Post by creekchub on 2008-05-03
how do i find out if a software application program will work in ubuntu.  i frequently use a archery program in windows that i would like to download and install in ubuntu if possible

---

### Post by Zorael on 2008-05-03
There's a database over at winehq.org - the official WINE site. Try searching it for your app name and see if there is an entry for it.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

If it doesn't work with wine, you could likely install Windows XP in a virtual machine, inside linux. That way you can boot up XP whenever you need to use that program, and then shut it down without rebooting your computer. You'll get XP support for most programs (except stuff like iTunes and other apps that need to access specific hardware, such as USB stuff or graphics accelerators), while at the same time enjoying the more stable linux environment.

---

### Post by creekchub on 2008-05-03
will that work with windows 2k pro as well or only XP

---

### Post by Zorael on 2008-05-03
Sure.

[http://en.wikipedia.org/wiki/VirtualBox](http://en.wikipedia.org/wiki/VirtualBox)
> Supported guest operating systems include FreeBSD, Linux, OpenBSD, OS/2 Warp, Windows and Solaris.

---

### Post by Game_boy on 2008-05-03
What no one has said yet is:

Any given program, unless specifically advertised for linux on their website, will not work in Linux.

There are several methods to get it to work:

1. Wine. This is a rewrite of some Windows code to get some Windows programs to run on Linux. Look on appdb.winehq.org to see if your program is listed. if it is, check whether it works. If it isn't, download Wine and your program and run them together. It may work.

2. Virtualisation. This is running real Windows inside of Linux. It can be slow and requires a lot of setting up, and 3D graphics generally do not work. You also need windows installed on that computer.

3. Alternatives. Look for a similar Linux program.

4. Dual-boot into Windows when you need it.

---

### Post by MattBD on 2008-05-03
> **Game_boy said:**
> What no one has said yet is:

Any given program, unless specifically advertised for linux on their website, will not work in Linux.

There are two methods to get it to work:

1. Wine. This is a rewrite of some Windows code to get some Windows programs to run on Linux. Look on appdb.winehq.org to see if your program is listed. if it is, check whether it works. If it isn't, download Wine and your program and run them together. It may work.

2. Virtualisation. This is running real Windows inside of Linux. It can be slow and requires a lot of setting up, and 3D graphics generally do not work. You also need windows installed on that computer.

3. Alternatives. Look for a similar Linux program.

4. Dual-boot into Windows when you need it.

You can of course also try running ReactOS in a virtual machine as well - but that's only really worthwhile either if everything else has failed or you haven't got a spare copy of Windows.

---

