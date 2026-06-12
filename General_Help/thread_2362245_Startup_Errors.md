---
title: "Startup Errors"
date: 2017-05-25
forum: General Help
---

### Post by shane_faulkinbury2 on 2017-05-25
When I boot into Ubuntu 16.04.2 LTS I get three error messages.  One shows up immediately and the other two appear after 30 seconds.  My question is what folder do I look in to find what to fix so I no longer get them?

On a side note, I thought I had asked this question about a year ago so I was looking for it and My Activity only goes back four weeks.  Is there anyway to look back on questions asked farther in the past?

---

### Post by vasa1 on 2017-05-26
Please ask one question per thread. Thanks!

Re. finding your older posts or threads: use the Advanced Search box near the top right of your screen. Stick *shane_faulkinbury2* into that box and press *Enter* on your keyboard.

---

### Post by howefield on 2017-05-26
Have a look in 

```
/var/crash/
```

for clues.

---

### Post by mörgæs on 2017-05-26
> **vasa1 said:**
> 

Re. finding your older posts or threads: use the Advanced Search box near the top right of your screen. Stick *shane_faulkinbury2* into that box and press *Enter* on your keyboard.

When I write my name in the search box in the top right corner I don't get same results as if I click the link *Advanced Search*, enter my name in the *User Name* box and click *Search Now*. I can't find a pattern but the latter seems more complete.

---

### Post by vasa1 on 2017-05-26
> **mörgæs said:**
> When I write my name in the search box in the top right corner I don't get same results as if I click the link *Advanced Search*, enter my name in the *User Name* box and click *Search Now*. I can't find a pattern but the latter seems more complete.+1. 83 threads by the latter, and 37 by the former, including threads not started by OP.

---

### Post by gordintoronto on 2017-05-26
Telling us the text of the error messages would help. Use your phone to take a video of the startup sequence, if the messages disappear too quickly. Ten to one, Google can find your answer, once you know the exact text of the errors.

---

### Post by shane_faulkinbury2 on 2017-05-26
I didn't post it earlier and it's just a simple little box.  It was about a year ago when somebody told me and I no longer know how to get a hold of him. but they're in a file in like /run or something.  It's not in a sub-directory.

---

### Post by shane_faulkinbury2 on 2017-05-26
I'll get a screen shot of the other errors when I log on tomorrow, but check this out!  Every time I login  I do a sudo apt-get update, but today when I did that the command wouldn't work.  So I opened the Software to see if it was updating and it said I had an OS update and that I needed to update Firefox.  So I pressed update all and noticed a red check mark in the upper right hand corner.  I clicked on iy and the screen shot shows what appeared.

---

### Post by mörgæs on 2017-05-27
The text tells exactly what is going on: Another process is upgrading packages. Just wait and let it finish.

---

### Post by shane_faulkinbury2 on 2017-05-27
Never mind all, this morning I immediately got the error and I hit the furthest right button to approve the upgrade.  It was all Firefox.  I opened Software and the Firefox upate was gone with only the OS update remaining.  I updated that and everything is running smoothly again!

---

### Post by shane_faulkinbury2 on 2017-05-30
They're back!  I thought this was resolved,but they came back the next day.  I gave it some time to see if it would r[ATTACH=CONFIG]275358[/ATTACH][ATTACH=CONFIG]275359[/ATTACH]esolve it's self, but as you see it hasn't.  I have screen shots of the problem.  As I said earlier the top error comes on immediately after boot up.  The second one comes on about 30 seconds later.  I know the second one has to do with Virtualbox as you can see from the screen shot.

What I specifically want to know is where to find the boot up directory.  That's all I need to know for future use because at this point I'm just going to Dban my desktop and reapply Ubuntui 167.04.

---

### Post by mörgæs on 2017-05-31
Good, please post if it helps.

---

### Post by shane_faulkinbury2 on 2017-06-02
I finally found it on my own!  It was in```
/var/log
``` and was called boot.log .  It looks like the problem is with lmetad not  being active which messes with the AppArmor initialization

```
lvmetad is not active yet, using direct activation during sysinit  Volume group "ubuntu-vg" not found
  Cannot process volume group ubuntu-vg
No key available with this passphrase.
No key available with this passphrase.
  /run/lvm/lvmetad.socket: connect failed: No such file or directory
  WARNING: Failed to connect to lvmetad. Falling back to internal scanning.
  Reading all physical volumes.  This may take a while...
  Found volume group "ubuntu-vg" using metadata type lvm2
  /run/lvm/lvmetad.socket: connect failed: No such file or directory
  WARNING: Failed to connect to lvmetad. Falling back to internal scanning.
  2 logical volume(s) in volume group "ubuntu-vg" now active
/dev/mapper/ubuntu--vg-root: clean, 289646/59981824 files, 11517494/239902720 blocks
[[0;1;31mFAILED[0m] Failed to start LSB: AppArmor initialization.
See 'systemctl status apparmor.service' for details.
```

---

