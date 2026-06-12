---
title: "Absolutely Perplexed?!?"
date: 2006-12-16
forum: General Help
---

### Post by rhodry on 2006-12-16
Hi Folks,

I am absolutely perplexed by something that happened yesterday and I am wondering if anyone can explain.

I have a fairly new laptop, Asus A6Jc. Even though I am an absolute Ubuntu fan (and my main production machine has been Ubuntu from Hoary through to Edgy); I run Windows XP on the laptop purely for home video/dvd production. It has a usb 'digitalnow' hdtv connector and uses ProjectX, VideoRedo Plus and TMPGEnc DVD Author for video and dvd work. Superb combination and I am sorry but there is nothing (IMHO) that comes close in Ubuntu land at this stage.

Anyway, I had a temporarily spare petition on the drive and thought I would just see what Ubuntu looked like on the machine. I went to put Edgy on and I came across apparently a common problem of no detection of the Realtek RTL8168/8111 network connection. This is a bit of a show stopper with Ubuntu of course given its method of internet repository use.

I did some forum searching in here and general googling and came across a couple of suggested fixes, downloaded the drivers from Realtek and followed the guides. Nothing would work properly, so I even tried a copy of Fedora6 and Opensuse10.2 I had laying around. Nothing would work. I then decided to try Feisty - as I thought the drivers might be compiled into the newer kernel. I hosed the install, my fault, did not check for corrupt disc before I started, and hosed the mbr in the process.

I pulled out the trusty old Kubuntu Dapper Live CD to get the boot loader/mbr working again and just out of curiosity decided to proceed to install, fully expecting no network detection?

To my absolute amazement, the network was detected without a hiccup?! I am writing this from the Dapper dual-booting laptop with local network, Internet, all working like a charm! I am running kernel 2.6.15-27-386?

How in the world can a couple of variations of Edgy plus other os'es, all with newer kernels not detect this thing and have so many people talking about it on the net, and then have little old Dapper with a 2.6.15 kernel work like a charm out of the box??

I do not understand how this is so. Why would the drivers come out as kernels progressed? I mean Edgy is 2.6.17 or 18 isn't it. Feisty is 2.6.19?

I am as happy as anything, don't get me wrong. I at least know that I can have my trusty Ubuntu running on the laptop so I can stay "true" for mail, etc whist on the move. I will have to dual boot only to specifically do my video/dvd work.

Does anyone know why this strange situation would have arisen?

---

### Post by scrooge_74 on 2006-12-16
Weird things like that happen to me in the past using Debian testing or unstable, things would  work pretty well with stable, but had problems with same machine using other versions

---

### Post by az on 2006-12-16
> **rhodry said:**
> 
Does anyone know why this strange situation would have arisen?

A bug.

Of course, this is not meant to happen.  Edgy was a release which had the goal of breaking new ground.  It sets the groundwork for the next few releases.  To the developers, that is important.

To most end-users, that means that there are more bugs to fix - or just stick with the LST release - Dapper.

---

