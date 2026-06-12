---
title: "Stupid Question"
date: 2007-12-13
forum: General Help
---

### Post by techgeek40 on 2007-12-13
I don't know if this can happen or not - but out of my own warped way of thinking:

Is it possible to "boot" Vista or XP while in Ubuntu (like in a termal window?)

---

### Post by ZipoTe on 2007-12-13
Yes, you can:

[http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

### Post by sloggerkhan on 2007-12-13
yeah, look up virtual box or vm ware. There are a lot of virtualization possibilities.

---

### Post by Origin415 on 2007-12-13
Yes.

You would use a program called VMWare with emulates a computer for Windows to run on.

I'm sure there are tutorials for this on these forums if you search for vmware

---

### Post by fjgaude on 2007-12-13
> **techgeek40 said:**
> I don't know if this can happen or not - but out of my own warped way of thinking:

Is it possible to "boot" Vista or XP while in Ubuntu (like in a termal window?)

Well, it's not really like a terminal window, but you install VMware Server on Linux, then you install Windows in VMware... from there you have full use of both Ubuntu and Windows in different windows or full screen through the use of the desktop switcher.

---

### Post by rune0077 on 2007-12-13
Another question: If I already have Vista installed, is it possible to boot the partition through a virtual box, or do I need to completely reinstall it?

---

### Post by techgeek40 on 2007-12-13
Okay - so

I have a computer running Vista - XP - UBUNTU (Triple boot)

I can boot INTO Ubuntu and - "somehow" boot XP or Vista (on the same computer that Ubuntu is running?

---

### Post by fjgaude on 2007-12-13
> **rune0077 said:**
> Another question: If I already have Vista installed, is it possible to boot the partition through a virtual box, or do I need to completely reinstall it?

I pretty sure it can be done... I've never done it, but if you do a web search you will likely find a how to. Or in the VMware help files I think they tell how to do it.

---

### Post by sloggerkhan on 2007-12-13
it's more typical to have a separate install as its own virtual machine.

---

### Post by rune0077 on 2007-12-13
> **sloggerkhan said:**
> it's more typical to have a separate install as its own virtual machine.

Yeah, but Vista is already installed on my computer, and I don't want to have to reinstall it, so it would be neat if I could just "run" it straight from Ubuntu (save me time of rebooting each time I needed to use it).

---

### Post by honeydew on 2007-12-13
> **rune0077 said:**
> Another question: If I already have Vista installed, is it possible to boot the partition through a virtual box, or do I need to completely reinstall it?

You can boot like this however this requires special chipset support I think for intel its the VT chipset (most core 2s have them and so do a few others), I am not sure what the AMD equivalent is.  However, if you are a novice diving into this may seem quite scary.  I would read up on xen technology.  Though now that I think of it.. does vista use a new filesystem? I wouldnt put it past them...   and all this aside this would def involve a fresh install.  (can vista be virtualized?)

---

### Post by techgeek40 on 2007-12-14
Actually, the new file system that Microsoft was going to use never got put out.
The file format is still NTSF - 

But I run an Intel Dual core 2 CPU - 

I've been a geek (tech) for 26-years. Just never at the level of Unix/Linux - 

I "briefly" tried my hand at it ten years ago - but I've mainly been working with Windows OS's (3.1 - workgroup - XP - 2000)

---

### Post by cytg on 2007-12-14
> **rune0077 said:**
> Yeah, but Vista is already installed on my computer, and I don't want to have to reinstall it, so it would be neat if I could just "run" it straight from Ubuntu (save me time of rebooting each time I needed to use it).

you do not wanna do that .. its doable but you dont wanna do it.

reason

your virtual hardware and physical hardware is NOT the same. That means that the same windows installation will have to switch between hardware drivers depending on how you boot into it ...

It IS doable ... but dont do it .. i've been down that road, and its not worth the hazzle.

discalimer ; i did this a few years back, software and hardware virtualization may have changed things ..

---

### Post by rune0077 on 2007-12-14
> **cytg said:**
> you do not wanna do that .. its doable but you dont wanna do it.

reason

your virtual hardware and physical hardware is NOT the same. That means that the same windows installation will have to switch between hardware drivers depending on how you boot into it ...

It IS doable ... but dont do it .. i've been down that road, and its not worth the hazzle.

discalimer ; i did this a few years back, software and hardware virtualization may have changed things ..

Nah, I just tried it. Spend most of last night trying to get it to work, then reached the same conclusion as you: I do not want to do that. Dual-boot seems the best option for me.

---

### Post by techgeek40 on 2007-12-14
Now that is sad, because it would seem to me that "Linux" users would like to be in 'Linux" and have access to "Vista" via a VM

---

### Post by rune0077 on 2007-12-14
> **techgeek40 said:**
> Now that is sad, because it would seem to me that "Linux" users would like to be in 'Linux" and have access to "Vista" via a VM

Not really a big deal for me. I'm a "Linux" user. I'm also a "Windows" user and have no problem with that. I don't prefer one of these over the other, I just use them for different things. I have no problem with choosing at start up what system I need to boot. What annoys me, is when I suddenly need to switch for whatever reason and have to do a reboot, so it would have saved me some time if I could have gotten this to work. Ah well, I'll survive without it.

---

### Post by honeydew on 2007-12-14
one thing my friend had running was sometype of virtual services in linux maybe virtual box.. and then he somehow connected to a application on the windows VM.. this was really cool because it was a VM but he didnt have to use the VM console bullocks he just connected somehow and had his win applications on the linux desktop.. he is a designer so I saw him use a system like this for a few months using flash, adobe CS.. and a few other programs.. I think this would be worth looking into if I needed windows aps in linux...

---

### Post by fjgaude on 2007-12-14
> **honeydew said:**
> one thing my friend had running was sometype of virtual services in linux maybe virtual box.. and then he somehow connected to a application on the windows VM.. this was really cool because it was a VM but he didnt have to use the VM console bullocks he just connected somehow and had his win applications on the linux desktop.. he is a designer so I saw him use a system like this for a few months using flash, adobe CS.. and a few other programs.. I think this would be worth looking into if I needed windows aps in linux...

Was it different than what you see in my screen shot?

---

### Post by cytg on 2007-12-14
arh .. but our time is coming ... indeed it is .. cause one of the next hot topics are 3D acceleration .. yes baby.. fire up that game-engine we call windows in your favorite virtual envoriment and do your thing.
Windows, hopefully, will be tomorrows game emulator.

---

### Post by honeydew on 2007-12-16
> **fjgaude said:**
> Was it different than what you see in my screen shot?

no... there was no vmware console window..  It appeared that his system was emulating it with something like wine.. but instead I am sure he was doing it with one of the virtualization techniques..(some networking remote desktop options?) I found it really interesting.. however never did it for myself, because there is no software out there that I need to run that wont run in linux..

---

### Post by honeydew on 2007-12-16
> **cytg said:**
> Windows, hopefully, will be tomorrows game emulator.

:guitar:

---

### Post by techgeek40 on 2007-12-16
> **fjgaude said:**
> Was it different than what you see in my screen shot?

NOW THAT would be cool - I would love to run that
Is that one of the VM that we are talking about here?

---

### Post by cytg on 2007-12-17
[http://www.google.dk/search?q=virtualbox+seamless+windows&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:da:official&client=firefox-a](http://www.google.dk/search?q=virtualbox+seamless+windows&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:da:official&client=firefox-a)

---

### Post by fjgaude on 2007-12-17
> **techgeek40 said:**
> NOW THAT would be cool - I would love to run that
Is that one of the VM that we are talking about here?

I'm running VMware Server; notice my signature.

---

