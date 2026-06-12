---
title: "How can I diagnose problem manifested on &quot;boot screen&quot;?"
date: 2017-08-03
forum: General Help
---

### Post by AbleTassie on 2017-08-03
For several days, when booting up into Lubuntu on the HDD, I am getting a long list of  apparent problems instead of just the usual "/dev/sda1: clean, 184181/303334976  files, 4052381/121312000 blocks". The screen looks like the attached example image below, which I just obtained from the internet to show what I mean. 

It is visible for such a short time that there is no way to take a screen shot and record it. And realistically, trying to take a digital photo seems unrealistic too. 

At first I thought I should just live with it, but then last night I found I could not access the Ubuntu.com keyserver via Terminal; and I also found I could not ping the server. I am, however, able to access and ping the key server when I boot into a Lubuntu full install I have on a USB pen drive.

In addition, I can no longer run a virtualized Windows Machine using Virtualbox (see error message below under the image).

QUESTION: Is there a log I can access that has the information in the "boot screen" that may help me diagnose the problems I am having?  

Thanks,

Able


[ATTACH=CONFIG]276239[/ATTACH]

**Error message related to failure to open virtual Windows machine:**

Failed to open a session for the virtual machine Able1.

The virtual machine 'Able1' has terminated unexpectedly during startup with 
exit code 1 (0x1).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: MachineWrap
Interface: IMachine {f30138d4-e5ea-4b3a-8858-a059de4c93fd}

---

### Post by AbleTassie on 2017-08-03
Perhaps what I am looking for can best be described as a log for boot messages, or a log for splash screen messages or a fsck log.

 I do not even know the terminology to use to properly ask the question. But the messages I see on boot up are so much longer than before, I feel they must indicate a problem. I've looked in the various documents in the var/log folder and they do not seem to be what I am looking for. The terminal command dmesg gives so much output that it is much longer than what I see on boot up.

Anybody have any comments?

Thanks,

A.

---

