---
title: "Resizing Partitions 'on the fly'"
date: 2007-04-10
forum: General Help
---

### Post by Catsworth on 2007-04-10
Hey Guys,

When I installed Edgy I totally screwed up my partitioning scheme and made /home/ waaaaay to small.  I've now run out of space in /home/ and would like to steal some from one of the other partitions so that I can keep working for a while longer.

I'm planning on reinstalling some time soon, I just need to fiddle a little bit to get me by for now.

Is it possible to change the size of /home/ and take some space from somewhere else?  Is it safe to do so?  I really don't want to lose any data and I can't afford to screw up the install.

Are there any system partitions (/root/ for example) that I shouldn't touch, or can I take the space from anywhere that I have it?

Is it safe to steal space from my Windows (dual-booted) install, or is that asking for trouble?

Thanks.

---

### Post by dfreer on 2007-04-10
hmmm. If you just need a little more space, you could always use a symbolic link to store stuff on the other linux partition. So let's say I have extra space on my / partition.
```
sudo mkdir /myhomestuff
sudo chown `whoami`:`whoami` /myhomestuff
sudo ln -s /myhomestuff ~/extraspace
```
just throw extra stuff in there. although resizing the partition might be okay, this way is definitely safe. You should be able to do the same thing with the windows partition, if you can read/write to it from Ubuntu.

---

### Post by Catsworth on 2007-04-10
Cool, didn't know that could be done that way - thanks for that.  I'll have a look at that tonight.  I take it that I'd need to set specific file permissions on that particular directory to match the home directory I'm trying to extend?  *chown* won't automatically replicate those permissions where I've set them up specially will it?

---

### Post by dfreer on 2007-04-10
Well, basically this method would create a folder in your */home/yourusername* called *extraspace* with drwxr-xr-x permissions for yourusername. So that folder would have the extra space, and that folder only, the /home partition would still be full. This is useful if you have say a large music collection located in your home directory that is taking up all your space. You could move it into this folder, and although it would appear to be on your /home partition it will really be on your root partition, if this makes any sense. Sorry, I speak english I just don't think straight lol.

---

### Post by az on 2007-04-10
> **dfreer said:**
> Well, basically this method would create a folder in your */home/yourusername* called *extraspace* with drwxr-xr-x permissions for yourusername. So that folder would have the extra space, and that folder only, the /home partition would still be full. This is useful if you have say a large music collection located in your home directory that is taking up all your space. You could move it into this folder, and although it would appear to be on your /home partition it will really be on your root partition, if this makes any sense. Sorry, I speak english I just don't think straight lol.

I'm not a fan of the seperate partition for the home drive for this reason.  And using this workaround takes away the (potential) advantage of keeping a seperate home partition.

The next time you reinstall, just put everything on the root partition like the default.  Back up your home partition the traditional way, if needed.

---

### Post by Austin_KW on 2007-04-10
You need never run out of space on a linux system, just mount a new partition/disk where you need it (/home, /home/user, /home/user/newfiles etc)

Even if you put everything on a single partition it does not stop you from adding a new disks/partitions later, where you need them. But having a seperate /home partition could save you a lot of grief if you decide to upgrade/reinstall/try a different distribution or OS

---

### Post by dfreer on 2007-04-11
> You need never run out of space on a linux system
,,,unless you are too poor to buy another hard drive :( lol

---

