---
title: "Did I just break sudo? Nothing happens!"
date: 2006-08-24
forum: General Help
---

### Post by abalone on 2006-08-24
Followed the Komba2 instructions in the KDE Help Centre:

> You have to change the permissions on smbmount and smbumount. Please note, it can open a security lack on your machine. So be carefull!

It would be enough to change the bit SETUID on smbmnt and smbumount. If this bit is set the programs start with the permissions of the owner (in this case root). Now all users can mount and unmount smb shares.

We tell you now how to set the permissions only to group of users. For following commands you must be root. At first you add a group to your system.

% groupadd sambamount

Now you add the users to the new group. 
% usermod -G sambamount username

Change the group on smbmount und smbumount to sambamount. 
% chgrp sambamount smbumount
% chgrp sambamount smbmount

At least you set the permissions that only users of the group (and root) can run smbmount and smbunmount and set the SUID bit 
% chmod 4750 smbumount
% chmod 4750 smbmount

Now you can use Komba2.

But of course I can't, because it's still not showing me any shares (it does show me the workgroup and my two PCs) -- what's worse, though, I can't seem to sudo *anything* anymore:

```
me@thiscomputer:~$ sudo vim /etc/fstab
me@thiscomputer:~$ sudo ls /
me@thiscomputer:~$ sudo -i
me@thiscomputer:~$ 
```

Nothing happens.

Gah.

Help? Please? Just this once? What's going on?

---

### Post by mlind on 2006-08-24
You have somehow removed yourself from **admin** group. Boot into recovery mode from GRUB menu, and make yourself part of these groups

```

adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner **admin**

```

To see all the groups you're in
```

groups

```

To add user in to group
```

adduser *user* *group*

```

---

### Post by aysiu on 2006-08-24
If *sudo adduser user group* doesn't work (because *sudo* itself isn't working), try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by abalone on 2006-08-25
Thank you! That worked.

---

### Post by ifokkema on 2006-08-26
It happened before recently that a user locked himself out of sudo using usermod -G and came here for advice. I guess this is what to do on some other distro, but in Debian/Ubuntu one uses 'adduser', as described before.

I'm not sure who's to blame - the authors of the how-to not checking the result of the command on other (popular) distros, or the user carelessly copying/pasting commands not knowing what they do? Possibly a little of both...

It's a good thing we have these forums :)

---

### Post by abalone on 2006-08-27
Well -- sure. I'd have been more cautious had this whole user group thing  been more than a sub-sub-problem of uncertain relevance to my *real* "quest". Still, how can you tell in advance which perfectly ordinary commands are "evil" in some given environment and which aren't? When you can't trust the documentation to work on the distro it's installed on, would you ever get anywhere at all? 

So, hm. If I'd been suspicious of usermod, how would I have found out what to do instead? "man usermod" doesn't say "WARNING! I'll break your stuff on Ubuntu!"

You're confronted with multiple Howtos and avalanches of new acronyms/commands/packages/config files while trying to get something to work. Most (sometimes all) of them don't apply to your configuration or are incomprehensible to you at this point. You can spend your nights trying to figure out what portaudio does or how to work JACK or if aoss is what you need in the hope that that might actually be important... or you can give up and just obey the instructions you're given. Which then don't work. ](*,) 

There's simply too much to learn about to bother with every unfamiliar term.

---

### Post by ifokkema on 2006-08-27
Sorry, didn't check before I posted - you installed an *Ubuntu package*, and the package's documentation lists this?!!?? I thought you used KDE documentation, not specifically for any distro.
File a bug at the package:
[https://launchpad.net/distros/ubuntu/+source/komba2/+bugs](https://launchpad.net/distros/ubuntu/+source/komba2/+bugs)

Because it 'breaks' your system quite badly (although not beyond repair) if you follow instructions shipped with the package.

The documentation should be updated to either use:
```
usermod -aG sambamount username
```
or
```
adduser username sambamount
```

The man page for usermod does mention using -G drops you from all other groups, not mentioned in the command. But I userstand you won't go through the man page of every command the documentation tells you to use :)

---

### Post by abalone on 2006-08-27
> **ifokkema said:**
> Sorry, didn't check before I posted - you installed an *Ubuntu package*, and the package's documentation lists this?!!?? I thought you used KDE documentation, not specifically for any distro.

The installed package is version 0.73.beta3-1ubuntu1, from the universe repository. The docs: /usr/share/doc/kde/HTML/en/komba2. 

Bug report still in order?

Frankly I'm not sure Komba2 is working at all - shouldn't it be showing me my samba shares even if I can't mount them as a mere user? But I'm getting along without it now.

---

### Post by ifokkema on 2006-08-27
> **abalone said:**
> The installed package is version 0.73.beta3-1ubuntu1, from the universe repository. The docs: /usr/share/doc/kde/HTML/en/komba2. 

Bug report still in order?
Yes, it is. I hope they fix it before anyone else follows the instructions :)

> **abalone said:**
> (I'm not sure it's working at all (shouldn't it be showing me my samba shares even if I can't mount them as a mere user?) but I've getting along without it now)
That I can't help you with; I don't know the package in question... ;)

---

### Post by abalone on 2006-08-27
The instructions aren't useful for me anyway. I get this when I try to mount "rootlessly":

libsmb based programs must *NOT* be setuid root.
5802: Connection to myothercomputer failed
SMB connection failed

But I'm letting fstab and powersave's resume script handle that now and it *seems* to be working :o

---

### Post by ifokkema on 2006-08-27
I've had my share of problems with this, too. Nowadays I use 'cifs', which is the next generation 'smb'. You can set the mount.cifs and umount.cifs suid, without a problem.

---

### Post by abalone on 2006-08-28
Mh, thanks for the tip. I might try that some time.

---

