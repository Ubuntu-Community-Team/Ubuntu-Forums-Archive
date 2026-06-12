---
title: "GRUB 1.99-21ubuntu3.7 removed countdown timer?"
date: 2013-01-23
forum: General Help
---

### Post by Nutria on 2013-01-23
Three issues seem to have happened at the same time.

One is that the GRUB countdown timer doesn't exist anymore.  I had set to 30 seconds.

Second is that there's now a GUI GRUB screen instead of text.

Thirdly, USB ports seem to have stopped working.  I've tried two KBs in multiple ports and I can't even get to the BIOS setup.  Booting from a CD is similarly useless


The disappeared GRUB countdown means that it won't boot at all so I can't even ssh in.

Any thoughts?

---

### Post by oldfred on 2013-01-24
There really is not a gui grub screen. So what is it showing?

You can add backgrounds to grub, but it still is the same text.

USB not booting issue should be totally different and you should always be able to get into BIOS, or do you have a new UEFI?

---

### Post by Nutria on 2013-01-24
> **oldfred said:**
> There really is not a gui grub screen. So what is it showing?

Call it "hi-res-graphic mode".  It's definitely different than the low-res text-mode GRUB that I'd seen before.

And the GRUB timer disappeared.  That's why it won't autoboot despite the USB issues.

> USB not booting issue should be totally different

> and you should always be able to get into BIOS

Correct.  Not an Ubuntu issue.

I'm concerned that there's a h/w issue.  I've tried two different keyboards, in all the USB ports, and when I press <Del> (that's the Gigabyte standard) at the BIOS splash screen nothing happens.

But I've never heard of just USB functionality failing.  There's been no lightning and it sits behind a UPS.

One morning it just stopped working.
 
> or do you have a new UEFI?

No, it's a good old-fashoned BIOS mobo on which I've been running Ubuntu for about 18 months.
.

---

### Post by oldfred on 2013-01-24
Did you install new graphic drivers or update them. Grub does try to use graphic mode and that will often change from 640x480 to whatever your default is. Then it looks a lot smaller.

Did you do a major grub update that rewrote /etc/default/grub or change a BIOS video setting?

 info -f grub -n 'Simple configuration'
> `GRUB_GFXMODE'
     Set the resolution used on the `gfxterm' graphical terminal.  Note
     that you can only use modes which your graphics card supports via
     VESA BIOS Extensions (VBE), so for example native LCD panel
     resolutions may not be available.  The default is `auto', which
     tries to select a preferred resolution.  *Note gfxmode::.


---

### Post by Nutria on 2013-01-24
> **oldfred said:**
> Did you install new graphic drivers or update them. Grub does try to use graphic mode and that will often change from 640x480 to whatever your default is. Then it looks a lot smaller.

Did you do a major grub update that rewrote /etc/default/grub or change a BIOS video setting?

I run 12.04 LTS on that machine and try to keep it up-to-date.

Isn't the whole purpose of /etc/default to preserve local modifications?

---

### Post by oldfred on 2013-01-24
Yes, but a total reinstall of grub may overwrite it. Otherwise it really should not have changed.

---

### Post by Nutria on 2013-01-24
> **oldfred said:**
> Yes, but a total reinstall of grub may overwrite it.

Didn't do that.  "apt-get dist-upgrade" is my friend. :)

> Otherwise it really should not have changed.

That's why I posted to the forum... :wink:

---

### Post by oldfred on 2013-01-24
Post your /etc/default/grub and I will compare to mine as it is the default I think.

---

### Post by Nutria on 2013-01-24
> **oldfred said:**
> Post your /etc/default/grub and I will compare to mine as it is the default I think.

I guess I haven't made myself clear: THE MACHINE WON'T BOOT.

Because the GRUB timer disappeared, "it" sits at the GRUB menu indefinitely.

Because I'm having apparent h/w related USB issues, I can't use the keyboard to manually choose a kernel to boot with.

---

### Post by oldfred on 2013-01-24
Does keyboard work to get you into BIOS before grub starts loading?

I thought USB was  related to reading flash drive or booting flash drive, not keyboard.
I used to have keyboard issues, years ago and that was a BIOS setting, but you should of had that from the beginning. Or did you flash BIOS? As that resets to defaults.

---

### Post by VyReN on 2013-01-24
> **Nutria said:**
> I guess I haven't made myself clear: THE MACHINE WON'T BOOT.

Because the GRUB timer disappeared, "it" sits at the GRUB menu indefinitely.

Because I'm having apparent h/w related USB issues, I can't use the keyboard to manually choose a kernel to boot with.

Sounds like a hardware issue with USB, but I'm seeing the same behavior with GRUB [Edit: The timer part, I have no change in appearance/display].  Working on several new VMs not yet deployed and this morning two of the five lost their GRUB timers, yesterday one (different than today's two) lost it's timer.

Something is causing GRUB to not "default boot".  You're not alone.  Came here via Google to see if this is a common/known issue...off to collect some data, maybe we can figure out the GRUB part.  You're probably SOL on that USB hardware issue, though.

---

### Post by Nutria on 2013-01-24
> **oldfred said:**
> Does keyboard work to get you into BIOS before grub starts loading?

I mentioned that in the original post: no, it doesn't.

```
Thirdly, USB ports seem to have stopped working. I've tried two KBs in multiple ports and I can't even get to the BIOS setup. Booting from a CD is similarly useless
```

> I thought USB was related to reading flash drive or booting flash drive, not keyboard.

Eh? :confused: I must have written the word "keyboard" a dozen times.

> I used to have keyboard issues, years ago and that was a BIOS setting, but you should of had that from the beginning. Or did you flash BIOS? As that resets to defaults.

Have never flashed that mobo's BIOS.  Would have thought of that first if I had recently flashed it.

---

### Post by Nutria on 2013-01-24
> **VyReN said:**
> Sounds like a hardware issue with USB, (snip) You're probably SOL on that USB hardware issue, though.

Thanks, but that confuses me.  How does USB just... fail?

(Note that it still sends power to my Nook and the lights in my keyboard keys.)

---

### Post by oldfred on 2013-01-24
do you have ps/2 ports and an adapter? I have 3 or 4 USB to ps/2 adapters (see below why).  New keyboards now do not include the adaptors.
Or is this a laptop.

Or it may just be keyboard, I have had several fail over the years, but I tend to buy cheap ones, so I pay the price. The only keyboard I really liked was the old IBM AT one.

---

### Post by Nutria on 2013-01-24
> **oldfred said:**
> do you have ps/2 ports and an adapter? I have 3 or 4 USB to ps/2 adapters (see below why).  New keyboards now do not include the adaptors.

No.  I have thought of that, but don't have any and haven't been able to get to Radio Shack yet.

> Or is this a laptop.

In that case I'd have unplugged the external k/b and used the internal one.

> Or it may just be keyboard

That's why I mentioned that I tried **two** keyboards.

---

