---
title: "mdadm and udev; can't create persistent md device"
date: 2007-11-12
forum: General Help
---

### Post by scram69 on 2007-11-12
I am trying to transition my system to a raid-1 setup.  I have added and formatted a second drive, but am having trouble trying to create the raid array.  I'm trying to follow the how-to in /usr/share/doc/mdadm/rootraiddoc.97.html.  The idea is you assemble a degraded (one disk missing) array using your new drive, then copy the system files over.  The problem is, I already have a raid-5 array set up for media storage as md0, and there is no /dev/md1.  From what I have read, this is a problem when using udev (I am using udev to keep my tuner cards straight under mythtv).

So, mdadm complains when I try to create an array using /dev/md1.  However, there is something called /dev/.static/dev/md1.  I can copy this md1 to /dev/md1 and successfully use mdadm, but md1 disappears again on reboot.  How do I get md1 to stick in /dev ?

---

### Post by fjgaude on 2007-11-12
You can use other than /dev/md1. Try something like /dev/md2 or higher when you create the array.

---

### Post by scram69 on 2007-11-12
unfortunately, the only md device in /dev/ is md0.  md1-md31 are all in /dev/.static/dev/ .  I can assemble the array using one of the md* in /dev/.static/dev, but it will not persist upon reboot...

---

### Post by fjgaude on 2007-11-12
What happens when you us /dev/md64. I've used that in the past without issue.

---

### Post by scram69 on 2007-11-12
> **fjgaude said:**
> What happens when you us /dev/md64. I've used that in the past without issue.

```
mdadm: error opening /dev/md64: No such file or directory
```

---

### Post by fjgaude on 2007-11-12
I meant to say to assemble the array as /dev/md64... can you do that? Or do you have to re-create it? I think before you can re-create you have to deactivate each drive in the array.

---

### Post by scram69 on 2007-11-13
When I created the array (after copying md1 from /dev/.static/dev/ to /dev/), I created it as md1.  Should I try and re-create as md64?
How do you de-activate a drive?

Thanks-

---

### Post by fjgaude on 2007-11-13
It's a good idea to study, really study, the man pages for mdadm.

First it good to stop, deactivate an array just to be sure:

sudo mdadm --stop /dev/md<whatever>

or

sudo mdadm /dev/md<whatever> -f /dev/sd[nn] -r /dev/sd[nn]

This will declare a drive faulty in an array and then remove it. Then do more as needed.

After you stop an array, I believe you can re-create it as another md[n], like /dev/md64 or whatever.

I hope this helps.

---

### Post by scram69 on 2007-11-14
I didn't know what you meant by "deactivate".  I have tried removing the array using -r:
```
steve@mediaserver:/dev$ sudo mdadm /dev/md1 --fail /dev/hdc1 --remove /dev/hdc1
mdadm: cannot get array info for /dev/md1

```

Anyway, since --assemble gives me the "no such file or directory" message, I tried --create:
```
steve@mediaserver:/dev$ sudo mdadm --create /dev/md64 --level=1 --raid-disks=2 missing /dev/hdc1 --auto=yes
Password:
mdadm: /dev/hdc1 appears to contain an ext2fs file system
    size=38451456K  mtime=Sun Nov 11 20:48:43 2007
mdadm: /dev/hdc1 appears to be part of a raid array:
    level=raid1 devices=2 ctime=Sun Nov 11 10:59:10 2007
Continue creating array? n
mdadm: create aborted.

```
It appears md1 is still resident.  Should I go ahead and "continue" anyway with the creation of /md/64?

---

### Post by fjgaude on 2007-11-14
I don't know what to make of all this either. If you don't have anything of value, or you have your data backed up, then create anew the array using the approach you started and backed out of. I don't know what else to suggest.

Sorry for taking so long to get back to you but have been away from computers most of the day.

---

### Post by scram69 on 2007-11-15
The new disk only has files that were copies of the existing file system, so I went ahead and tried the create using md64.  It appears to have worked.  Although I can't find anything in the mdadm man page that would indicate why md64 would work when md1 would not...

Anyway, thanks for your help!

---

### Post by fjgaude on 2007-11-15
The only thing I can think of is that something was done wrong in creating the md1 and that code is still in some config file somewhere on the computer. I remember something like this happening years ago when the name of an array was given md1p by mistake and mdadm automatically changed the name to md32, if memory serves.

Anyway, it's working... we learn something new everyday, eh?

---

