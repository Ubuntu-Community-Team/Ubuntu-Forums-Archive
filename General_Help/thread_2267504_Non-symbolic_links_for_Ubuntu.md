---
title: "Non-symbolic links for Ubuntu"
date: 2015-03-02
forum: General Help
---

### Post by jwn-2 on 2015-03-02
Ubuntu 14.04 LTS

Is there an Ubuntu version of Windows shortcuts to files and folders. The Ubuntu symbolic links do have their useful place, but they can also be a real nuicance when you try to copy folders from a shared disk in a Windows VirtualBox VM. Windows sees them as a real folders and copies the contents of the target, which is not what you want.

---

### Post by Bucky Ball on 2015-03-02
*Thread moved to **General Help**.*

Why not aim the VM machine at the real target? That is also the target of the symlink (which means the symlink is not the target you should be aiming at). 

I have four installs (plus an unused Win7) all symlinked to the same data directories on a data partition. I only need to back up the directories on the data partition. There is nothing but symlinks in the /home directory of each install. ;)

---

### Post by jwn-2 on 2015-03-02
Bucky Ball, I do not want to copy the data from the target. I want to copy data from the shared disk, including the links to the target, but not the contents of the target.

---

### Post by ajgreeny on 2015-03-02
Can you give more details as I have become totally lost in respect of where the files are actually sitting to which you want soft or symbolic links.  Are all these data files and folders actually on the Windows VM or on a real, ie not a virtual, data partition on a host machine with symbolic links between them and the Windows OS?

---

### Post by jwn-2 on 2015-03-02
The data files are on a shared partition of the real disk. There are also several Ubuntu symbolic links there. I want to copy the data (including the links). Problem is, Windows sees the links as real folders and copies the contents of the target instead of the link.

Another reason why symbolic links can be a real pain in tha ass is when I have two folders cross linked. Somtimes I have to jump several times during the day between the two folders, which just takes me deeper and deeper into an artificial directory structure. Windows type shortcuts would be much better as they take you directly to the target.

---

### Post by mcduck on 2015-03-02
Most programs and command can be told to not follow symbolic links. Although I got the idea that you are actually doing the copying from Windows? In that case I have no idea what optiosn you have.

Anyway, the direct equivalent of Windows shortcuts would be the .desktop files. The only problem is that since Linux users don't usually need them for anything apart from using them as application launchers (which you don't need to create manually that often), there's no option to create them as easily as you'd do in Windows. However you can make it a bit easier by creating a template .desktop file in ~/Templates.

...and of course you might be able to use hard links instead of symbolic ones, depending on what you need them for.

edit: This might help you: [http://superuser.com/questions/148099/windows-7-symlinks-how-do-i-copy-a-symlink-to-a-directory]("http://superuser.com/questions/148099/windows-7-symlinks-how-do-i-copy-a-symlink-to-a-directory")

---

