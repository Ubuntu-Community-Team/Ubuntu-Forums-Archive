---
title: "[SOLVED] /home in a different partition?"
date: 2007-07-31
forum: General Help
---

### Post by yehudaco on 2007-07-31
hey, i have installed all of my Os on the same partition and recently i've heard that it is much better and safer to install  the /home directory on a different partition why?? i would appreciate if any one would be able to explain me the reason, or give me a link to a site that would, and help me find a guide to do it...
thanks!

---

### Post by bbzbryce on 2007-07-31
> **yehudaco said:**
> hey, i have installed all of my Os on the same partition and recently i've heard that it is much better and safer to install  the /home directory on a different partition why?? i would appreciate if any one would be able to explain me the reason, or give me a link to a site that would, and help me find a guide to do it...
thanks!

For my purposes having the /home directory on its own partition allows me to format the / partition when I perform a clean distribution upgrade. It saves a bit of time because even though I back everything up on /home (I've made mistakes in the past) I don't have to restore information assuming everything worked flawlessly.

---

### Post by nitro_n2o on 2007-07-31
Having your /home in a different partition will increase your chances of saving your data if your / partition failed for any reason. It's also recommend to keep /var in a different partition if you are running a server, since logs can fill the disk quickly in some cases. 
doing this is like 'prevention is better than cure'  and as bbzbryce said you can restore your settings and upgrade the system easily

---

### Post by bluenova on 2007-07-31
Here's the guide:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I do it so I can reinstall ubuntu or any other distro and have all my files and settings intact.

---

### Post by fjgaude on 2007-07-31
Yes, yes... question: once you have installed Ubuntu with /home on the same partition as /, is there a way to move /home to another partition?

frank

---

### Post by merlinus on 2007-07-31
Did you look at the link in the previous post?

-merlin

---

### Post by fjgaude on 2007-07-31
No, I didn't. Shame on me... will do it now. Thanks.

frank

---

### Post by fjgaude on 2007-07-31
Okay, I did a similar thing with the find | cpio copy command, but I did it to a software RAID5 array made up of three other drives, some weeks ago.

I now believe that I have to compile a kernel with the raid built-in instead of it being a external module (md). I could be wrong. I'm using 2.6.20-16. It seemed that mounting the raid as /home didn't work. I'll give it one more try before I think about re-compiling the kernel, waitng for Gusty to be released.

Thanks for the link page.

frank

---

### Post by yehudaco on 2007-08-01
thank you all guys - it was very helpful!!
i think i'll do it....sounds wise...:shock:

---

