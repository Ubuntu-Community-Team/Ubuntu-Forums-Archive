---
title: "[SOLVED] Kubuntu/Ubuntu installation failure"
date: 2008-07-08
forum: General Help
---

### Post by surveyork on 2008-07-08
Hi there!

I tried installing Kubuntu 4 KDE but failed every time. First, Avast! antivirus 4.8 would go off when running wubi, saying that wubi is a virus. Running a manual scan on wubi doesn't detect any virus. I re-downloaded Wubi from different mirrors, always with the same results.

Then I decided to turn Avast! off during the installation process and things went a bit better, but not good enough. I had previously downloaded the Kubuntu KDE 4 iso and placed it on the same folder as wubi. After finishing the Wubi wizard, Wubi started copying the Kubuntu iso to the /ubuntu/install folder. Then, wubi performed checksums, and then... it **deleted** the Kubuntu iso and started downloading a new iso from the server.

Anyways, I then tried to install Ubuntu Gnome via wubi downloading the iso from the server and got installation error after a few seconds. This happened multiple times.

Any clues of what's going on? I'm running Windows XP SP3 on an AMD Turion 64. I have no problems at all with all my other software.

Thanks in advance.

---

### Post by ago on 2008-07-08
> **surveyork said:**
> Then, wubi performed checksums, and then... it **deleted** the Kubuntu iso and started downloading a new iso from the server.
Most likely the ISO was corrupt. 

Can you please send the wubi logs for the rest? They are in the user temp folder.

---

### Post by surveyork on 2008-07-08
> **ago said:**
> 
Can you please send the wubi logs for the rest? They are in the user temp folder.

Oops! I just flushed my temp folder. There's no trace of the logs, sorry.:(

---

### Post by surveyork on 2008-07-08
I tried a few more times. Log attached.

---

### Post by ago on 2008-07-08
There were some issues with kubuntu server settings, either retry later or use Ubuntu and then install the kubuntu-desktop package. You can also try to download the kde ISO manually and install without network connection.

---

### Post by surveyork on 2008-07-10
Hi there again.

Finally, I was able to install Kubuntu using VMware. So far, so good. The only glitch I found is the mouse wheel, which doesn't work.

I have to say that I'm very happy with Kubuntu and very impressed by Adept: I installed 20+ software in one shot and without rebooting :lolflag:

Now I hope to get the hang of Kubuntu step by step. I'm specially worried about how to install software that has to be compiled first, but that's another story and I'll ask in some other forum.

Lastly, I just wanted to say that Wubi gave me many headaches: Avast! warnings, failed installations... I sincerely hope the next version would be better.

---

