---
title: "/home seperate partition"
date: 2008-04-22
forum: General Help
---

### Post by ryth on 2008-04-22
Hi folks,

Bit of a newb question here, but I'll throw it out there anyway.

I've installed Gutsy on my home machine with /home on it's own partition.  I'm planning on wiping my Gutsy partition and doing a fresh install of Hardy.

My question is:  On my current Gutsy install let's say my primary user account is "ryth".  If when I'm doing the fresh Hardy install and I specify in the setup for it to use my current home partition for /home and the admin username as "ryth" is it going to overwrite the previous /home/ryth or will it just point toward my already established /home/ryth ?

I hope that makes sense.

r

---

### Post by bingoUV on 2008-04-22
Depends on how you created the user ryth. If during installation of Gutsy you specified ryth as the user account (the first one, not as additional user accounts), its user id would be 1000(could be 500/1000/1001/501 , I forget which but it is a fixed number for ubuntu). 

Now during installtion of Hardy if you do the same, the user id of the user ryth in Hardy will also be 1000 and all will be well. The directory /home/ryth will be owned by user 1000 i.e. ryth , permissions will be set correctly and angels will smile on you.


If, on the other hand you created user ryth as the second or later non-root account in the installtion of Gutsy, its user id will be 1001, or more. Now the owner of /home/ryth is 1001 but user ryth is 1000. It will be difficult to login or do anything worthwhile because you don't own your own home directory. All hell will break loose and your computer might even explode(kidding).

---

### Post by kpkeerthi on 2008-04-22
The installer has an option where you can specify not to format the partition that will be mounted as /home.

However, I would simply avoid having same user names (& same home folder) across distros as the UID may not match even though the user IDs match. So rename your gutsy's /home/ryth to /home/ryth-gutsy from a live CD. After installing hardy copy/move the files over to from /home/ryth-gutsy to hardy's /home/ryth.

---

### Post by ryth on 2008-04-22
> **bingoUV said:**
> If, on the other hand you created user ryth as the second or later non-root account in the installtion of Gutsy, its user id will be 1001, or more. Now the owner of /home/ryth is 1001 but user ryth is 1000. It will be difficult to login or do anything worthwhile because you don't own your own home directory. All hell will break loose and your computer might even explode(kidding).

Is it not possible to change the owner UID of the gutsy /home/ryth to match that of the primary user i set up in Hardy if they don't match?  

And just to clarify, regardless of whether the UIDs match on the Hardy install it shouldn't overwrite anything in the current /home? Because of the use of the same usernames it would 'just' cause conflicts because of the UID difference?

---

### Post by bingoUV on 2008-04-22
Well it is possible but I am a bit scared of distros like ubuntu which do not set a password for root by default. They can still be fixed, but it is more work.

[B]change the owner UID of the gutsy /home/ryth
[/B]    Possible, but you have to be root somehow. Booting from a live CD and mounting the home partition is also fine. Now
```

sudo chown -R 1000:1000 /home/ryth

```
If you are working from a live CD, you will have to replace /home/ryth by "path/to/where/home/partition/is/mounted"/ryth.

Not only this, once you are root in live CD, you can also change the UID of the user ryth. Edit the /etc/passwd file (path will be different if doing this from live CD). The third and fourth fields are UID and GID. Change them to your lucky numbers, change ownerships if all the files you need and celebrate. But ensure uniqueness and validity of UIDs and GIDs in /etc/passwd. Hell hath no fury as /etc/passwd scorned.


[B]Hardy install it shouldn't overwrite anything in the current /home
[/B]    As far as I am aware, OS installation never changes anything in /home. When you try to login, initialization scripts will be picked up from your home directory. If you have permissions to run them, fine. Otherwise login completes with errors / fails. When you start an application (say firefox) it looks for its initialization folder (~/.mozilla/firefox). If you have appropriate permissions on them, fine.

---

### Post by mozetti on 2008-04-22
The added benefit (or bane if you don't like the old config settings) of "re-using" your /home partition is that any config settings that were stored in the old /home partition will be "brought forward" in Hardy.

---

### Post by jen1963 on 2008-04-22
In order to prevent my personal files from getting whacked during an install or upgrade I store my files on a separate /Archives directory off off / (root) on a second hard drive formatted in EXT3. Set Read Only & strict users permissions on /Archives. Then I simply link to my files in /Archives in /home/*user* or /home/*user*/Desktop .
Make sure the Format box on the partitoner remains UNCHECKED and that the mount point is set properly during the install or upgrade.
I have personal files in my /Archives that date back to my Corel Linux days and they have survived many installs, updates & crashes without data loss or corruption.
By using /home as just a file of links then nothing is lost if /home gets whacked...

---

