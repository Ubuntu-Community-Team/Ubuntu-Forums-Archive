---
title: "Cannot download Pro"
date: 2023-07-19
forum: General Help
---

### Post by himmit on 2023-07-19
I'm logged in, and I click "Download Ubuntu Pro, and skips the download and jumps to my profile page. There are no downloads there. There is a "token" but no idea what it's for.

It can be repeated:
[LIST=1]
[*]Goto [Ubuntu.com]("https://ubuntu.com/")
[*]Scroll down to "Get Ubuntu Pro" button and click it.
[*]I end up at having to register to get it. I see I'm logged in but I need to register again, and again....
[*]It dos show me as logged in, my account and max 5 devices for it. No download button/link.
[/LIST]

I disabled all the anti-stalkers... those *'if ya want it, drop your privacy level'* offers.

I got to fill in a lot information, some rather odd for something that is (A) Free and (B) Nowhere to be found and shown my registration information, but no download. 

Of special note is that I'm doing thins on a Windows desktop, via Googles chrome, and when I shrink the screen width, the 'free' runs into $500.00 yr. Is it free and that's why I can't find it, or is it $500.00 Yr that I might see if I pay $500.00 for the free one.

Oh Yes, The "Contact Support is not contacting support, it's a trip to the FAQs, no contacts.

SCREENCAP 1 Wide screen showing "Free":

SCREENCAP 2 Cell users view of free for $500.00

Sorry. I screen capped the pages and now find we can't upload them. Well, imagine them :D

TIA to the brave volunteers that make the forum that without we'd not have any support,

[I]Himmit

[/I]

---

### Post by #&amp;thj^% on 2023-07-19
This may sound very silly but it is important>>>What Version Ubuntu?
ATM I'm running 23.04 and that's not supported fully as seen with:
```
pro status --all
SERVICE          ENTITLED  STATUS    DESCRIPTION
cc-eal           yes       n/a       Common Criteria EAL2 Provisioning Packages
cis              yes       n/a       Security compliance and audit tools
esm-apps         yes       n/a       Expanded Security Maintenance for Applications
esm-infra        yes       n/a       Expanded Security Maintenance for Infrastructure
fips             yes       n/a       NIST-certified core packages
fips-updates     yes       n/a       NIST-certified core packages with priority security updates
livepatch        yes       n/a       Canonical Livepatch service
realtime-kernel  yes       n/a       Ubuntu kernel with PREEMPT_RT patches integrated
ros              yes       n/a       Security Updates for the Robot Operating System
ros-updates      yes       n/a       All Updates for the Robot Operating System

Enable services with: pro enable <service>


```
Or a better look:
```
sudo pro enable realtime-kernel
One moment, checking your subscription first
Real-time kernel is not available for Ubuntu 23.04 (Lunar Lobster).

```

---

### Post by MAFoElffen on 2023-07-19
Let me point you to "how to enroll" your 5 free Ubuntu Pro subscriptions... (LOL): [https://ubuntu.com/pro/tutorial](https://ubuntu.com/pro/tutorial)

What you do is to make sure package 'ubuntu-advantage-tools' is installed, then use your token from that subscription status page to enroll your machine(s), using various ways to do that... The ways depend on whether your machine is Desktop or Server. The CLI method for Server Edition works for both Server and Desktop Editions.

Forum voted in 'Official Ubuntu Members', with that in their Avatar, and listed as such at LaunchPad (you are not a voted in Ubuntu Member), get up to 50 free machines, instead of just 5.

---

### Post by #&amp;thj^% on 2023-07-19
+1 to the above, i was making sure they weren't wasting their time is all....(more common sense)lol I'm going to get a lot of mileage from that one...:lolflag:
```
pro --version
28.1~23.04

```

---

### Post by ajgreeny on 2023-07-19
I have read about this a fair amount but I'm still not totally sure what extras it offers to someone like me who moves from LTS to LTS every two years.
Surely everything on 22.04 is still supported and gets updates/upgrades without Ubuntu-Pro enrollment.
Or do I still misunderstand what this is all about?

---

### Post by #&amp;thj^% on 2023-07-19
For the best define see Post #8

---

### Post by grahammechanical on 2023-07-19
The Ubuntu Pro offer is useful for those who do not want to upgrade to the latest LTS every 2 years. Or, even upgrade after the traditional 5 year support is ended. I think it must be worth the money to businesses compared to the effort to upgrade the OS on every computer which may included a measure of re-training of staff.

I have activated Ubuntu Pro on my install of Ubuntu 20.04. It was pre-installed on the laptop when I purchased it. The install included a keyboard driver that activated keyboard functions such as lights under the keys.

I tested 22.04 in a dual boot and the keyboard driver was not installed. So, I activated Ubuntu Pro on my 20.04 while I investigated how to get the supplier provided keyboard driver in 22.04. And in future on 24.04. It took a bit of thinking but I finally I worked it out. So, I now have a fully functional keyboard in 20.04; 22.04 and 24.04 (development version).

Jumping to the next LTS is usually a risk free exercise but it is nice to have a fully function machine and OS as a stand-by just in case.

Regards

---

### Post by ian-weisser on 2023-07-19
> **ajgreeny said:**
> I have read about this a fair amount but I'm still not totally sure what extras it offers to someone like me who moves from LTS to LTS every two years.

During years 0-5, Pro adds security updates for some Universe packages. Pro does NOT add security updates for Main packages. Everybody gets those already.
  
Universe packages are supposed to be provided by the community, but few volunteers do it, so generally they were not happening for many less-popular packages. The community can still patch them; MOTUs will still upload them. The community avenue is still open.

  Pro does NOT accelerate security patches in Main, nor offer "premium" expedited access in Main. Everybody already gets Main security updates the same way they always did, as rapidly as the Ubuntu Security Team can do the work. 

During years 6-10, Pro adds security updates for all Main and some Universe packages. No bugfixes. Just security.

Pro is aimed squarely at the enterprise market: Organizations that stick to LTS to avoid disrupting their workflow -- the original purpose of LTS. The (oversimplified) concept is that their needs will drive the list of "some" universe packages, and that their fees will pay for the work. In turn, the free-tier community users will benefit from universe security updates and safer systems in the hopes that the community will grow and continue to contribute.

---

### Post by MAFoElffen on 2023-07-19
For those who are "Ubuntu Members", I had a thread in the Members Area about when I tested the Ubuntu Pro subscription process for us and those extended subscription numbers...I recommended changes to our wiki to better explain the process for us. I don't see that anyone has done that.

I have to say, I thought it would be 'more' value than it actually is, at least in what I saw, and what I use. It really is geared more for businesses or Academics who do not upgrade from LTS to LTS.

Status on the "Security Compliance and Audit Tools"... Last i heard, it is still hung up with the external process review of what Ubuntu 22.04 needs to be certified. That was supposed to be completed last quarter. If someone hears if that is done yet, please notify me. This is important to Govt. Contractors and such.

---

### Post by ajgreeny on 2023-07-20
Thanks to all those who have clarified the situation for me and others who move every two years.
It seems that things are more or less as I suspected but could not quite be sure of,

I do accept that for a business that uses Ubuntu, avoidance of the disturbance caused by upgrading your OS's version is needed in order to keep the business running smoothly and without interruption but for a personal user like me who retired many years ago it is much less important.

Ubuntu and Linux is really just my hobby now and no longer needed for running any business software, not even tax management applications, so it looks as if Ubuntu-Pro is not really essential to me.

---

### Post by donald187 on 2023-07-22
> **ian-weisser said:**
> 
  Universe packages are supposed to be provided by the community, but few volunteers do it, so generally they simply were not happening. The community can still patch them; MOTUs will still upload them. The community avenue is still open.


Is this true as well from Thomas Ward on AskUbuntu.com?  I've been kind of hanging my hat on it.

> 
While  you are not guaranteed any updates for these packages [in Universe], a lot of the  popular ones will have enough attention to usually have someone working  to try and patch security issues


[https://askubuntu.com/questions/618727/is-running-packages-from-ubuntu-universe-more-risky-than-running-the-same-packag](https://askubuntu.com/questions/618727/is-running-packages-from-ubuntu-universe-more-risky-than-running-the-same-packag)

---

