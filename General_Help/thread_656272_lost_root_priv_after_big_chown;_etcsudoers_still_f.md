---
title: "lost root priv after big chown; /etc/sudoers still fine"
date: 2008-01-02
forum: General Help
---

### Post by AR_Kozz on 2008-01-02
Have mysteriously lost root power on my Feisty partition...

This is weird and it has me stumped. Annoyed at locked game files in my /usr folder that kept them from running properly, I used sudo to 

sudo chown -R (me) /usr

that is, recursively gave myself ownership of the entire /usr folder and everything in it.

But now every time I try to sudo I get

sudo: must be setuid root

I have logged in in recovery mode to check out the usual suspects. My username still exists, and /etc/sudoers is as it should be, set to all;
in fact, it is identical to the one in my dapper-installed partition where sudo still works for me.

Anyone know of anything else that may be the culprit, that I could go back to recovery mode and fix quicker than it would take to reinstall?

---

### Post by rubicon on 2008-01-02
Well, it seems that owner of some files in /usr must be root.

I have experienced almost the same problem when changed owner of /var (there is folder /var/run/sudo, which must be owned by root), and I just boot in single-user mode (from GRUB) and changed permissions back.

Try booting in single-user mode, then do "chown root:root -R /usr" back. This is dirty method, but I think this'll work :)

---

### Post by rubicon on 2008-01-02
But I must warn -- this way you could break something. For example, when I did "chown root:root -R /var", locate tool broke. Because /var/lib/slocate/ must be owned by root:slocate, not root:root. So be careful.

---

### Post by chrisccoulson on 2008-01-02
The problem is is that the sudo executable is no longer owned by root, and the error message also suggests that the setuid bit is no longer set. You'll need to chown /usr/bin/sudo (at least) back to root again (although I would go with the above suggestion and chown the whole of /usr back to root) and set the setuid bit of /usr/bin/sudo using chmod, or sudo won't work anymore.

---

### Post by jken146 on 2008-01-02
Don't chown things outside of /home!  Chances are you'll break something.

---

### Post by chrisccoulson on 2008-01-02
> **jken146 said:**
> Don't chown things outside of /home!  Chances are you'll break something.

Good advice, but in this case it is too late though.

---

### Post by Furat on 2008-01-02
I think it is better to do chown -R root /usr 
and not 
chown -R root:root /usr
since you didn't change the group in first command

---

### Post by capink on 2008-01-02
if you have a live cd, copy the contents of the live cd /usr over your system /usr :

1. Boot the computer using your live cd.
2. Make a new directory to mount the partition containing your installation:

```
mkdir rootfs
```

3. Run fdisk to know the device name of you partition:

```
sudo fdisk -l
```

from the output of the previous command you can know the device name of your installation partition (e.g /dev/sdaX)

4. Mount your installation partition:

sudo mount -t ext3 /dev/sdaX ./rootfs

5. Copy the live cd /usr over your installtion /usr

```
sudo cp -avf /usr/* ./rootfs/usr
```

Or you can use rsync instead

```
sudo rsync -av /usr/* ./rootfs/usr
```

Edit: Added the -f option to the cp command

---

### Post by AR_Kozz on 2008-01-03
A lot of good answers and I'll try them in the order that seems best and post back

But what is there in the /usr folder that has to be root-owned in order for sudo to work? 

Oh wait I see it. The binary sudo is in /usr, I thought it was in /bin. That explains it.

---

### Post by chrisccoulson on 2008-01-03
> **AR_Kozz said:**
> A lot of good answers and I'll try them in the order that seems best and post back

But what is there in the /usr folder that has to be root-owned in order for sudo to work? 

Oh wait I see it. The binary sudo is in /usr, I thought it was in /bin. That explains it.

I would raise the question the other way around - what is there in /usr that needs to be user-owned in order for you to get working. You should never need to chown or mess with permissions on anything in /usr, except for maybe something you've installed manually from source. In that case, you'd do adjust ownership / permissions on only the files / folders concerned.

---

### Post by AR_Kozz on 2008-01-03
whoa, I made another post a few hours ago maybe I hit preview and not "submit"

Anyway it was to the effect that, as you, C.C., said, and as my terminal kept repeating, the setuid bit needed to be set back on. 

I knew chowning /usr was a risky move but not that sudo resided there... if it hadn't I could have dealt with the consequences easier.  I was searching via gnome 
through endless trees of stuff that autoinstallers had improperly set to root

anyway all that was needed to get sudo back was to chown it to root in recovery, and then chmod with the 4- prefix.

I expect it will be far easier to go back and find everything in /usr that should be root, than it would have been to have everything set to root and have to go back and reset all the stuff that I don't want root-privileged. The 1st may take a while but the 2nd would have taken forever.

Most of my /usr stuff is 3rd party - that is, not from repo or debian install, yet the installers put it there anyway before I have a chance to route it to home.

---

### Post by capink on 2008-01-03
> **AR_Kozz said:**
> 
But what is there in the /usr folder that has to be root-owned in order for sudo to work? 


the file /usr/bin/sudo need to be suid in order to work properly.
When you change ownership you lose the suid. ( i.e set user id)
So setting suid for /usr/bin/sudo would have the trick for you. But I guess you would still face some problems from other binaries in /usr

---

### Post by rubicon on 2008-01-03
Normally, when you do ```
ls -Al /usr/bin/sudo
```, you see ```
-rwsr-xr-x 2 root root 107776 2008-01-02 16:38 /usr/bin/sudo
```. You may use it as reference :)

---

### Post by capink on 2008-01-03
> **rubicon said:**
> Normally, when you do ```
ls -Al /usr/bin/sudo
```, you see ```
-rwsr-xr-x 2 root root 107776 2008-01-02 16:38 /usr/bin/sudo
```. You may use it as reference :)

In other words peform these two commands:

```
sudo chown root.root /usr/bin/sudo
```

```
sudo chmod 4755 /usr/bin/sudo
```

But since you cannot use sudo you will have to do it from a live cd after mounting you root partition. So the command should be modified to:

```
sudo chown root.root /path/to/root/usr/bin/sudo
```

```
sudo chmod 4755 /path/to/root/usr/bin/sudo
```

---

### Post by -Zeus- on 2008-01-03
couldn't you just boot to recovery mode?...

---

### Post by AR_Kozz on 2008-01-06
to the 4 or so people who posted after my last post, thanks, but you could have saved yourselves a bit of effort, as I said up above all I needed to do was, indeed, to reset the uid bit with a chmod, and that's what I did...
IOW the problem is resolved

---

