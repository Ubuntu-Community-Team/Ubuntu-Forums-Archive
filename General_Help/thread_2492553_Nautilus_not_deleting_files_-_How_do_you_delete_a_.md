---
title: "Nautilus not deleting files - How do you *delete* a file?"
date: 2023-11-14
forum: General Help
---

### Post by fiscoking on 2023-11-14
Hello,

I'm trying to delete some files from a Ubuntu installation that no longer boots because the hdd is full. An installation went wrong and used up too much disk space - I did check before hand. 

I've booted from the live CD and have run sudo nautilus to get past all the permission of the files I want to delete on the hdd.

I've deleted a bunch of files to free up some disk space, but the hdd remains full. No space is freed up.

Could Nautilus be just moving the files somewhere else instead of deleting them? 

If so, how do I find these files and delete them?

Thanks.

---

### Post by MAFoElffen on 2023-11-14
If you are using Nautilus, the default behavior is to move the files to Trash... ---> Right click on the Trash Icon on the left, and select "Empty Trash".

---

### Post by fiscoking on 2023-11-14
Trash cannot be displayed while in su mode, it generates an error. In normal user mode the trash is empty, but the disk free space doesn't increase.

I'm looking at the disk free space in GParted.

I also get some warnings like that below while deleting files as su (on a live recovery system), so it looks like nautilus is trying to move them to a 'trash' can somewhere.

The irony of me deleting files on a full system to free up space, with the system complaining it can't move files to trash because it's full up. Sigh.

[https://i.ibb.co/vqcq3VH/Untitled.jpg](https://i.ibb.co/vqcq3VH/Untitled.jpg)

---

### Post by ian-weisser on 2023-11-14
> **fiscoking said:**
> I've deleted a bunch of files to free up some disk space, but the hdd remains full. No space is freed up.

I think we need to know more details about exactly what you are doing and how you are doing it.

The use of Nautilus, for example, tends to be inefficient ...as you have discovered... since you must either bypass the trash or (essentially) delete everything twice.

---

### Post by fiscoking on 2023-11-14
I'm booting from an Ubuntu DVD (20.04) and selecting the evaluation option. This loads Ubuntu into ram and leaves the hdd untouched.
I then run terminal and type 'su nautilus'. I then click on 'other locations' and the partition that's full. I then navigate to the files I want to delete and press the delete key.
Once done, I fire up GParted and look at the free disk space. Nothing has changed.

---

### Post by fiscoking on 2023-11-14
After some more investigation I've found the problem.

Nautilus hides hidden files and folders by default. You have to override this in preferences 'show hidden files'. At this point the trash location for the su user becomes visible - assuming you're running Nautilus as su which I am to get past file permissions. It's in /.trash-0/files/ on the partition you delete files from. Deleting all the files in this folder (as su) removes them from the partition, and GParted shows the newly created free disk space.

I suppose you just have to be aware of the above when using the Ubuntu live DVD as a recovery option. I normally use PartedMagic and that really does kill a file when you delete it. Doesn't hide anything by default either.

---

### Post by MAFoElffen on 2023-11-14
I don't use Nautilus as Sudo... But then again I am at home at a console prompt or terminal session...

I filter out what I find what is taking space up in the filesystem...
```

mafoelffen@Mikes-ThinkPad-T520:~/Downloads/ISO$ sudo du -cha --max-depth=1 2>/dev/null / | grep -E "M|G"
1.7G    /opt
270G    /home
265G    /var
225G    /zfs-backups
8.5M    /run
17M    /etc
9.7G    /usr
473M    /boot
9.5G    /snap
2.9G    /root
782G    /
782G    total

```
Then start following the breadcrumbs
```

mafoelffen@Mikes-ThinkPad-T520:~/Downloads/ISO$ sudo du -cha --max-depth=1 2>/dev/null / | grep -E "M|G"
1.7G    /opt
270G    /home
265G    /var
225G    /zfs-backups
8.5M    /run
17M    /etc
9.7G    /usr
473M    /boot
9.5G    /snap
2.9G    /root
782G    /
782G    total
mafoelffen@Mikes-ThinkPad-T520:~/Downloads/ISO$ sudo du -cha --max-depth=1 /var 2>/dev/null / | grep -E "M|G" | grep /var
611M    /var/cache
260G    /var/lib
4.9M    /var/backups
3.1G    /var/snap
660M    /var/log
159M    /var/crash
452M    /var/tmp
265G    /var
mafoelffen@Mikes-ThinkPad-T520:~/Downloads/ISO$ sudo du -cha --max-depth=1 /var/lib 2>/dev/null / | grep -E "M|G" | grep /var/lib
104M    /var/lib/apt
2.4M    /var/lib/lightdm
26M    /var/lib/swcatalog
6.2G    /var/lib/snapd
1.1M    /var/lib/smartmontools
253G    /var/lib/libvirt
3.8M    /var/lib/aspell
546K    /var/lib/NetworkManager
2.1M    /var/lib/command-not-found
63M    /var/lib/dpkg
1.3M    /var/lib/gdm3
1.9M    /var/lib/fwupd
260G    /var/lib
mafoelffen@Mikes-ThinkPad-T520:~/Downloads/ISO$ sudo du -cha --max-depth=1 /var/lib/libvirt 2>/dev/null / | grep -E "M|G" | grep /var/lib/libvirt
253G    /var/lib/libvirt/images
253G    /var/lib/libvirt

```
Once you find out what is taking up space, decide if it needs to be uninstalled (like programs, Linux Kernels, etc.), deleted (data files), or resized (journctl logs)...

If deleted like you asked, then I do one of the following 
```

sudo rm /path/to/filename
sudo rm /path/to/filename_with_wildcards
sudo rm /path/to/filename_with_pattern_matching
find <path_start> -name <pattern> -exec sh -c "sudo rm  {}'

```
But I test those with 'ls' in place of 'rm' first to ensure that whatever I use, is going to work on the expected files!

And you can see that I do backups to restore to...

---

### Post by ian-weisser on 2023-11-15
> **MAFoElffen said:**
> I filter out what I find what is taking space up in the filesystem...
...
Once you find out what is taking up space, decide if it needs to be uninstalled (like programs, Linux Kernels, etc.), deleted (data files), or resized (journctl logs)...
...
If deleted like you asked, then I do one of the following 
...
But I test those with 'ls' in place of 'rm' first to ensure that whatever I use, is going to work on the expected files!


An excellent method: Efficient, fast, and safe. And easy to understand.
I don't have full storage devices. But if I did, this would be the first page of my notes for how to fix it.

---

