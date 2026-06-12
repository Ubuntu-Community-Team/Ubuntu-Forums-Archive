---
title: "What to back up?"
date: 2008-01-29
forum: General Help
---

### Post by infamousjre on 2008-01-29
Alright, my laptops very close to kickin the bucket. I'm going to miss the bugger, but the hard drive is full of errors and my battery is completely dead. I'm lucky to be typing this right now after an hour of restarting and fsck'ing.

The thing is, I just got this thing running the way I like it (newly converted to ubuntu that is) and I want to preserve some of what I got.

I'm not very familiar with the unix directory structure, so what I'm really asking is, what do i back up so that I can move my desktop as seamlessly as possible to another computer. Sort of like an Ubuntu Bucket List

I know /home/ for my personal files, but how about my programs?

---

### Post by sumguy231 on 2008-01-29
Since programs aren't kept in their own specific directories in the filesystem, it wouldn't be very viable to copy your applications to the new hard drive. Instead, you can get a list of packages you've installed which you can use to reinstall with later. Use:
```
dpkg --get-selections > packagelist.txt
```
To make a list of installed packages, and on your new system you can use:
```
sudo dpkg --set-selections < packagelist.txt
```
to reinstall everything.

Other than that, you might want to back up any config files in /etc if you've edited them yourself.

---

### Post by nick_h on 2008-01-29
The user configuration for your programs is stored in hidden files and directories in your home directory.

System configuration files are stored in /etc which would be worth backing up.

You may also want to save your package configuration with:
```
dpkg --get-selections > packages.txt
```
so that you can install the same packages on your new installation.

---

### Post by infamousjre on 2008-01-29
thanks. I was kind of hoping there was some sort of list of all my programs, didn't know it would be that awesome and just let me install the entire list on a new computer.

i'm having trouble copying the /etc directory. sudo skips over all of the subdirectories, is there a flag i need to use?

---

### Post by logos34 on 2008-01-29
> **infamousjre said:**
> i'm having trouble copying the /etc directory. sudo skips over all of the subdirectories, is there a flag i need to use?

**sudo cp -r** 

You could also backup /var/cache/apt/archives -- then you wouldn't have to redownload all the packages with sudo dpkg --get-selections < packagelist.txt.  Just an option to consider.

---

