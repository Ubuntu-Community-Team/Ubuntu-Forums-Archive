---
title: "changed /etc/init.d/rc"
date: 2014-12-18
forum: General Help
---

### Post by pfeiffep on 2014-12-18
I was attempting to change the rc script to enable shell concurrency and made a mistake. 
Now I can only boot to root in recovery mode with no gui **AND** /etc/init.d file system is read only.
I can open rc file an notice the mistake but I'm unable to save the file.

I've tried using this [technique]("http://www.geekyboy.com/archives/629") outlined ```
:w ! sudo tee %
```to no avail.

The error made was on my Dell Laptop running Ubuntu 14.04.1 gnome session fallback metacity.

I don't know how to mount the file system  ( /dev/sda6 ) read - write 

I need some assistance please.

---

### Post by Bashing-om on 2014-12-18
pfeiffep; Hi !

Well;
> 
I don't know how to mount the file system ( /dev/sda6 ) read - write 


Try as:
From the grub boot menu -> advnaced options -> recovery kernel, -> root shell ->> type the terminal command :
```

mount -o remount rw /

```
now with nano (vim) can re-edit the file.

[INDENT][INDENT]workie great
[INDENT][INDENT][INDENT]last long time ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pfeiffep on 2014-12-18
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1111508_1.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1111508") 				 				 					 						 	[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508") 
Thanks a million! worked like a charm

---

### Post by Bashing-om on 2014-12-18
pfeiffep; Great !

Pleased it worked out.

[INDENT]buntu
[INDENT][INDENT]more than 1 way to an end
[/INDENT][/INDENT][/INDENT]

---

