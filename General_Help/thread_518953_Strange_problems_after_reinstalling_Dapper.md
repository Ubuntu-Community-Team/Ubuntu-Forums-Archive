---
title: "Strange problems after reinstalling Dapper"
date: 2007-08-06
forum: General Help
---

### Post by tszanon on 2007-08-06
Oh well. This is not a "help me" thread, neither a rant, just a case that is happening to me and I'm curious about why it is happening.
I was using Dapper and decided to upgrade to Feisty. Everything went smoothly, but I decided to go back to Dapper (reasons are irrelevant). I had made a partition image using partimage, but it didn't work. So, I used another backup image of /. I must say that my disks are like this:
/boot: sda1
/: md0 (raid0)
/home: md1 (raid0)
swap: md2 (raid0)

I had not made an image of /boot, just /. Everything restored, but Ubuntu stopped after boot (blank screen, could not even log in). So I decided to reinstall Dapper, reusing /home. Done. Now my problems start:
**1. gnomebaker** had a different interface. Instead of asking me what I wanted to do (data cd, data dvd, and so on), it shows me an Nero-like interface. It couldn't even format my dvds. After checking for cdrecord, cdrdao and dvdrwtools, I decided to install k3b, and it worked. Gnomebaker's behavior is still a mistery to me.
**2. p7zip (7z)**: this little guy decided to refuse the multithread switch (-mmt=on). It worked fine before the whole upgrade/downgrade procedure, but now it gives me a segmentation fault if I use -mmt=on.

I'm preparing myself for a full-system reinstall, including some rearraging of the partitions, but, anyway, I'm curious about why these errors are happening. If anyone has a clue, I'd like to know.

My computer:
Athlon64 X2 3800+
1 GB RAM
most recent linux-image for Dapper-64bits, specific for amd64-k8.

---

### Post by Butthead on 2007-08-06
Stupid question, but did you ever have the amd64-k8 kernel successfully running under Dapper?

The reason I'm asking is that I tried installing the k8 kernel on my X2 processor after reading another thread that claimed I might not be using my CPU up to it's full potential with just the amd64-generic "Dapper" kernel (even though issuing the "top" command under konsole shows two cores showing up with just the generic kernel installed), and it promptly locked up on me when I tried to reboot with the new k8 kernel installed. 

I'm wondering if Dapper has trouble with the k8 kernel (especially after seeing that the Adept installer referred to it as an "Edgy" kernel?). :confused:

---

### Post by tszanon on 2007-08-07
> **Butthead said:**
> Stupid question, but did you ever have the amd64-k8 kernel successfully running under Dapper?

The reason I'm asking is that I tried installing the k8 kernel on my X2 processor after reading another thread that claimed I might not be using my CPU up to it's full potential with just the amd64-generic "Dapper" kernel (even though issuing the "top" command under konsole shows two cores showing up with just the generic kernel installed), and it promptly locked up on me when I tried to reboot with the new k8 kernel installed. 

I'm wondering if Dapper has trouble with the k8 kernel (especially after seeing that the Adept installer referred to it as an "Edgy" kernel?). :confused:
I didn't do anythng special to use it. I just installed it, removed the amd64-generic, and that's it.
About Dapper not using the full potencial of the processor, I think it's just because the amd64-generic is not compiled specifically for k8. It performs slower than the k8, but people say the difference is irrelevant (and this was one of the reasons that made the developers discontinue a specific k8 linux-image). If I recall correctly, this irrelevant difference in performance is the only difference between amd64-generic and amd64-k8.

---

### Post by Butthead on 2007-08-07
> **tszanon said:**
> I didn't do anythng special to use it. I just installed it, removed the amd64-generic, and that's it.
About Dapper not using the full potencial of the processor, I think it's just because the amd64-generic is not compiled specifically for k8. It performs slower than the k8, but people say the difference is irrelevant (and this was one of the reasons that made the developers discontinue a specific k8 linux-image). If I recall correctly, this irrelevant difference in performance is the only difference between amd64-generic and amd64-k8.

Well, if you're having no problem running the k8 kernel under Dapper (as in it not locking Dapper up), I see no reason in not continuing to use it. :)

As for me, the AMD64-generic kernel seems to run plenty snappy on my X2 rig (even shows two cores showing up when issuing the "cat /proc/cpuinfo" command).  I see no reason to go in there and possibly break a good thing. :guitar:

---

### Post by tszanon on 2007-08-08
> **Butthead said:**
> I see no reason to go in there and possibly break a good thing. :guitar:

According to my experience, as I mentioned earlier, that's a good idea! :)
Or you could create a partition image of each partition you have and then try...:)

---

### Post by Butthead on 2007-08-08
> **tszanon said:**
> 
Or you could create a partition image of each partition you have and then try...:)

Naw, that sounds too much like work (which is something I try to avoid doing too much of). :mrgreen:

---

