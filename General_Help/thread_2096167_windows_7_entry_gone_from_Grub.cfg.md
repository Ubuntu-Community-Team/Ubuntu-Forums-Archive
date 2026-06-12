---
title: "windows 7 entry gone from Grub.cfg"
date: 2012-12-19
forum: General Help
---

### Post by nisargparikh69 on 2012-12-19
thank u so much man!! wow .. u just solved my prob. but i see two entries for win 7 ,sda2 and sda3.. what do i do for only 1 entry?

---

### Post by overdrank on 2012-12-19
Hi and welcome, I have moved your post to it's own thread. No need to revive a two year old thread. 
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

### Post by oldfred on 2012-12-19
Did you run Boot-Repair. It copies essential Windows boot files from boot partition to main install as a backup, then then grub finds both.

You can use Grub customizer to hide entries. Or manually copy only the entries you want into 40_custom and turn off os-prober so grub does not find any entries. 

       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer & manual ways
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

