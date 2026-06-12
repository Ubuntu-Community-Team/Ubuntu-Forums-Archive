---
title: "Custom Kernel Compilation {removing smp and rt2570 drivers}"
date: 2006-07-03
forum: General Help
---

### Post by ihavenoname on 2006-07-03
Ok, here is the deal. I am having stability problems with the default kernel in Ubuntu,( when I upgraded to the latest one it seemed to get worse (if there was a change) ) My whole problem can be found in this thread if you are interested 

[http://ubuntuforums.org/showthread.php?p=1211146#post1211146]("http://ubuntuforums.org/showthread.php?p=1211146#post1211146")

In any case here is what I want to do in order to (hopefully) remedy the situation, compile the kernel without the rt2XXX (rt2570,rt2500,rt2400 etc.) wirless drivers, and without smp support (although it seems the 2.6.17 kernel has a diffrent way of doing this...) 
I am using this guide to help me get the kernel and compile it: [https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28kernel%29](https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28kernel%29)

however this does not seem to tell me anything about removing the rt2XXX drivers or the smp support. If anyone could tell me what changes I need to make or at least point me to where I may find out what to do T in order to achive the above mentioned result it would be greatly  appreciated.

---

