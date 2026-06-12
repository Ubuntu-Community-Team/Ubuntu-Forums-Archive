---
title: "ls give an Inpu/Output error"
date: 2005-08-21
forum: General Help
---

### Post by adwait on 2005-08-21
Hello,

Well, I was downloading some files with Firefox and it crashed....

Now, firefox showes those files as completely downloaded, but they don't show up in the directory that I download them to. Also, now, whenever I run an ls in that directory, it gives me an error along with the directory listing:
> 
ls: MaRewa-1.mp3.part: Input/output error
ls: AlmsforShanti-Varanasi.mp3: Input/output error
ls: AlmsforShanti-Superbowl.mp3: Input/output error
ls: AlmsforShanti-IWishIWasaWhale.mp3: Input/output error
ls: AlmsForShanti-Kashmakash.mp3: Input/output error


---

### Post by Dogmeat on 2005-08-22
I once had a problem with a huge file I couldn't delete. My hard drive died soon after, so I suggest you do a backup of your important things. Of course it could also just be a file system screw up, but if I were you i'd do it just to be on the safe side.

Now to fix your filesystem. I'm assuming you have firefox installed in the same partition that you boot from. If not, skip the next paragraph.

Boot from a live cd, or another linux partition if you have it. If you have neither, I recommend getting a utility live CD. RIP worked for me (its just 28 mb, search for "Recovery Is Possible" on google, or find another one you might like.)

Now as root, run fsck the partition which contains the I/O problem. It should say its fixing stuff, then when it's done you can try mounting the partition again. ls shouldn't give the error again, but if it does, your hard drive is probably physically damaged.

---

### Post by adwait on 2005-08-22
Hey thanks for the reply..........but I ran dir, and it didnt show any errors. So I just deleted the files, and everythings peachy now :)

---

