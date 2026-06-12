---
title: "why are there 2 LTS versions on the go at once"
date: 2015-05-23
forum: General Help
---

### Post by bobmac on 2015-05-23
Folks,

I've really got 2 problems...

I'm completely confused. I believe that version 12.04 will be good until 2017. Up till now I'v only seen 1 LTS version on the go at any one time. I've always upgraded to the latest LTS version, but not this time. 

I've tried to download and install version 14.x.x but my I get a message telling me something about my graphics no being compatible with 14.x.x.

My questions are:

Why are there 2 LTS versions on the go at the same time?

why can't I install the new LTS version?

While I've been USING ubuntu for some time, I'm only a user as opposed to a guru. For example, I don't have a clue where most of the programs etc are stored. I tend to stick to my home directory. So, if you do answer these questions I'd be grateful if you could tell my problems in simple terms.

Regards,

Bob

---

### Post by QIII on 2015-05-23
The desktop LTS releases used to be supported for three years and the server LTS releases for five.  Canonical aligned them, most likely to cut down on maintenance effort, so that both are now supported for 5 years.  So for some part of 2016, there will actually be three supported LTS releases.  For you, that overlap means that you don't have to suddenly switch.     

> I've tried to download and install version 14.x.x but my I get a message  telling me something about my graphics no being compatible with 14.x.x.

why can't I install the new LTS version?

To even begin to answer this, we would need to know which release you are currently using, which exact point release you are trying to install (14.04, 14.04.1, 14.04.2), your graphics adapter OEM and model and the exact message you are getting.

---

### Post by bobmac on 2015-05-23
QIII,

Many thanks for your reply.
I'm currently using version 12.04.5 with all the latest updates installed.

sudo lshw -C video shows:

description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:ee00(size=256) memory:fdee0000-fdeeffff memory:fdd00000-fddfffff

When I attempt to upgrade to version 14.x.x, the installation appears to start OK. However, when the Distribution Upgrade dialog displays shows Upgrading to Ubuntu version 14.04, I seems to go through the Preparing to upgrade, but then stops and displays **Fetching is Complete**, then displays the message below. 


Your graphics hardware may not be fully supported in Ubuntu 14.04.

Running the 'unity' desktop environment is not fully supported by your graphics hardware. You will maybe end up in a very slow environment after the upgrade. Our advice is to keep the LTS version for now. For more information see [https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D) Do you still want to continue with the upgrade?

As I don't want to cause problems with my current version. I stop and this point and abort the installation.

Hope this helps.

Regards,

Bob

---

### Post by sudodus on 2015-05-23
I suggest that you stay with 12.04.5 and keep it up to date. It will be supported until April 2017, so almost two more years to go.

And when you want to prepare for the upgrade, you can try new versions of Ubuntu live without installing, and that way find out if there are working drivers for your graphics.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by bobmac on 2015-05-26
Sudous,

Many thanks for your reply. However, do you have any idea why i get the 'Your graphics hardware may not be fully supported in Ubuntu 14.04' message?

Regards,

Bob

---

### Post by jimmy-frydkaer on 2015-05-26
> **bobmac said:**
> Sudous,

Many thanks for your reply. However, do you have any idea why i get the 'Your graphics hardware may not be fully supported in Ubuntu 14.04' message?

Regards,

Bob

Your graphics adaptor might no longer be supported by the Linux kernel. 

Every once i a while the kernel developers remove kernel driver module for very old, or even just older, hardware. This is done to keep the kernel at a reasonable size and the kernel source easy to handle. If the Linux kernel should support very old hardware, or hardware no longer available from manufacturers, the kernel would be impossible to handle.

---

### Post by sudodus on 2015-05-26
> **jimmy-frydkaer said:**
> Your graphics adaptor might no longer be supported by the Linux kernel. 

Every once i a while the kernel developers remove kernel driver module for very old, or even just older, hardware. This is done to keep the kernel at a reasonable size and the kernel source easy to handle. If the Linux kernel should support very old hardware, or hardware no longer available from manufacturers, the kernel would be impossible to handle.

+1

I think jimmy-frydkaer describes the situation with hardware drivers. Maybe also the automatic system to select driver might confuse some old hardware with some new hardware (I don't know the details of the hardware drivers and how they are selected). Sometimes, far from always, a developer can put in a check and write such a warning message 'Your graphics hardware may not be fully supported in Ubuntu 14.04' 

This is one reason why it is a good idea to stay with an old version which works. And stay with the long time support (LTS) versions, because they last so much longer than the other versions. Instead of upgrading to the next version or the next LTS version, ***try*** how the new release works and backup your old system before upgrading or making a fresh installation. Try it live without installing.

---

### Post by grahammechanical on 2015-05-26
The newest versions of Ubuntu come with the latest stable versions of proprietary video drivers. Which, as has already been pointed out, do not always support older video adapters.

Or, it may be that video adapter does not support Unity 3D. It does not do hardware accelerated 3D rendering. Now, with 12.04 this problem was overcome by the system using Unity 2D but that is no longer available in newer versions of Ubuntu. Instead we get a video driver called llvmpipe that gives an approximation of 3D rendering on video adapters that cannot do 3D rendering.

The trouble with llvmpipe is that even on powerful video adapters the performance is slow. My advice would be to test if the video adapter can run Unity 3D by running this command

```
/usr/lib/nux/unity_support_test -p
```

If the answer is No, then you will get llvmpipe. Even if the answer is Yes, I think that it would be best to use Additional Drivers to switch to the open source driver before upgrading and then afterwards go to System Settings>Software & Updates>Additional Drivers tab an see if you are offered a legacy driver. The latest drivers will not support that adapter. We can also get legacy video drivers from the Software Centre.

You could also download 14.04.2 and run a live session. They use open source video drivers. In this way you will test out the user experience on your machine.

Regards.

---

### Post by bobmac on 2015-05-26
Folks,

Does this mean that when the next LTS version in 2017 comes out that I'll still have the same problem with the graphics stuff. If so, perhaps i need to upgrade my system to be able to handle all the new stuff.

Regards,

Bob

---

### Post by monkeybrain20122 on 2015-05-26
I think that card is supported by kernel, probably just not Unity 3d as others have pointed out. I installed xubuntu 14.04 on a computer with that graphic card if I remember correctly.
Anyway, you should run a live usb and if decide to update, backup your data and do a fresh install. A bad upgrade is going to cause you a lot of problems and even if it works, it will take a long time.

---

### Post by bobmac on 2015-05-28
Folks,

The result of the command - /usr/lib/nux/unity_support_test -p
is:

Xlib:  extension "GLX" missing on display ":0".
Error: GLX is not available on the system

But what does this mean?

Regards,

Bob

---

