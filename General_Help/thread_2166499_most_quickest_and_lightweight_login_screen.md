---
title: "most quickest and lightweight login screen?"
date: 2013-08-09
forum: General Help
---

### Post by physman2 on 2013-08-09
So I use lxde and lubuntu and the login screen when I first turn on my laptop looks nice, except I don't really need / want a visually appealing login screen. I just need something which will prompt for a password. I want a really 'lightweight' login screen which doesn't take long to load (I know that the original lubuntu login screen doesn't take that long to load in the first place, but I just want something even more quicker).. how would I go about doing so? Is there a basic 'login screen theme' which I can somehow install?

What would be ideal for me is just the command prompt / shell prompting me for my password, would that be possible?

---

### Post by SweetAurora on 2013-08-09
Yes, command prompt will be the lightest, but it assumes you only have one desktop enviroment. The next step up would be XWM, X Window Manager which is a basic a gui you can get. You also have WDM (WINGs Display Manage) and SLiM (Small Log-in Manager) .

---

### Post by physman2 on 2013-08-09
> **kitsuneinari78 said:**
> Yes, command prompt will be the lightest, but it assumes you only have one desktop enviroment. The next step up would be XWM, X Window Manager which is a basic a gui you can get. You also have WDM (WINGs Display Manage) and SLiM (Small Log-in Manager) .

Hm, what do you mean by 'but it assumes you only have on desktop environment'..
don't I already only have one desktop environment? How would I make it prompt me for my password in command prompt at start up?

---

### Post by ibjsb4 on 2013-08-09
I believe your running lightdm as a display (login) manager.  There are several to choose from.

[http://ubuntuforums.org/showthread.php?t=2112818](http://ubuntuforums.org/showthread.php?t=2112818)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=lightweight+display+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2Fresults%2F%3Fcx%3D006238239194895611142%3Au-ocqbntw_o%26q%3Dlightweight%2Bdisplay%2Bmanager%26sa%3DSearch%26cof%3DFORID%3A9](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=lightweight+display+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2Fresults%2F%3Fcx%3D006238239194895611142%3Au-ocqbntw_o%26q%3Dlightweight%2Bdisplay%2Bmanager%26sa%3DSearch%26cof%3DFORID%3A9)

---

### Post by physman2 on 2013-08-09
> **ibjsb4 said:**
> I believe your running lightdm as a display (login) manager.  There are several to choose from.

[http://ubuntuforums.org/showthread.php?t=2112818](http://ubuntuforums.org/showthread.php?t=2112818)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=lightweight+display+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2Fresults%2F%3Fcx%3D006238239194895611142%3Au-ocqbntw_o%26q%3Dlightweight%2Bdisplay%2Bmanager%26sa%3DSearch%26cof%3DFORID%3A9](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=lightweight+display+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2Fresults%2F%3Fcx%3D006238239194895611142%3Au-ocqbntw_o%26q%3Dlightweight%2Bdisplay%2Bmanager%26sa%3DSearch%26cof%3DFORID%3A9)

hm, but without changing the display manager, how would I just change the login screen to a shell which prompts for a user name and password? Is there a way to make it so that when the laptop starts up, the shell prompts for a password and when I sign in, then it just displays the normal lubuntu desktop which I have? I just want to change the start up.

---

### Post by DuckHook on 2013-08-09
The biggest part of boot delay is not the display manager overhead, but the modules, services and various initializations of the boot process. You will get much further eliminating unnecessary cruft from your system than changing display managers. For example, if you don't use bluetooth, then blacklisting the module (which otherwise automatically loads) will cut down on load delay. You must be careful not to disable services that your system needs. Some people have been known to disable networking or worse. Can't give you general instructions because every system is so different, but Google for various suggestions to fine tune performance.

---

### Post by ibjsb4 on 2013-08-10
> but without changing the display manager, how would I just change the  login screen to a shell which prompts for a user name and password?

This is all that I can think of.
[https://wiki.ubuntu.com/LightDM#Configuration_and_Tweaks](https://wiki.ubuntu.com/LightDM#Configuration_and_Tweaks)

DuckHook has a good point, better to tweak your kernel.

And as mention SLiM is a good lightweight DM.  And if I remember right XDM was another good one.

---

### Post by Cheesemill on 2013-08-10
I posted instructions on how to boot into a command-line login prompt in your other thread yesterday...

[http://ubuntuforums.org/showthread.php?t=2166148](http://ubuntuforums.org/showthread.php?t=2166148)

---

