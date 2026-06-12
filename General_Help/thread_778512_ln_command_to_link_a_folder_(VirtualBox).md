---
title: "ln command to link a folder (VirtualBox)"
date: 2008-05-02
forum: General Help
---

### Post by giumbolo on 2008-05-02
Hi, I want to make a link to a folder (/media/windows), say that I want to call it /home/user1/win.

I issue ln -s /media/windows /home/user1/win 
Issuing the command ls -l  i get 
user1@baluba:~$ ls -l win
lrwxrwxrwx 1 user1 user1 14 2008-05-02 10:09 win -> /media/windows

while I was supposed to see the list of files in /media/windows.

I can cd into, but cannot list the files from outside. If I cd into the folder I ca list the files, so it is not an authorization issue.
------------------------------------
If you've been so patient to read up to here, I have to say why this is important to me.
Here's the scenario, Hardy with the PUEL version of VirtualBox, I want to have a shared folder in the VitualBoxed windows, which in turn contains a soft link to the drive where the original windows reside.

In fact everything is fine from the guest windows, but when I click on the link, within the shared folder, I can't see any file within.   
Strangely, exploring the network resources, under \\VBOXSRV I find the share and can get into to other inner folders ...

Any idea ? Thanks in advance.

---

### Post by Zorael on 2008-05-02
Curious. I can't make sense of why you can sometimes see files in it and sometimes not, to be honest.

Make sure the ~/win directory doesn't exist before creating the symlink, so as to be certain it was created properly.
```
zorael@sunspire:~$ ln -s /usr test
zorael@sunspire:~$ ls test
bin  etc  games  include  lib  lib32  lib64  local  sbin  share  src  X11R6
```

Else you can try mount --binds, I guess.
```
$ mkdir ~/win
$ sudo mount --bind /media/windows ~/win
```

---

### Post by giumbolo on 2008-05-02
In fact it was peculiar to my configuration.
I use the command (an alias) dir which in turn is a ls -l
Running ls alone let me see the files in the directory pointed by the soft link.

Also, accessing the same files, from a Virtualboxxed XP, in a shared folder, is now ok. I only have to wait some seconds more than I expected, being the folder very crowded.

Thanks Zorael
Let us consider this thread fixed.

---

