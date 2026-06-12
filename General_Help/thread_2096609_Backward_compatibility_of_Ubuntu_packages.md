---
title: "Backward compatibility of Ubuntu packages"
date: 2012-12-20
forum: General Help
---

### Post by Holmes.Sherlock on 2012-12-20
I haven't used Ubuntu much. Now I want to give it a try. The problem I'll face is t install software from the repository. I don't have a "thick" Internet connection. So I googled a bot and found [this thread]("http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline") which elaborates a few methods to download repository contents offline and use later. This way I can get the packages downloaded onto some other PC having a good Internet connection and install on my laptop. Now the doubt I have is, say I download packages for Ubuntu 10.04. Since Ubuntu releases a upgrades bi-annually, later on I switch to some other version, say 12.10. Do I need to download all the packages again, or will the older packages which I already downloaded for 10.04 be still installable on newer platform? Are Ubuntu distros backward compatible as far as packages are concerned? Someone please clarify.

---

### Post by snowpine on 2012-12-20
No, every package in every Ubuntu release is different than in the release that came before. All of the software in 12.10 is 2 and a half years newer than in 10.04, there is no backwards compatibility.

If you have a very slow connection then I recommend the LTS releases (currently 12.04) as you can use them up to 5 years with only minor security/stability patches.

---

### Post by Holmes.Sherlock on 2012-12-20
> **snowpine said:**
> No, every package in every Ubuntu release is different than in the release that came before. All of the software in 12.10 is 2 and a half years newer than in 10.04, there is no backwards compatibility.
Does it mean one has to install whole lot of packages bi-annually if he wants to stay updated with Ubuntu? 

Crazy.

---

### Post by snowpine on 2012-12-20
New Ubuntu releases are 100% optional, nobody forces you to update. But the majority of users **want** updated software and new features on a semi-regular basis, which is why Ubuntu is the #1 consumer distro, consistently beating out more conservative distros that are slower to adapt, evolve, and change. It's human nature, no different than buying a "new and improved" iPhone 5 even though your iPhone 4 works just fine. Why do you think that is "crazy" to want the latest & greatest? :)

I am sorry that you have a slow connection, but this is 2012 and the average person can download in less than 15 minutes an entire Ubuntu release containing 6 months of updates, innovations, and new features. Are you implying Ubuntu should be frozen in time, the programmers should be fired, and development should cease on these updates, innovations, and new features, in order to cater to the needs of those unfortunate few without broadband? ;)

---

### Post by Pjotr123 on 2012-12-20
Stick to the LTS; starting with 12.04, they last five years with only security updates and stability updates (plus the occasional new Firefox and Chromium thrown in).

Explanation of LTS:
[https://sites.google.com/site/easylinuxtipsproject/version](https://sites.google.com/site/easylinuxtipsproject/version)

Explanation of updates:
[https://sites.google.com/site/easylinuxtipsproject/faq#TOC-When-do-I-get-the-newest-version-of-an-application-from-the-Ubuntu-update-servers-](https://sites.google.com/site/easylinuxtipsproject/faq#TOC-When-do-I-get-the-newest-version-of-an-application-from-the-Ubuntu-update-servers-)
(item 16, right column)

---

### Post by grahammechanical on 2012-12-20
Where do you live? Can you buy Linux magazines that give away DVDs of Linux? When I installed Ubuntu in 2007 I had a dial-up modem but I went from 7.04 up 9.04 every six months by getting a free DVD from a Linux magazine.

Once you have Ubuntu 12.04 installed you will not need to change for another five years. Any security updates will not take excessive times even with dial-up.

Regards.

P.S. I have thought of something else as to why 12.04 packages cannot be backwards compatible with 10.04 - Gnome. Ubuntu is built on the Gnome Desktop Environment. Ubuntu 10.04 is built upon Gnome 2 DE, which is no longer being developed by the Gnome Organization. So, Ubuntu has had to switch to the Gnome 3 DE, which is what we get from Ubuntu 11.10 onwards. There are also special libraries in 12.04 onwards that make using 32 bit applications on the 64 bit Ubuntu more effective. These libraries do not exist for 10.04.

---

### Post by snowpine on 2012-12-20
Also note there are many reputable online vendors who will snail-mail you an Ubuntu DVD for about $5 + S&H.

---

### Post by Holmes.Sherlock on 2012-12-20
I am not quoting anyone. But this is the reply to last four posts on this thread. You have misinterpreted the word "Crazy" in relating to its context. As I prepare, say Ubuntu 10.04, with all the software I need, why should one re-download "everything" (not talking about the distro ISO image, but the software running on it) if I want to say updated with Ubuntu releases. What makes all the packages for 10.04 to get invalidated with 10.10? I am using a Windows box and there are two pieces of legacy software which were meant for Win 98, but works perfectly fine till Win 7 (Don't know whether work with Win 8 or not). Imagine the situation of users if they were to download/buy all the software they use with every release of Windows, had it NOT been backward compatible. So, once I prepare a distro with all apps on it, am I not being forced to make use of it in spite of new releases are coming up? Hope you have got my point. No offense, please.

---

### Post by snowpine on 2012-12-20
I may have misunderstood your original post, apologies.

If you are talking about 3rd-party software NOT provided by Canonical (software you have manually purchased/downloaded/installed, analogous to the legacy Win 98 apps you are currently running in Win 7), then it is possible this software might work (or might not work) in newer Ubuntu releases. This would be up to the 3rd-party software developer and is not something Canonical/Ubuntu can control or guarantee. :)

Furthermore Linux has tools such as virtualization and chroot that professionals can and do use to run legacy applications on an everyday basis.

Hope that helps clear up our earlier misunderstanding.

---

### Post by Holmes.Sherlock on 2012-12-20
> **snowpine said:**
> 
...then it is possible this software might work (or might not work) in newer Ubuntu releases. This would be up to the 3rd-party software developer and is not something Canonical/Ubuntu can control or guarantee. :)
.
.
.
Hope that helps clear up our earlier misunderstanding.

Yes, I got it. :)

Then what policy do you (means regular Ubuntu users) follow to update Ubuntu? Do you update Ubuntu with every new release and re-install 3rd party apps again or stick to a version which you yourself familiar with? 

If I start using Ubuntu now, shall I go for latest 12.10 or some earlier release?

---

### Post by snowpine on 2012-12-20
I do not use Ubuntu personally, but my philosophy in general is to do a fresh reinstall. I like that "fresh clean" feeling of starting over with a new release, rather than an upgrade. It's a good opportunity to clean out the junk and start filling it up with more junk. :)

More specifically to your question, I see many failed updates due to 3rd party repositories. Therefore I recommend disabling all 3rd party repos before attempting an Ubuntu upgrade. Also as mentioned above I recommend the LTS releases (currently 12.04, which is supported through April 2017) for someone in your situation.

---

### Post by Holmes.Sherlock on 2012-12-20
> **snowpine said:**
> I do not use Ubuntu personally, but my philosophy in general is to do a fresh reinstall.

Means it is better to re-install 3rd party apps with every new release.

> **snowpine said:**
> 
Also as mentioned above I recommend the LTS releases (currently 12.04, which is supported through April 2017) for someone in your situation.

How does LTS and non-LTS release differ?

---

### Post by snowpine on 2012-12-20
> **Holmes.Sherlock said:**
> Means it is better to re-install 3rd party apps with every new release.


How does LTS and non-LTS release differ?

60 months vs. 18 months support.

Also I wouldn't say "better," just "what I do." :)

---

### Post by Holmes.Sherlock on 2012-12-20
> **snowpine said:**
> 60 months vs. 18 months support.
Does "support" mean that after 60 or 18 months, no "new" software/application for that platform will be uploaded in the repositories?

---

### Post by snowpine on 2012-12-20
> **Holmes.Sherlock said:**
> Does "support" mean that after 60 or 18 months, no "new" software/application for that platform will be uploaded in the repositories?

No "new" software is ever uploaded to the repositories, period.

---

