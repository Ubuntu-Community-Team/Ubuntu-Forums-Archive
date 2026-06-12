---
title: "After the last update crashed"
date: 2018-01-12
forum: General Help
---

### Post by ubu112 on 2018-01-12
I have Acer Aspire One AOA150 with Lubuntu 16.04.3 LTS.

Today,after update,I rebooted and I had just a black screen with strange lines.,later 3/4 black and 1/4 the regular screen,but I can do nothing.

I can install a new version of Lubuntu,because I don't have nothing important.

But,if the problem is the last update,I'd return to the same situation.

Can,please,someone suggest to me what can I do?

Thank you

---

### Post by cruzer001 on 2018-01-12
Could it be?

[https://ubuntuforums.org/showthread.php?t=2382325&p=13729977#post13729977](https://ubuntuforums.org/showthread.php?t=2382325&p=13729977#post13729977)

---

### Post by ubu112 on 2018-01-12
cruzer001,thank you for your answer.

I'm not an expert and honestly I don't know if this can be the same or similar.

If I understand well you suggested to come back to the previous kernel,but first I don't know how it can be done,can you,please,explain to me what have I to do?

Second,in this situation seem to me that I can do nothing,but maybe I'm wrong.

Thank you

---

### Post by cruzer001 on 2018-01-12
Hay, not a problem and its painless :)

When you boot your system you have a screen that looks something like this:

[http://i1-news.softpedia-static.com/images/news2/How-to-Log-In-Ubuntu-Without-Knowing-the-Password-460864-2.jpg](http://i1-news.softpedia-static.com/images/news2/How-to-Log-In-Ubuntu-Without-Knowing-the-Password-460864-2.jpg)

Use the arrow keys and select advance options.  It will then give you the option to boot from previous kernel or a choice of older kernels.

And your done, continue the boot process.

More here if you want some reading:

[https://www.google.com/search?client=ubuntu&channel=fs&q=how+to+boot+from+old+kernel+in+ubuntu&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=how+to+boot+from+old+kernel+in+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by monkeybrain20122 on 2018-01-13
Or you can upgrade your Nvidia driver [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742095/comments/29](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742095/comments/29)

---

### Post by ubu112 on 2018-01-13
@cruzeroo1,now I have 4.13 kernel,I tried with the previous 4.10 and it works fine.Therefore,4.13 seem to be the problem.Now,I don't know what have I to do?

@monkeybrain20122,as I said,I'm not an expert.Have,this old netbook,Nvidia driver?

Thank you

---

### Post by ubu112 on 2018-01-13
@Pilot6,as you can read above,after the last update my system crashed.

I fund your solution :  [https://askubuntu.com/questions/945403/how-to-downgrade-kernel-after-bad-update-16-04](https://askubuntu.com/questions/945403/how-to-downgrade-kernel-after-bad-update-16-04)

I deleted the bad kernel 4.13.0-26 and then : sudo apt install linux-generic.

If I'm not wrong,this was the Meltdown patch and,obviously,I need it.

Now,I'm working with the previuos kernel and everything is fine.

I'd like to understand,because I'm not an expert,if ,the next time, this kernel will be updated? and,I hope,it will be the right kernel.

Thank you

---

### Post by asi6 on 2018-01-16
> **ubu112 said:**
> I have Acer Aspire One AOA150 with Lubuntu 16.04.2 LTS.

Today,after update,I rebooted and I had just a black screen with strange lines.,later 3/4 black and 1/4 the regular screen,but I can do nothing.

I can install a new version of Lubuntu,because I don't have nothing important.

But,if the problem is the last update,I'd return to the same situation.

Can,please,someone suggest to me what can I do?

Thank you

Hello, I have a similar netbook (Asus eee 901) with xubuntu 16.04 only and yesterday after the upgrade I ended with the same error as you described. But I have the problem that when booting I can not see the grub menu screen (I am not sure if this is because it is not active or because is too fast or what) and I dont know how to boot with an older kernel.

---

### Post by cruzer001 on 2018-01-16
> **asi6 said:**
> I have the problem that when booting I can not see the grub menu screen (I am not sure if this is because it is not active or because is too fast or what) and I dont know how to boot with an older kernel.

The Google link in post #3 will not work for you (the very top one in that link)?

---

### Post by asi6 on 2018-01-21
I have finally been able to enter the GRUB menu, tried to play with recovery mode and discovered that if I select resume with standar loading, I can get into the system but the display driver apparently is not loaded then (it boots at 800x600 instead 1024x600 resolution and detects a "generic" screen) but when I reboot the computer again without stopping on the grub menu the screen goes crazy again.
Finally I have installed grub-customizer (too lazy to edit files) to select the 4.10.0-42-generic as default. Now I can boot without that screen artifacts.
Is there any problem to stay with that "old" kernel? Will I be able to upgrade to new versions in the future?
thanks

---

