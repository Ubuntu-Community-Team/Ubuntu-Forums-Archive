---
title: "How to disable the onboard keyboard?"
date: 2023-05-12
forum: General Help
---

### Post by ssreddy555 on 2023-05-12
Though I put the toggle button to off in the accessibility settings, the inbuilt onboard keyboard still comes up on touching the screen. How to disable it?

---

### Post by sudodus on 2023-05-12
Which version are you running (22.04.2 LTS or another one)? Are you running Ubuntu Desktop or one of the community flavours (Kubuntu, Lubuntu ...)?

I am running Ubuntu Desktop 22.04.2 LTS and can check easily there, but if you have something else, the settings may be different.

---

### Post by ssreddy555 on 2023-05-12
I'm running Ubuntu 22.04.2 LTS.

---

### Post by sudodus on 2023-05-13
I tested in a 'clean' Ubuntu 22.04.2 LTS: a live system booted from USB on a Dell Latitude E7240 with a touch screen.

I could toggle the inbuilt onboard keyboard using the switch "Screen Keyboard". See the attached screenshot. I guess you have turned that switch off too.

Maybe you have done something with your Ubuntu system that stopped the toggle function. The alternative is that some automatic update && upgrade is guilty. A third possibility is that the touch screen and its driver are different between your computer and mine.

[HR][/HR]
I suggest that you try with a live 22.04.2 LTS system, if it works like your installed system or like my live system.

You can also try with some other version of Ubuntu: 20.04.6 LTS, 23.04 or some community flavour: Kubuntu, Lubuntu, Ubuntu Budgie, Ubuntu MATE ... Xubuntu.

---

### Post by ssreddy555 on 2023-05-13
What I'm saying is when I put the toggle to off position like in your post, the onscreen keyboard is still appearing on touching the screen to fill in a field which I don't want because I'm using a different keyboard called "onboard" keyboard.  

I want to totally disable/ uninstall the inbuilt keyboard as I'm using the "on board keyboard" & there is a clash in between the two. 

I can as well keep the inbuilt one & do away with the other but for the fact that I don't see it has any settings where I can change its size, lay out etc. Where can I find its settings?

---

### Post by sudodus on 2023-05-13
I must admit that I don't know which file is storing the settings for the built-in screen keyboard. Let us hope that someone who knows better than I will see this and chip in here and help you.

I think I understand your problem, but I cannot reproduce it in a 'clean' 22.04.2 LTS system. There is one more thing that I should add: I'm running X (not Wayland), and I think the separate program **[FONT=Courier New]onboard[/FONT]** works best in X so I have assumed that you run X too. Anyway, whichever desktop session type you run, please try the other one.

I think it would also be worthwhile to test versions and flavours according to my previous post, because I don't know how to turn off or remove the built-in screen keyboard. The reason is that it is integrated in the Gnome desktop environment. So if you use another version, the integration might be easier to manage via the obvious interface, and with another flavour (Kubuntu, Lubuntu ...) there is another desktop environment, which would eliminate the problem.

---

### Post by ssreddy555 on 2023-05-13
I'm also running x org mainly because I need auto screen rotation for my Lenovo Yoga laptop and it's not available in Wayland.
Thanks a lot for your time & advice.

---

### Post by ssreddy555 on 2023-05-14
Does this pertain to the default onscreen keyboard?
I have installed another onscreen keyboard called "onboard" keyboard. I don't want to uninstall this one. I want to remove the default one.

---

### Post by coffeecat on 2023-05-14
@ssreddy555, I believe your post immediately preceding this one was responding to a post which has now been removed. It was from a spammer who was simply copy-pasting ChatGPT output. You can ignore it as being worthless.

---

