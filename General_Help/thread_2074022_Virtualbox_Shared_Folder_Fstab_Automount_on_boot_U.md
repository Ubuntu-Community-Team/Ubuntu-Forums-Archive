---
title: "Virtualbox Shared Folder Fstab Automount on boot Ubuntu 10.04 and/or 12.04"
date: 2012-10-20
forum: General Help
---

### Post by deckerry on 2012-10-20
[SIZE="4"]**_PROBLEM:_**[/SIZE]

[COLOR="Red"]My shared folders won't automount at startup. Please help.[/COLOR]

Host: Windows 7
Virtualbox Guest 1: Ubuntu Server 12.04
Virtualbox Guest 2: Ubuntu Desktop 10.04

I'm trying to integrate the Documents folders on all my machines. (Or, at the very least, set up a shared folder to automount on startup.)

Step 1:
I used the Virtualbox interface to setup a shared folder, selecting the correct host path ```
C:/users/username/Documents
``` and checking "Make Permenant."

Step 2:
On my UbuntuServer12.04 guest, I created a mountpoint directory, ```
/home/username/Documents
```. On the other guest, there is already a Documents folder which I will use as the mountpoint.

Step 3:
I entered this into /etc/fstab on both guest systems:
```
Documents	/home/username/Documents	vboxsf	uid=username,gid=groupname	0	0
```

Step 4:
I even tested /etc/rc.local (made sure it was executable) by adding one of these three lines (tested one line, rebooted, replaced it with the next line, rebooted, tested the third...):

```
mount /home/username/Documents
```
```
mount Documents
```
```
mount -t vboxsf Documents /home/username/Documents
```
```
mount -a
```

I'm pulling my hair out faster than it's already thinning and I'm going to go balled in no-time if I don't get some help (know what I mean?)

[SIZE="4"]**_SOLUTIONS:_**[/SIZE]

Shared folders are automatically mounted in /media/sf_sharename. There are 2 ways to make your shared folder appear where you actually want them to go.

[SIZE="3"]**Solution 1:**[/SIZE]
Bind them to another folder.

1: Check if you are in the vboxsf group with ```
groups username
```

2: If you don't see vboxsf, join the group by doing this, otherwise skip to step 3: ```
sudo usermod -a -G vboxsf username
```

3: Bind the automatically generated shared folder to your mountpoint by putting this line into /etc/rc.local: ```
mount --bind /media/sf_sharename /path/to/mountpoint
```

[SIZE="3"]**Solution 2:**[/SIZE]
Just make a symbolic link:
```
ln -s /media/sf_sharename /wherever/you/want
```

---

### Post by Morbius1 on 2012-10-20
Since Version 4 of Virtual Box  a Linux guest will automatically mount all host shared folders to:
> /media/sf_*name-of-vbox-host-shared-folder*
Does that by itself without any interventions on the users part.

---

### Post by deckerry on 2012-10-20
> **Morbius1 said:**
> Since Version 4 of Virtual Box  a Linux guest will automatically mount all host shared folders to:

Does that by itself without any interventions on the users part.

Oh my freakin' goodness. I didn't see that one coming. THANK YOU!!!!!!!!

But Damn. I don't like that at all. How would you make content from ```
/mount/sf_Documents
``` show up in ```
/home/username/Documents
``` at startup then? By editing /etc/fstab or /etc/rc.local somehow?

---

### Post by Morbius1 on 2012-10-20
You could create a symlink from one to the other.

You could also bind it from one to the other:

For a temporary bind mount try this:
```
sudo mount --bind /media/sf_Documents /home/username/Documents
```If that does what you want then stick that in rc.local - without the sudo.

I prefer binds to symlinks but that's just me.

---

### Post by deckerry on 2012-10-20
Well, on my UbuntuServer12.04 guest, I just made a symbolic link and it works:

```
ln -s /media/sf_Documents /home/username/Documents
```

But on my UbuntuDesktop, the changes to either /etc/fstab or /etc/rc.local were enough (even though there were directories in /media produced by Virtualbox.) Then I'm left with both the /media/sf_Documents folder AND folders mounted by /etc/fstab.

Weird... and messy...

NOTE: I posted this before reading the one by Morbis1, which is basically makes the thread solved. Thank you Morbis1!!!!!!!!!!!!

---

### Post by deckerry on 2012-10-20
> **Morbius1 said:**
> You could create a symlink from one to the other.

You could also bind it from one to the other:

For a temporary bind mount try this:
```
sudo mount --bind /media/sf_Documents /home/username/Documents
```If that does what you want then stick that in rc.local - without the sudo.

I prefer binds to symlinks but that's just me.

My only problem with symbolic links is this: If you are using Ubuntu Desktop with GNOME, you'll have to delete the original Documents folder which has cool little folder icons different from regular folder icons.

---

### Post by deckerry on 2012-10-20
> **Morbius1 said:**
> You could create a symlink from one to the other.

You could also bind it from one to the other:

For a temporary bind mount try this:
```
sudo mount --bind /media/sf_Documents /home/username/Documents
```If that does what you want then stick that in rc.local - without the sudo.

I prefer binds to symlinks but that's just me.

I absolutely love your --bind idea except there are permission issues. I tried this but it didn't work either: ```
sudo mount --bind -o uid=username,gid=groupname /media/sf_Documents /home/username/
```

---

### Post by deckerry on 2012-10-20
> **deckerry said:**
> I absolutely love your --bind idea except there are permission issues. I tried this but it didn't work either: ```
sudo mount --bind -o uid=username,gid=groupname /media/sf_Documents /home/username/
```

I figured it out. The only reason binding wouldn't work is because I wasn't part of the vboxsf group. Here's how I joined the group:

```
sudo usermod -a -G vboxsf username
```

---

