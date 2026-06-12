---
title: "How do we update the repositories to latest supported Chromium?"
date: 2024-02-22
forum: General Help
---

### Post by johsal on 2024-02-22
I need Ubuntu 16 for customization purposes where Chromium updates to 90. 

Chromium 106 works in 16 with normal dependencies. 

How do we update the repositories for the most current browsers?

---

### Post by TheFu on 2024-02-23
In Ubuntu, Chromium is provided as a snap package. The snap subsystem on your computer checks for updates 4x a day.  In short, Chromium isn't in any Canonical repo.

I stopped using Ubuntu Desktops when they changed the browsers to snaps. I run Linux Mint on my desktop. Still use Ubuntu Server on the other systems here, well, mostly.  Both Chromium and Firefox are shipped by default in Ubuntu as snap packages.

If you want to go outside Canonical supported snaps and use repos from other people, then that is up to you to decide who is and isn't trustworthy.

For firefox, I block the snap package and setup a Mozilla PPA (repo). Additionally, I switched from their 'edge' releases to their corporate ESR releases using /etc/apt/sources.list.d/mozillateam-ubuntu-ppa-focal.list to extend the normal repos.  If you google "firefox PPA", you can find reputable articles for how to install the PPA, then how to install the different program packages.  This effectively extends the default repos to use those trusted PPAs like they were from Canonical.  I figure that the software is already from Mozilla, so using a PPA they curate isn't adding any risks to my systems.  I've decided to trust them already.

The firefox version on my systems are:
```
firefox-esr    115.8.0esr+build1-0ubuntu0.20.04.1~mt1
firefox             122.0.1+linuxmint1+virginia
```

I dropped using chromium over the snap problem.  Switched to Brave.
```
brave-browser  1.62.165
```

We each have to make our own choices about how much hassle we are willing to have to get a system we'd like.  Chromium was a core tool that I used, but with snaps, the way I used it was totally broken, making it useless.  I had months to decide and plan. Switching to Mint was the least effort solution for my desktop needs.

---

### Post by johsal on 2024-02-23
> **TheFu said:**
> In Ubuntu, Chromium is provided as a snap package. The snap subsystem on your computer checks for updates 4x a day.  In short, Chromium isn't in any Canonical repo.

I stopped using Ubuntu Desktops when they changed the browsers to snaps. 




I am confused about Ubuntu-based Linux families & the conversion to Snap they do not follow. Wouldn't that put everyone on Snap?

I used recently my first app package, Chromium 120 in Ubuntu 16. I consider it a step forward.

Otherwise I am leaning towards standalone browsers, also a bit ironic as like the app package systems they demand dependencies.

The software managers we use are significant & demand comprehension. I was pulled to Ubuntu by it being the basis of other distro families via its repositories, but I am not married to it, just inclined to user-friendliness & standarization with aesthetic & modest system resource constraints. 

All these packages I'm installing are in .deb format so I would easily head over to Debian if not for user-friendliness.

Firefox is important & I use it, but I also find it much easier to install, ahead of the Chromium-based commerical packages which are ahead of Chromium itself. 

I have Chromium-based 106 as a .deb for the most common browsers save Chromium itself.

My preferred source of browsers is the makers' sites themselves.

Thus far I prefer Ubuntu to Mint.

Firefox 115.8 ESR is a compelling standard for the time. 

As an old PC user I need to test what will work in 32-bit Ubuntu 14 (Tahr) & 32-bit Windows 7. Once no current browsers the OS thus machines are relegated.

I like your Mozilla PPA method, but know it's not required for Firefox most of the time. In Linux it simply runs & when it doesn't it's close time to move on, in my case well after most other users.

---

### Post by TheFu on 2024-02-24
> **johsal said:**
>  
As an old PC user I need to test what will work in 32-bit Ubuntu 14 (Tahr) & 32-bit Windows 7. Once no current browsers the OS thus machines are relegated.

Running unsupported OSes puts everyone at risk from your machines.  You are like the drunk driver on a road.
Please keep those systems off the internet completely.

I doubt newer snaps will have 32-bit binaries, so if you truly are stuck on 32-bit hardware (pre-Core2 Duo), then you are passed time to get a new system. 18.04 was the last ESM supported 32-bit Ubuntu and regular support for it ended in 2023.

Please don't compute while drunk.

---

### Post by donald187 on 2024-02-24
> **johsal said:**
> 
As an old PC user I need to test what will work in 32-bit Ubuntu 14 (Tahr) & 32-bit Windows 7. Once no current browsers the OS thus machines are relegated.


I believe Debian still supports 32-bit hardware.  It's easier to install than it used to be since they included the non-free firmware in the installer.  But it seems you have to use the traditional network installer instead of the live images for 32-bit architecture.

---

### Post by johsal on 2024-02-25
> **TheFu said:**
> 
I doubt newer snaps will have 32-bit binaries.
[cut]
Please don't compute while drunk.

The only thing I'm doing on a 32-bit computer in Lubuntu is USB tethering. It works where my regular distro does not. Snaps or any new package systems are not a consideration. 

Translating the security threat from developers to the masses reads like an ongoing need & void. Relatively I see the threat is at most to me, personally. That is why I prefer read-only boots. The hacks I experience are institutional & Gmail accounts. Deletion of my Drive data is most frustrating.

---

### Post by johsal on 2024-02-25
> **donald187 said:**
> I believe Debian still supports 32-bit hardware. 

Indeed. I have this weird relationship with Bionic (18) with newer app version support while preferring Xenial. 20 will drive us to new machines or Debian. 

Right now my faith is in GRUB2 for booting, with challenges of course.

---

