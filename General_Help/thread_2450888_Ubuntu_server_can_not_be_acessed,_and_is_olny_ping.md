---
title: "Ubuntu server can not be acessed, and is olny pingable for a short time. SSH not work"
date: 2020-09-22
forum: General Help
---

### Post by evil-goat on 2020-09-22
My server is going wacko, and i'll try to explain to the best of my abilities. I have a minnowboard turbot with ubuntu server 20.04 installed. (its kind of like a raspberry pi or other single board computers, except it is x86_64.

So earlier today, my server was not accessible (i mainly use it to serve my web apps locally). So i rebooted it, and it worked fine for around 30 minutes, and every time i rebooted it, the time that is was usable got lower.

I also received tons of alerts from pulse way that my server was shutting down (i never shut it down).

I plugged the boot drive into my laptop, and booted it with vmware. Everything seemed to work fine in vmware ssh, my apps, etc, however, it was slow to boot. To try to fix it, i ran **_*sudo apt upgrade*_**, and i think it installed a newer kernel. I also disabled some services that used ram and cpu. None of this helped.

My server also takes forever to boot up. If i run a continuous ping, then it pings for about 1 min, then stops, then 5 minutes later, it starts pinging again, then it stops. When it is not pingable the ethernet light turns off. If i try to ssh into it, it says connection refused. One time it worked, then it said _***System is going down. Unprivileged users are not permitted to log in anymore. For technical details, see pam_nologin(8)***_. My account is not root, but it has sudo privileges. Why is this happening? It worked yesterday. Am I being hacked?

A similar thing happened a couple of months ago with linux mint, and i fixed it by installing a different os.

I do not have a monitor that is compatible with my server. Everything worked yesterday, and i didnt do anything that would cause this to happen

Please Help!

---

### Post by guiverc on 2020-09-22
Also asked at [https://askubuntu.com/questions/1277049/ubuntu-server-can-not-be-acessed-and-is-olny-pingable-for-a-short-time-ssh-als](https://askubuntu.com/questions/1277049/ubuntu-server-can-not-be-acessed-and-is-olny-pingable-for-a-short-time-ssh-als)

---

### Post by HermanAB on 2020-09-22
My guess is that you have a DHCP problem.

If the network basics are not configured right - nothing will work.

---

### Post by evil-goat on 2020-09-23
I don't have DHCP set up, and my adress is manual. It was working fine for several months with my configuration.

---

### Post by HermanAB on 2020-09-23
Well, if ping doesn't work, nothing else will.  The easiest debug solution is to log into the machine with a keyboard and screen, then verify that the network setting are indeed the way they are supposed to be.

BTW, even though you are not using DHCP, the client may be running and connecting to your router and then get a bad address after a minute or two.  So there are a number of low level things to investigate.

---

