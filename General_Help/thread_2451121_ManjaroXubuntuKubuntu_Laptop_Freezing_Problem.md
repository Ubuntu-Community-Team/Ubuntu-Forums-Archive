---
title: "Manjaro/Xubuntu/Kubuntu Laptop Freezing Problem"
date: 2020-09-27
forum: General Help
---

### Post by sheerpython on 2020-09-27
Hello!
I have been trying to get my laptop working on linux since i won't have access to my desktop for a while, but I have been having some problems. I started with a installation of Manjaro KDE and it installed without any problems, after using it for a bit and setting up everything it started to crash/freeze the whole system and will only resume after a hard shutdown. That was about a week ago and just now had time to start looking at it again. I opened some logs and also made the discovery that when doing a reboot gets stuck on disabling iq9 and that it needs to fully shutdown to avoid this problem. So after that I tried 2 other distros first Kubuntu since I like KDE and at the end of the installation it gave an error that the installer could not finish. I fixed it by booting in rescue mode and enabling networking and ran updates. After using it for a bit the problem came back while trying to copy files, so since the problem was still occuring I tried Xubuntu but very quickly found out that the problem wasn't fixed.

So some testing and trying 'fixes' that I found online and I still can't fix the problem. I found out that the problems occur when installing/launching applications and sometimes completely at random. When launching a installer of Kubuntu/Xubuntu its giving a lot of errors which I added with this post.

Something that happend while writing this post is after I have connected a second display the plasma-shell doesn't start anymore and had to psot this using a live usb of kubuntu.

If there are any logs that I need to provide than please explain me how to get them since I'm a noob at troubleshooting. :)

Operating System: Kubuntu 20.04
KDE Plasma Version: 5.18.5
KDE Frameworks Version: 5.68.0
Qt Version: 5.12.8
Kernel Version: 5.4.0-42-generic
OS Type: 64-bit
Processors: 8 × Intel® Core™ i5-8300H CPU @ 2.30GHz
Memory: 7,7 GiB of RAM
Gpu: gtx 1050 4GB
Storage: NVME Kingston SSD 1TB


Some errors in KSystemlog after installing the proprietaiy drivers
[IMG]https://i.imgur.com/Jpl5FCi.png[/IMG]

Errors when booting USB of Kubuntu:
[IMG]https://i.imgur.com/AFECJXQ.jpeg[/IMG]
[IMG]https://i.imgur.com/qWReVa9.jpeg[/IMG]

---

### Post by CelticWarrior on 2020-09-27
Welcome.

Please assure you're booting > installing in UEFI mode with Secure Boot OFF / Fast Boot OFF and in your specific case TPM OFF.
In any case you may need UEFI and SSDs firmwares upgrades.

---

