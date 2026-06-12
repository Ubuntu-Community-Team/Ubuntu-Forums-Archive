---
title: "Trying to raise the dead with an old device?"
date: 2019-02-05
forum: General Help
---

### Post by adrian-h on 2019-02-05
I have some old thin clients  these are pre PAE systems with the Transmeta Crusoe TM5800 processors and I managed to download a iso for ubuntu server version 11.04 from one of the links off the main download site.

Problem I have is if I wish to install anything else apt-get can not find it as I get

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources  404  Not Found [IP: 91.189.88.161 80]
```

Which is not surprising as it is obsolete.
Now when I log in I get a message
New release '12.04.5 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

I have not tried this yet as I know that the kernel in 12.04 will not run on the processor even with trying to forcepae.

Can I release upgrade without the kernel being changed or is that it for these devices.  I am basically trying to make an embedded style box with the thin client, it draws very little power and is fanless so no noise, has a parallel port to allow some interfacing with the outside world.

Any advice appreciated.

Adrian

---

### Post by Frogs Hair on 2019-02-05
12.04 is out of support an not secure either. If you were to upgrade and not remove the old packages you could retain the old kernel and try to boot from it. My recommendation is to retire the computer or use only off line.

---

### Post by adrian-h on 2019-02-05
This is only for internal house use.

I will do a do-release-upgrade and see what happens, but may need to ask about keeping the kernel?

Adrian

---

### Post by adrian-h on 2019-02-05
OK I managed to get upgraded to ubuntu 12.04.05 LTS with kernel 3.2.0-126-generic-i586 and that works OK.

getting hints to go to 12.10, but I think that is for another evening. Correction just tried and 12.10 does not support a non PAE processor so I am where I am going to stay with this hardware I think?

Adrian

---

### Post by Frogs Hair on 2019-02-05
The old repositories may be helpful.
[https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release](https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release)

---

### Post by HermanAB on 2019-02-05
For museum items, OpenBSD may be best.  They provide hardware support for a very long time.

---

### Post by Impavidus on 2019-02-06
If I remember correctly, Xubuntu 12.04 was the last Ubuntu flavour/version that supported a non-PAE kernel. It's no longer supported. But there are Linux distros specifically for old hardware. One of those may still provide a non-PAE kernel.

---

### Post by adrian-h on 2019-02-06
Sorry for the delay in getting back and thank you all for the responses, I have been busy and had little time with the PC tonight.

I am happy to have got it up to 12.04 and provided I can download the odd extra bit of software for learning a bit more on I will be happy.  I have also got one of the puppy 5.7.1 iso's on a unit based on Slackware I believe that was still an old release as they all seemed to go PAE and when I tried the software repository for that it was no longer working.

All I need to do now with this old unit is regain some space by removing the older kernals, it still has:

3.0.0-12 generic/recovery mode as well as the later 3.2.0-126. 

When I do a dpkg --list | grep linux-image it shows versions:
 3.2.0-126.169
3.2.0-126.141.
3.0.0-12.20

So I have removed 3.0.0 that has given approx 170 Mb extra in flash memory.

All is good it still boots!

Adrian

---

