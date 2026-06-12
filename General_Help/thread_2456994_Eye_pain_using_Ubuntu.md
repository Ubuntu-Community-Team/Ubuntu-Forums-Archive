---
title: "Eye pain using Ubuntu"
date: 2021-01-23
forum: General Help
---

### Post by roman2526 on 2021-01-23
Hello guys,

I tried Ubuntu, but I experience eye pain after 30-45 minutes of using it. I do not experience any eye pain using windows. I have a GTX 1060. I checked the resolution and refresh rate, both are native to my monitor. 
I would appreciate any help!

Thank you.

---

### Post by gdesilva on 2021-01-23
If you are using the computer in the evening or night times, try redshift-gtk which filters blue light. In my case it certainly has helpd relieve eye strain when watching the screen at night.

---

### Post by roman2526 on 2021-01-23
I have blue light filter on my monitor, and on windows I don't experience any eye pain. The problem must be with Ubuntu, but I don't know what it is.

---

### Post by Tadaen_Sylvermane on 2021-01-23
Maybe just the color tone? I know for me the default Ubuntu colors, the orangish / brown in particular is harsh for my eyes. I don't really know why but I typically come up with grey / bluish themes.

---

### Post by HermanAB on 2021-01-24
Well, with Linux, one tends to consume large amounts of coffee and other hot drinks, while pondering the intricacies of the system.  So, maybe you should just make sure that you remove the spoon from the mug, so that you don't poke it in your eye...

---

### Post by ordak on 2021-01-24
Have you installed NVidia drivers ?

---

### Post by dinkidonk on 2021-01-24
There is a big difference between font rendering in Windows vs. Linux, so if the eye strain was caused by reading then try to fiddle with the font rendering settings in Linux.

---

### Post by Impavidus on 2021-01-24
Hard to deal with vague complaints. Have you looked at font size or design?

---

### Post by dragonfly41 on 2021-01-24
You can go to very top bar, far right dropdown arrow (where you Power Off) and select Settings. 
Then Appearance.
Try Window Theme > dark to ease the eye strain.
There are other UI tweaks you can make. Font size etc.

---

### Post by roman2526 on 2021-01-24
Thanks for your response guys. I know my description is pretty vague, but the problem is really frustrating. I installed the Nvidia driver, Dark theme seems to help a little bit. I installed Gnome tweaks, but I dont really know what to change in the fonts menu. I will try to fiddle around hope the eye strain gets better. Is there any graphics driver changes I can make?

---

### Post by dinkidonk on 2021-01-25
Personally I think that dark themes make the eye strain worse. [How to change font settings.](https://www.omgubuntu.co.uk/2016/03/how-to-change-ubuntu-desktop-font)

---

### Post by username2758 on 2021-01-25
Try Ubuntu with the Unity desktop environment. I find it to be the best in terms of eye-strain levels and still don't know why.

It's really unfortunate that Linux users have to deal with eye-strain more than Windows.

To make things worse, LED-backlit monitors which has become pretty much the standard often has worse eye-strain levels than its predecessor LCD and CCFL backlight.

---

### Post by dinkidonk on 2021-01-25
> **username2758 said:**
> Try Ubuntu with the Unity desktop environment. I find it to be the best in terms of eye-strain levels and still don't know why.

It's really unfortunate that Linux users have to deal with eye-strain more than Windows.

To make things worse, LED-backlit monitors which has become pretty much the standard often has worse eye-strain levels than its predecessor LCD and CCFL backlight.

Both CCFL and LED backlit monitors are LCD. LED backlight may cause problems if it uses PWM for dimming, otherwise not. Most monitors of a decent quality does not use PWM anymore. The main issue is fonts and the rendering thereof and usually there are workarounds for most users if they take the time to fiddle with fonts styles and rendering settings (anti-alias, hinting etc.).

I remember once there was an update of Internet Explorer on Windows, may have been from V9 to V10 or V11, where the text rendering was suddently so blurry and unsharp that is was really strenuous to read text. This new "feature" could not be turned of and that was what pushed me to use Firefox. Never looked back, though! ;)

---

### Post by username2758 on 2021-01-25
> **dinkidonk said:**
> Both CCFL and LED backlit monitors are LCD. LED backlight may cause problems if it uses PWM for dimming, otherwise not. Most monitors of a decent quality does not use PWM anymore. The main issue is fonts and the rendering thereof and usually there are workarounds for most users if they take the time to fiddle with fonts styles and rendering settings (anti-alias, hinting etc.).

I remember once there was an update of Internet Explorer on Windows, may have been from V9 to V10 or V11, where the text rendering was suddently so blurry and unsharp that is was really strenuous to read text. This new "feature" could not be turned of and that was what pushed me to use Firefox. Never looked back, though! ;)

Yeah, by LCD I was referring to the different type of backlighting prior to the advent of LEDs. Think it was called fluorescent? The tonality of LEDs is naturally colder thus much harder on the eye.

I haven't fiddle with font rendering yet, but I do like what comes with Unity DE. 

Do you know if changing rendering settings in the OS also changes the font rendering in Mozilla Firefox? Or each browser has its own font rendering settings? How does that work?

---

### Post by dinkidonk on 2021-01-26
> **username2758 said:**
> Think it was called fluorescent? The tonality of LEDs is naturally colder thus much harder on the eye.

I haven't fiddle with font rendering yet, but I do like what comes with Unity DE. 

Do you know if changing rendering settings in the OS also changes the font rendering in Mozilla Firefox? Or each browser has its own font rendering settings? How does that work?

The "F" in CCFL stands for fluorescent, AFAIK there are only CCFL and LED backlighting in LCD's and the LED's are more color accurate than CCFL. The "warmth" of the screen can be adjusted, I use Kubuntu and there is a neat "night" setting which turns down the blue light gradually so you do not notice it happens. If you like the default settings, no need to fiddle with it I guess. As far as I recall, Firefox uses the system settings for font rendering but it may to some degree also be controlled by CSS/stylesheets on websites. It's free to fiddle with settings and revert to default afterwards.

---

### Post by The Cog on 2021-01-26
It may be the blur-iness of the text in font rendering. 
This page may help find the settings: [https://askubuntu.com/questions/19770/how-do-i-change-fonts-and-adjust-their-size](https://askubuntu.com/questions/19770/how-do-i-change-fonts-and-adjust-their-size)
Particularly the antialiasing and hinting settings alter the appearance and blurring of the text. Try fiddling with those.

---

### Post by mIk3_08 on 2021-01-26
> **username2758 said:**
> Ubuntu with the Unity desktop environment.  Me too. I'm on Ubuntu Unity desktop environment. I'm using this for many years now, But I haven't experience any eye strains yet. I think you should give time to rest closing your eyes and take a break.

---

### Post by username2758 on 2021-01-26
> **dinkidonk said:**
> The "F" in CCFL stands for fluorescent, AFAIK there are only CCFL and LED backlighting in LCD's and the LED's are more color accurate than CCFL. The "warmth" of the screen can be adjusted, I use Kubuntu and there is a neat "night" setting which turns down the blue light gradually so you do not notice it happens. If you like the default settings, no need to fiddle with it I guess. As far as I recall, Firefox uses the system settings for font rendering but it may to some degree also be controlled by CSS/stylesheets on websites. It's free to fiddle with settings and revert to default afterwards.

I've never heard LED backlighting improves color accuracy, in fact CCFL used to have a wider color gamut than most LED-based LCD's but I am not sure if it's solely because of the type of backlighting. In my opinion, there are far more disadvantages than advantages to using LED backlighting, especially if the manufacturer doesn't have good Quality Control in production. For example, many LG IPS panels suffer from ridiculous amounts of backlight bleeding, IPS glow and clouding, which causes further strain on the eyes. Of course all this could be remedied if manufacturers chose direct-lit  backlighting (called full-array local dimming on TVs) instead of cheaper  edge-lit backlighting, but to be honest I never experienced eye-strain  or any backlight bleeding/glow before the advent of LED panels.

> **mIk3_08 said:**
> Me too. I'm on Ubuntu Unity desktop environment.  I'm using this for many years now, But I haven't experience any eye  strains yet. I think you should give time to rest closing your eyes and  take a break.

Yeah. The only problem with Unity though is the lack of a dark theme (plus they are charging for a dark theme?). This is Linux, come on! But in terms of eye-strain levels Unity is still the best for me.

---

### Post by T6&amp;sfpER35% on 2021-01-26
[Here](https://www.bestbuy.com/site/shop/eye-strain-computer-glasses) you go 

you're welcome

:P

---

### Post by dinkidonk on 2021-01-26
> **3nd said:**
> [Here]("https://www.bestbuy.com/site/shop/eye-strain-computer-glasses") you go 

you're welcome

:P

Placebo, waste of money.

---

### Post by T6&amp;sfpER35% on 2021-01-26
> [COLOR=#000000]Placebo, waste of money.[/COLOR]
probably , never used it 
my suggestion was more tongue in cheek

---

### Post by mIk3_08 on 2021-01-28
> **username2758 said:**
> The only problem with Unity though is the lack of a dark theme (plus they are charging for a dark theme?).  I am happy enough using mono dark theme and with the service of my O.S,  I don't demand any since it has given to me free of use as in Free Open Source. I am more contented with it. Ubuntu to you all guys. :-D

---

### Post by laluz2 on 2021-06-18
I have "upgraded" my monitor to the one having a smaller pixel pitch 0.25 mm -> 0.23 and suddenly eyestrain became unbearable, similar to what you describe. Mostly in Firefox Mozilla, though, so I have opened a question here [https://support.mozilla.org/en-US/questions/1339647](https://support.mozilla.org/en-US/questions/1339647) So far I have worked around it by using gnome-tweaks. I have increased Scaling Factor to 1.25 and decreased system fonts to 9-10. Hinting is on Slight, Antialiasing on Subpixel.

---

