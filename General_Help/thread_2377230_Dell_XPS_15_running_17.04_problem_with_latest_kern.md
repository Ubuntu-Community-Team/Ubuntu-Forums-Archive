---
title: "Dell XPS 15 running 17.04 problem with latest kernels."
date: 2017-11-10
forum: General Help
---

### Post by jmcentee on 2017-11-10
I have a Dell XPS 15 running 17.04

  It has been automatically updating its self. The 4.10.0-21-generic  kernel is the last working one I have, anything later then  4.10.0-21-generic boots the computer, but after entering my username and  password the screen shows the default background but does not load the  desktop and I can't do anything. Just booting with the earlier  4.10.0-21-generic kernel is all I need to do to fix it though.
  Any ideas, as I am reluctant to move to 17.10 before I understand whether it will work.

---

### Post by monkeybrain20122 on 2017-11-10
Ubuntu keeps two kernels, the current one and the previous one. So unless you have deleted it you can always boot into the previous working kernel. At boot, quickly press and hold the shift key (on my computer the escape key works too) to bring up the boot menu, you will see an advanced option, choose it and pick your kernel and you will boot into it. Once you are in it you can delete the new kernel from synaptic (remove the linux-image and linux-headers associated with it, there are 4 packages) and hold off kernel update until the next one comes out. Alternatively, you can just keep the current kernel and wait for it to upgrade normally amd do the same boot routine every time  A third way would be to grab a newer kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by DuckHook on 2017-11-10
Please refrain from unneeded formatting when posting. It is difficult to render on mobile devices and a chore to read.

Re: your problem.

My suggestion is a bit more of a meta-observation: too many users jump into the non-LTS versions under the impression that latest is always greatest. Ubuntu does not work that way. The even years numbered with the *.04 versions are Long Term Support (LTS). These are supported for 3 to 5 years depending on flavour and are generally far more stable than the non-LTS versions. The last LTS was Xenial (16.04). The next will be Beaver (18.04). Unless you have a pressing reason to go with a non-LTS, like unsupported HW or a desire to help the developers troubleshoot, then I would suggest sticking with Xenial. Doing so will likely render irrelevant such problems as the one you are experiencing. You can make the decision to upgrade to Beaver when the time comes. If you so decide, I would suggest refraining from doing so until at least the first point release (18.04.1). Doing so will allow others to act as the guinea pigs.

---

