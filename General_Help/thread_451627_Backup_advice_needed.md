---
title: "Backup advice needed"
date: 2007-05-22
forum: General Help
---

### Post by Eagleon on 2007-05-22
Hi Everyone,

I was wondering what advice I can get on backing up my files. 

1) What are the most common folders in which the file system stores user data. Before I format my system, I want to copy anything that might belong to a program I am using. For example, /var/www/ has my server data. I know about this one so I will back it up... but what about other common folders that are used to store user files? /home/user/ is also another one I know.. but I don't want to wipe out my HDD and remember something later on that I forgot to backup. Also, is there a way I can tell ubuntu not to store user files all over the place after my next install?

2) What software should I use to backup these files? I usually compress them in archives, but is there something else that you could recommend?

3) I also have a recovery partition that came with the laptop that I want to backup with something like "Norton Ghost' in Linux. I want to make sure the MBR and stuff also gets backed up, so I won't mess up the partition. Although, I must admit that I have no idea what I am doing, so any further advice will be greatly appreciated! Thank you so much.

Eagleon

---

### Post by vanadium on 2007-05-22
My approach is: I just back up my data files. These live under /home/yourusername. In fact, I only selectively back up documents and my .evolution folder there. Obviously, if you have other data you know about, such as your server data, you will want to back these up as well.

With megabite USB disks getting cheap these days, I back up using rsync. The great thing of rsync is that it only copies the changed files. Backups therefore are a matter of seconds to minutes. Moreover, rsync can delete files on the backup that do not anymore exist on the source, making it possible to maintain a perfect replica of your data.

You can use rsync to "synchronise'local data, and no root rights are needed. However, you can also syncronize over an ssh connection. Also, yo can syncronise any network connection that you can mount as a local folder.

The basic usage for "mirroring" is

rsync -a /path/source /path/destination

To delete files in the destination that do not anymore exist in the source, use --delete. To make the proces a bit less tacitus, add -v for "verbose. Thus, you get my favourite line:

rsync -av --delete /path/source /path/destination

---

### Post by Eagleon on 2007-05-22
thanks for the info, i will definitely try resync! what about the "Norton Ghost" like program for ubuntu though, do you know of anything that has similar functionality?

also...

> 
My approach is: I just back up my data files. These live under /home/yourusername. In fact, I only selectively back up documents and my .evolution folder there. Obviously, if you have other data you know about, such as your server data, you will want to back these up as well.


the problem is, I don't know exactly where my data could be other than for /home/user/ and /var/www/ ... might you be able to tell me what folders applications are not allowed to write to?  I mean system folders... ( i think /dev/ ... ) are like this right? If I know what folders ubuntu won't put my user data in, I can check all the other places for any data that might exist! 

Thanks.. :)

---

