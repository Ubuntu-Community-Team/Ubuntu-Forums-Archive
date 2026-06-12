---
title: "Dual Booting Issues"
date: 2016-11-06
forum: General Help
---

### Post by blindgungfu on 2016-11-06
so a while ago i tried dual booting kali and ubuntu on an hp, so i partitioned just fine, both btrfs systems, then when installed the second os, for some reason it only put a mount point on the most recently installed one, (viewing from gparted)  renderring the other partition/os just a plain old storage system. since then i have changed things and just have ubuntu on the laptop, but would really like to be able to dual boot these. im still learning alot and i know its probably right in front of my face. but im scared to install anything on the other partition because i dont want to do the whole transfer of info and re-re-reinstall again. ugh.

---

### Post by Bashing-om on 2016-11-06
blindgungfu; Hello;

Perhaps show us a screen shot of what GParted sees for the hard drive structure ? So that we are all on the same page.

I too multi-boot - ext4 file system(s) - and as I am a control freq, the only problem I have is managing grub - in my thought process it is hands on controlling grub from my primary booting system. Took a bit to adjust and learn what is required .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by blindgungfu on 2016-11-07
Thank you for your reply, I have succeeded! I did not have grub configured properly. easy peasy thank you thank you!!!!!

---

### Post by Bashing-om on 2016-11-07
blindgungfu; Great .

Glad ya got it sorted out .
Now consider how to prevent it happening again .
My solution - and only one solution of many - is to disable in the secondary system 30_os-prober in /etc/grub.d/.
But this does entail that anytime grub is updated in this secondary system that in the primary you run:
```

sudo update-grub

```
to propagate the changes to this primary system so it is consistent with the secondary system.

If this matter is now concluded to your satisfaction:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

