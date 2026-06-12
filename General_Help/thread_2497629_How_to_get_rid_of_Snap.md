---
title: "How to get rid of Snap ?"
date: 2024-05-13
forum: General Help
---

### Post by dpadhy on 2024-05-13
I have been an ubuntu fan since a decade and its been a smooth sail more or less. 

But I upgraded to ubuntu 22.04 last fall and since then I am having some harrowing experiences where my system is rebooting / or re logging in every now and then. 

After some poking around it seems to have something to do with the snap deamon. I was never very happy with snap in the first place. 

Why is this thing a must have on ubuntu LTS ? Cant we get rid of entirely ?

Please help

---

### Post by coffeecat on 2024-05-13
From the strapline for *The Cafe*:

> **Forum: The Cafe**

The Community Chat area is for lighthearted and enjoyable discussions, such as you might find around a water cooler at work.

Most topics which are not technical support requests may be discussed here. 

*Thread moved to **General Help**.*

---

### Post by gezzer2 on 2024-05-13
here is a howto if you wish to remove snaps ..

[https://www.debugpoint.com/remove-snap-ubuntu/](https://www.debugpoint.com/remove-snap-ubuntu/)

or

[https://www.baeldung.com/linux/snap-remove-disable](https://www.baeldung.com/linux/snap-remove-disable)

there are others that are similar ..

---

### Post by den_ on 2024-05-26
> **dpadhy said:**
> I have been an ubuntu fan since a decade and its been a smooth sail more or less. 

But I upgraded to ubuntu 22.04 last fall and since then I am having some harrowing experiences where my system is rebooting / or re logging in every now and then. 

After some poking around it seems to have something to do with the snap deamon. I was never very happy with snap in the first place. 

Why is this thing a must have on ubuntu LTS ? Cant we get rid of entirely ?

Please help

Snap is still relatively new from the point of view of Ubuntu 22.04. It has improved a lot in the later versions of Ubuntu. It is Linux, so if the daemon really bothers you, there is a way to remove it, but you could also simply choose another distro.

Canonical is a commercial company, and Snap as an idea is generally not bad, even if it was bad for your use case. Canonical makes money from enterprise customers, and most Ubuntu machines are headless, run in VMs, and serve containers, APIs, etc.

Snap can theoretically increase security through process isolation and help with the shipping and maintenance of packages by including the complete required environment. This has pros and cons similar to statically linking libraries when compiling/creating a deb package. 

It also has stricter review process compared to Flathub, what is a pro when your software solution relies on Ubuntu. Seven years down the line, you're still getting security upgrades from Canonical, you can still upgrade your API by simply shipping new Snap (w/o having to bother with the dependencies etc), you have a company taking care of the Snap store (Reviews, maintenance etc.). 

I am not saying Flatpak, Flathub, or debs are bad (I myself mainly use deb). Use whatever you like, but the reasons in favor of Snap should be obvious. It feels strange how people who have been using Ubuntu for a decade can't wrap their minds around this. Maybe it's some weird mass psychology Reddit phenomenon.

---

### Post by currentshaft on 2024-05-26
> **dpadhy said:**
> 
After some poking around it seems to have something to do with the snap deamon. I was never very happy with snap in the first place. 


Not that I'm doubting you, but what facts lead to this conclusion? Did you file a bug report if snap is not performing as expected?

---

### Post by iamjiwjr on 2024-05-26
Remember part two after deleting snap - 

I use the Synaptic package mgr to follow up after I deleted the "snaposphere." Using Synaptic, I searched for gnome-software, a package that manages flatpaks easily. After installing gnome-software I searched flaptpak. When I click the box to install it, I see that snap tries to dig in again by installing a package called gnome-software-plugin-snap. I deselect it. I then can install flatpak safely without snap jumping in and taking over again. I then add the flatpak repo from flathub, reboot, and I'm good to go.

---

