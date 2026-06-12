---
title: "CD writing problem - setting write speed"
date: 2007-10-29
forum: General Help
---

### Post by yme on 2007-10-29
Hi:

I'm trying to write a CD using Feisty but it won't let me choose write speed but defaults to the highest and the results are ropey. I want to choose the lowest but it just won't allow me access to the list of write speeds. 

I read one post about this being an unresolved issue in Dapper. Can anyone tell me more?

yme

---

### Post by SPr on 2007-10-29
> **yme said:**
> Hi:

I'm trying to write a CD using Feisty but it won't let me choose write speed but defaults to the highest and the results are ropey. I want to choose the lowest but it just won't allow me access to the list of write speeds. 

I read one post about this being an unresolved issue in Dapper. Can anyone tell me more?

yme

From ```
man eject
```
>  -x <speed>
            With this option the drive is given a CD-ROM select speed command.
            The speed argument is a number indicating the desired speed  (e.g.
            8  for 8X speed), or 0 for maximum data rate. Not all devices sup&#8208;
            port this command and you can only specify speeds that  the  drive
            is  capable  of.  Every  time  the media is changed this option is
            cleared. This option can be used alone, or  with  the  -t  and  -c
            options.


read the eject manual for more info (it's worth it :))

HTH.

Edit:
I haven't tried that so I don't whether it works or not. It must be worth a go though.

---

### Post by yme on 2007-10-30
In a million years I never would have though eject controlled the CDROM. Seems like it is rather misnamed to me.

Anyway, I had a look and tried 'eject -X' in order to probe the available speeds and got:
eject: error while finding CDROM name

I then did 'eject -d' to probe the default device name and got: 
eject: default device: `cdrom'

Then I tried again 'sudo eject -X cdrom' but still got:
eject: error while finding CD-ROM name

Any ideas?

---

### Post by SPr on 2007-10-30
LOL I only found out about eject by accident :)

I can't help you with your new problem I'm afraid :( I don't know what could be wrong.

There are some very knowledgable people on here so hopefully someone can help :)

---

### Post by yme on 2007-11-30
I'm still stuck on this one and quietly fuming that eject -d tells me the name of the cdrom but eject -X won't recognize that name :confused:

---

### Post by logos34 on 2007-11-30
eject -h

eject [-vn] -x <speed> [<name>]       -- set CD-ROM max speed

i.e.
sudo eject -x <speed> /dev/hdc (or /media/cdrom0)  (-->or maybe it's /dev/scd0...check mount or /etc/fstab)


OR set it this way:

alt+F2

type
sudo gconf-editor

Apps>Nautilus-cd-burner>default speed

---

