---
title: "I am getting a 1360 x 768 screen resolution on one laptop but not the other."
date: 2015-01-28
forum: General Help
---

### Post by yeto on 2015-01-28
I have a flashdrive that is provided to me from the company that I work for that I think is Ubuntu. I have two laptops. When I use the flashdrive on the one laptop I get the following available screen resolutions when I click on the "gear" icon in the lower left corner. This laptop has an Intel i7 core processor with a Nvidia GeForce 310M GPU. 

 1680 x 945, 1152 x 864, 1024 x 768 and  800 x 600

On my other laptop which has an Intel Pentium processor which just uses the embedded GPU I get the following available screen resolutions.

1600 x 900, 1440 x 900, 1360 x 768, 1152 x 864, 1024 x 768 and  800 x 600.

 I need a 1360 x 768 display option to be available on the laptop with the  GeForce GPU to run a certain program. That option is available when I run Windows 7 but it does not show when I use the flashdrive. Are there any settings I can change that will enable the 1360 x 768 option to show when I use the flashdrive? Is the GeForce GPU preventing the other options from showing? Do I need to somehow disable the GeForce GPU?

When I boot the flashdirve I see the word "xforcevesa". I don't know what that means but I thought it might be helpful to include that information.

Thanks in advance for any help,
yeto

---

### Post by SeijiSensei on 2015-01-28
What resolutions are available when you run the NVIDIA Settings utility?

---

### Post by yeto on 2015-01-28
> **SeijiSensei said:**
> What resolutions are available when you run the NVIDIA Settings utility?

Thank you for your reply.

1680 x 945
1600 x 900
1360 x 768
1280 x 800
1280 x 768
1280 x 720
1152 x 864
1024 x 768
800 x 600

Thank you,
yeto

---

### Post by efflandt on 2015-01-28
I imagine that the USB flash drive has default video drivers if it should work universally for different computers, so there would be no NVIDIA X Server Settings, which would not work with nouveau drivers anyway.

I did notice that when booting live/install iso on my laptop with hybrid Intel/Nvidia graphics, it seemed to be using the Nvidia graphics, because my power LED was amber instead of blue. But I did not pay attention to whether there was a way to switch that, which would likely require **nomodeset** boot parameter in order to even be able switch video modules. I know that **xrandr** does not work with proprietary nvidia drivers, but have not paid attention to whether that works with nouveau. But if that does work, there may be a way to run a script that uses xrandr to add a suitable video mode and switch to it.

PS: If NVIDIA X Server Settings does display those video modes is it actually able to switch to 1360x768, assuming that laptop also has a screen with about that resolution (although, mfr may call it 1366x768).

PPS: I was mistaken about live/install iso just using nvidia. It used nvidia during boot, but then switched to Intel graphics (then blue instead of amber power LED). So xrandr was able to list video modes on that laptop without using nomodeset. But Nvidia 310M is probably rather old, so that laptop might only have nvidia graphics, so not sure how to switch resolution of that with unknown drivers, or maybe a general vesafb mode, since it seems to be listing default resolutions for unknown VGA.

---

### Post by yeto on 2015-01-28
> **efflandt said:**
> I imagine that the USB flash drive has default video drivers if it should work universally for different computers, so there would be no NVIDIA X Server Settings, which would not work with nouveau drivers anyway.

I did notice that when booting live/install iso on my laptop with hybrid Intel/Nvidia graphics, it seemed to be using the Nvidia graphics, because my power LED was amber instead of blue. But I did not pay attention to whether there was a way to switch that, which would likely require **nomodeset** boot parameter in order to even be able switch video modules. I know that **xrandr** does not work with proprietary nvidia drivers, but have not paid attention to whether that works with nouveau. But if that does work, there may be a way to run a script that uses xrandr to add a suitable video mode and switch to it.

PS: If NVIDIA X Server Settings does display those video modes is it actually able to switch to 1360x768, assuming that laptop also has a screen with about that resolution (although, mfr may call it 1366x768).

Would it be worth a try to go under Adapter > Properties > Driver > and  click disable for the Nvidia GPU. Would my laptop then only use the embedded Intel GPU and maybe Ubuntu would give me more display options. My main concern would be if I disable the Nvidia GPU that I get a black screen that would render my computer useless. I don't have enough of a computer education to re-enable the Nvidia GPU with a black screen.

Thanks in advance for any help,
yeto

---

### Post by SeijiSensei on 2015-01-29
So did you try setting the resolution from the NVIDIA utility?  What happened?

---

### Post by yeto on 2015-01-30
> **SeijiSensei said:**
> So did you try setting the resolution from the NVIDIA utility?  What happened?

This is what I have tried so far. 

I disabled the Nvidia GPU and then booted the flash drive. (result = no difference)

I re-enabled the Nvidia GPU and updated the drivers. (result = no difference)

Using the Nvidia utility I changed the screen resolution. (result = no difference)

I just can't understand what Ubuntu "sees" on the one laptop versus the other that gives me those "extra" screen resolution options.

Thanks in advance for any help,
yeto

---

### Post by SeijiSensei on 2015-01-30
Likely the adapter supports those resolutions, but the screen does not.  What if you connect the laptop to an external monitor over HDMI?

---

### Post by yeto on 2015-01-30
> **SeijiSensei said:**
> Likely the adapter supports those resolutions, but the screen does not.  What if you connect the laptop to an external monitor over HDMI?

Please help me understand your reply. The screen supports those resolutions because when I change to those resolutions in Windows 7 they display with no problem. It is just when I boot the Ubuntu flash drive I have limited options. I don't understand why the Ubuntu flashdrive will give me more screen resolution options on one laptop versus the other. I would think they would both be the same.

Kind regards,
yeto

---

### Post by SeijiSensei on 2015-01-30
> **yeto said:**
> I don't understand why the Ubuntu flashdrive will give me more screen resolution options on one laptop versus the other. I would think they would both be the same.
Why? The laptops have different video adapters.

Now if this is a "hybrid" laptop with both an NVIDIA and an Intel graphics adapter, things can be much more complicated.  I disable the Intel card in the BIOS on machines like this to force them to use the NVIDIA adapter.  I presume you installed the NVIDIA driver to the flash drive, right?  You might also take a look at this: [http://www.bumblebee-project.org/](http://www.bumblebee-project.org/).

---

### Post by yeto on 2015-02-01
> **SeijiSensei said:**
> Why? The laptops have different video adapters.

Now if this is a "hybrid" laptop with both an NVIDIA and an Intel graphics adapter, things can be much more complicated.  I disable the Intel card in the BIOS on machines like this to force them to use the NVIDIA adapter.  I presume you installed the NVIDIA driver to the flash drive, right?  You might also take a look at this: [http://www.bumblebee-project.org/](http://www.bumblebee-project.org/).

I guess what I don't understand is that I have a lot more screen resolution options available in the Windows environment versus the Ubuntu environment. It would seem to me that the screen resolution options would be the same whether using Windows versus Ubuntu.

---

### Post by SeijiSensei on 2015-02-01
Well, yes, but that's because there are good Window drivers for these hybrid laptops, while Linux implementations have had to be reverse-engineered.  That's why I've found it easiest to disable the Intel adapter and just use the NVIDIA one.  That avoids the problem altogether.  If you want to look further into this, take a look at the [Bumblebee project](http://www.bumblebee-project.org).

---

