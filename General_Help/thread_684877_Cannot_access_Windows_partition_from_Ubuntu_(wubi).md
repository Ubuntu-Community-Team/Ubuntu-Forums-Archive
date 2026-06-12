---
title: "Cannot access Windows partition from Ubuntu (wubi)"
date: 2008-02-01
forum: General Help
---

### Post by breaking on 2008-02-01
Hi, i'm having some difficulty here, wondering if someone can help me out..
I've installed Wubi 7.10 on my Dell Inspiron 1520 laptop. Everything works beautifully, including the wireless, which was a pain in the *** to setup. The only thing that I can't figure out is why I can't access the Windows system partition from within Ubuntu. When I try to mount it, I get this error:
```

fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda2 ()

```
This is the line from my /etc/fstab
```
/dev/sda2   /media/Windows   ntfs   ro,auto,user,fmask=0111,dmask=0000   0   0
```
Any ideas?

---

### Post by jan quark on 2008-02-02
pls run the following commands and post the results

```
mount
```

```
sudo fdisk -l
```

---

### Post by ago on 2008-02-02
If this is the partition where you have wubi, it will be available as /media/host in 7.10 and /host in 8.04

---

### Post by breaking on 2008-02-05
> **ago said:**
> If this is the partition where you have wubi, it will be available as /media/host in 7.10 and /host in 8.04
Wow, thanks! I am running 7.10 and it is located in /host though, not /media/host.

---

### Post by breaking on 2008-02-06
Just 1 more question, is there a way to have a link to that partition show up on the desktop? If I mount a partition in /media it shows up on the desktop too, can I do that somehow with /host ?

---

### Post by mohnish82 on 2008-05-01
Yes, you can create a shortcut to the same and place it on the desktop.

Right click > "Create Launcher" > In command section type "nautilus /host"

Enjoy :)

---

### Post by haleem on 2008-05-01
I think this will helpfull to you

The Windows partition where you installed Wubi is available as /host within Ubuntu All the other partitions will be available under /media/ 
If you are using Wubi-7.04 (7.10 and 8.04 users can skip this), write support for ntfs is disabled by default, to enable it: 
1.	Make sure you have internet access (see the network icon on the top right) 
2.	Open the "Applications" menu and select "Add/Remove..." 
3.	In the listbox on the right select: "Show All Available Applications" 
4.	Search for "NTFS" and select "NTFS Configuration Tool". Click OK to install it 
5.	Run the configuration tool under Applications > System Tools > NTFS Configuration Tool 
6.	Select "Enable write support for internal device". Click OK to set it up. 

Where did you got the Wubi 7.10 ? Please let me know the link? Oficial sourceforge doesnot have that, ([http://sourceforge.net/project/showfiles.php?group_id=198355](http://sourceforge.net/project/showfiles.php?group_id=198355) )
Enjoy the Ubuntu with wubi

---

### Post by OMA2k on 2008-05-01
Hi, I've installed Wubi 8.04 in two PCs so far (one is a regular PC with just one NTFS partition, and the other is a Tablet PC with two NTFS partitions).

In the Tablet PC with two partitions, Wubi automatically added an icon in the desktop and in the "Places" menu to just one of the partitions (the first one, C: in Windows), but it didn't mount or add any icon for the second partition (D: in Windows). The Wubi installation was done to D: since it had the most disk space. Does that mean Wubi doesn't configure the partition it's installed to for auto mount?

In the regular PC with one partition, Wubi didn't automatically mount that one partition. Why is that? Again, being the only partition in the PC, it's obviously the partition that contains the Wubi installation, but I don't see that a good reason not to automount the partition.

Why are Wubi host partitions not automatically mounted?

---

### Post by ago on 2008-05-02
The partition in which you install Wubi is not shown in the desktop and it is available as /host

As mentioned by mohnish82 

Right click on the desktop > "Create Launcher" > In command section type "nautilus /host"

---

### Post by OMA2k on 2008-05-02
> **ago said:**
> The partition in which you install Wubi is not shown in the desktop and it is available as /host


Thanks for your reply. What's the reason for that? It would make sense to mount it in /media/ along with the other partitions, wouldn't it?

Having one partition in a different location is inconvenient, not only because it doesn't appear in the desktop, but also because it doesn't appear in "Places", so all Open/Save dialog boxes doesn't have a handy access to that partition (you have to manually go to /host/).

Isn't it possible to have the Wubi partition be exactly the same as the rest of partitions? (automounted in /media/ and automatically visible in desktop and Places).

Regards.

---

### Post by OMA2k on 2008-05-03
So there's no way to properly mount the /host/ drive in /media/?

---

### Post by ago on 2008-05-03
/host is special because it /hosts root 

and unlike any other partition in /media, it cannot be unmounted

You can use a launcher or a symlink to a similar effect.

---

### Post by zaivala on 2008-05-04
Um, "nautilus /host"?  what if you don't have Nautilus installed?

Also, can this work with subdirectories of Windoze?  For instance, c:\Documents\HP User\My Documents\My Music, would that translate to /host/documents/hp_user/my_documents/my_music ?

Moss

---

### Post by ago on 2008-05-04
say you use XYZ for browsing files, the launcher command would be

XYZ /host

If you want a particular windows folder

XYZ /host/path/to/windows/folder

---

### Post by steve101101 on 2008-06-13
When I enter the code 

```

nautilus /host/

```

it says that the folder doesn't exist. Even if i try to navigate other windows folder they don't exist. Also if i try to explore the folder with a gui the host folder is magically missing. 

This happened after i resized the drive with LVPM

---

### Post by steve101101 on 2008-06-15
the way i fixed it was to make sure the host folder still exists in your home folder. then in etc/fstab that it is being mounted. add to in if needed...

```

/dev/sda3 ~/host ntfs defaults 0 0

```

I hope that helps

---

### Post by ago on 2008-06-16
> **steve101101 said:**
> When I enter the code 

```

nautilus /host/

```

it says that the folder doesn't exist. Even if i try to navigate other windows folder they don't exist. Also if i try to explore the folder with a gui the host folder is magically missing. 

This happened after i resized the drive with LVPM

That is a bug in LVPM. I haven't looked at the code but most likely it skips the /host folder, while that is required as a mountpoint, so the directory must exist in the new system. Try to run

sudo mkdir /host

then reboot

---

### Post by sagararora on 2008-07-01
hello everyone....i think most of the post have said how to see the partition.but i am getting a differnt error.

i have installed Ubuntu in my c: drive and able to see it under the /host.

i was also able to see cdrom and my other partition through Places earlier.

but from last 2 days whenever i click that it says unable to mount with this error:

[B]Windows is hibernated,refused to mount.failed to mount '/dev/sda3': operation not permitted the NTFS partition is hibernated.please resume and shutdown windows properly , or mount the volume read only with the 'ro' mount option,or mount the volume read write with the 'remove_hiberfile' mount option. for example type on the command line: mount -t ntfs-3g /dev/sda3 /media/disk -o remove_hiberfile.

[/B]Moreover i have removed my hibernation file in windows and shutdown it completely before moving to Ubuntu.i am also not able to see my cdrom under removable disk.

please help me on this..
looking for some advice...
thanks

---

