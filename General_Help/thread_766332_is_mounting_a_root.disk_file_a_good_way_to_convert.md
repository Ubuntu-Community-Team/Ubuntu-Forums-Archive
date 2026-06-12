---
title: "is mounting a root.disk file a good way to convert a wubi install to a regular one?"
date: 2008-04-25
forum: General Help
---

### Post by amirman on 2008-04-25
Hi forum friends, (first post)
Ok, so i've been using a wubi install of ubuntu 8.04 for a while and decided i wanted to convert to a full install so i could use the hibernate function and get maximum speed out of it but since there is no standard method given for doing this conversion i came up with an idea that i wanted to run by some of you who actually know what you're doing with linux.

i had my wubi installed on my D:\ which is really just a partition on my hard drive.  I want to dualboot with windows XP which is on the C:\ so i copied the root.disk file to my C:\ and i'm hoping that once i get Ubuntu installed on the D:\ partition that i could mount the root.disk file from within Ubuntu and just copy all the files and folders in root.disk onto my Ubuntu install so that i would have all the same system settings, software, windows themes, etc.

My questions are these:

[LIST]
[*]Does my method make any sense?
[/LIST]

[LIST]
[*]how do you mount the root.disk file? i know that the command is something like this:
[/LIST]

> mount -o loop 

/host/path/to/home.disk.

old /new/mountpoint

[INDENT][/INDENT]but i don't know what a real mountpoint would look like or where i should place it. so instead of "/new/mountpoint" what should i write?

[LIST]
[*]am i correct to assume all my settings and software are contained in this root.disk file? i'm not worried about the stuff in my home folder.
[/LIST]

[LIST]
[*]If i follow this method are there any specific folders i should definitely **NOT** copy over into the new install? it seems to me that there might be some system settings particular to a wubi install that would corrupt a normal install? (boot folder perhaps)
[/LIST]

If anybody has a different method for transferring my settings, software, key-bindings, and skins as they are please suggest them.  I am very new to linux and though i understand more than most people i understand less than most of the people on these forums so please excuse my ignorance of how terminal commands work.  I would be very much appreciative of any help any of you could give me.

[INDENT][/INDENT]thanks.

---

### Post by ago on 2008-04-25
[https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7)

---

### Post by amirman on 2008-04-25
> **ago said:**
> [https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7)

I'm very confused by the link you sent me.  please be assured i wouldn't be wasting anyone's time if i could have easily found this information elsewhere. I've looked through the existing wubi threads and also the wubi guide about 20 times.  I don't think that LVPM will work for me since i installed via WUBI on the 8.04 release candidate disc.  I don't think LVPM supports that version. i'm very easily confused by terminal commands so sending me to that link has me a lot more confused than before especially since what they were doing is not what i'm talking about doing.  I really appreciate you taking the time to send me a link though. I just wish it would have answered some of my questions

---

### Post by ago on 2008-04-25
The instructions above are for reading an old virtual disk from withing another Linux/Ubuntu installation. 

Migrating to a real partition is a bit more involved than just accessing the files. Tools will be available to do that in the near future.

---

### Post by amirman on 2008-04-25
> **ago said:**
> Migrating to a real partition is a bit more involved than just accessing the files. Tools will be available to do that in the near future.

So, do you think i should just start over from scratch? how soon will the new migration tools be available?

---

### Post by ago on 2008-04-25
Might be end of may. Not sure.

---

### Post by amirman on 2008-04-26
i went ahead with a fresh install and just redid all my settings. i'm really loving it on my laptop. thanks.

---

