---
title: "Ubiquity/d-i, Something Else, No Swap. How?"
date: 2016-03-03
forum: General Help
---

### Post by mikodo on 2016-03-03
Hi,

The last 2 release fresh installs of the Xubuntu .iso dvd (12.04 & 14.04) with ubiquity using the *Something Else* option, I couldn't for the life of me, find how to install without setting a *swap *partition. It just didn't seem to allow me to go forward in the installer, if I didn't set a partition for it.

I don't want one, (swap partition), so what I have done is, as soon as the system is installed, I use Gparted to *swap-off* and then delete that partition.

1. Am I missing an option to allow for no swap partition in the installer? If so, I'll look harder next time.

2. Is the way I have done it with swap-off and removing its' partition the same as having no swap?

3. Swap file. What is that? Does ubiquity make one in the system when, one installs including a swap partition initially or, does the user need to make one if they want it, (I don't). So, using the delete swap partition after install, do I need to look for deleting a swap-file too?

Thank you.

---

### Post by sudodus on 2016-03-03
In the 'Something else' window of the installer, have you tried to turn off swap (select the swap partition and select not to use it)?

If you remove swap afterwards, you should also remove the line specifying it in the file /etc/fstab.

It is possible to have a swap file. I don't know if it is created automatically (I don't think so, I think you have to create it manually).

When booted into the installed system you can check what swap is active with the following command

```
swapon -s
```

You need sudo to turn on and turn off swap, but not to check it.

---

### Post by mikodo on 2016-03-03
> **sudodus said:**
>  - What you wrote -

Hi, sudodus!

No, I haven't tried selecting the swap partition and selecting *not*  to use it. Seems a strange way of doing things. You would think one  would have the choice to have one or not. Maybe d-i is set that way for  unknown reasons to me. I'll try it though.
```
~$ swapon -s
Filename                Type        Size    Used    Priority
- [I]NOTHING -
mikodo@mi[/I]kodo:~$ 
```
And, /etc/fstab shows no swap partition. I must  have zipped it out completely. I don't remember now.

If you think a swap file must be created by the administrator then, that's good enough for me to believe it as *true*.

FYI: I was reading here: [https://wiki.archlinux.org/index.php...kup_with_rsync]("https://wiki.archlinux.org/index.php/full_system_backup_with_rsync")

"If you use a *swap file*, make sure to exclude it as well".

That's what took me down this path. :smile:

Thank you, again!

---

