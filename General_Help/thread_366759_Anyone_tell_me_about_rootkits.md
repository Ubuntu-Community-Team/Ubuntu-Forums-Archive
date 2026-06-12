---
title: "Anyone tell me about rootkits?"
date: 2007-02-21
forum: General Help
---

### Post by wej1971 on 2007-02-21
I've recently posted this thread: -

[http://www.ubuntuforums.org/showthread.php?t=365573](http://www.ubuntuforums.org/showthread.php?t=365573)

Someone suggested that the symptoms I am seeing might be something called a rootkit (which I'm assuming is a trojan that allows someone to adopt root privileges) but is there anyway I can find/remove this if this is the case?

---

### Post by gruffy-06 on 2007-02-21
There are *chkrootkit* and *rkhunter* packages available in the Ubuntu repos. If these programs do not detect any signs of any rootkits, you should use other scanning tools to check for spyware and other malware.

If you are unlucky, you may not be able to remove the rootkit. In the end, I suggest you backup your valuable data to a CD/DVD or USB Flash Memory, perform a full format to your hard disk and reinstall everything.

---

### Post by bobosity on 2007-02-21
I read your link/post. Likely, you have not been rooted, you've just been hosed. Probably something you did yourself. (no criticism, I do it all the time) ;-}

I agree with gruffy-06. Nothing like a fresh install to make things smell sweet. The more I work with linux, the less I re-install. It's a learning thing.

Good luck.

---

### Post by wej1971 on 2007-02-22
Is that really the only option, to reinstall? The reason I ask is that it's taken 2 weeks (no exaggeration) to get my wireless network working, and I'm damned if I'm going to do it all again.

Oh, and if I *do* reinstall, will I need to do anything to clear-down the grub menu or does the install take care of it itself?

---

### Post by bobpaul on 2007-02-23
> **wej1971 said:**
> Is that really the only option, to reinstall? The reason I ask is that it's taken 2 weeks (no exaggeration) to get my wireless network working, and I'm damned if I'm going to do it all again.

Oh, and if I *do* reinstall, will I need to do anything to clear-down the grub menu or does the install take care of it itself?

I would follow these instructions and [seperate your /home to it's own partition]("http://www.psychocats.net/ubuntu/separatehome"). Most application settings and configs are stored in your /home/username folder, and this will save you a lot of time on during your install. Just make sure you don't format /home when you're installing!

As far as you're wireless stuff goes, yes, you'll probably have to re-do it, but it should be faster the second time because you've already done it. Also, you could backup the specific config files in /etc that you modified to make your wireless work.

For complicated procedures like that, I keep a folder ~/install that contains instructions as well as any files I need. That way I can look at my instructions and don't have to search for things like windows drivers for ndiswrapper a second time.  This proved very useful when the dapper->edgy upgrade broke my system.

---

