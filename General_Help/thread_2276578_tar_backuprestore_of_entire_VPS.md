---
title: "tar backup/restore of entire VPS"
date: 2015-05-03
forum: General Help
---

### Post by Vaindil on 2015-05-03
I'm running a VPS and I need to remove/recreate it for housekeeping purposes. I've started [this guide]("https://help.ubuntu.com/community/BackupYourSystem/TAR") for creating a complete tar backup, and I will download that when it is complete. Before I start, however, I have several questions. (This is specifically regarding my VPS which is running Ubuntu Server 15.04, but I assume the answer will apply to other variants as well so I'm posting in the General Help forum.)


First, running the backup itself. I started the backup using the command "sudo tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --one-file-system /". It errored out while running, however, with the error "tar: /: file changed as we read it". How do I avoid this problem? I'm not running anything critical, so anything that changes can be ignored--using either the old or the new version is fine. Is there a way to make tar just try again to read the specific file that changed?


That guide assumes that the device can be booted from live media, which I cannot do with my VPS provider. I will actually have to reimage the system with Server 14.04. Will I be able to simply put the full backup tar at the root, then run "sudo tar -xvpzf /backup.tar.gz --numeric-owner" ? I feel like this wouldn't work, but I don't know, which is why I'm asking. 


My third question involves the fact that I'll be reimaging with Server 14.04. Both will be x64, so that's not an issue, but, assuming the above question is answered and works, is it okay to completely overwrite 14.04 with my full 15.04 backup? It doesn't matter to my VPS provider, I know that, I just don't know if 15.04 over 14.04 would create an issue.


Any advice would be greatly appreciated. Thank you!

---

### Post by SeijiSensei on 2015-05-03
You VM provider should have a utility that will let you take a snapshot of the virtual machine.  Then if something goes awry, you just spin that up as a new VM.  I use [Linode](http://www.linode.com/) and have taken advantage of snapshots when I'm making changes to VMs.

Overwriting 14.04 with 15.04 could work or it could not. Personally I'd try a bit longer approach:

1) Use "dpkg -get-selections" to build a list of installed packages on the 15.04 machine.  Run "dpkg --set-selections" on the 14.04 machine to have it install the comparable set of packages.  See "man dpkg" for details.

2) Copy the contents of /home from the old machine to the new.  I'd use rsync for this task since both machines should be visible to each other over the Internet.

I'd probably reboot now and see how well things are working.

3)  Now comes the tricky part.  If you have made customizations that are stored in /etc, you'll need to copy that over as well.  For instance, the Apache webserver configuration resides in /etc/apache2.  It's possible that some of the default 15.04 configuration files in its copy of /etc are incompatible with the versions of those files on the 14.04 machine.  I'd say the risk is probably small, but I'd first copy /etc to /etc.old on the 14.04 machine before using rsync to transfer the copy of /etc from the 15.04 machine.  

If things don't come back up properly after moving the files, you can delete the 14.04 VM and start over.  Better yet, if the VM provider offers you a virtual terminal visible over the Web, you can boot up in recovery mode then move /etc.old back to /etc.  Then if the server boots, you can figure out what differs in the two versions of /etc.

---

### Post by Vaindil on 2015-05-03
My provider unfortunately doesn't offer that capability right now, which is why I need to do things this way. I can put in a ticket to see if they can do it manually for me, but it isn't something they have. Thank you for the other information though, it's very helpful.

I know 15.04 is only supported for 9 months. The only critical thing I have running is my personal website, which gets like 1 view per month so I'm not too worried about that. I mainly have it just to play around with, really. I have a lot of stuff installed on it though, which is why I'd like to take a full backup rather than simply getting a list of packages and reinstalling them manually.

Edit: Looks like you edited your post while I was writing mine. I only have one server; I unfortunately have to back up the one server, remove it, create a brand new one, then restore the backup. I do have access to a virtual terminal though.

---

### Post by matt_symes on 2015-05-03
Hi

> sudo tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --one-file-system /

You can create the backup file before running the tar command.

```

sudo touch /backup.tar.gz && sudo tar -cvpzf /backup.tar.gz --exclude=/backup.tar.gz --one-file-system /
```

It should still create the backup file though, even if the backup file is missing and you are getting that error.

Why are you not "--exclude"ing pseudo filesystems such as /sys, /proc, /dev, any tempfs and other file systems ?

Anyway the tar'ed file can be downloaded to a safe machine. Another point. Do you have space on the vm's hard drive to create the tar file ?

> That guide assumes that the device can be booted from live media, which I  cannot do with my VPS provider. I will actually have to reimage the  system with Server 14.04. Will I be able to simply put the full backup  tar at the root, then run "sudo tar -xvpzf /backup.tar.gz  --numeric-owner" ? I feel like this wouldn't work, but I don't know,  which is why I'm asking.

I've never tried this so i can't say 100% if it will work or not but it leaves me very uneasy. It will leave multiple versions of libraries on your system at a minimum, could cause apt and dpkg problems, maybe leave the alternatives inconsistent, potential bootloader problems.....

...you'll be untaring a 15.04 archive over a live 14.04 filesystem and tar'ing a live, and so changing, 15.04 filesystem. You'll have to be very careful with what you exclude from the tar.

Are you moving from 15.04 to 14.04 and staying on 14.04 (a sensible choice unless 15.04 is needed for a specific reason and this is what i'm really unclear about ) ?

Can you clarify this please.

Anyway, If so, then i would think the advice from SeijiSensei is doubly worth considering when setting up the 14.04.

You would need an...

```
sudo apt-get dselect-upgrade
```

...after setting the selections (--set-selections) IIRC.

Are you using any PPAs ? I don't suspect so but just in case you are then don't forget them.

Upgrading is easier than downgrading.

If you're intending to stay on 15.04 (crazy unless you have some very specific reason) then a 14.04 -> 15.04 upgrade and then untaring your backup *may* work better than untaring 15.04 over 14.04 but i still don't like it.

... so you may want to consider changing providers.

Kind regards

---

### Post by Vaindil on 2015-05-03
> **matt_symes said:**
> Why are you not "--exclude"ing pseudo filesystems such as /sys, /proc, /dev, any tempfs and other file systems ?
The guide says "--one-file-system" automatically skips those. Do I need to "--exclude" them even with that flag?

> **matt_symes said:**
> Anyway the tar'ed file can be downloaded to a safe machine. Another point. Do you have space on the vm's hard drive to create the tar file ?
Yes, according to ncdu I'm only using ~3GB and I have 20GB of space total.

> **matt_symes said:**
> Are you moving from 15.04 to 14.04 and staying on 14.04 (a sensible choice unless 15.04 is needed for a specific reason and this is what i'm really unclear about ) ?

Can you clarify this please.
I would like to stay on 15.04. I like having newest versions, and this server is only running things for personal use, so I'm not concerned about it only being supported for 9 months.

> **matt_symes said:**
> If you're intending to stay on 15.04 (crazy unless you have some very specific reason) then a 14.04 -> 15.04 upgrade and then untaring your backup *may* work better than untaring 15.04 over 14.04 but i still don't like it.

... so you may want to consider changing providers.

Kind regards
I'd love to change providers, but I paid a one-time fee and it's a pretty acceptable service so I'm sticking with it while I can (I just back up my config files as necessary).

I guess what I'll end up doing is getting a list of all installed apps ("dpkg --get-selections > packages"), then figure out which ones I actually need to reinstall (just the important ones; I'll let apt figure out any dependencies). I'll save that list separately and back up all of the necessary files, then manually reinstall all of them. This will be my way of cleaning house while doing this. :)

Thank you everyone, I appreciate it!

---

### Post by matt_symes on 2015-05-03
Hi

> The guide says "--one-file-system" automatically skips those. Do I need to "--exclude" them even with that flag?

Far enough, i missed that. It's now 3.45 am in the UK and i really should have gone to sleep hours ago. You don't need to --exclude them with the --one-file-system switch. You can, of course, check what that switch will exclude using the mount command.

> I would like to stay on 15.04.

Seriously ? Personally i usually stick to LTS for servers and upgrade desktops regularly; although this particular laptop - my main one - is still on 14.04 and likely to stay that way for a while yet. 

But it's your choice to upgrade your server as much as you like and, as you say, the only important part is your website so you may want to get a separate backup of that by itself.

Post back on how it goes. I'd be interested to hear what you decide to do.

Good luck :)

Kind regards

---

### Post by SeijiSensei on 2015-05-04
I suggest excluding the following directories from the backup; they are recreated anew at every boot. "One-file-system" should have the same effect, but I prefer to be literal.
```

/proc
/sys
/dev
/run

```
You might want to use the "--files-from" and "--exclude-from" options to tar to prune the backup.  I'd tar /etc to its own backup and omit it from the main one.  Then when you unpack the backup you can see what happens with the 15.04 image and the 14.04 /etc directory.

---

