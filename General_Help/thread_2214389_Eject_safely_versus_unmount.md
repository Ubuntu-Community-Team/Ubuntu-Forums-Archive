---
title: "Eject safely versus unmount?"
date: 2014-04-01
forum: General Help
---

### Post by vasa1 on 2014-04-01
[deadflowr posted a nice link]("http://ubuntuforums.org/showthread.php?t=2214272&p=12973797#post12973797") that shows how Nautilus offers intelligent options for dealing with devices: [http://askubuntu.com/q/5845/](http://askubuntu.com/q/5845/)

But what about other file managers? Thunar and PCManFM seem limited in this respect. How can users of these file managers remove devices safely?

---

### Post by sudodus on 2014-04-01
I usually have (at least) one terminal window open, and I prefer unmounting via the command line (and checking with ***df***). But I understand your issue, I think many people rely on ejecting USB drives before unplugging, so it is important that it is safe at least from all the file browsers, that are default in the Ubuntu flavours.

---

### Post by vasa1 on 2014-04-01
> **sudodus said:**
> I usually have (at least) one terminal window open, and I prefer unmounting via the command line (and checking with ***df***). But I understand your issue, I think many people rely on ejecting USB drives before unplugging, so it is important that it is safe at least from all the file browsers, that are default in the Ubuntu flavours.

Hi sudodus, please see this post: [http://askubuntu.com/a/86021](http://askubuntu.com/a/86021)

In it, the poster describes the steps that I think are helpful: first, there should be a sync of data and then the unmount should proceed and then the user should be notified that it is safe to physically remove the device.

In your method, do you wait for some time before running the unmount command? That is a precaution I always take.

---

### Post by vasa1 on 2014-04-01
There's an "indicator" available here: [USB Safe Removal]("http://askubuntu.com/a/37989") but it's a .deb and not from the USC. It seems to be written in Python and my knowledge of that is zero.

---

### Post by bapoumba on 2014-04-01
> **vasa1 said:**
> [deadflowr posted a nice link]("http://ubuntuforums.org/showthread.php?t=2214272&p=12973797#post12973797") that shows how Nautilus offers intelligent options for dealing with devices: [http://askubuntu.com/q/5845/](http://askubuntu.com/q/5845/)

But what about other file managers? Thunar and PCManFM seem limited in this respect. How can users of these file managers remove devices safely?

Just to state that PCManFM 1.2.0 on 14.04 offers the option to eject, either by clicking on the eject icon or right click.

---

### Post by vasa1 on 2014-04-01
> **bapoumba said:**
> Just to state that PCManFM 1.2.0 on 14.04 offers the option to eject, either by clicking on the eject icon or right click.
Is there also the unmount option?

---

### Post by ajgreeny on 2014-04-01
There is also a panel applet called ejecter which is useful to eject USBs and also CD/DVDs from the drive.
I use it in xubuntu and lubuntu panels, but have no idea if it works in unity. Add it to your startup applications with a sleep option to make sure the DE is running and an icon will appear only when a USB or CD/DVD is present.

---

### Post by sudodus on 2014-04-01
> **vasa1 said:**
> Hi sudodus, please see this post: [http://askubuntu.com/a/86021](http://askubuntu.com/a/86021)

In it, the poster describes the steps that I think are helpful: first, there should be a sync of data and then the unmount should proceed and then the user should be notified that it is safe to physically remove the device.

In your method, do you wait for some time before running the unmount command? That is a precaution I always take.

I am rather sure, that ***umount*** flushes the cached data to disk before actually unmounting, in other words, performs ***sync***.

See this link

[https://lists.debian.org/debian-user/2010/09/msg01323.html](https://lists.debian.org/debian-user/2010/09/msg01323.html)

and some extra information at

[http://www.linfo.org/umount.html](http://www.linfo.org/umount.html)

---

### Post by vasa1 on 2014-04-01
> **sudodus said:**
> I am rather sure, that ***umount*** flushes the cached data to disk before actually unmounting, in other words, performs ***sync***.

See this link

[https://lists.debian.org/debian-user/2010/09/msg01323.html](https://lists.debian.org/debian-user/2010/09/msg01323.html)

and some extra information at

[http://www.linfo.org/umount.html](http://www.linfo.org/umount.html)

Both useful links. Thanks!

---

### Post by bapoumba on 2014-04-01
> **vasa1 said:**
> Is there also the unmount option?
From memory yes, but I'm not on my ubuntu machine right now. I'll double check tonight.

---

### Post by bapoumba on 2014-04-01
@vasa : yes.

---

### Post by vasa1 on 2014-04-01
> **bapoumba said:**
> @vasa : yes.

Thanks! I had looked at [PCMANFM 1.2.0 AND LIBFM 1.2.0 RELEASED!]("http://blog.lxde.org/?p=1082") for details but didn't find any :(
However, it seems a lot of work has gone into 1.2. Among other things, it will be possible to sort folders separately, and "open as root" has been removed.

---

