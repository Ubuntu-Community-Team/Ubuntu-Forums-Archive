---
title: "Eye strain and headaches"
date: 2024-04-12
forum: General Help
---

### Post by woodrock on 2024-04-12
I would like to try the upcoming LTS release but every time I have tried to use Linux in the past it has caused me to have sore eyes and headaches. It is not hardware related because I can use Windows on the same hardware with no problem. I do not think it is anything to do with fonts or font rendering because I start to feel ill just viewing and editing photos. It is not video driver related either because I tried different drivers for my onboard Intel video card and a Nvidia video card I fitted later to see if that would help.
Has anybody else suffered with eyestrain and found a solution? 
(Some smart phones give me headaches too. I think it may be something to do with pulse width modulation dimming of OLED screens because I am okay with the IPS screen in my cheap Nokia. I think I am correct in saying IPS screens do not use PWM.)

---

### Post by hyperlinxe on 2024-04-12
That's pretty funny, you want to try the upcoming lts release but you are worried about head aches. 

ZING. You nailed it buddy. New releases are often times a giant headache. You're better off waiting for a few months at least any time a giant new release, like the entire operating system, comes out, to avoid head aches.

Also for eye strain, I recommend using light backgrounds and reducing the brightness of your screen. It seems counterintuitive because instinctively the dark background *feels* like it's more comfortable, but what is actually happening is that the light's brightness is independent of it's color, and the way we interpret it's effect is not indicative of the solution to this problem.

---

### Post by Rubi1200 on 2024-04-12
Might be a good idea to read through this page.
[https://help.ubuntu.com/stable/ubuntu-help/a11y.html.en](https://help.ubuntu.com/stable/ubuntu-help/a11y.html.en)

There may be some tips to help you adjust settings to deal with some/all of the things you mentioned.

---

### Post by guiverc on 2024-04-13
If it's color related.. you may find using apps like *redshift* can be helpful.

[https://help.ubuntu.com/community/Redshift](https://help.ubuntu.com/community/Redshift)

Whilst the main intention is to adjust the *blue light* out of screens when it gets dark outside.. If you go and manually edit the configuration file, you can change a lot of things, INCLUDING settings for daytime too.  There are settings for *gamma*, *temperature *and more, though for full details you may need to go to other (*newer*) docs than the old Ubuntu link I've provided.

---

### Post by woodrock on 2024-04-27
Thank you all for trying to help. I found this,
[https://askubuntu.com/a/516194](https://askubuntu.com/a/516194)
I think it is what I need but it looks too complicated. I don't want to damage my hardware.

---

### Post by hong-xu on 2024-04-29
The post refers to PWM, but PWM is mostly controlled by hardware and only to some extent by software (driver). If you have switched to a new screen, you may not experience this any longer.

Based on my own experience, even if the PWM frequency is high enough that I don't explicitly feel eye-strains, I actually got tired sooner than otherwise.

If you need a monitor that doesn't have PWM, I would recommend [BenQ]("https://benq.com") monitors, which are PWM-free guaranteed. For laptops, I refer to [LaptopMedia]("https://laptopmedia.com/top-laptop-pwm-ranking-rated-by-negative-impact-on-eyesight/"). For more information, also check out the [PWM_sensitive subreddit]("https://www.reddit.com/r/PWM_Sensitive/").

Further discussion on PWM is likely out of topic on this forum :P

---

### Post by dragonfly41 on 2024-04-29
Accessibility forum might offer other ideas.

[https://ubuntuforums.org/forumdisplay.php?f=145](https://ubuntuforums.org/forumdisplay.php?f=145)

---

