---
title: "backup advice"
date: 2006-11-18
forum: General Help
---

### Post by cptjaben on 2006-11-18
Recently I've been [unable to boot into Ubuntu]("http://ubuntuforums.org/showthread.php?p=1773195#post1773195"). I'm thinking the best way to solve the problem is to simply reinstall a fresh copy of edgy. however, I want to save all my firefox bookmarks as well as my saved email in evolution. Does anyone know how one could accomplish this if they cannot boot into Ubuntu? Thanks

---

### Post by DOD1951 on 2006-11-18
Are the files on a dual boot pc? If pure Ubuntu only does the pc have a cd reader and separate cd writer?

---

### Post by aysiu on 2006-11-18
Your Firefox and Evolution files and settings are stored in hidden directories in /home/cptjaben (otherwise known as ~/)

Back up these two directories, and you should be set:
~/.mozilla
~/.evolution

Alternatively, you can [create a separate home partition](http://www.psychocats.net/ubuntu/separatehome), which will then save all your settings and personal files when you reinstall.

---

### Post by druhboruch on 2006-11-18
You may try to boot from live CD or Knoppix.

It will give you the access to your partition and enable you to mount your USB stick.

---

### Post by cptjaben on 2006-11-18
I'm Dual booting windows and ubuntu on one harddrive and then I have another harddrive with most of my files that is fat32 so both can read, the windows partition is fat32 as well and the ubuntu partition is ext3. Right now i'm on the windows parition and i can access the two fat32 paritions but not the ext3 one, which has the files i need on it.

What would one suggest would be the easiet method to back up my bookmarks and emails as well as my home folder. Thanks much

---

### Post by aysiu on 2006-11-18
> **cptjaben said:**
> I'm Dual booting windows and ubuntu on one harddrive and then I have another harddrive with most of my files that is fat32 so both can read, the windows partition is fat32 as well and the ubuntu partition is ext3. Right now i'm on the windows parition and i can access the two fat32 paritions but not the ext3 one, which has the files i need on it.

What would one suggest would be the easiet method to back up my bookmarks and emails as well as my home folder. Thanks much
This will help you:
[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by cptjaben on 2006-11-18
Awesome, now is there a way to have sudo power using this broswing program, because i believe i may be able to solve [the problem]("http://ubuntuforums.org/showthread.php?p=1773195#post1773195") by deleting /bin/sh but it says i don't have permission to do it. Thanks

---

### Post by cptjaben on 2006-11-19
any ideas?

---

### Post by aysiu on 2006-11-19
As far as I know, the FS driver does give you *sudo* power. If that doesn't work, do you have a live CD (Ubuntu Desktop CD or Knoppix CD)?

---

### Post by cptjaben on 2006-11-20
yes, i have an ubuntu 6.06 live/install cd, how would i go about deleting the file?

---

### Post by aysiu on 2006-11-20
Let's assume your Ubuntu partition is /dev/hda2 (you would know, of course, which one it is--if you don't, paste ```
sudo fdisk -l
``` in the terminal to find out).

Boot the live CD and go to the terminal. Type ```
sudo mkdir /media/recovery
sudo mount -t ext3 /dev/hda2 /media/recovery
gksudo nautilus
``` Then go to /media/recovery and find whatever you want to delete and delete it.

---

### Post by jkroto on 2006-12-06
> **aysiu said:**
> 
Alternatively, you can [create a separate home partition](http://www.psychocats.net/ubuntu/separatehome), which will then save all your settings and personal files when you reinstall.

Aysiu,
I did create a separate /home partition when I installed Dapper on my machine (upon the advice of your guides; thank you for those, they are very helpful).  

Are you saying that I could install a new version, or re-install, and retain everything in /home?  If so, do you know of any guides on doing this?  And what happens to the programs that were installed?
Just asking in case I have a need for the info in the future.
Thanks,
John

---

### Post by aysiu on 2006-12-06
Yes, you could install Edgy or Feisty or Feisty+1 and retain your same /home--that is the benefit of a separate /home partition.

This guide shows you how to do that (using the example of mounting /documents, but the same principle applies--mount the partition as /home and choose not to reformat it):
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by jkroto on 2006-12-06
> **aysiu said:**
> Yes, you could install Edgy or Feisty or Feisty+1 and retain your same /home--that is the benefit of a separate /home partition.

This guide shows you how to do that (using the example of mounting /documents, but the same principle applies--mount the partition as /home and choose not to reformat it):
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Thanks Aysiu,
I think I'm going to go back and create a separate partition for /documents as well as /home. Most of what I would want to save during an upgrade or re-install would be media and personal files, etc.
Thanks again.

---

### Post by aysiu on 2006-12-06
> **jkroto said:**
> Thanks Aysiu,
I think I'm going to go back and create a separate partition for /documents as well as /home. Most of what I would want to save during an upgrade or re-install would be media and personal files, etc.
Thanks again.
Well, you don't really need both. Presumably, your documents would be inside your /home directory. For example, /home/*username*/music or /home/*username*/movies

It makes sense to make a separate /documents partition only if you don't want to keep your settings.

---

### Post by jkroto on 2006-12-06
> **aysiu said:**
> Well, you don't really need both. Presumably, your documents would be inside your /home directory. For example, /home/*username*/music or /home/*username*/movies

It makes sense to make a separate /documents partition only if you don't want to keep your settings.

I guess I don't know when I would and would not want to keep the settings.  I need to learn more before I go any further.
I do like your idea of a separate /documents partition and then symlink (as I read about in other posts of yours) but don't know anything about symlink's either.
The learning goes on, and, thanks again for the advice.

---

### Post by aysiu on 2006-12-06
There are a few reasons I don't keep settings:

1. I like to do clean reinstalls of new releases to see what they're like. I can't see the default settings (background wallpaper, theme, icons) if I already have all that stuff customized.

2. Sometimes my settings suck. I customize too much and just have too much junk--menu entries I've deleted, too many keyboard shortcuts. I like to have a fresh start every six months (with the new Ubuntu release).

3. Sometimes when I do reinstalls, I change my username to something else. I don't want to have to bother copying my old username's home folder and then *chown*ing (changing ownership of) my home directory to make everything work again (might as well just have a separate /documents partition instead... which is what I do).

Now, I do keep some settings (Firefox and Thunderbird and Rhythmbox) on my /documents partition and then symlink those to my home directory. So /home/*username*/.mozilla links to /documents/.mozilla 

As for symlinks, they're basically just pointers to other folders. In Windows they're called *shortcuts*. In Mac they're called *aliases*. So it appears there's a folder called /home/*username*/music, but it really is just a pointer to /documents/music. Does that make sense?

---

### Post by jkroto on 2006-12-06
1. I don't do a lot of customization and I would like to see the new stuff.

2. Sometimes my settings suck as well...usually because **_I_** broke something.  This would be the main reason I would want to upgrade or re-install and thus I would not want the junk left over.

I use Firefox and Thunderbird.  Coming from another OS, I do understand shortcuts, thank you for the simple analogy.
So I guess what I want to do is re-install with a /documents and not a separate /home partition and make the symlinks.  Thanks for the educated opinion and advice.

---

