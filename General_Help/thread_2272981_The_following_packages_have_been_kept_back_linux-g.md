---
title: "The following packages have been kept back: linux-generic-lts-utopic linux...."
date: 2015-04-09
forum: General Help
---

### Post by DomOctober on 2015-04-09
Hello all, 

 Not sure if there's a better place to post this, but I have a question about updating. While doing the normal 'sudo apt-get upgrade && sudo apt-get install' I get the message that:

"The following packages have been kept back: linux-generic-lts-utopic linux-headers-generic-lts-utopic linux-image-generic-lts-utopic"

I understand that this would normally just require an 'apt-get dist-upgrade' , but I am content with keeping my 14.04 LTS setup just as it is. Am I to just continue ignoring this message, or will it eventually install and upgrade me to Utopic once the dependencies or whatever have been met? I'm just not sure what to do and I hope I have phrased my question properly.

Thanks in advance,

 Dom

---

### Post by Bashing-om on 2015-04-09
DomOctober; Hello;

Did you opt in for HardWare Enablement ?
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I do suggest that you follow your intuition and:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
this will install the current system updates and will not release upgrade to 'utopic' .. just the kernel and xorg will be on 'utopic's' stack.

[INDENT][INDENT][INDENT]just my thought
[/INDENT][/INDENT][/INDENT]

---

### Post by DomOctober on 2015-04-09
Good call, Bashing-om. Thank you for your insight and a quick reply. Based on the information provided in the link, it does seem that because I just recently did a fresh install from 14.04.2 live cd that I have this feature enabled. So I'm to understand that this just allows my current LTS to update to the newest kernel without "changing" it to 14.10 Utopic. Do you forsee any trouble in having a newer kernel with the older Trusty packages?

---

### Post by QIII on 2015-04-09
Hello!  Do you use AMD graphics and, if so, do you use the proprietary driver?

If you do, there is currently a bug that will spoil the update to the new graphics stack.

---

### Post by DomOctober on 2015-04-09
Thanks for the heads up, QIII. I am using an NVIDIA GTX750ti so I hope that there won't be any issues. I'm using the recommended NVIDIA drivers and haven't had a problem so far.

---

### Post by Bashing-om on 2015-04-09
DomOctober; Welp, wellll ...

> 
 Do you forsee any trouble in having a newer kernel with the older Trusty packages?


No way top call that one. As the purpose of HWE is to support new hardware. I can not say what the result will be, as what you had may have been stable on the standard install.  Just depends on your hardware and how it all interacts.
Wont hurt a thing to see what happens and worse case situation -> (RE-)install with release 14.04.1 and NOT opt in for HWE.

[INDENT][INDENT]mind ya, I am a firm believer
[INDENT][INDENT][INDENT][INDENT]if it ain't broke;
[INDENT][INDENT][INDENT][INDENT][INDENT]don't fix it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by DomOctober on 2015-04-09
> **Bashing-om said:**
> DomOctober; Welp, wellll ...



No way top call that one. As the purpose of HWE is to support new hardware. I can not say what the result will be, as what you had may have been stable on the standard install.  Just depends on your hardware and how it all interacts.
Wont hurt a thing to see what happens and worse case situation -> (RE-)install with release 14.04.1 and NOT opt in for HWE.
[INDENT][INDENT]mind ya, I am a firm believer[INDENT][INDENT][INDENT][INDENT]if it ain't broke;[INDENT][INDENT][INDENT][INDENT][INDENT]don't fix it
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thank you! I'll give it a shot, and keep my fingers crossed. Like I've mentioned, it's a relatively new install so no harm done if I do need to reinstall. I suppose I just didn't expect this new LTS enablement stack to be a thing, as I haven't seen it in the past. I really appreciate your help.

---

### Post by Bashing-om on 2015-04-09
DomOctober; Hey;

Like this; If you are stable and solid now, you can expect to continue to be.
HWE can be a good thing .

[INDENT][INDENT]our developers
[INDENT][INDENT][INDENT][INDENT]keeping things current
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by DomOctober on 2015-04-09
> **Bashing-om said:**
> DomOctober; Hey;

Like this; If you are stable and solid now, you can expect to continue to be.
HWE can be a good thing .[INDENT][INDENT]our developers[INDENT][INDENT][INDENT][INDENT]keeping things current
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I did have an NVIDIA related e[FONT=arial]rro[/FONT]r [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1268257](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1268257) and I ran the dpkg reconfigure for my driver and haven't seemed to come across any issues since then.

---

### Post by skeeter-mcbee-y on 2015-04-09
Is the update the reason why I'm having issues <snip> with my system? I figured I would not be affected by this because I'm running 3.17 instead of 3.16.

---

### Post by QIII on 2015-04-09
Please don't hijack others' threads, particularly to redirect to your own.

Also please do not use shortened urls.  You may use the link button to create a link out of part of the text of your post.  This will allow others to hover over and view the full url rather than clicking blindly.

Thanks.

---

### Post by Bashing-om on 2015-04-09
DomOctober; Hey, Hey;

In the case of the Nvidia build bug, I bet that HWE is a God-send. I expect now you have the kernel in -place that the work-a-round is not required.
Your link is good-to-know && keep-in-mind. I appreciate that contribution.

If this matter is now concluded - and it has been my pleasure -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

### Post by DomOctober on 2015-04-27
> **Bashing-om said:**
> DomOctober; Hey, Hey;

In the case of the Nvidia build bug, I bet that HWE is a God-send. I expect now you have the kernel in -place that the work-a-round is not required.
Your link is good-to-know && keep-in-mind. I appreciate that contribution.

If this matter is now concluded - and it has been my pleasure -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
[INDENT][INDENT]good things do happen
[/INDENT]
[/INDENT]


Indeed! As an update, everything has been running very well with my current setup. Thank you all kindly for the help. Marking as Solved!

---

### Post by Bashing-om on 2015-04-27
DomOctober; Good deal .

Pleased things have worked out:
> 
Indeed! As an update, everything has been running very well with my current setup. Thank you all kindly for the help. Marking as Solved!


[INDENT][INDENT]dirty job done dirt cheap
[/INDENT][/INDENT]

---

