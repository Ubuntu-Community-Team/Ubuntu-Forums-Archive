---
title: "Synaptic not working"
date: 2006-12-24
forum: General Help
---

### Post by tjay on 2006-12-24
Hi,

I installed darcs with synaptic today and immediately after it installed, synaptic popped up an error message and stopped working. Now when I open synaptic I get the error and I don't see any packages to install. If I try to Reload the packages synaptic will crash (disappear without even the Gnome crash tool) after downloading the stuff.

The error is:

```
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.

```

(This is the error I get when I open synaptic now. I'm not sure whether this is the same as the one immediately after i installed darcs, but I think it is.)

How do I fix this? (I'm using 6.10)

TJ

---

### Post by Spin Doctor on 2006-12-24
Tjay,

I belive I had this happening to me once aswell. It seems your etc/apt/sources.list has become corrupted, meaning probably it doesnot follow the formats required for Synaptic to read the list.

What I did to solve the problem was:
[LIST]
[*]First backup your etc/apt/sources.list
[*]Go to System mainmeny, Select Administration submeny, and select software sources menyoption.
[*]Uncheck everything you have selected, leaving it as blank as possible.
[*]Restart Synaptic to see if it will load the sources.list[/LIST]If this does not work: open you etc/apt/sources.list.
If you see a format error, go ahead and delete just that. 
If not, delete everything there, and save, leaving it blank. Then google to find a default sources.list and paste into yours. And make extra additions based on if you are running Automatix or any other unsupported repositories.

I belive this should help you!

---

### Post by tjay on 2006-12-24
Thanks a lot! That worked like a charm :)

Cheers and have a merry Christmas ;)

---

### Post by Spin Doctor on 2006-12-25
I am glad you got it solved! Have a great day!

---

