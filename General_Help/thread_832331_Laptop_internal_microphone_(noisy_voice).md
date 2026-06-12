---
title: "Laptop internal microphone (noisy voice)"
date: 2008-06-17
forum: General Help
---

### Post by pb_online on 2008-06-17
I used to have Ubuntu with no problem with microphone.

Now I have Kubuntu (clean install).

When I have an audio conversation on Skype, my voice sounds noisy. I mean, my voice is not clear.

I try play with settings on Kmix without effect.

Anyone with similar problem?

---

### Post by darik on 2008-06-22
I am also having the same issue in Hardy with a laptop Acer Aspire 5003wlmi.

Did you find any solution yet?



lspci | grep audio

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

---

### Post by rchar66 on 2008-08-27
I've seen this problem before and even just recently. It's usually just as simple as adjusting the slider down slightly for the microphone you're are using, and it will sound really clean.

For example; on my laptop when it was set at 100%, it was really dirty sounding and distorted. When I adjusted the slider to anywhere between 70% - 80%, it sounded crystal clear.

It just takes a little playing with to get it adjusted right. I would start at 80% and see how it sounds and if you need to, adjust it down about 5% and check it again.

---

