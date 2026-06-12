---
title: "Ubuntu Studio LTS releases (18.04 says it's not)"
date: 2018-04-27
forum: General Help
---

### Post by kazakore on 2018-04-27
Aren't always even year number, 04 (April) release meant to be LTS versions of Ubuntu? Why does the Ubuntu Studio website claim that the just released 18.04 is a "regular release, which we will be supporting for 9 months" rather than an LTS release with 3 years support?? What is going on here?!?!

[https://ubuntustudio.org/download/](https://ubuntustudio.org/download/)

What does this really mean??

"Unlike the other Ubuntu flavors, this release of Ubuntu Studio is not a Long-Term Suppport (LTS) release. As a regular release, it will be supported for 9 months. Although it is not a Long-Term Support release, it is still based on Ubuntu 18.04 LTS which means the components will be supported as usual for a LTS release."

The core, desktop stuff will get the LTS support but the media software etc wont?!?! How can you have some official flavours LTS and some not on the same version when they use exactly the same repos?!?! Saying somebody could install everything from Studio into standard Ubuntu (or any other flavour) and would expect the usual LTS support when doing so!! It really makes no sense to say only a single flavour is not LTS!!

[https://ubuntustudio.org/2018/04/ubuntu-studio-18-04-released/](https://ubuntustudio.org/2018/04/ubuntu-studio-18-04-released/)


Take into account that Ubuntu Studio says it's LTS are supported for 3 years, not the 5 years of the other flavours, as it is and that means there will be one whole year with no LTS version of the Studio flavour which is officially supported at all!! This makes not logical sense!

---

### Post by PaulW2U on 2018-04-27
> **kazakore said:**
> Aren't always even year number, 04 (April) release meant to be LTS versions of Ubuntu? Why does the Ubuntu Studio website claim that the just released 18.04 is a "regular release, which we will be supporting for 9 months" rather than an LTS release with 3 years support?? What is going on here?!?!
I don't have the answer to all of your questions but with such a small development team presumably a three year support period is something that the team feel that they cannot offer. Ubuntu Studio is being rebooted - [Ubuntu Studio Plans a Reboot for 18.10 release]("https://www.omgubuntu.co.uk/2018/04/ubuntu-studio-plans-to-reboot") - so there will be an 18.10 release and presumably then every nine months with 20.04 being the next LTS.
> **kazakore said:**
> 
The core, desktop stuff will get the LTS support but the media software etc wont?!?! How can you have some official flavours LTS and some not on the same version when they use exactly the same repos?!?!
Yes, different components the release have different support periods. It's been that way ever since Ubuntu offered five years of support whilst most of the flavours remained at three years. In reality the lowest support period is the one that really counts as you will only get updates for the components that are still supported.

I don't think many people realise that the Ubuntu flavours are put together by just a handful of unpaid devoted members of the community and not Canonical employees as with Ubuntu.

---

### Post by kazakore on 2018-04-27
But surely Ubuntu support should be for everything in their repos, this doesn't matter what you have installed as your base, so it seems rather strange to me that the different flavours have different support lengths when they are sharing repos and taking the same updated packages at the same time! So somebody manually installing a program which isn't installed by default on any flavour has zero support ever?!!?!? That's not how i thought it was meant to work!!

---

### Post by mörgæs on 2018-04-27
> **kazakore said:**
> 

Take into account that Ubuntu Studio says it's LTS are supported for 3 years, not the 5 years of the other flavours

Only Ubuntu itself has 5 years of support. Alle the flavours have 3.

Try the command 
```
ubuntu-support-status --show-all
```

---

### Post by kazakore on 2018-04-27
> **mörgæs said:**
> 
Try the command 
```
ubuntu-support-status --show-all
```

Thanks, not seen that before. I know a few of mine are from other repos or manual installs but still a little surprised with the figures here and some of/number of packages already not supported any longer.

> You have 2015 packages (56.8%) supported until April 2021 (Canonical - 5y)
You have 69 packages (1.9%) supported until April 2021 (Community - 5y)
You have 704 packages (19.9%) supported until April 2019 (Community - 3y)

You have 48 packages (1.4%) that can not/no longer be downloaded
You have 710 packages (20.0%) that are unsupported


But it still doesn't answer the question of how and why having no LTS version at all for Studio between 19.04 and 20.04 makes sense to anybody........

---

### Post by PaulW2U on 2018-04-27
> **kazakore said:**
> But surely Ubuntu support should be for everything in their repos, this doesn't matter what you have installed as your base
But that's not how it works in practice and it does matter what you install as your base. Support is split between Canonical and the community. Canonical have the resources and wish to offer five years of support but the community supported flavours don't.

[What’s the Difference Between Main, Restricted, Universe, and Multiverse on Ubuntu?]("https://www.howtogeek.com/194247/whats-the-difference-between-main-restricted-universe-and-multiverse-on-ubuntu/") is an interesting article on package support. I think the sentence:
> Main and Restricted are fully supported by Canonical, while Universe and Multiverse don’t receive the support you might expect.
sums up your wish for more support than you're ever going to get. ;)

---

### Post by Impavidus on 2018-04-27
> **PaulW2U said:**
> 
Yes, different components the release have different support periods. It's been that way ever since Ubuntu offered five years of support whilst most of the flavours remained at three years. In reality the lowest support period is the one that really counts as you will only get updates for the components that are still supported.


It's been like that since 6.06, the very first LTS release, as the server edition had 5 years of support and the desktop edition just 3.

The repositories have multiple sections. "main" has full support from Canonical, expect less support in "universe".

---

### Post by yancek on 2018-04-27
The only Ubuntu releases I am aware of ever having 5 year support are Ubuntu, Mint  and Kubuntu.  The others such as Lubuntu, Xubuntu, etc. have been 3 years.  Different developers as explained above.

---

### Post by kazakore on 2018-04-27
Thanks for all the clarifications guys! :)

I'm at a loss whether to install 16.04 or 18.04 on my new SSD now.... Usually I would wait until a LTS.01 release for minor bugs to be ironed out but as I have just bought a new, nice and large SSD to replace my current one I am going to be doing a fresh install very soon. As both have support that expires on near enough the same date now I wonder if there is any point even considering 18.04 at all......

Can anybody give clarification on at last the kernel support expiry for Studio 18.04? If we can expect to see the low latency kernel supported up until the next LTS release in 20.04 then I feel it will be worth going with. If not... Well...... :-/

---

### Post by mörgæs on 2018-04-27
Take a look at the [release notes]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Known_issues"). If nothing there bothers you then go for 18.04.

---

### Post by kazakore on 2018-04-28
> **mörgæs said:**
> Take a look at the [release notes]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Known_issues"). If nothing there bothers you then go for 18.04.

For Studio you'd be better checking [https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes/UbuntuStudio](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes/UbuntuStudio) and [https://wiki.xubuntu.org/releases/18.04/release-notes](https://wiki.xubuntu.org/releases/18.04/release-notes) most likely also checking against the main release notes....

But having given more thought I guess there is one key concern which I'd like answered if possible:
What support cycle is the low-latency kernel used by Studio covered by?

If the low-latency kernel has the three year support then I'd be happy. I'm used to Ubuntu not keeping much software uptodate so if there's any I use regularly and want the new features I add a dedicated ppa or install manually. Office software and browsers etc (which is general are most likely to need a security update) will be covered by the LTS cycle of other versions. This just leaves the kernel to worry about keeping patched after the 9 months are up....

---

