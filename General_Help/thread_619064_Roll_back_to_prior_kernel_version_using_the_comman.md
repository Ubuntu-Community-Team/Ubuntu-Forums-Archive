---
title: "Roll back to prior kernel version using the command line"
date: 2007-11-21
forum: General Help
---

### Post by Grafster on 2007-11-21
I'd like to roll back to the kernel version prior to the one that was released through the update manager this weekend. I think it conflicts in some fashion with my hardware and/or negatively affects Xorg.

I only have access to a command line.
Is there any simple way to apt-get the prior kernel and replace the modern version?
Were there other updates this past weekend (i.e. was Xorg updated?) that I need to roll back as well.

I know it's an irritating question but I can't think of any other way to dig myself out of this hole.

---

### Post by darwin81 on 2007-11-21
Did you use Envy to install your graphic card drivers? Also, you should be able to boot into the old kernel by selecting it in the Grub boot list.

---

### Post by Grafster on 2007-11-21
I'm not familiar with Envy.
I just installed fluxbuntu from the CD.

Before that I also just installed Xubuntu from the CD.

I am an idiot for not booting with the prior kernel from my old Xubuntu install, but I can't change that. At the time I wasn't aware that Fluxbuntu installed from the repos. (I thought it was similar to other distros and had it's own, older, stable kernels & Xorg).

---

### Post by hikaricore on 2007-11-21
Errmm... why can't you just select the previus kernel from the Grub boot menu like suggested?

It will still be there unless you intentionally removed it..

---

### Post by Grafster on 2007-11-21
> **hikaricore said:**
> Errmm... why can't you just select the previus kernel from the Grub boot menu like suggested?

It will still be there unless you intentionally removed it..
Or it wouldn't be there if I'd just done a fresh install of fluxbuntu.

OK. I see the confusion.
Fluxubuntu installs its installer but (unlike other verisions of Ubuntu) it doesn't include a fully functioning system. It just goes partway (and I mean very partway), and then it runs apt-get to get everything else. 

So doesn't do a full system install for you and then have you update. 
I only have three choices on grub. 
1 Normal (non functioning)
2 safemode (leads to log-in and command line)
3 memory test

(I -didn't- know this when I was installing it on top of Xubuntu).

---

### Post by hikaricore on 2007-11-21
My appologies, I see the issue and I'm sorry I misunderstood you.  >.<

I hope someone can show you the right path to a fix as I'm not sure how much of a mess Fluxbuntu made of your previous install.  :(

---

### Post by Grafster on 2007-11-22
I wouldn't say mess. In principal apt-getting the newest kernel and latest programs would save time. That's the first thing a new user normally does.

It's just that one time in x (1000?) a user doesn't want to be up-to-date.

I didn't know about the behavior and/or appreciate just how much my hardware configuration doesn't like something that was in this weekends update.

---

### Post by Grafster on 2007-11-23
From the lack of responses should I assume that this installation is doomed, move on, and reinstall some other OS?

like fiesty server ubuntu + fluxbox or something?

---

