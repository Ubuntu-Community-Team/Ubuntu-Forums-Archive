---
title: "random fscking"
date: 2007-07-01
forum: General Help
---

### Post by Ultra Magnus on 2007-07-01
Hi, I was just wondering why at seemingly random intervals when I boot up, the fsck thing decides to check my drive - It usually says something like disk has been mounted X number of times without being checked and then takes a couple of minutes to check the filesystem - Is this normal and to be expected - I'm an ex Windows user so I'm used to this sort of thing happening after a crash so it makes me a bit nervous!

---

### Post by tillo on 2007-07-01
I hate saying that but... just do "man tune2fs" and see the first option ("-c"). It describes what is it, why is it there and how to change it.

---

### Post by FuturePilot on 2007-07-01
That's normal. It will always do that after 30 boots. You can turn it off, but that's not recommended.

---

### Post by nickj6282 on 2007-07-10
> **FuturePilot said:**
> That's normal. It will always do that after 30 boots. You can turn it off, but that's not recommended.

Is there a way to set this to a number other that 35 (the default setting on my machine)? Or maybe give some sort of warning that the next fsck cycle is coming up soon so we can be prepared? I hate that it randomly takes an extra five minutes to boot without warning. If I needed my PC up in a hurry, I'd be rather annoyed.

---

### Post by coffeecat on 2007-07-10
> **nickj6282 said:**
> Is there a way to set this to a number other that 35 

Have a look at tillo's post - two up from yours. It's all there. :)

---

### Post by nickj6282 on 2007-07-10
> **coffeecat said:**
> Have a look at tillo's post - two up from yours. It's all there. :)

Thanks, that worked perfectly! So does anyone know of a way to see how many times the filesystem has been mounted so that I can get some kind of idea when it will be checked again?

Thanks!
-Nick

---

### Post by StefanoCole on 2007-07-11
To see how many times your filesystem has been mounted type the following from terminal:

$ sudo tune2fs -l /dev/hdx

where x is the desired partition (1, 2, etc.)
The above command will give you many infos about the filesystem, check the output line related to number of mounting.

Stefano

---

### Post by dannyboy79 on 2007-07-11
> **nickj6282 said:**
> Thanks, that worked perfectly! So does anyone know of a way to see how many times the filesystem has been mounted so that I can get some kind of idea when it will be checked again?

Thanks!
-Nick
yeah, there's a program out there, I think it's called bonager. also, you can check it from the command line at any time using this command:
sudo dumpe2fs -h /dev/sdb1 | grep -i 'mount count'

or, you can check out showfsck, it was available for edgy in the repo's I read. All this info is from this post so I can't take credit for any of it.
[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

