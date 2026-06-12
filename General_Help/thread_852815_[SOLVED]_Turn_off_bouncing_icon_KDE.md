---
title: "[SOLVED] Turn off bouncing icon KDE"
date: 2008-07-08
forum: General Help
---

### Post by czechman86 on 2008-07-08
I would like to turn off the bouncing application icon in KDE, but cannot find the option in system settings. For those who are maybe confused by my wording, every time you open a program in KDE, a little icon bounces next to mouse cursor and I would like turn this off. Thanks for your help!

---

### Post by txcrackers on 2008-07-08
System Settings -> Keyboard & Mouse -> Mouse -> Visual feedback on activation

---

### Post by p_quarles on 2008-07-08
Actually I believe he's referring to something else:
KControl > Appearance & Themes > Launch Feedback. Change the setting to "No busy cursor."

---

### Post by czechman86 on 2008-07-09
> **p_quarles said:**
> Actually I believe he's referring to something else:
KControl > Appearance & Themes > Launch Feedback. Change the setting to "No busy cursor."

first off, thanks to you both. i can find what the first post is suggesting that i do, but i cannot find this section. i am used to working with vanilla kde and the modifications on kubuntu are kind of strange to me. under the appearance section of the kcontrol, in kubuntu, i cannot find this option. a while back i saw a guide on how to get vanilla kcontrol back in kubuntu and if anyone knows how to do this, it would be much appreciated. and it would maybe even solve my problem with the bouncing icon. if not, i can live with it. thanks!

---

### Post by p_quarles on 2008-07-09
> **czechman86 said:**
> first off, thanks to you both. i can find what the first post is suggesting that i do, but i cannot find this section. i am used to working with vanilla kde and the modifications on kubuntu are kind of strange to me. under the appearance section of the kcontrol, in kubuntu, i cannot find this option. a while back i saw a guide on how to get vanilla kcontrol back in kubuntu and if anyone knows how to do this, it would be much appreciated. and it would maybe even solve my problem with the bouncing icon. if not, i can live with it. thanks!
Here's a screenshot with the dialogue I mentioned open. Can you just confirm that this definitely doesn't show for you?

If not, I should be able to find the rc file that controls this setting.

---

### Post by czechman86 on 2008-07-09
i can confirm that i do not have the vanilla kcontrol panel that you do and that in my options for appearance, there is no option like you have. am i perhaps missing a module that i can install? thank you!

---

### Post by czechman86 on 2008-07-09
got this solved. just had to change the system preference manager from the kubuntu specific one to kcontrol. after that your instructions were cake. thanks!

---

### Post by p_quarles on 2008-07-09
> **czechman86 said:**
> got this solved. just had to change the system preference manager from the kubuntu specific one to kcontrol. after that your instructions were cake. thanks!
Yeah, I was going to ask if you had tried typing "kcontrol" into the terminal, but sounds like you found a switch that brought it up in any case.

---

### Post by czechman86 on 2008-07-09
> **p_quarles said:**
> Yeah, I was going to ask if you had tried typing "kcontrol" into the terminal, but sounds like you found a switch that brought it up in any case.

actually thats exactly what i did. it was quite a relief to see my beautiful vanilla menu pop up!

---

### Post by dijxtra on 2008-08-04
Hm, I am trying to find this options in KDE 4.1, but can't. There's no "Visual feedback on activation" in System Settings -> Keyboard & Mouse -> Mouse, and Kcontrol controls my KDE 3, not KDE 4. Any idea how to turn off this most idiotic feature ever in KDE 4?

---

### Post by jlacroix on 2008-08-17
I can't find this option in KDE 4.1 either. I've checked everywhere you guys have said.

---

### Post by jlacroix on 2008-08-17
Actually, I think I've found it. In System-Settings, go to Desktop. On the left column choose "Launch Feedback".

I have yet to test this to see if it actually works but I think this is it.

---

### Post by deeplink on 2010-02-20
Yes, it is working...
Thanx...

---

