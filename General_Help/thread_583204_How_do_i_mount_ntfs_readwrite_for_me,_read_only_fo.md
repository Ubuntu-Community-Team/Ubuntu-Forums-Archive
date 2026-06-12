---
title: "How do i mount ntfs read/write for me, read only for others"
date: 2007-10-20
forum: General Help
---

### Post by McQuaid on 2007-10-20
I use ntfs-3g in feisty to mount my ntfs partition like so:

ntfs-3g /dev/hda5 /media/xp/

Here's how it's mount point looks before I mount it:

drwxr-xr-x  2 root root     4096 2007-01-31 13:20 xp

and after running above cmd:

drwxrwxrwx  1 root root     4096 2007-10-20 05:04 xp

I was kind of surprised the actual directory (media/xp) changes it's permissions.  Obviously one can't apply unix style permissions to ntfs dirs, but I thought one could control it by setting the permissions on where they are actually mounting it, so I was kind of surprised that the permissions above change, why is that?    


I haven't set it up in fstab just cause I rarely need the ntfs part.  However I'm going to install gutsy for a friend and I know he'd like to have his ntfs part r/w by him and read only for others.  Even though my mount point has group 'root', I've noticed plugdev is usually the normal group for mount points.  But even setting up the proper group won't give me the ability I need.

And this I think is impossible with mounting ntfs, but say he doesn't want anyone to read his home dir from ubuntu except himself, can that be accompished?

---

### Post by -Zeus- on 2007-10-20
about the home dir, do this

$ sudo chmod 700 /home/<username>/

I *think* this will work.

also, anyone will need to be using sudo to edit the XP partition.

---

### Post by McQuaid on 2007-10-20
Sorry I wasn't clear on the home dir I meant.  I meant his home directory from xp under documents and settings, he'd prefer that to remain private.  I don't think sub dir mounting is possible to give it specific permissions though.

And as I described it on my machine, all users have full read write on my ntfs partition.  And I installed gutsy the other day for a friend and his ntfs parts were automatically mounted with full read/write for all users, no admin privileges required.   There must be a way around that. 

For example users that have accounts for their kids, you might want them to be able to access their xp home directories, but you certainly don't want them to have write access to program files and windows dirs.  There must be a way to mount it so particular users have read/write and other users have only read access.

I thought it would simply be changing the permissions of where one is mounting it, but that has no effect.

---

### Post by LanDan on 2007-10-20
think this one should be moved to [http://www.microsoft.com/forum](http://www.microsoft.com/forum)

---

### Post by McQuaid on 2007-10-20
I hope you're trying to be funny cause that comment kind of annoyed me.

And even though I've been using linux for years, there are some things (lots) I don't know yet.  Or I've learned in the past and have forgotten.

A little bit of investigating and I've seen others have mounted their ntfs with r/w for them r only for others by utilizing gid umask settings in fstab.  I'm not just how this affects a default ubuntu install with it using the group plugdev for mounted drives though.  I'll read more and figure it out, but if anyone has anything (constructive) to add that would be great.

---

### Post by SomethinSnappy on 2007-10-20
> **McQuaid said:**
> I use ntfs-3g in feisty to mount my ntfs partition like so:

ntfs-3g /dev/hda5 /media/xp/

Here's how it's mount point looks before I mount it:

drwxr-xr-x  2 root root     4096 2007-01-31 13:20 xp

and after running above cmd:

drwxrwxrwx  1 root root     4096 2007-10-20 05:04 xp

I was kind of surprised the actual directory (media/xp) changes it's permissions.  Obviously one can't apply unix style permissions to ntfs dirs, but I thought one could control it by setting the permissions on where they are actually mounting it, so I was kind of surprised that the permissions above change, why is that?    


I haven't set it up in fstab just cause I rarely need the ntfs part.  However I'm going to install gutsy for a friend and I know he'd like to have his ntfs part r/w by him and read only for others.  Even though my mount point has group 'root', I've noticed plugdev is usually the normal group for mount points.  But even setting up the proper group won't give me the ability I need.

And this I think is impossible with mounting ntfs, but say he doesn't want anyone to read his home dir from ubuntu except himself, can that be accompished?

What happens if you attempt chmod after it mounted?? I'm still learning over here. :popcorn:

---

### Post by LanDan on 2007-10-20
> **McQuaid said:**
> I hope you're trying to be funny cause that comment kind of annoyed me.

And even though I've been using linux for years, there are some things (lots) I don't know yet.  Or I've learned in the past and have forgotten.

A little bit of investigating and I've seen others have mounted their ntfs with r/w for them r only for others by utilizing gid umask settings in fstab.  I'm not just how this affects a default ubuntu install with it using the group plugdev for mounted drives though.  I'll read more and figure it out, but if anyone has anything (constructive) to add that would be great.

i'm glad i made you smile ;) but i was refering on the permissions settable within NTFS.

you might want to fiddle around with uid and gid options in fstab cause i think ubuntu sets everything rw by default

---

### Post by TheZeusJuice on 2007-10-22
Anybody have a solution? I'm in a similar predicament, i need an NTFS partition rw for my account but ro for the guest account.

 By default, ubuntu runs ntfs-3g under root (which seems to me kinda negates the whole point of using FUSE in the first place, but whatever). So, I was thinking that one possibility is to run separate instances of ntfs-3g for my account and the guest account. But would that work? I'm afraid of concurrency or lock issues, so I haven't tried it. Also, I can't find any information online about such a setup, much less how to go about it.


So, any help anyone?

---

### Post by louieb on 2007-10-22
:twisted:Good thought LanDan. :confused:However don't believe that Linux cares about NTFS permissions.  Maybe it will get built into ntfs-3g someday.  I know when you install  ext2ifs  on windows it sure doesn't care about Linux permissions.  Short term you could create a "public" ntfs partition, mount it and use it for shared data.

---

### Post by mahousaru on 2007-10-22
To mount with ntfs-3g so that the owner and group are 1000 (first user)

```
sudo ntfs-3g /dev/sda1 /mnt -o uid=1000,gid=1000,umask=0022
```

The umask will set it so that you have the following file rights

drwxr-xr-x /mnt

But it does mean that files are counted as executable, so you could use

```
sudo ntfs-3g /dev/sda1 /mnt -o uid=1000,gid=1000,fmask=0133,dmask=0022
```

drwxr-xr-x /mnt

Files will be interperated as 
-rw-r--r--

and directories as
drwxr-xr-x

To automate it in fstab add the line:

```
/dev/sda1 /media/somedir ntfs-3g uid=1000,gid=1000,fmask=0133,dmask=0022 0 0
```


For those who want to increase their geek levels, the f and d masks work like this.

start with 7777 

The first number in the octal is a special character which you can ignore for now, so lets use 777

Now lets say you wish to create files with the following rights

-rw-r-----

Now each number matches up to rwx rwx rwx, would be 7 7 7, because:
r = 4
w = 2
x = 1

So for the required file rights we want 

6 4 0

so do 7-6 7-4 7-0
Which gives a mask of 1 3 7.  So setting fmask as 0137 would mean files are considered to have the rights 

-rw-r-----

And the same is for dmask but that affects directories

---

### Post by McQuaid on 2007-11-04
Awesome post mahousaru!! Thank you

---

