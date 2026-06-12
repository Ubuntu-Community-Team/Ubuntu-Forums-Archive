---
title: "apt-get gives lock error - can someone help?(also posted in beginnertalk)"
date: 2006-07-17
forum: General Help
---

### Post by Gig on 2006-07-17
Hi

I have been working with Hoary for a while and run it as a proxy at my home. I have also installed Samba and use it as a Fileserver/ backup for our little network.

Recently I tried to install apache-mysql-php so I can do some programming in php but my system keeps giving me this error:

root@server:/var/lib/dpkg # apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (20 Not a directory)
E: Unable to lock the list directory

It gives me the error on update, upgrade and any install.

I have searched everywhere but no fix seems to help. Can anyone with a bit of experience please advise me as I am stumped and cant make my system an apache server to test scripts, etc.

Thanks

---

### Post by gborzi on 2006-07-17
Have you checked how much free space you have in the partition containing /var and the permission and owner of /var/lib/apt/lists/ ?

---

### Post by Gig on 2006-07-17
Hi Gborzi

No I havent, any idea how I do that??

Gig

---

### Post by gborzi on 2006-07-17
Look at your /etc/fstab to see which partition contains /var. In case you don't understand fstab content, please post it. To see the permission and owner of /var/lib/apt/lists/ give the following command:> ls -ld /var/lib/apt/lists/
that should give an output like this one
> drwxr-xr-x 3 root root 8192 2006-07-17 07:35 /var/lib/apt/lists/

EDIT: also post the output of the *df* command.

---

### Post by penguinfan on 2006-07-17
Delete the lock files in /var/cache/apt/archives
Do sudo apt-get clean
its safe and will b re-created when you do apt-get.

hope this helps

---

### Post by Gig on 2006-07-17
Hi

Thanks for helping me. It came back with the following:
drwxr-xr-x  3 root root 4096 2005-11-30 13:50 /var/lib/apt/lists/

how do I rund the fstab option?

Thanks

---

### Post by Gig on 2006-07-17
Hi

sorry, ignore the previous post, I was distracted and postef form the wrong server.

Here is the df command:
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             18975324   1941860  16069568  11% /
tmpfs                    47280         0     47280   0% /dev/shm
/dev                  18975324   1941860  16069568  11% /.dev
none                      5120      2752      2368  54% /dev

The - ls -ld /var/lib/apt/lists/ - command give the following error:
ls: /var/lib/apt/lists/: Not a directory

D you know what this could mean??

sorry for messing you around, someone distracted me.

Thanks

---

### Post by Gig on 2006-07-17
Hi Penguinfan

I tried that and it tells me this:

E: Lists directory /var/lib/apt/lists/partial is missing.

It still doesn't seem to be working. Anything else you could recommend??

---

### Post by gborzi on 2006-07-17
Sorry for the delay in the answer. The fstab + df was meant to check taht you have enough free space on your hd, and you have it.
It seems that on your system the directory /var/lib/apt/lists/ doesn't exist anymore. I can't imagine how this happened and I'm not sure about the solution. Perhaps you can try the following:
> sudo mkdir -p /var/lib/apt/lists/
sudo apt-get install -f
Hope this helps, I'm just guessing a solution.

---

### Post by Gig on 2006-07-17
Hi

I think when I installed Samba it overwrote the apt directory with a apt file. Very odd and this is what is in it:

"MSHOME"       c0001000 "SERVER"                      "MSHOME"
"SERVER"       40049a03 "server server (Samba, Ubuntu)" "MSHOME"
"GRANT"        40011203 "Grant"                       "MSHOME"
"NICOLA"       40011203 "Nicola"                      "MSHOME"

Simply too weird I think. What do you think I should do with this file? It would probably mess up samba if I delete it, or do you think its simply a waste??

Thanks for helping I really appreciate it..

---

### Post by gborzi on 2006-07-17
I don't know samba, I have never used it. Surely if samba changed the directory /var/lib/apt/lists to a file this package is somewhat broken. I suggest you to make a backup of that file (i.e. /var/lib/apt/lists) somewhere, make the directory and give the apt-get command. Then check if samba still works.

---

### Post by Gig on 2006-07-29
For those who are having this problem and can't understand whats up, I was able to fix it by deleting the partial "file" and replacing it with a partial "directory", commands as follows:

## to get to the directory

cd /cd /var/lib/apt/lists/

## to remove the partial file (no directory was present)

rm partial

## to create the partial directory

mkdir /var/lib/apt/lists/partial

AND............it worked.

Thanks for all the help guys. Good luck to those that are having this problem, hope it helps.

Gig

---

