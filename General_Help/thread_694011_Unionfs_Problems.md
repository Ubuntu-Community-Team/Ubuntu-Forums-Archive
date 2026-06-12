---
title: "Unionfs Problems"
date: 2008-02-11
forum: General Help
---

### Post by jediborger on 2008-02-11
First off if anyone can point me to some real documentation on Unionfs I would greatly appreciate it as I can't seem to find any. Right now my problem is that I have directory A and B. I want to combine the contents of A into B so that all files in A appear in B but if I were to add more files then they are written to B not A. This might make more sense with my final application. I'm trying to setup a computer lab and I want some standard gimp brushes to be mounted from the server (directory A) on each of the client machines to the gimp brushes directory. But if a user were to manually add their own brushes then I only want those to be written to the brush folder on the client computer (directory B) and not back to the server (directory A).

I'm just testing this on my computer with two directories test and test2.
So here's the command I tried:
```
sudo mount -t unionfs ./test ./test2 -o dirs=./test=ro:./test2=rw
```
But get this error:
```
mount: wrong fs type, bad option, bad superblock on /home/matthew/test,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I am able to mount this setup by switching the rw and ro:
```
sudo mount -t unionfs ./test ./test2 -o dirs=./test=[COLOR="Blue"]rw[/COLOR]:./test2=[COLOR="Blue"]ro[/COLOR]
```
But then if I write a file to test2 it shows up in test, not what I want.

BTW I'm running Gutsy 2.6.22-14-generic 32-bit.

---

### Post by jediborger on 2008-02-12
bump

---

### Post by SonicSteve on 2008-02-12
[QUOTE=jediborger;4312189
```
mount: wrong fs type, bad option, bad superblock on /home/matthew/test,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


BTW I'm running Gutsy 2.6.22-14-generic 32-bit.[/QUOTE]

Whenever I've had this error it has come because I've tried to mount a Samba share without installing the SMBFS. 
You might try 
sudo apt-get install unionfs 

if that fails try 
sudo apt-get install unionfs-tools (thats its name in synaptic)

I don't know if unionfs is a standard file system or if needs to be installed like SMBFS does.

---

### Post by jediborger on 2008-02-12
After some more searching I've found that the unionfs man page is in the unionfs-tools package, maybe this should be included with the main OS as unionfs is now built into the kernel but anyways my syntax was wrong and the error was because the rw branch needs to be listed first in the dirs option. So the following is the correct command:
```
sudo mount -t unionfs -o dirs=./test2=rw:./test=ro unionfs ./test2
```

Now that I can mount the directories and create files in test2 that don't show up in test, is there a way to prevent deleting files from test that are mounted in test2. In reality they aren't really deleted but instead a "whiteout" file is created by unionfs that in effect "deletes" the file. 

Is there a way to prevent this pseudo file deletion without manually deleting the whiteout files? 

I might have to sit around on some kernel IRC channels to find out this answer.

---

