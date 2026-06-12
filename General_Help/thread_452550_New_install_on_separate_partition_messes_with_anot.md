---
title: "New install on separate partition messes with another install"
date: 2007-05-23
forum: General Help
---

### Post by troymcdavis on 2007-05-23
Hey gang. Here's the deal. I had three partitions (+ a swap) on my laptop. sda3 was an old /home directory back-up, sda4 was my Kubuntu Edgy install, and sda6 is my Feisty install. The goal was to remove sda3 and sda4 so that I could install Ubuntu Studio. 

So, using a GParted LiveCD, I get rid of sda3 and sda4, merge them into one big partition, and format as ext3. Everything seems normal.

Then, I do a server install (not realizing the server disc I have is 6.10), and that goes fine. Since I don't have a DVD burner, I try to add the repos, but I get a 404 on the repository (not realizing the I've added the repo for FIESTY, not FEISTY). I try to boot up my faithful Fiesty Install to see if anyone else is having similar problems. Everything *seems* alright. We go to the ubuntu logo/progress bar, make it about 1/3 of the way through, then it drops to terminal. Here's the tail of the output:

```
 * Checking file systems...
fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=49750cc8-a389-4a91-86a1-1e1937f541ae'
fsck.ext3: Unable to resolve 'UUID=0f3bf70e-17da-4831-bbaf-f913d6138b0d'
fsck died with exit status 8
[RIGHT][fail][/RIGHT]
 * File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
 * A maintenance shell will now be started
CONTROL-D will terminated this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: The: command not found
The program 'apt-get' is currently not installed. You can install is by typing: apt-get install apt
bash: apt-get: command not found
bash: dircolors: command not found
bash: The: command not found
The program 'apt-get' is currently not installed. You can install it by typing: apt-get install apt
bash: apt-get: command not found
root@computer-name:~# _
```

Here is the log file mentioned above:
```
Log of fsck -C -R -A -a
Wed May 23 08:26:33 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=49750cc8-a389-4a91-86a1-1e1937f541ae'
fsck.ext3: Unable to resolve 'UUID=0f3bf70e-17da-4831-bbaf-f913d6138b0d'
fsck died with exit status 8

Wed May 23 08:26:33 2007
-----------------
```

"The program 'apt-get' is currently not installed. You can install it by typing: apt-get install apt." :lol: 

Control-D does get me back into my install, and everything appears to be just fine. Any insight on what the deal is?

---

### Post by troymcdavis on 2007-05-23
"UUID=49750cc8-a389-4a91-86a1-1e1937f541ae" and "UUID=0f3bf70e-17da-4831-bbaf-f913d6138b0d" are representations of the partitions that are hard-coded into the /etc/fstab file. The computer was attempting to check the disk (as it tends to do every 30 boots), but it couldn't find those partitions I had erased, and thus the error. Old values in /etc/fstab commented out; problem solved.

---

