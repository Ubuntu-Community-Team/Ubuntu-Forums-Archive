---
title: "Problem installing Simple scan"
date: 2020-05-08
forum: General Help
---

### Post by nwpll on 2020-05-08
Today i couldn't get Simple scan to scan a document. 
I deleted Simple scan and tried to reinstall but it stopped partway through the install. 
I then tried to install via the Terminal and again a problem i have copied and pasted from the terminal.
If i try to install another scan program the same happens.
Thanks for taking the time to read my post

```
sudo apt-get install simple-scan
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-wine libodbc1 libosmesa6 libwine linux-headers-4.10.0-37
  linux-headers-4.10.0-37-generic linux-headers-4.10.0-38
  linux-headers-4.10.0-38-generic linux-image-4.10.0-37-generic
  linux-image-4.10.0-38-generic linux-image-extra-4.10.0-37-generic
  linux-image-extra-4.10.0-38-generic wine32
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed
  simple-scan
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 170 kB of archives.
After this operation, 1,196 kB of additional disk space will be used.
Err:1 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) zesty/main i386 simple-scan i386 3.24.0-0ubuntu1
  404  Not Found
N: Ignoring file 'tor.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/pool/main/s/simple-scan/simple-scan_3.24.0-0ubuntu1_i386.deb](http://pt.archive.ubuntu.com/ubuntu/pool/main/s/simple-scan/simple-scan_3.24.0-0ubuntu1_i386.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by slickymaster on 2020-05-08
*Thread moved to **Hardware**.*

---

### Post by The Cog on 2020-05-08
Doesn't sound like a hardware problem to me.

Zesty is out of support (released in 2017). You haven't had security updates for 2 years, and I guess the software repository has been removed. You really should upgrade. 20.04 was released recently, and that is a Long Term Support release.

---

### Post by slickymaster on 2020-05-08
> **The Cog said:**
> Doesn't sound like a hardware problem to me.

Zesty is out of support (released in 2017). You haven't had security updates for 2 years, and I guess the software repository has been removed. You really should upgrade. 20.04 was released recently, and that is a Long Term Support release.

Quite right, The Cog.

Moving it back to General Help

---

### Post by nwpll on 2020-05-08
Thanks Guys

I should have said i am using 17.04 because my machine is old and will not update past 17.04 until i can afford a newer machine i am stuck with 17.04 but i still need to be able to scan documents.

Sorry i didn't put this information in my original post.

Peter

---

### Post by CelticWarrior on 2020-05-08
There are no significant differences between 17.04 and newer releases in what concerns hardware support. Ubuntu 20.04 should run as well or even better than 17.04. Have you tried yet? Or are you assuming it *will not update past 17.04* because of some failed attempt of online upgrade in the past? All those attempts will surely fail now because the time frame to do that ended in January 2018.

Do NOT use End of Life releases, ever. There's no excuse, period.

---

### Post by nwpll on 2020-05-08
I tried to upgrade from the terminal
sudo apt-get upgrade
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
N: Ignoring file 'tor.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

Can someone tell me now what do i do to upgrade Please

---

### Post by lwalper on 2020-05-09
From what I've seen at the upgrade page is that using the automatic update like you tried will not work until there is a dot update (ie. 20.04.1). It appears that that should happen in about 3 months.

In the meantime you can download the .iso file and do a full install of 20.04. That's what I did and it works great for me. The only thing with that (and maybe with the automatic update??) is that the install process will overwrite any and all personal stuff in the previous install. Back-up anything you want to keep, make note of any software you like to use so you can reinstall it, and go for it.

On another note, I've been trying to use Simple Scan unsuccessfully for a few months now on 18.04.6. No joy! Unhappy. :( Still stuck with WinXP for that.

---

### Post by CelticWarrior on 2020-05-09
> **nwpll said:**
> I tried to upgrade from the terminal
sudo apt-get upgrade
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
N: Ignoring file 'tor.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

Can someone tell me now what do i do to upgrade Please

Please understand those commands keep the current release updated, they don't upgrade to the next release. And also as commented several times already there are NO updates for 17.04 now.
There's no online upgrade path from 17.04 to anything with support other than going 17.04 > 17.10 (another EoL release) > 18.04 (supported). Doing so will take a lot more time (10x more) than installing fresh and anything wrong can and will hapeen. So no, DON'T EVEN THINK ABOUT IT.

Please do your backups - something you should do anyway - and then install from scratch the current LTS which is 20.04 and supported until April 2025.

---

### Post by The Cog on 2020-05-09
Sorry, but I think CelticWarrior is right. Your path of least pain is to make sure you have a good backup of your /home directory, and then install 20.04, then restore the home backup.

---

