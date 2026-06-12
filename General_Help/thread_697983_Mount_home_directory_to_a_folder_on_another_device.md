---
title: "Mount home directory to a folder on another device?"
date: 2008-02-15
forum: General Help
---

### Post by Mortie on 2008-02-15
This is the case: I've got a 250 GB HDD, which I have formatted into a **15 GB ext3 partition** (**/dev/sda1**, for installing Ubuntu onto), a **201 GB ext3 partition** (**/dev/sda6**, which is intended to keep /home directory and to store media files  -- music, videos -- among the users), and of course a swap.

The **/dev/sda6** is mounted to **/media/sda6** in **fstab** during boot time, and it contains two folders -- "**storage**" and "**home**".

Basically what I want to do is to kind of mount **/home** to **/media/sda6/home** so that all home-stuff gets stored on that large partition (which is also separated from the OS itself).

I know that it is possible to mount **/home** to a device (partition), but that would eliminate my whole idea of **/home** and "storage" sharing the space on the larger partition entirely dynamically. 

My question: is it possible to mount a another local directory i.e.** /media/sda6/home** to i.e. the **/home** directory?

Thanks in advance :)

---

### Post by dcstar on 2008-02-15
> **Mortie said:**
> 
.........
My question: is it possible to mount a another local directory i.e.** /media/sda6/home** to i.e. the **/home** directory?


Yes, do a search for **separate home partition**.

---

### Post by Rocket2DMn on 2008-02-15
Have a look here - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Mortie on 2008-02-15
My intentions are not to mount an entire partition to the /home directory but merely a folder  on another partition:

1. OS is installed on **/dev/sda1**. 

2. **/dev/sda6** is a larger partition containing two folders -- "storage" and "home".

3. **/dev/sda6** is mounted to **/media/sda6**.

What I want to do: mount the *folder* **/media/sda6/home** to the **/home** location.

Sorry if I was a bit unclear, english is not my native language, so I might have some difficulties expressing myself in it :)

---

### Post by dcstar on 2008-02-16
> **Mortie said:**
> My intentions are not to mount an entire partition to the /home directory but merely a folder  on another partition:

1. OS is installed on **/dev/sda1**. 

2. **/dev/sda6** is a larger partition containing two folders -- "storage" and "home".

3. **/dev/sda6** is mounted to **/media/sda6**.

What I want to do: mount the *folder* **/media/sda6/home** to the **/home** location.

Sorry if I was a bit unclear, english is not my native language, so I might have some difficulties expressing myself in it :)

That is not "mounting", rename /home and make a new /home as a softlink to that folder (with exactly the same permissions as the original /home).

---

### Post by axel1973 on 2008-03-27
> **dcstar said:**
> That is not "mounting", rename /home and make a new /home as a softlink to that folder (with exactly the same permissions as the original /home).

have u ever testet your suggestion ??

since i tried exactly that! i copied /home to some other filesystem mounted as /FLASH so i now got /FLASH/home with the same file-permissions. then i renamed the old /home to /home.old and created a symlink /home pointing to /FLASH/home.

After reboot the User was not able to login anymore. The Ubuntu Desktop appeared but keeps BLANK with no taskbar and all.

After restoring old conditions anything got back up working.

so what ?? Why cant i just use a symlink to relocate the /home directory to whatever i like to ?

---

### Post by lloyd_b on 2008-03-27
> **axel1973 said:**
> have u ever testet your suggestion ??

since i tried exactly that! i copied /home to some other filesystem mounted as /FLASH so i now got /FLASH/home with the same file-permissions. then i renamed the old /home to /home.old and created a symlink /home pointing to /FLASH/home.

After reboot the User was not able to login anymore. The Ubuntu Desktop appeared but keeps BLANK with no taskbar and all.

After restoring old conditions anything got back up working.

so what ?? Why cant i just use a symlink to relocate the /home directory to whatever i like to ?

Offhand, that issue you had with the experiment sounds like you had a permissions problem with "/FLASH" (working with symlinks, it doesn't matter if you have the proper permissions set for "/FLASH/home" - if you don't have at least read+execute permissions on "/FLASH" you won't be able to access that directory).

And it *is* possible to mount a directory in one filesystem to a specified point in another (or the same) filesystem.  Edit the file "/etc/fstab" (you'll need a "sudo" or "gksudo" to edit it), and add the following line:
```
/media/sda6/home   /home   bind   bind
```
and then reboot your system.  Make sure that you have all of your stuff copied, and that you have the proper permissions (if you can copy the stuff from your existing home directory without using "sudo" then you've probably got the permission right).

Be aware - if something goes wrong with this, you'll have to reboot into recovery mode to undo it.

Lloyd B.

---

