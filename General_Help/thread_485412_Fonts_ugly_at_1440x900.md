---
title: "Fonts ugly at 1440x900"
date: 2007-06-26
forum: General Help
---

### Post by mr_ed on 2007-06-26
I hate to post another font thread, but here goes...

I read that I may have a video card problem rather than a font problem, which is possible... especially since I have a Voodoo3 2000.
Everything looks better at 1152x764, but maybe that's because all the text is larger there. 

I just bought this new Acer 19" widescreen monitor, and everything looks beautiful except the fonts.  I'll attach a screenshot.  Come to think of it, I'll attach a 1152x768 screen too.

Can anyone tell me what's wrong?

Oh, and I find it odd that the frequency is listed as 60Hz @ 1440x900 and 55Hz @ 1152x768.. shouldn't they be more in the range of 75-85?  Or is that just for CRT monitors?

Oh, and BTW, I've clicked every button on the Font app (System->Preferences->Font) and they  all look crappy.

EDIT:  I just looked at both of those screenshots, and they look identical -- both bad at 1440x900 and both good at 1152x768.
Maybe I should take a picture with a camera at the two different resolutions and post those... :(

---

### Post by coffeecat on 2007-06-27
I can't actually see the difference in font quality between the two screenshots except with the 1440x900 one you have to click on an '+' icon to bring it into focus. However, I can see that the fonts are not autohinted - typical of a default Ubuntu install, and with deformed letter shapes. If you would like to see the effect of autohinting, open a terminal and do:

```
sudo dpkg-reconfigure fontconfig-config
```Answer yes to autohinting and accept the defaults for the other two questions. You have to restart the xserver to see autohinting in action. If you don't like it simply run that command again and switch autohinting off.

Also - this is my personal preference - download and install the msttcorefonts package and then choose Verdana for your desktop fonts (and firefox too if you like it). That particular font with autohinting makes for a very pleasant desktop in my view.

As far as the refresh rate is concerned, 60 should be fine for a flat-screen monitor. That's what I use most of the time. In fact your monitor handbook should tell you the correct refresh rate for each resolution. It rarely goes above 75 for a flat screen. CRTs need higher refresh rates to prevent flicker.

---

### Post by ThrobbingBrain66 on 2007-06-27
Give these font patches a try, they really do wonders.

[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

---

### Post by djchandler on 2007-06-27
> **mr_ed said:**
> I hate to post another font thread, but here goes...

I read that I may have a video card problem rather than a font problem, which is possible... especially since I have a Voodoo3 2000.
Everything looks better at 1152x764, but maybe that's because all the text is larger there. 

I just bought this new Acer 19" widescreen monitor, and everything looks beautiful except the fonts.  I'll attach a screenshot.  Come to think of it, I'll attach a 1152x768 screen too.

Can anyone tell me what's wrong?

Oh, and I find it odd that the frequency is listed as 60Hz @ 1440x900 and 55Hz @ 1152x768.. shouldn't they be more in the range of 75-85?  Or is that just for CRT monitors?

Oh, and BTW, I've clicked every button on the Font app (System->Preferences->Font) and they  all look crappy.

EDIT:  I just looked at both of those screenshots, and they look identical -- both bad at 1440x900 and both good at 1152x768.
Maybe I should take a picture with a camera at the two different resolutions and post those... :(

Mr. Ed,

I just looked at your screen captures, and your fonts seem to be the same resolution in both. Obviously you are wanting to get more stuff viewable simultaneously on one screen, but it might help if you increased the dpi resolution of your fonts at 1440x900, higher than the res you are using at 1152x768. Go to the details screen of the font preferences and play with the dots per inch setting and see if that helps. It will make the fonts bigger too, though, so this may be defeating your purpose. I've had to settle with 1280x768 with my combination, but I'm using a 27" that's really supposed to be a HDTV. I'm betting that if I upgraded my GForce2 at least to the FXs that I could at least get 1360x768, but that will be the max for this LCD. A Riva TNT2 was actually better at getting 1360x768, but was too slow with this Athlon 64 3200 in this MOBO. I'm thinking that going to a new video card is your best bet.

But I would also give those patches a try just to see before spending money.

D. J.

---

### Post by mr_ed on 2007-06-27
> **djchandler said:**
> I just looked at your screen captures, and your fonts seem to be the same resolution in both.

I know... that's what I wrote in my edit above.
The size of the fonts is exactly what I want at 1440x900, so I don't want to mess with DPI (I played around with them anyway, and it still looked bad).

The thing that struck me most was that both screenshots looked bad at 1440x900 and both looked good at 1152x768.

I'll try the dpkg-reconfigure again, and I'll definitely try the patches.  Thanks.

---

### Post by stchman on 2007-06-27
> **mr_ed said:**
> I hate to post another font thread, but here goes...

I read that I may have a video card problem rather than a font problem, which is possible... especially since I have a Voodoo3 2000.
Everything looks better at 1152x764, but maybe that's because all the text is larger there. 

I just bought this new Acer 19" widescreen monitor, and everything looks beautiful except the fonts.  I'll attach a screenshot.  Come to think of it, I'll attach a 1152x768 screen too.

Can anyone tell me what's wrong?

Oh, and I find it odd that the frequency is listed as 60Hz @ 1440x900 and 55Hz @ 1152x768.. shouldn't they be more in the range of 75-85?  Or is that just for CRT monitors?

Oh, and BTW, I've clicked every button on the Font app (System->Preferences->Font) and they  all look crappy.

EDIT:  I just looked at both of those screenshots, and they look identical -- both bad at 1440x900 and both good at 1152x768.
Maybe I should take a picture with a camera at the two different resolutions and post those... :(

I really can see zero difference in the two screen shots from a font perspective.

I have my fonts look like Windows XP which are really nice.

[http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html)

Give this one a try and you will see how good your fonts can look.

---

### Post by mr_ed on 2007-06-27
I really just need to take a picture with a camera and upload those ones.

---

### Post by mr_ed on 2007-06-27
> **ThrobbingBrain66 said:**
> Give these font patches a try, they really do wonders.

[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

Well that made a HUGE difference.  Thanks very much!

---

### Post by mr_ed on 2007-06-29
Well... everything was a little better, but it was still kind of ugly.

That is until I bought a new GeForce 5200.  Now everything is super smooth.  I'm astounded at the difference!

---

### Post by djchandler on 2007-07-02
> **mr_ed said:**
> Well... everything was a little better, but it was still kind of ugly.

That is until I bought a new GeForce 5200.  Now everything is super smooth.  I'm astounded at the difference!

Cool. Just made my decision for me which way to go next. The FX 5500 comes out of the XP box and is getting in this one and I'll get an FX 7 series card for the XP box. The FX GPUs are much better than their predecessors. When the TNTs and MXs were new, 1440x900 and wide screens were nowhere in my plans. I saw a great LCD running 1440x900 in my doctor's office last Friday. Now I know what you wanted, and it was probably more than worth the price of the FX 5200 card. 

Enjoy!:popcorn: 

DJ

---

### Post by RAH66 on 2007-07-16
I had the same issue and this worked for me

Ubuntu Linux has an option for font smoothing that isn’t turned on by default for some strange reason. This makes fonts significantly smoother, enough to be very noticable. To enable this option, you need to edit the .fonts.conf file in your home directory.

To create and open the file, run this command and paste in the xml data below it.

sudo gedit ~/.fonts.conf

Paste in this text:

<?xml version="1.0" ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>
</fontconfig>

You’ll have to log out and back in to see the difference.

---

