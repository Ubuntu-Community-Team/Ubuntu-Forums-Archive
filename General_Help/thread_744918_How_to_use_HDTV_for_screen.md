---
title: "How to use HDTV for screen?"
date: 2008-04-04
forum: General Help
---

### Post by JimBuntu on 2008-04-04
So, I have a 52" LCD 1080p and I want to use it as my screen. I have tried to hook it up using  a DVI to component that came with my video card, but I kept getting the wrong screen resolution. Does anyone know exactly how to do this? Should I be using a dvi to hdmi? When I go to the screen resolution settings it doesn't have the correct resolution to choose.

---

### Post by danwood76 on 2008-04-04
Well you can do DVI to HDMI very easily which is what I would use to connect a HDTV.
I doubt DVI to component is very good as you are then using the VGA outputs on the DVI connector.

Get a DVI - HDMI cable and try it with that.

---

### Post by JimBuntu on 2008-04-04
When you hooked up to your big screen did you get the appropriate resolution? I would like 1920x1080...

---

### Post by chewearn on 2008-04-04
What video card do you have?

---

### Post by JimBuntu on 2008-04-04
BFG 8600 gt over clocked 512mb gddr3 memory.

---

### Post by stefangr1 on 2008-04-04
I assume you have installed the proprietary drivers from the nvidia site (using envy or by ourself). 
You can't change the resolution in the nvidia configuration panel (you can also enter a resolution yourself, by pressing the advanced button in the X Sever Configuration thing)?

---

### Post by JimBuntu on 2008-04-04
I dont have a nvidia configuration panel. At least not that I know of... I do have the nvidia drivers installed.  But no nvidia configuration panel.

---

### Post by stefangr1 on 2008-04-04
> **JimBuntu said:**
> I dont have a nvidia configuration panel. At least not that I know of... I do have the nvidia drivers installed.  But no nvidia configuration panel.

try the command below (as normal user):

 nvidia-settings

---

### Post by JimBuntu on 2008-04-04
that code worked and I saw finally the nvidia settings. Is there a way to include that in the System>Preferences tab. Also, while looking at the available settings I only saw 1024x768. Is this because that is the highest resolution available with my current screen? If I hook it up to my HDTV will I see more options?

---

### Post by JimBuntu on 2008-04-04
bump

---

### Post by chewearn on 2008-04-04
> **JimBuntu said:**
> that code worked and I saw finally the nvidia settings. Is there a way to include that in the System>Preferences tab. 

Rightclick on your panel menu, select Edit Menus.  Poke around in there, and see if you can find an entry for Nvidia Settings.  There should be one under Applications > System Tools.  If not create one yourself, click New Item button.


> Also, while looking at the available settings I only saw 1024x768. Is this because that is the highest resolution available with my current screen? If I hook it up to my HDTV will I see more options?Plug in you HDTV, click "Detect Displays" button.  After you have adjusted the settings to your satisfaction, click "Save X configuration file" button.  Navigate to your home directory to save the file (if not you will get "permission denied" when saving).

Then, finally:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup  # make backup
sudo cp ~/xorg.conf /etc/X11/xorg.conf  # copy new settings
```and CTL+ALT+Bacspace

---

### Post by skydiver|goose on 2008-04-04
I know from working at radioshack that if you're trying to get 1080p picture on your HDTV, the ONLY cable that will properly send that signal is either a Monster brand cable or a Blue-Jean brand cable. Any/all other cables will work; but only for a couple of weeks before they start to eat through their own shielding. I know Radioshack doesn't sell a direct HDMI-DVI cable; however, we do sell HDMI cables and HDMI-DVI adapters that are both Monster brand. Monster is ridiculously expensive, though. If you plan on upgrading your cables, I'd recommend becoming certified on the Monster website. You get 70% off of online orders.

Any other HDMI/DVI cable will work if you're doing 1080i, or any other picture. But 1080p requires Monster/Blue Jean

---

### Post by 7/9 on 2008-04-04
Which of the nvidia driver packages do you have installed?

I wrestled with one of these 52" babies last week, hooked up to a freshly installed Ubuntu on one of our demo setups. However, I couldn't get it to show any other resolutions than SVGA/XGA -- no widescreen, no 1080p. 

However, replacing my graphics driver set with this one did the trick:

**NVidia binary X.Org driver ("new" driver)**

The legacy driver was installed with Ubuntu, so a simple change to this one gave me widescreen resolutions way over 1080p! If this is in fact the one that you have installed, you could always try replacing it with the legacy one.

It's worth a shot!

---

### Post by chewearn on 2008-04-05
> **skydiver|goose said:**
> I know from working at radioshack that if you're trying to get 1080p picture on your HDTV, the ONLY cable that will properly send that signal is either a Monster brand cable or a Blue-Jean brand cable. Any/all other cables will work; but only for a couple of weeks before they start to eat through their own shielding. I know Radioshack doesn't sell a direct HDMI-DVI cable; however, we do sell HDMI cables and HDMI-DVI adapters that are both Monster brand. Monster is ridiculously expensive, though. If you plan on upgrading your cables, I'd recommend becoming certified on the Monster website. You get 70% off of online orders.

Any other HDMI/DVI cable will work if you're doing 1080i, or any other picture. But 1080p requires Monster/Blue Jean

Nah, I have to disagree with you on this one.  A non-brand cheap cable with proper construction will work as well.

---

### Post by tgalati4 on 2008-04-05
I like Geffen cables over Monster.  Better quality and cheaper too.  AudioQuest from Fry's seem to work as well.

---

### Post by danwood76 on 2008-04-05
Th eOP is trying to connect through component and I know for a fact that the component out on a graphics card wont go higher than 1024x768.
The OP does need to buy a cable.

IMO name brand cables are **** unless you pay a hell of a lot of money, you can get good cables for next to nothing if you shop around that are perfect for home use.
My DVI ual link cost me a £5er and it works flawlessly ;).

---

### Post by chewearn on 2008-04-05
> **danwood76 said:**
> Th eOP is trying to connect through component and I know for a fact that the component out on a graphics card wont go higher than 1024x768.
The OP does need to buy a cable.


Not exactly.  TheOP is using "DVI to component".  This is most likely a DVI-VGA cable, utilising the analog part of DVI.  VGA can support the highest resolution possible from a PC.  And if the cable is correctly made, the DCC wire will be connected for transmitting the resolution info supported by the display.

---

### Post by Yfrwlf on 2008-04-11
> **AstalaVista said:**
> Not exactly.  TheOP is using "DVI to component".  This is most likely a DVI-VGA cable, utilising the analog part of DVI.  VGA can support the highest resolution possible from a PC.  And if the cable is correctly made, the DCC wire will be connected for transmitting the resolution info supported by the display.

Very interesting thread, and thanks AstalaVista I was wondering about how that worked.  I was really hoping that the Screen Resolution in Hardy would show the TV Out display but due to Nvidia being a bunch of aholes with their closed hardware, you have to use the Nvidia X Settings Configuration GUI found in System > Admin it seems.  Under that, the weird svidieo-like component out still only shows that it's able to go up to 1024x768 for me even though my TV supports 1080i and 480p/i.  I was thinking that perhaps I may need a TV that has a DVI/HDMI/VGA in if I wanted to get beyond that, but now I'm thinking it may be a driver limitation for the component out, and that if I used the DVI/HDMI out port to a cable that converts to component, perhaps then I'll see the proper available resolutions.  Thank you driver limitations...

Getting off topic, but there are other brands of cards, like Intel and AMD, that have HDTV output, those may work better since Intel and AMD are more open than Nvidia.  Also [add VIA to the mix]("http://www.phoronix.com/scan.php?page=article&item=via_oss&num=1") now, too, even though I don't think they make any higher powered graphics chips, but neither does Intel really.  Perhaps ATI/AMD will be our savior with Novell helping them, but their open source driver is still quite a ways off apparently, so you're kind of stuck if you want something now that has lots of capabilities and can do as much on Linux as the Windows drivers can.  Wish they'd just ditch the proprietary driver or open it so we can start making a driver that is *better* than the Windows drivers which can do more.  Reminds me of Creative going after the Vista driver developer.  Just shoot yourself in the foot, I'm sure that'll really help your company.  Just because you've relied upon the added sales boost by using your proprietary drivers as a wedge to force everyone onto an upgrade treadmill doesn't mean you're free to do it forever, not in this new world of information sharing. </rant>

> **7/9 said:**
> Which of the nvidia driver packages do you have installed?

I wrestled with one of these 52" babies last week, hooked up to a freshly installed Ubuntu on one of our demo setups. However, I couldn't get it to show any other resolutions than SVGA/XGA -- no widescreen, no 1080p. 

However, replacing my graphics driver set with this one did the trick:

**NVidia binary X.Org driver ("new" driver)**

The legacy driver was installed with Ubuntu, so a simple change to this one gave me widescreen resolutions way over 1080p! If this is in fact the one that you have installed, you could always try replacing it with the legacy one.

It's worth a shot!

Are you using component, DVI, or HDMI out from the graphics card to get that working, and what was on the other end?  I'm guessing you were doing something like DVI/HDMI to DVI/HDMI.

> **skydiver|goose said:**
> I know from working at radioshack that if you're trying to get 1080p picture on your HDTV, the ONLY cable that will properly send that signal is either a Monster brand cable or a Blue-Jean brand cable. Any/all other cables will work; but only for a couple of weeks before they start to eat through their own shielding. I know Radioshack doesn't sell a direct HDMI-DVI cable; however, we do sell HDMI cables and HDMI-DVI adapters that are both Monster brand. Monster is ridiculously expensive, though. If you plan on upgrading your cables, I'd recommend becoming certified on the Monster website. You get 70% off of online orders.

Any other HDMI/DVI cable will work if you're doing 1080i, or any other picture. But 1080p requires Monster/Blue Jean

Also highly disagree.  That's what their marketing departments want you to believe.  They make more money on cables than most other products for a reason.  Especially with digital connections, shielding is usually not that important at all for most home theater setups, but even if you need shielding, there are many cables out there that don't cost $$$.  The only reason why stores sell cables at that price is that they convince consumers that it's important, and "not that much money" in comparison to the $$$ they just spent on the rest of the components, and they're usually right about that, but wrong about the price you have to pay for getting the quality that's needed.  For analogue connections it's more important since it lacks the integrity checking like digital provides, but again there are much cheaper cables that are shielded, and you only need some kind of extra shielding if you have a lot of high powered cables around them that could interfere with the signal.  Also, you do need higher gauge cabling if you're planning on pushing a lot of power through them, but as we're talking about video cables that's usually not a concern at all.  Shop around.

---

### Post by stchman on 2008-04-11
> **JimBuntu said:**
> So, I have a 52" LCD 1080p and I want to use it as my screen. I have tried to hook it up using  a DVI to component that came with my video card, but I kept getting the wrong screen resolution. Does anyone know exactly how to do this? Should I be using a dvi to hdmi? When I go to the screen resolution settings it doesn't have the correct resolution to choose.

You will need a DVI-HDMI cable.

If your LCD is 1080P then the native resolution is 1920x1080

You will need to update your xorg.cont with that resolution.

There is no DVI to component as DVI is digital and component is analog.

---

### Post by Yfrwlf on 2008-04-11
> **stchman said:**
> You will need a DVI-HDMI cable.

If your LCD is 1080P then the native resolution is 1920x1080

You will need to update your xorg.cont with that resolution.

There is no DVI to component as DVI is digital and component is analog.

That last part is incorrect.  How do you think it's possible hooking up DVI to VGA monitors with a simple "dumb" converter?  DVI is capable of both analogue and digital.

**HDMI** is the one that only supports digital, and specifically, purposefully, does not support analogue because the intention behind it is to close the analogue hole to enable DRM.  DVI and HDMI are basically the same thing any way, HDMI was simply a hasty follow-up to try to push DRM IMO.

However, as far as monitor resolution detection goes, I'd guess that surely it must be done over component, or in other words surely devices can auto-detect monitor resolutions over component?  If not, you'd have to "force" (i.e. specify) the screen resolution for these "dumb" devices.  Who knows any way since you have to use Nvidia's closed source driver for all of this, so who knows what they are doing or not doing.

Any way, I'm trying various setups, and as soon as I get mine working I'll let this thread know how and what I needed to do.

---

### Post by chewearn on 2008-04-12
There seemed to be some confusion about analog video, namely "component video", DVI and VGA.

To clear the matter up:

1. Component video is commonly used to refer to YPbPr connection.  This is the 3-cinch (or in the old days RCA connector) of green-blue-red.

2. The OP of this thread probably use "component video" phrase to refer to VGA (since he stated "DVI-component" cable).  This is not a common usage, but we can deduced he was actually referring to DVI-VGA cable.

3. DVI is introduced by the computer industry to supercede VGA.  In order to maintain backward compatibility, the DVI has a digital part and an analog part.  However, it is not mandatory for a DVI device to support the analog signal.

4. VGA (whether from the D-sub or DVI) can support any PC resolutions.

5. Component video (YPbPr) supports NTSC, PAL and P-scan (according to international / national standards).  In practice, it can also support HDTV resolutions, though if I remember correctly, this is forbidden by some DRM specifications.

---

