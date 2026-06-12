---
title: "Ubuntu Mini ISO - is it possible to create a bootable ISO?"
date: 2014-02-08
forum: General Help
---

### Post by amjjawad on 2014-02-08
Hi,

First of all, if this is not the right sub-forum for such question, feel free to move this there where it belongs.

Second of all, I am not a developer so easy on me :)

Some think it is possible. Some other think it is **not** possible. I am lost in between.

Is it possible to make a bootable ISO out of a [modified mini ISO]("https://blueprints.launchpad.net/torios/+spec/ubuntu12.04-mini-iso") ? or it is not possible?

Many thanks :)

---

### Post by ian-weisser on 2014-02-08
> **amjjawad said:**
> Is it possible to make a bootable ISO out of a [modified mini ISO]("https://blueprints.launchpad.net/torios/+spec/ubuntu12.04-mini-iso") ?

I suppose so. The [ordinary, unmodified mini .iso]("https://help.ubuntu.com/community/Installation/MinimalCD") is already bootable.
However, it's not very useful for general-purpose activity because it lacks most of the tools you need. It's shell environment lacks a lot of basic functionality you expect.

---

### Post by amjjawad on 2014-02-20
> **ian-weisser said:**
> I suppose so. The [ordinary, unmodified mini .iso]("https://help.ubuntu.com/community/Installation/MinimalCD") is already bootable.
However, it's not very useful for general-purpose activity because it lacks most of the tools you need. It's shell environment lacks a lot of basic functionality you expect.

Hi and thanks for posting :)

It is indeed bootable. What I was trying to say/ask is:
Can I create a LiveCD/LiveUSB version of a system that is based on Ubuntu Mini ISO with some modification? 


Example:
Ubuntu Mini ISO + DE/WM + File Manager + Browser + Terminal + Synaptic = Create New Bootable ISO that can be downloaded and installed. 

I had a chat with the creator of [Bento]("http://linuxvillage.org/en/2013/11/bento-ubuntu-remix-rc/") Project and she said it is 'not' possible. She edited the white board of this blueprint but perhaps that wasn't clear that she said it is 'not' possible. However, she sent me a very long email that I couldn't understand it (was so long and wasn't clear to me) which explains it is not possible to do that.

I actually disagree with her but can't prove it, that is why I am asking.

I [have played with the Mini ISO]("http://amjjawad.blogspot.com/2013/06/mini-lubuntu-part-2.html") before, more than once. However, never ever created a bootable ISO out of any setup.

---

### Post by buzzingrobot on 2014-02-20
Research how to create a bootable iso that contains those packages.  It probably is practically impossible, or not worth the effort, to add packages to an existing iso image. 

Once you have the image, you can burn it to something.  If you want to use it to install on other machines, you'll need an install script.

---

