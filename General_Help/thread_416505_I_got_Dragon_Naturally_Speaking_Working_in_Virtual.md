---
title: "I got Dragon Naturally Speaking Working in Virtualbox"
date: 2007-04-21
forum: General Help
---

### Post by rolfotto on 2007-04-21
I [posted in this thread here](http://ubuntuforums.org/showthread.php?t=412418&highlight=dragon+naturally) that I had some problems getting my microphone to work under Linux and therefore couldn't get Dragon NaturallySpeaking (DNS) to work under the virtualized Windows XP.  I thought that this was the case because linux's sound recorder wouldn't pick up a thing -- and Windows sound recorder only picked up garbled nonsense as if every other millisecond was being cut off.

I fiddled with this for a week and finally stumbled upon the _**low latency linux kernel**_ in synaptic.  Even though I didn't think this was a problem, I give it a shot anyway.  It did the trick and I was able to get a clear recording from Windows sound recorder (I never did get Linux's sound recorder to work) and from there was able to Dragon NaturallySpeaking to work.

I know other people in the past were trying to get this software to work and I hope this helps.  I am using version 9 that I got loaned out from a friend to see if it would work for me and the OEM Dragon NaturallySpeaking USB headset.  I'm using a 3 1/2 year old computer(P4 2.6 GHz, 2.5 GB RAM) and I'm surprised to see perfectly good performance under virtualization(a Core2Duo would be nice).  I would hesitate to run anything heavy-duty along with it but I typed this entire post using [DNS running in Windows XP running on top of Ubuntu.](http://xs414.xs.to/xs414/07166/Screenshot-1.png)

[[img]http://xs414.xs.to/xs414/07166/Screenshot-1.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs414&d=07166&f=Screenshot-1.png)

---

### Post by bodhi.zazen on 2007-05-28
AWESOME DUDE !!!!

Thank you, thank you, thank you :)

---

### Post by strabes on 2007-05-28
That's a pretty nice 3.5 year old computer. I bought my laptop at the end of last summer and it's only 2ghz, 1gb ram.

---

### Post by bodhi.zazen on 2007-06-05
I have tried this method and rergret to report poor performance.

Yes, the low latency kernel is sufficient to get through set-up of Dragon, BUT:

1. VirtualBox is not yet stable. I am having difficulty with frequent crashes when using VB with dragon.

2. The accuracy and speed are poor. I have better performance, both speed and accuracy with Dragon. The problem seem to be when dictating long sentences or paragraphs there is failure of the sound interface. This leads to poor accuracy, slower performance, and at times failure to recognize large fragments of dictated speech.

3. It is not a memory issue as I have given VirtualBox 1 Gb RAM.

I have returned to DNS 7 and wine for now which gives much much better performance, although certainly there are issues with this solution as well (DNS 7 is a relatively old version and the GUI does not work 100 %).

I am hoping that future releases of VirtualBox and the low latency kernel will improve the performance of Dragon in VirtualBox.

This is NOT a criticism of VirtualBox, which is a fine product.

---

