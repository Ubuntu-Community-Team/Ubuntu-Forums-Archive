---
title: "help linux won't boot"
date: 2007-12-22
forum: General Help
---

### Post by TechnoJunky on 2007-12-22
I'm not sure what happened, I had a good installation that I've been using for some time.  Today I booted up (laptop) and the package manager said there were 9 packages to update, I did.  Then I turned the external monitor off.  When I came back it looked like it rebooted on me and the screens said "startingup ... [   11.301529] kernel panic -not synching: no init found.  Try passing init= option to kernel".  Anyone have any ideas?

---

### Post by Sef on 2007-12-22
What make and version of *buntu are you using?

---

### Post by TechnoJunky on 2007-12-23
Kubuntu 7.10

---

### Post by TechnoJunky on 2007-12-24
?

---

### Post by burbankmarc on 2007-12-24
yeah the init part of your grub isn't set up properly. Can you boot into any of the other, older linux kernels?

---

### Post by TechnoJunky on 2007-12-24
Can you tell me how I would pick an older kernel? I've booted to the install CD and mounted my drive.  The Grub menu only has 2.6.22.14-generic and the boot dir only has files with that version listed as well.

---

### Post by benrboone on 2007-12-24
This also happen to me, my solution was to push e at the grub menu and edit the harddrive to be (hd0,1) not (hd1,1).  I'm not sure of your set up but for grub drive 0 is the first one.  So (hd0,1) means harddrive 1 partion 1.  If this dosn't make cents then make sure to ask or research grub a little bit

---

