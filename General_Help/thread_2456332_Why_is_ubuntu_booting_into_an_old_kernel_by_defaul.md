---
title: "Why is ubuntu booting into an old kernel by default?"
date: 2021-01-09
forum: General Help
---

### Post by DanR01 on 2021-01-09
I'm running 20.04. Grub detects the following kernels.

```


Found linux image: /boot/vmlinuz-5.8.0-36-generic
Found initrd image: /boot/initrd.img-5.8.0-36-generic
Found linux image: /boot/vmlinuz-5.8.0-34-generic
Found initrd image: /boot/initrd.img-5.8.0-34-generic
Found linux image: /boot/vmlinuz-5.4.0-61-generic
Found initrd image: /boot/initrd.img-5.4.0-61-generic
Found linux image: /boot/vmlinuz-5.4.0-58-generic
Found initrd image: /boot/initrd.img-5.4.0-58-generic


```

For some reason, ubuntu always boots into 5.8.0-36-generic. 

The relevant output of cat /etc/default/grub is

```


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Does anyone have any suggestions on how to have a newer kernel automatically selected at boot?

Thank you

---

### Post by #&amp;thj^% on 2021-01-09
Kernel 5.4.0-61, is The LTS kernel=default >>> kernel 5.8.0-36-generic is more or less a point release, and currently breaking  some WiFi chips along with sound.
Newest isn't always better.rr 
For your question though, you would have to show us this as well:
```
ls -l /lib/modules/
```

---

### Post by ajgreeny on 2021-01-09
It is not booting to an old kernel; look properly at the kernel version numbers, in particular the second of the 4 digits in the version numbers and you will see you are now booting to 5.8.0-36.

Both of the two kernel versions that I believe you think are newer than 5.8.0-36 are in the 5.4 series.

Where id that 5.8.0-36 kernel come from; was it through normal upgrades?

---

### Post by DanR01 on 2021-01-09
My mistake, I didn't check the kernel versions properly. 

Thank you both of you. 

I had a kernel panic, I think due to a problem with the bcmwl-kernel-source package. I enabled focal-proposed updates to see if there was a newer kernel version which may be why I have a more recent linux version.

---

### Post by #&amp;thj^% on 2021-01-09
> **DanR01 said:**
>  I enabled focal-proposed updates to see if there was a newer kernel version which may be why I have a more recent linux version.
And thank you for adding "focal-proposed", this helps. :)

---

### Post by jeremy31 on 2021-01-09
> **ajgreeny said:**
> It is not booting to an old kernel; look properly at the kernel version numbers, in particular the second of the 4 digits in the version numbers and you will see you are now booting to 5.8.0-36.

Both of the two kernel versions that I believe you think are newer than 5.8.0-36 are in the 5.4 series.

Where id that 5.8.0-36 kernel come from; was it through normal upgrades?
It is coming from normal upgrades, you can check to see the results from ```
apt policy linux-generic-hwe-20.04
```
If you want to avoid the 5.8 kernels, you might have to ```
sudo apt remove linux-generic-hwe-20.04 && sudo apt autoclean && sudo apt install linux-generic
```

---

### Post by #&amp;thj^% on 2021-01-09
> **jeremy31 said:**
> It is coming from normal upgrades, you can check to see the results from ```
apt policy linux-generic-hwe-20.04
```


jeremy31 do you have proposed enabled??? I never showed kernel 5.8 until I enabled it. (This was a month or so ago)
Even then apt-policy never showed proposed as a source. I'm trying to clear up some confusion.

---

### Post by jeremy31 on 2021-01-09
> **1fallen said:**
> jeremy31 do you have proposed enabled??? I never showed kernel 5.8 until I enabled it. (This was a month or so ago)

Actually it happened on a fresh install with updates enabled.  I then reinstalled without internet, did a sudo apt update and then looked at results from the apt policy command, it showed a 5.4 kernel as installed version and 5.8.0-36 as candidate

I asked about in in #ubuntu-kernel and Kleber Souza replied
> By default the 20.04 media installs the hwe kernel for desktop images. The hwe meta was still pointing to the 5.4 generic kernel, until this week when we released an update to pull the hwe-5.8 backport

---

### Post by #&amp;thj^% on 2021-01-09
> **jeremy31 said:**
> Actually it happened on a fresh install with updates enabled.  I then reinstalled without internet, did a sudo apt update and then looked at results from the apt policy command, it showed a 5.4 kernel as installed version and 5.8.0-36 as candidate

I asked about in in #ubuntu-kernel and Kleber Souza replied

Big Baada Boom! ....Thank You Sir, that explains it.

---

### Post by ajgreeny on 2021-01-10
Does this depend on the original .iso version installed?  I installed right at the start of life of the released version 20.04, not 20.04.1, and I am not offered the 5.8 kernels when upgrading, only the 5.4 series.

I have no hwe packages installed but I'm aware that I could add them if I wanted, which currently I don't.

---

### Post by The Cog on 2021-01-10
I have a similar question. My laptop (Ryzen 4700U) doesn't work with the 20.04 kernels because they don't have the required drivers, so I had to install a recent kernel-ppa/mainline. I tend to get and install the latest whenever I see an apt update fetching another 5.4 kernel, on the basis that there must be a seciruty update in there. I'm currently on 5.10.5. This also involved disabling secure boot.

I gather that there may now be linux-generic-hwe-20.04 and linux-generic-hwe-20.04-edge package that could be installed. Apparently, these install kernel 5.8.0. Is there any more information on these anywhere? I haven't seen any announcements, let alone advice on which of the two is recommended under what circumstances.

---

### Post by jeremy31 on 2021-01-10
> **ajgreeny said:**
> Does this depend on the original .iso version installed?  I installed right at the start of life of the released version 20.04, not 20.04.1, and I am not offered the 5.8 kernels when upgrading, only the 5.4 series.

I have no hwe packages installed but I'm aware that I could add them if I wanted, which currently I don't.

TJ on IRC said that the 20.04 desktop ISO had the hwe listed in the manifest.  It is possible that an update in the past removed the hwe and installed linux-generic.  My ISO was dated 24 April 2020 so it was from before the first point release

I found the manifest file at [http://old-releases.ubuntu.com/releases/20.04.0/ubuntu-20.04-desktop-amd64.manifest](http://old-releases.ubuntu.com/releases/20.04.0/ubuntu-20.04-desktop-amd64.manifest) and it does list linux-generic-hwe-20.04	5.4.0.26.32

> **The Cog said:**
> I have a similar question. My laptop (Ryzen 4700U) doesn't work with the 20.04 kernels because they don't have the required drivers, so I had to install a recent kernel-ppa/mainline. I tend to get and install the latest whenever I see an apt update fetching another 5.4 kernel, on the basis that there must be a seciruty update in there. I'm currently on 5.10.5. This also involved disabling secure boot.

I gather that there may now be linux-generic-hwe-20.04 and linux-generic-hwe-20.04-edge package that could be installed. Apparently, these install kernel 5.8.0. Is there any more information on these anywhere? I haven't seen any announcements, let alone advice on which of the two is recommended under what circumstances.

I suspect if you remove linux-generic you won't get any more 5.4 kernel updates that you don't need.

The linux-generic-hwe and edge likely install the same kernel now but edge could change when 21.04 is released

---

### Post by ajgreeny on 2021-01-10
I installed 20.04 on 16 April 2020 but I do not have the .iso file any more so can not tell you when it was created or downloaded, but as you will see from that date, I downloaded it a few days before it was released, probably the RC version.

I do have **linux-generic** installed, as I thought was the case, so I do get, and will continue to get, kernel versions in the 5.4 series as expected.

However, I do not have the **linux-generic-hwe-20.04** package and did not expect it to be installed, therefore I do not get the 5.8 series of kernels and incidentally have no need for that series as my hardware is six years old.  You seem to be suggesting that the linux-generc-hwe-20.04 was included in your .iso file dated just 8 days after mine though I was always believed that package and the hwe kernel versions appeared by default only after the release of the point 2 versions of the .iso.

Do you know if there has been, or is intended to be, any change to the timing of the hwe kernels being included in .iso files in future?

---

### Post by jeremy31 on 2021-01-10
I did notice that the 20.04 Beta ISO did not have the hwe installed according to the manifest file but instead used linux-generic which would keep you on 5.4

---

### Post by ajgreeny on 2021-01-10
That explains it then, but it is certainly a change from what I thought was the expected behaviour related to the hwe updating system, ie, it would be included only in iso point version 2.

---

### Post by #&amp;thj^% on 2021-01-10
> **ajgreeny said:**
> That explains it then, but it is certainly a change from what I thought was the expected behaviour related to the hwe updating system, 

ajgreeny I was going batty over this at first....I kept asking folks in other threads about proposed but none replied back. (Shame on them ;) a simple yes or no)
jeremy31 finally put the madness to ease in the post above. 
> the hwe meta was still pointing to the 5.4 generic kernel, until this week when we released an update to pull the hwe-5.8 backport 

---

### Post by jeremy31 on 2021-01-10
> **ajgreeny said:**
> That explains it then, but it is certainly a change from what I thought was the expected behaviour related to the hwe updating system, ie, it would be included only in iso point version 2.

Yes indeed as in the past only the second point release caused this madness

---

### Post by kansasnoob on 2021-01-12
I asked about this at ubuntu-release:

[https://lists.ubuntu.com/archives/ubuntu-release/2021-January/005145.html](https://lists.ubuntu.com/archives/ubuntu-release/2021-January/005145.html)

That was the 9th, in the wee hours of the morning. So far no response. I maintain too many computers to fool with HWE unless it's absolutely needed for specific hardware which very seldom happens since most of the hardware I deal with is C2D era stuff, with a bit of I3, I5, and I7 stuff thrown in, and a couple of old but reliable AMD based PC's that just won't die!

---

### Post by CelticWarrior on 2021-01-12
> **ajgreeny said:**
> Does this depend on the original .iso version installed?  I installed right at the start of life of the released version 20.04, not 20.04.1, and I am not offered the 5.8 kernels when upgrading, only the 5.4 series.

I have no hwe packages installed but I'm aware that I could add them if I wanted, which currently I don't.

It does.
It has been that way at least since 16.04 but probably before. I noticed that due to an old Nvidia that was/is supported by the 304 driver only. That driver could be installed up to the original 16.04 kernel. I had to chase the original 16.04 ISO with the LTS kernel, any other point release would either install a newer "304 incompatible" kernel or would update to one soon after.

So, assuming the same situation here, those who installed pre-releases or the original release of 20.04 will be kept in the 5.4 series for the entire LTS life - getting security updates only for said kernel series - and may opt-in newer kernels by installing HWE. Everybody else, since 20.04.1, will get kernel updates to same kernel series the current release comes with after some time after said interim release. The 5.8 series kernel is the same as 20.10.

---

### Post by ajgreeny on 2021-01-12
But it used to be the point 2 release version that automatically upgraded the the higher kernel version, not the point 1 release as is currently happening.
That is why I was asking the question, now answered it seems by jeremy31 in post #17.

---

### Post by kansasnoob on 2021-01-12
I'm reasonably certain that this was a screw-up. Besides [the link I included with my message to ubuntu-release]("https://ubuntu.com/kernel/lifecycle#support-lts") this link reaffirms that:

[https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle](https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle)

I assume that at some point during 20.04.1 development 'linux-generic' was replaced by 'linux-generic-hwe-20.04'. In fact if this had been intentional the HWE update should also have included the HWE Xstack.

---

### Post by kansasnoob on 2021-01-13
> **jeremy31 said:**
> I did notice that the 20.04 Beta ISO did not have the hwe installed according to the manifest file but instead used linux-generic which would keep you on 5.4

In deed. I checked the .iso manifests this morning and both 20.04 and 20.04.1 show linux-generic-hwe-20.04, but the Beta shows linux-generic. This was clearly a mistake based on all the support documentation I've found.

---

### Post by darand on 2021-01-13
> In deed. I checked the .iso manifests this morning and both 20.04 and  20.04.1 show linux-generic-hwe-20.04, but the Beta shows linux-generic.  This was clearly a mistake based on all the support documentation I've  found.

I am not sure if I understand it right. The only way to stay with 5.4 kernel is to install Ubuntu 20.04 (beta)? Can I expect they (Ubuntu team) will change both Ubuntu 20.04 and Ubuntu 20.04.1 to work this way?

---

### Post by jeremy31 on 2021-01-13
I think if you install 20.04 or 20.04.1 without internet, so it doesn't update, you should be able to boot into the install and remove the linux-generic-hwe-20.04 and install linux-generic before updating and you should be able to stay on the 5.4 LTS kernel

---

### Post by kansasnoob on 2021-01-13
I'm still gathering data as time allows. This appears to be limited to Ubuntu only. I didn't check all of the flavors but for Ubuntu MATE, Kubuntu, Xubuntu, and Lubuntu have linux-generic on their 20.04.1 images. I'm going to see what happens if I do a fresh install of Ubuntu MATE, update, and then install 'ubuntu-desktop' to see what happens. Obviously I need to file a bug report because no one at ubuntu-release answered my question. And it's really not a 'linux' bug - it's a build bug. So I'm just trying to figure out how best to file a bug report. I think it falls into the 'ubuntu-meta' category but you can't file an ubuntu-meta bug because it's not an installed package.

---

### Post by kansasnoob on 2021-01-14
I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1911614](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1911614)

More subscribers and marking it as effecting you too will turn up the heat. No heat - no fix.

---

### Post by darand on 2021-01-14
Thanks for answers. I am afraid this is disaster for newcomers dependent on nvidia-340 driver. They had fine working OS and all of the sudden after nine months, they had to become power users or worst, they gave up on Ubuntu.

---

