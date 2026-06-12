---
title: "Wubi stuck on first boot"
date: 2008-05-14
forum: General Help
---

### Post by Pocker on 2008-05-14
So i downloaded the iso, mounted it and tried Wubi.
That didn't work. Then i downloaded the latest Wubi and put the iso in the same folder, and ran Wubit. That doesn't work.

With either way i do it, i reboot then choose ubuntu, then it starts to load and hangs on the loading screen. The bar always stops in the same spot. I have tried safe graphics, with no luck.

I was reading a few threads and i got an idea to check the log, everything looked fine, at the bottom it said complete, but the first thing i saw that looked off was this.
```
arch=amd64
```
I have an intel processor. I am a rookie but i think this is the source of my problem, is there a way to fix this? Has this happened before?

---

### Post by Pocker on 2008-05-14
i've been toying arround with no luck.
i uploaded the log. hopefully someone can lend some help.

---

### Post by ago on 2008-05-15
Amd64 is fine for all 64 bit processor, amd or intel, such as core Duo

Try to press ESC after selecting "Ubuntu" at boot and try the other options (in particular ACPI workarounds).

---

### Post by Pocker on 2008-05-15
i just tried the acpi work arround and all i get is a black screen and a underscore/prompt thing at the top left that flashes

---

### Post by ago on 2008-05-15
And what happens with the safe graphic mode option?

---

### Post by Pocker on 2008-05-15
none of the other modes have helped. i tried all of them except the last one and get nothing good. the normal boot stops part way through. and the other option ones all have a black screen with a flashing bar on the top left.

---

### Post by ago on 2008-05-15
Can you try booting off the live CD? It might not be wubi related. You may want to search the forum for the make and model of your machine, it might be that special boot parameters are required by your hardware.

---

### Post by Pocker on 2008-05-20
Alright, ive tried everything.
I'm just gonna give up and try andLinux.

---

### Post by abn91c on 2008-05-20
> **Pocker said:**
> So i downloaded the iso, mounted it and tried Wubi.
That didn't work. Then i downloaded the latest Wubi and put the iso in the same folder, and ran Wubit. That doesn't work.

With either way i do it, i reboot then choose ubuntu, then it starts to load and hangs on the loading screen. The bar always stops in the same spot. I have tried safe graphics, with no luck.

I was reading a few threads and i got an idea to check the log, everything looked fine, at the bottom it said complete, but the first thing i saw that looked off was this.
```
arch=amd64
```
I have an intel processor. I am a rookie but i think this is the source of my problem, is there a way to fix this? Has this happened before?

are you running the wubi installer from within windows? not sure what you mean by mounting wubi but you have to run the wubi installer just like any windows program, defrag windows first and make sure your firewall is not blocking the installer

---

### Post by ago on 2008-05-21
Some machines have incompatible hardware and require some kernel workarounds such as: acpi=off or irq=poll

If that is the case, the same issue will present itself when you boot from the Live CD. That is hence the first thing to try. If you cannot boot from Live CD either, it is not a Wubi issue and you have to search this forum for the make and model of your machine to find out what are the appropriate boot parameters.

If that is the case is usually a good idea to also report a bug in launchpad and provide the info the devs will request so that in the next release your hardware can be sorted out and no workaround will be needed for you and all the .

---

