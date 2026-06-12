---
title: "Filesystem error during Startup"
date: 2008-01-02
forum: General Help
---

### Post by Covered in Dog Hair on 2008-01-02
I'm running 7.10 and its been running fine for five months now with no problems. When I went to restart after an update, it paused on the Ubuntu loading bar screen and then went to the command line and said the file system has errors on in, and that I need to run fsck. I ran fsck and said yes to all the prompts but it did not move on after one of the prompts, I left it for about a half hour then restarted my computer and tried again to no avail.

I had a similar problem when i was running 6.06 and I reinstalled because I found no solutions.

I am just booting Ubuntu off a 200GB hd with only Ubuntu booting from it 

I was wondering if there is a way to fix this or do I need to reinstall

---

### Post by -Zeus- on 2008-01-03
try booting to recovery mode and see if you can do that... then type this command

```
touch /forcefsck && reboot
```

---

### Post by Covered in Dog Hair on 2008-01-03
Ok I forgot to mention that it gives me the same responce when I try to boot it in recovory mode also. 

Here is basically what it says when I start it.

/dev/hda1 contains a file system with errors                                                   [2%]
[this number changes 41.084052] Buffer I/O error on device hda1, logic block 1343994
[...] "                                                                                                    "   1343994
to 
[73.066436] Buffer I/O error on device hda1, logic block 1344010
/dev/hda1: Unexpected inconsistancy; Run fsck Mannally
           (ie with out -a or -p)
fsck died with exit status 4                                                                          [Fail]

* An automatic file system check of root file systme failed 
Manual file system check must be preformed, then restarted.
fsck in matanince mode w/ root file systme in read olny mode
*Root file system in read olny 


Then it give me the comand prompt where I type fsck 
then it goes on and says 

[565.638755(this number changes)] Buffer I/O error on Device hda1, logic block 1540369
Force rewrite(Y): 
(it gave me a few before this but hung up on this one for about 15 min untill I restarted and tried booting in recovory mode)

It gives me differtent numbers except for the procentage, th exit status and the logic blocks. 


Is there a way to fix this with the live CD? 

Any help is appriceated.

---

### Post by Kzin on 2008-01-03
> **Covered in Dog Hair said:**
> 
fsck in matanince mode w/ root file systme in read olny mode


I think that is the secret key
In slackware, you would boot from the cd, at the command prompt type something like sata.i root=/dev/sda1 ro noinitrd then you would be able to run fsck.
If anyone can translate that into Debian?  What that says is boot from the kernel on the cd, sata.i so I can read my sata drive, the root partition is /dev/sda1, read only, do not load the init ram disk.
The error message seems to say that you need to boot up with the drive in read only?

I could be totally wrong tho.

My other question would be is this the same hard drive this happened on with the other Ubuntu install?

---

### Post by xeth_delta on 2008-01-03
You could boot from a live CD and then run fsck on the affected partition from it.

---

### Post by Covered in Dog Hair on 2008-01-03
It is the same dirive that that it happened to with the other ubuntu intallations.

I will try runing fsck from the live cd but im down loading it now so it will be a while befor I can try.

---

### Post by xeth_delta on 2008-01-03
Remember to check the integrity of the downloaded image ([https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")) and to burn at a low velocity (4x at the most)

---

### Post by Covered in Dog Hair on 2008-01-04
I got the live cd working and im runing fsck on the hard drive. Its a 200gb hard drive with a little under 40 gb used. Does any one know how long it should take to run fsck on a drive of this size. 

This is the information its given me so far.

"   ubuntu@ubuntu:~$ sudo umount /dev/hda1
ubuntu@ubuntu:~$ fsck /dev/hda1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Permission denied while trying to open /dev/hda1
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$ sudo fsck /dev/hda1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/hda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes

Error reading block 1344000 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 1344001 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 1540124 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 1540246 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 1540369 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 1540492 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes   "

It has been sitting at this point for the last 30 min

---

### Post by Covered in Dog Hair on 2008-01-04
I just came back to my computer and this is what it said in terminal after the last line in my previous post.
"
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/hda1: 115655/23855104 files (2.2% non-contiguous), 8617538/47700993 blocks
ubuntu@ubuntu:~$ 
"

---

### Post by Covered in Dog Hair on 2008-01-04
The fsck worked and I was able to boot off the hard drive. 

Thanks for the help.

---

### Post by xeth_delta on 2008-01-05
> **Covered in Dog Hair said:**
> The fsck worked and I was able to boot off the hard drive. 

Thanks for the help.

Glad to know it worked!

---

