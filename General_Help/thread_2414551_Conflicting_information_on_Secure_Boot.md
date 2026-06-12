---
title: "Conflicting information on Secure Boot"
date: 2019-03-12
forum: General Help
---

### Post by ardouronerous on 2019-03-12
My brother is sending me a HP 850 G2 laptop, based off what I've researched, this laptop comes with Secure Boot and that feature will make it difficult to install Lubuntu on that laptop.

Being that I've never installed Lubuntu on a computer with Secure Boot, I've searched the forums, and there seems to be a divide amongst users, some say I need to disable Secure Boot, while others say I don't need to disable it, so this mixed opinion confuses me.

Please help, thanks.

---

### Post by ajgreeny on 2019-03-12
Does that laptop have Windows installed that you wish to keep?

If Windows does not figure in your situation you can certainly disable secure boot as it is of no consequence to any Linux OS.
This, of course, assumes you can disable secure boot in the UEFI/BIOS and that it does not need Windows itself to disable it, as I believe some do.

My desktop machine allows me to disable it quickly and easily in the UEFI configuration screen and I have never had it enabled in my Linux only systems.

---

### Post by ardouronerous on 2019-03-12
> **ajgreeny said:**
> Does that laptop have Windows installed that you wish to keep?

If Windows does not figure in your situation you can certainly disable secure boot as it is of no consequence to any Linux OS.

No, the laptop has no hard drive, so I'll have to buy one for it when it arrives.

> This, of course, assumes you can disable secure boot in the UEFI/BIOS and that it does not need Windows itself to disable it, as I believe some do.

My desktop machine allows me to disable it quickly and easily in the UEFI configuration screen and I have never had it enabled in my Linux only systems.

Is there anyway of knowing this beforehand? The laptop has been sent by mail already and will arrive in one month, so I can't really ask my brother about this.

---

### Post by ajgreeny on 2019-03-12
> **ardouronerous said:**
> No, the laptop has no hard drive, so I'll have to buy one for it when it arrives.

Get an SSD if it is a possibility for you; more expensive but so much faster read/write speeds, and much more reliable than they used to be when first available.

> **ardouronerous said:**
> Is there anyway of knowing this beforehand? The laptop has been sent by mail already and will arrive in one month, so I can't really ask my brother about this. I'm not sure but I suspect it is always possible to disable it in the UEFI settings; I was, I think, muddling it up with fast start, ie the hibernation used instead of a full shutdown, by default in Win 8, 8.1 and 10.

I haven't used Windows since 2005 so I never know too much about it and its settings.

---

### Post by CatKiller on 2019-03-12
> **ardouronerous said:**
> there seems to be a divide amongst users, some say I need to disable Secure Boot, while others say I don't need to disable it, so this mixed opinion confuses me.

For Secure Boot to work, all your software would need to be signed with Microsoft's signing key.

Canonical and Red Hat got *their* signing keys signed with Microsoft's signing key. So if you're using one of those, you can probably still use Secure Boot. You'll then need to use *those* signing keys to sign things like the Nvidia driver or VirtualBox's kernel modules, or they won't work.

It doesn't really provide much benefit. The malware that it protects against only targets Windows. The DRM to stop you copying media also only targets Windows. If it's enabled, but you haven't jumped through all the hoops, your computer may not boot or may not work properly.

So you might as well disable it, although you don't strictly have to, as long as you're using one of the operating systems that Microsoft approves of.

---

### Post by ardouronerous on 2019-03-12
> **ajgreeny said:**
> Get an SSD if it is a possibility for you; more expensive but so much faster read/write speeds, and much more reliable than they used to be when first available.

 I'm not sure but I suspect it is always possible to disable it in the UEFI settings; I was, I think, muddling it up with fast start, ie the hibernation used instead of a full shutdown, by default in Win 8, 8.1 and 10.

I haven't used Windows since 2005 so I never know too much about it and its settings.
[FONT=Times]> **CatKiller said:**
> For Secure Boot to work, all your software would need to be signed with Microsoft's signing key.[/FONT][COLOR=#222222][FONT=Times]
Canonical and Red Hat got *their* signing keys signed with Microsoft's signing key. So if you're using one of those, you can probably still use Secure Boot. You'll then need to use *those* signing keys to sign things like the Nvidia driver or VirtualBox's kernel modules, or they won't work.

It doesn't really provide much benefit. The malware that it protects against only targets Windows. The DRM to stop you copying media also only targets Windows. If it's enabled, but you haven't jumped through all the hoops, your computer may not boot or may not work properly.

So you might as well disable it, although you don't strictly have to, as long as you're using one of the operating systems that Microsoft approves of.

Thanks for the advice guys. On SSD, that's what I'm planning on getting.
So, Secure Boot doesn't really provide much protection to Linux than the protection that Linux provides out of the box? Okay, thanks for clarifying that.

On disabling Secure Boot in BIOS/UEFI settings, I'll have to wait and see when it arrives by mail next months.

Thanks[/FONT][/COLOR]

---

### Post by oldfred on 2019-03-13
Slightly different model HP.

        HP Elitebook 745 G2  Newbie trying to install Ubuntu as dual boot  with Windows10 us 
[https://ubuntuforums.org/showthread.php?t=2412901](https://ubuntuforums.org/showthread.php?t=2412901)

---

