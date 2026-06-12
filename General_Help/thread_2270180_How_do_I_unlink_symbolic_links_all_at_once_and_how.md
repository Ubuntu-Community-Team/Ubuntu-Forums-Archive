---
title: "How do I unlink symbolic links all at once? and how do I make symlinks permament?"
date: 2015-03-21
forum: General Help
---

### Post by KayeNg on 2015-03-21
Hi guys. I'm using Lubuntu.  

In my Windows 7 partition, I have my own set of wallpapers in /media/Kaye/Windows/Windows/Web/Wallpaper/Fantasy .   Inside that folder are wallpaper .jpg files that I want to link to this directory:

/usr/share/lubuntu/wallpapers  (which is the actual directory of the built-in wallpapers for Lubuntu).  I have successfully linked the files using "ln -s target source".

Just for the sake of experimenting, I have also successfully unlinked each file INDIVIDUALLY, like so:   sudo unlink /usr/share/lubuntu/wallpapers/dragon.jpg

First question:   How do I unlink the files ALL AT ONCE? I thought this would do it but apparently not:  sudo unlink /usr/share/lubuntu/wallpapers/*

Second question:  If I reboot, the symlinks are gone.  How do I make them permanent?

(Also, nothing to do with the question but someone told me to use gksu instead of sudo if I want to use the file manager as root.  I don't understand, they seem to have the same effect)

Thank you for your time!

---

### Post by sudodus on 2015-03-21
1. You can use ```
rm linkname
``` for example ```
rm  /usr/share/lubuntu/wallpapers/*
```

Warning: ***rm*** is very powerful, and you can easily damage your system, if you use rm without knowing what you are doing!

See also ```
man rm
```

2. Symbolic links survive a reboot. I have several symbolic links, that have survived hundreds of reboots.

But if you are running a live session, not an installed system, nothing will survive (except what is written to separate (non-system) partitions). And if you link to an external drive, and do not mount that drive after reboot, the link will be broken until you mount that drive again.

Edit: See this link about sudo and gksudo and gksu
[URL="http://ubuntuforums.org/showthread.php?t=2269093"]
Caution running GUI programs like gedit with sudo[/URL]

---

### Post by CaptainMark on 2015-03-21
1. I though unlink would support multiple arguments but apparently not, use this instead
```

sudo find /usr/share/lubuntu/wallpapers -type l -exec unlink {} \;

```
To do them all at once

2. I'm not 100% so I'll reserve opinions on that one and let people with Windows experience comment first

3. Using sudo for a graphical application can cause issues with configuration files being written as root but to your home directory. Say you open firefox with sudo you may end up having root access but writing config files for settings over your own firefox profile in /home/kaye with a new one that is marked as being owned by root and not yourself. Using gksu or similar will open firefox using a profile in /root and not affect /home

***Watch Out***

While Sudodus has been around a lot longer than me and I am thankful for his/her help when I ask for it too, the rm command will delete any and all files in the wallpaper directory, it probably safer to use find -exec unlink, perhaps Sudodus I'd recommend altering your post

---

### Post by Holger_Gehrke on 2015-03-21
Actually 'unlink' and 'rm' do the same thing, removing files by removing hard links. A bit of background: on Unix-style file systems the actual identifier of a file is it's inode-number. A name is just an entry in a directory associated with that number. So one file can have several names, the inode contains (among other things) a counter of the names (hard links) and the space used by the file is marked as available when this count drops to zero. Hard links obviously can only point to files on the same file system because inode-numbers are not unique across file systems. Soft links can cross file systems because a soft link is just a text file containing the name of the linked file and a special bit set in it's inode. The main (only ?) difference between the programs 'unlink' and 'rm' is that 'rm' can handle multiple files in one go and 'unlink' can't.

---

### Post by KayeNg on 2015-03-21
Thanks guys, I now know something about rm and unlink.  However, Holger, I'm a bit confused by your statement,
"Actually 'unlink' and 'rm' do the same thing, removing files by removing hard links."

I've tried the unlink and it removes the link only, as I expected.  For example, this directory

/media/kaye/Windows/Windows/Web/Wallpaper/Fantasy   

contains my personal wallpapers, and I have linked them to this directory:

/usr/share/lubuntu/wallpapers

so that my personal wallpapers are in the same directory as the Lubuntu wallpapers.

I have tried to unlink a file from /usr/share/lubuntu/wallpapers, and the link does get removed, but the original file in /media/kaye/Windows/Windows/Web/Wallpaper/Fantasy is still there, as I expected.

So I don't understand your statement about unlink removing files by removing hard links, because I saw only the symbolic link removed.

Anyway, symbolic links do survive a reboot. The reason I thought it didn't survive is because, upon reboot, the partition which contains my wallpapers are unmounted;  I simply have to mount it again.

Thank guys

---

### Post by sudodus on 2015-03-21
rm removes the link in the same way as unlink. In you particular case you want to remove a symbolic link. The hard link to a picture files in

**/media/kaye/Windows/Windows/Web/Wallpaper/Fantasy   **

will remain. When you 'delete' alias 'remove' that file, you actually remove the hard link to it (so the file system does not know about it).

The content of the picture file is still there on the disk surface, and can be recovered with PhotoRec (unless overwritten with some other file's data). It is possible but not very convenient, and something that should be avoided. Backup your data often and carefully! That will save the day, when your disk is damaged.

---

### Post by Impavidus on 2015-03-21
A hardlink is a reference to a file in the file system. Most files only have a single hard link. **unlink** is a lower level command to remove a hardlink, **rm** is somewhat higher level. **rm** is smarter, it can do some more checks on what it's removing and it can remove multiple hardlinks at once. Internally, both use the same unlink() system call. When the last hardlink to a file has been removed, the file is effectively removed. As most files only have a single hardlink, removing a hardlink is usually equivalent to removing a file.

A symlink is a special kind of file. It contains a path to a different file. As a symlink is a file, it can be removed using **rm** or **unlink**.

Having your wallpaper on a partition that's not mounted at login time is not very convenient. Setting that wallpaper won't survive a reboot. Better either copy the wallpaper to the Ubuntu partition (storing it in your home directory works too), or list your Windows partition in fstab to mount it automatically at boot.

---

### Post by Holger_Gehrke on 2015-03-21
A soft or symbolic link is two links for the price of one:
[LIST]
[*] one (hard) link from the name of the symbolic link to its inode
[*]one link from the inode to the file you actually want to access (basically, there's a bit in the inode that tells the system: "This file is a link"; the system then gets the name of the file linked to from the content of the link file)
[/LIST]
When the first link (the hard link) is removed and the (soft) link's hard-link count in it's inode drops to zero, the link file is removed, but the linked to file is left alone. 
Clearer ? ;-)

---

### Post by CaptainMark on 2015-03-22
All due respect to you guys trying to help the op here but this is all getting a bit off topic here. The op hasn't asked for the differences between unlink and rm. The find command I gave I claimed to be the safest way because it simply cannot remove regular files, all you guys stating that rm is just the same as unlink are giving a command that in the hands of a beginner could cause extensive and data loss not to mention if the op has regular files in the wallpapers directory, youve all just told him how to accidentally delete them too. To avoid such risks don't use rm unless you have to.
Stay focused and stay vigilant.

---

### Post by The Cog on 2015-03-22
unlink can remove regular files. Try it:
```
steve@StevesPC:~$ echo hello sweetie > test.txt
steve@StevesPC:~$ cat test.txt 
hello sweetie
steve@StevesPC:~$ unlink test.txt 
steve@StevesPC:~$ cat test.txt 
cat: test.txt: No such file or directory
steve@StevesPC:~$ 

```
So the only difference I'm aware of is that rm has lots more options, and can do multiple files.

To remove **only the symlinks** in a directory, this should work:
```
sudo rm $(find -type l /usr/share/lubuntu/wallpapers)
```

---

### Post by CaptainMark on 2015-03-22
Again, read my first post which I've restated once, find -exec unlink is safest, and it cannot remove regular files.

---

### Post by The Cog on 2015-03-22
Agreed, I misunderstod your last post. 

But it I did, then maybe others will. So at the risk of being boring and pedantic, I will point out that both unlink and rm can remve real files - it is the "-type l" option of the find command that was able to pick out just the symlinks for deletion. Another point that was not mentioned, find will also search sub-folders by default: use "-maxdepth 1" to prevent burrowing into subdirectories.
Find can be very useful.

---

