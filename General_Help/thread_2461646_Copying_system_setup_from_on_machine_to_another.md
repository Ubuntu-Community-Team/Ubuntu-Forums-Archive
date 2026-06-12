---
title: "Copying system setup from on machine to another?"
date: 2021-05-04
forum: General Help
---

### Post by GhX6GZMB on 2021-05-04
I have two HW-wise identical laptops (HDD size and RAM size differ).

I'm trying to make two identical machines SW-wise. One is already running perfectly, the other has a base 20.04 install which boots just fine.
The machines have different UUIDs and users, and that's how it's supposed to be.

My idea was copying the / file system from the running machine to the new one, but excluding the following files:

```
/etc/default/grub
/etc/fstab
/etc/passwd
/etc/nsswitch.conf
```

This doesn't work, unfortunately. After doing the copy, login is no longer possible (password not accepted).

Two questions:
1: Is this idea insane?
2: If not, what else do I need to exclude from the copy to make it work?

Thank You.

---

### Post by oldfred on 2021-05-04
You should just need to copy /home.
That has all your user settings.

If you have installed a lot of software you can export list of installed apps and use that to reinstall everything on 2nd system.

My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

### Post by GhX6GZMB on 2021-05-04
Apparently, I expressed myself badly.
I have /home fully under control and I do not want to copy it (it's on a separate partition, BTW).

I want to copy / to a new machine to create an identical software setup, but with other users. A machine that's a copy of the first when it comes to installed programs, setups etc.

---

### Post by guiverc on 2021-05-05
I have no recent experience of any value sorry.

I volunteered at a recycler ([https://www.computerbank.org.au/](https://www.computerbank.org.au/)) years ago where we removed drives of donated hardware,  dban was run on drives, then the customized Ubuntu was cloned onto the drives and they were just stacked according to drive capacity.

During the 'build' phase of the process a drive of wanted capacity was grabbed, put into the box and the system booted & verified that everything was working as expected (minor things like audio tweaked, boot time stop watched, graphics tested and drivers added if required etc) & once checklist was completed, form was completed, box priced and it was was moved to the 'shop'.

We straight cloned drives... 

I do **note** you mention `/etc/passwd` but not the *secondary* password file (`/etc/shadow`). Was that an error?, as I can't imagine not ensuring both are in sync.   (*since you're changing usernames; if you're missing that file that could create problems for you!  I forget what the effects are if not in sync, but I'd expect problems*)

---

### Post by GhX6GZMB on 2021-05-05
@guiverc, 1000 Thanks.
I was _not_ aware of /etc/shadow and it seems very likely that that's part of my problem.

I'll try that tonight.

---

### Post by TheFu on 2021-05-05
> **ml9104 said:**
>  
Two questions:
1: Is this idea insane?
2: If not, what else do I need to exclude from the copy to make it work?

1: No.
2: Too many things to list and we'd have to assume all sorts of things that haven't been said which may not be correct.  Identical hardware seldom is truly identical, even when contractually mandated during procurement.  Versions of chips get modified in the supply chain, for example.

fstab, networking, users, groups will all be different, assuming everything really is identical.

It is not possible to safely clone a running OS.  Open files prevent that from working correctly.  You can mirror it using an rsync running as root for a first pass of each partition, but you'll need to boot from alternative media, connect 2 storage devices/partitions under that other OS, then re-run rsync (as root again) to get clean copies of all the files that weren't possible to get before.

BTW, when copying files, you'll need to exclude all FIFOs, Queues, Sockets and Named pipe files from the copy.  After all, reading from /dev/random will never complete - not ever.

Then you'll need to go back into the target file system, modify the passwd, group, shadow, gshadow files to be consistent. Don't forget to move whatever the old HOME directories in passwd were to the new names. That isn't strictly mandator, but username "joe" would love to cd ~joe and end up in /home/joe, not /home/user1.  This won't harm anything except the human's brain.  HOME directories don't need to map to the username, humans just prefer that.

Ok, so you can do that stuff and deal with the other little things that will come up, if any.
OR
you can use your backup/restore method to move everything to a new system. I've written about what to backup here 20+ times and I've written what needs to be restored, in what order once.  [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

There are lots of things possible when we understand the userid/username/uid and groupid/groupname/gid relationships and can manually manipulate those.  At restore time, it is really easy to handle those manipulations.

Another key idea is to place system stuff only in /etc/ and personal stuff only in HOME directories.  Some tools will put localized settings into /lib/ or /var/lib/ ... which really isn't following the Linux file system hierarchy standards.  For example, ufw commands get put into /lib/ufw/, so if you have used those and have them persistent between boots, then you'll need to backup /lib/ufw/ in addition to /etc/.  I specifically DON'T use ufw commands directly to avoid that. UFW settings belong in /etc/ufw/ ... where is unimportant to me, since I backup all of /etc/ for my sanity.  Same for systemd-unit files that I've customized.  I force those to be under /etc/ so backups get them, regardless of where systemd wants them.

As you can see, it is easy for each system to be a little different and the way that each admin actually performs their admin duties can drastically impact which areas need to be backed up.  On a desktop, I backup:
```
my $backup_sources  = "--include /root
--include /etc
--include /var/www
--include /var/log/nginx
--include /var/lib/awstats
--include /usr/local
--include /home";
```
That is directly from the backup script.

On a VM server, I backup:
```
my $backup_sources  = "--include /root
--include /etc
--include /usr/local
--include /home";
```
I don't backup each VM - they are responsible for their own backups.  Anyways, you get the idea.

---

### Post by GhX6GZMB on 2021-05-05
_First, let me report success!!!_

The scenario was to set up a "new" HW-identical laptop as an existing one, with new UUIDs, users etc., but to avoid reinstalling programs and program settings. This sort of ruled out the backup/restore scenario.

I copied the complete / file system fron the existing/running machine onto the new one (freshly installed with a new root user), but excluded the following files:

```
/etc/fstab/
/etc/passwd
/etc/passwd-
/etc/shadow
/etc/shadow-
/etc/group
/etc/group-
/etc/gshadow
/etc/gshadow-
[COLOR=#ff0000]/etc/subgid
/etc/subgid-
/etc/subuid
/etc/subuid-
/etc/hosts
/etc/hostname[/COLOR]
/etc/default/grub
/etc_nsswitch.conf
```

The reference from @guiverc to the /etc/shadow file was gold, but I also found that the new /etc/group needs to be left undisturbed.

@TheFu: you're the guru here on this kind of thing, but your own setups are so complicated and involved that I get lost. This is no criticism, quite the opposite. Your expertise is needed.
I only have personal stuff and settings under /home. /etc and /usr and such are strictly reserved for the system.
I understand your reference to HW not being always the same, but in this case it's not so.

I Thank You both.

Cheers.

EDIT: I've added a couple of files to my list that should also NOT be copied to the new system (in red).

---

### Post by scorp123 on 2021-05-06
> **ml9104 said:**
> ... to create an identical software setup ...

Then why not just tell **"dpkg"** to do that for you? Let the packet manager handle that.

On the original installation you do this:
[LIST]
[*]copy **/etc/apt/sources.list**  to the target computer  ... this file needs to be identical on the target
[*]copy **/etc/apt/sources.list.d/***  to the target computer  ... if there's anything here. These files also need to be on the target.
[/LIST]

Then tell **"dpkg"** to write down what's installed into a file:
```
sudo dpkg --get-selections > mypackagelist.txt
```

Copy that file "mypackagelist.txt" to the target too.

Then, on the target computer, do:
```
sudo dpkg --set-selections < mypackagelist.txt
```

The target computer will mark all the packages the original computer had as packages it now wants too.

Then you just trigger the re-installation of everything:
```
sudo apt-get dselect-upgrade
```

The result should now be that the target computer has the exact same packages the original computer had, independent of any user accounts that might or might not be present, network configuration, etc. This just "clones" what software was installed on the original and tells a target computer to go and install the same stuff, it doesn't mess with anything else.

---

### Post by TheFu on 2021-05-06
*dpkg --get-selections/--set-selections* leaves packages inside APT with less-than-great tags for the installed packages. They all get marked as manually installed, so dependencies which would be removed later should another package be deleted from the system won't be removed.  Just something to consider.

But **apt-mark showmanual** can make lists of manually installed packages which can be used similar to the technique provided. By only installing the manually installed packages and letting the dependency engine solve that aspect, we have correct dependencies on the new box. Just something to consider.

---

### Post by him610 on 2021-05-07
Something I do; maybe it will help you. 
Perhaps you have some unique aliases you have defined in .bash_aliases file. A new installation does not come with .bash_aliases installed in its home directory. You can immediately use your previously defined aliases after you *scp* the file from your origin system to your clone system.

---

### Post by GhX6GZMB on 2021-05-08
> **him610 said:**
> Something I do; maybe it will help you. 
Perhaps you have some unique aliases you have defined in .bash_aliases file. A new installation does not come with .bash_aliases installed in its home directory. You can immediately use your previously defined aliases after you *scp* the file from your origin system to your clone system.

Thank You.
I have no aliases or anything like that, my machines are relatively simple.

I just wanted to avoid the hassle of reinstalling and reconfiguring everything, and that worked extremely well in the end.

BTW, it's not a "clone", but just an identical setup.
A clone would have been easy (eg, a Timeshift restore).

---

### Post by wyattwhiteeagle on 2021-08-31
> **scorp123 said:**
> Then why not just tell **"dpkg"** to do that for you? Let the packet manager handle that.

On the original installation you do this:
[LIST]
[*]copy **/etc/apt/sources.list**  to the target computer  ... this file needs to be identical on the target
[*]copy **/etc/apt/sources.list.d/***  to the target computer  ... if there's anything here. These files also need to be on the target.
[/LIST]

Then tell **"dpkg"** to write down what's installed into a file:
```
sudo dpkg --get-selections > mypackagelist.txt
```

Copy that file "mypackagelist.txt" to the target too.

Then, on the target computer, do:
```
sudo dpkg --set-selections < mypackagelist.txt
```

The target computer will mark all the packages the original computer had as packages it now wants too.

Then you just trigger the re-installation of everything:
```
sudo apt-get dselect-upgrade
```

The result should now be that the target computer has the exact same packages the original computer had, independent of any user accounts that might or might not be present, network configuration, etc. This just "clones" what software was installed on the original and tells a target computer to go and install the same stuff, it doesn't mess with anything else.


Will this work in going from Ubuntu to Lubuntu?

---

### Post by wyattwhiteeagle on 2021-08-31
> **wyattwhiteeagle said:**
> Will this work in going from Ubuntu to Lubuntu?

Nevermind...I asked that before actually checking the files.

It won't work going from the Main Ubuntu to a lighter Ubuntu.

---

### Post by monkeybrain20122 on 2021-08-31
I used to do that quite a bit even for unidentical hardware: use fsarchiver to make a clone (you can exclude directories in your $HOME) then restore to the second machine. Done. Might have to reinstall grub.

---

