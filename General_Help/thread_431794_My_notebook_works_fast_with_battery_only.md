---
title: "My notebook works fast with battery only"
date: 2007-05-03
forum: General Help
---

### Post by OmeuNOME on 2007-05-03
Hi!

I have an Asus A6Va and when I use Ubuntu with battery only, he runs fast, but when I plugged in the AC power, he runs slowly. I have Beryl with AIGLX and the graphics card is ATI X700 Mobility.

I have more performance with battery only, and when AC power is plugged in the performance slow down, but if I unplugged again, the performance increases.

If anybody knows how to fix the problem, I appreciate.

thanks

(sorry about my English)

---

### Post by deathbyswiftwind on 2007-05-03
sounds like your power management is screwy. Are you running ubuntu or kubuntu? If Kubuntu just right click on your power icon and switch your cpu to performance.  I dont know how to change it right in gnome but I will look into it and get back to you

---

### Post by OmeuNOME on 2007-05-03
I use Ubuntu 7.04 Beta, but all the updates are installed.

I try to change the power options, but doesn't work. :(

thank you!

---

### Post by pcjoe on 2007-05-09
I've had various issues with my asus z70va notebook jumping around in performance. I figured it was the x700 as well since my beryl would randomly lock up, but apparently it was a cpu issue. From _**[this](https://launchpad.net/ubuntu/+source/linux-meta/+bug/30570)**_ bug, it seems like a Pentium M issue. The suggested fix is to enter the following command as root (sudo su):
echo 1 > /sys/module/processor/parameters/max_cstate

This change doesn't persist over reboots... If your performance increases, you should add it to your /etc/rc.local file (before the exit 0 line). This seems to have fixed my performance problems with my laptop, hope it helps you out too :)

---

### Post by OmeuNOME on 2007-05-14
> **pcjoe said:**
> I've had various issues with my asus z70va notebook jumping around in performance. I figured it was the x700 as well since my beryl would randomly lock up, but apparently it was a cpu issue. From _**[this](https://launchpad.net/ubuntu/+source/linux-meta/+bug/30570)**_ bug, it seems like a Pentium M issue. The suggested fix is to enter the following command as root (sudo su):
echo 1 > /sys/module/processor/parameters/max_cstate

This change doesn't persist over reboots... If your performance increases, you should add it to your /etc/rc.local file (before the exit 0 line). This seems to have fixed my performance problems with my laptop, hope it helps you out too :)


thank tou very much, my performance increases since I enter de command, now I will add it to my rc.local file. problem fixed ;)

thanks

---

### Post by fragility14 on 2007-07-08
it says bash command not found...

I am having similiar problems though maybe not entirely the same....I want to test this fix though.

---

