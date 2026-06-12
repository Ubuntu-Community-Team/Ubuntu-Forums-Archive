---
title: "ext3 vs. ext4 in a fresh install"
date: 2013-03-29
forum: General Help
---

### Post by jsvidyad on 2013-03-29
Hello,

   I am not sure if this is the appropriate place to post this. if not, please move it to the appropriate forum.

   I am putting in a new hard drive for my laptop. So, I am going to create partitions again from scratch. But, I'm not sure if I should use ext4 partitions or ext3 partitions. I was using ext3 earlier as I read somewhere that there were stability issues with ext4. Do these stability issues still exist? I am going to install ubuntu 12.04. So, all questions are with regards to ubuntu 12.04. Also, I remember that the /boot partition could not be of type ext4. Is this limitation still valid? What are the advantages /disadvantages of ext4 vis-a-vis ext3 ? The hard drive only has a capacity of 500 GB. So, going by size alone, I guess I could use either ext3 or ext4. Is there any performance advantage to using ext4 instead of ext3?

---

### Post by oldfred on 2013-03-29
You do not need a /boot partition. I would use ext4 and use it for all new partitions I create. Some of the issue that there were are over 2 years old. Ext4 runs fsck faster when it runs as part of a reboot. It has other internal improvements over ext3, not sure of all the details anymore.

I prefer to keep system partition or / (root) at 25GB and either have separate /home or what I use is separate data partitions with only the mostly hidden user settings still in /home which still is inside my 25GB root partition. I use about 9GB total of the 25GB.

---

### Post by jsvidyad on 2013-03-30
I usually have separate partitions for /, /boot and /home. Can I use ext4 for /boot partition too? What you are saying is that for / and the /home partitions I can use ext4, right? You are saying that ext4 for ubuntu 12.04 is stable?

---

### Post by carl4926 on 2013-03-30
ext4 is fine
never had a problem with it

I too do not use /boot

Just
swap
/
/home

---

### Post by carl4926 on 2013-03-30
> **jsvidyad said:**
> 
I usually have separate partitions for /, /boot and /home. 
Can I use ext4 for /boot partition too? [COLOR=#800000]**Yes**[/COLOR]
What you are saying is that for / and the /home partitions I can use ext4, right? [COLOR=#800000]**Yes**[/COLOR]
You are saying that ext4 for ubuntu 12.04 is stable?[COLOR=#800000]** Yes**[/COLOR]



I'd still say drop /boot
unless you can think of a good reason to have it

---

### Post by jsvidyad on 2013-03-30
The reason I use a separate /boot is so that if I compile a custom kernel, I don't lose it when I install a later version of the OS. Though I must admit that I never had to compile a custom kernel for ubuntu.

---

### Post by carl4926 on 2013-03-30
> **jsvidyad said:**
> The reason I use a separate /boot is so that if I compile a custom kernel, I don't lose it when I install a later version of the OS. Though I must admit that I never had to compile a custom kernel for ubuntu.

That's OK
Some folks get in a mess with it. You seem to know what you are doing...

---

### Post by kurt18947 on 2013-03-30
There was an signifant issue with libreoffice & ext4.  People were losing documents 'saved' on ext4 partition and weren't able to recover them.  Ext3 partitions didn't seem to have the same problem.  This was quite some time ago and I haven't heard/read of that problem in the past year or more.  That's the only ext4 problem I can recall.

---

### Post by 3rdalbum on 2013-03-30
I don't believe Ext4 gives you any cause for concern these days. It's pretty mature now.

---

### Post by tgalati4 on 2013-03-30
When compiling a custom kernel, be sure to give it a different name than your existing kernels and you should be fine.  I can't think of a single use case where a separate /boot would provide a significant advantage.  The downside is that if you have partition problems then you loose boot immediately, and that makes troubleshooting more difficult.

---

### Post by rnerwein on 2013-03-30
> **jsvidyad said:**
> Hello,

   I am not sure if this is the appropriate place to post this. if not, please move it to the appropriate forum.

   I am putting in a new hard drive for my laptop. So, I am going to create partitions again from scratch. But, I'm not sure if I should use ext4 partitions or ext3 partitions. I was using ext3 earlier as I read somewhere that there were stability issues with ext4. Do these stability issues still exist? I am going to install ubuntu 12.04. So, all questions are with regards to ubuntu 12.04. Also, I remember that the /boot partition could not be of type ext4. Is this limitation still valid? What are the advantages /disadvantages of ext4 vis-a-vis ext3 ? The hard drive only has a capacity of 500 GB. So, going by size alone, I guess I could use either ext3 or ext4. Is there any performance advantage to using ext4 instead of ext3?
hi
i think the first you must think about - what i'm doing on the file system --> what's the score.
my opinion is (sorry when i am wrong )  to take "ext2" for boot and root (it's not so fast but that's my experience it's stable). take a seperate for /var (for me i don't need accesstime there) and just give "ext4" a try for home. but for performace have a look at the mount options, there you can do a lot (e.g. blksize, accesstime .....). it's what i want to say a matter of what you will do (e.g. for video etc. give them a bigger blocksize) with your file-system.
just play with the mkfs and mount options. to get the accurate value you have to do this. no system is used the same way and, there is no sulution what i know, for ervery application anybody runs on a system.
ciao

---

### Post by cmcanulty on 2013-03-30
I have used ext4 on numerous machines for years with no issue at all. It is fast too.

---

### Post by jsvidyad on 2013-05-04
Hello,

   I was concerned because of the negative reports I had heard about ext4 some time ago. Since everyone seems to think that ext4 is error-free now, I will use ext4 partitions for my system.

---

### Post by Stonecold1995 on 2013-05-04
> **jsvidyad said:**
> Hello,

   I was concerned because of the negative reports I had heard about ext4 some time ago. Since everyone seems to think that ext4 is error-free now, I will use ext4 partitions for my system.
That's probably the best idea.  I've used ext4 for a while as well and never had any problem with it, plus it's saved my data from corruption quite a few times!

---

### Post by jsvidyad on 2013-11-14
So,

  Is the version of ext4 on ubuntu 12.04.3 stable for daily desktop usage?

---

### Post by Impavidus on 2013-11-14
I've used ext4 for years &#8211; since installing 10.04 &#8211; and it has been the default for years. Never had any trouble. Those reports saying it's unstable must be quite old by now.

---

### Post by 3rdalbum on 2013-11-14
> **jsvidyad said:**
> So,

  Is the version of ext4 on ubuntu 12.04.3 stable for daily desktop usage?

Did you not read the very thread you bumped?

Ext4 has been stable since 2010. The problem reported back in 2009 did not affect many people, and it was fixed straight away. I was already using Ext4 then and never had a problem before or since.

---

### Post by jsvidyad on 2013-11-22
Thanks for the replies.

---

