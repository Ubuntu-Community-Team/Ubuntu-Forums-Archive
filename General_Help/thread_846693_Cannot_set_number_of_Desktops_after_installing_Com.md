---
title: "Cannot set number of Desktops after installing Compiz"
date: 2008-07-01
forum: General Help
---

### Post by CyberDude4819 on 2008-07-01
Alright, so I have had this problem twice now, once I install Compiz onto my Ubuntu, both Gutsy and the new 8.07, I am no longer able to control how many desktops I have and has defaulted to 2. First I thought that I screwed something up in the install since I was having some other issues so I just formatted and reinstalled my Ubuntu and immediately set my desktops to 4 and it worked fine. Once I installed Compiz I no longer had 4 desktops, only 2, and cannot get any more or less even than 2 - it is just stuck there. I can change the numbers to whatever I want, but it doesn't make a difference, just sticks on the 2 desktops.

[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

above is the guide I followed, and everything else seems to be working fine as I can use the cube effect to switch between the desktops, and all the other stuff is fine...so what could be doing this?

---

### Post by petzworld999 on 2008-07-01
If there are two boxes in the right of the bottom panel, right click on that and click preferences. Increase the number of workspaces. If there is not, right click on any panel and add a workspace switcher. Then, do the steps above.

---

### Post by CyberDude4819 on 2008-07-01
> **petzworld999 said:**
> If there are two boxes in the right of the bottom panel, right click on that and click preferences. Increase the number of workspaces. If there is not, right click on any panel and add a workspace switcher. Then, do the steps above.

I have already done that. It is already currently set to 4 but still only has 2. Like I said above it doesn't matter what number I have it set to after installing compiz. Pre-install it worked as it was supposed to.

---

### Post by CheeseEatingBulldog on 2008-07-02
If you are running compiz (desktop effects) you will only see one desktop on the bottom right, to add more install the advanced desktop settings package "compizconfig-settings-manager" by opening a terminal and typing

```
sudo aptitude install compizconfig-settings-manager
```

Now you can access it from your System-->Preferences menu

Here you can modify all the plugins to your hearts content, Click on the General options and select the desktop size tab, here you can add and remove desktops for the switcher.

---

### Post by CyberDude4819 on 2008-07-02
> **CheeseEatingBulldog said:**
> If you are running compiz (desktop effects) you will only see one desktop on the bottom right, to add more install the advanced desktop settings package "compizconfig-settings-manager" by opening a terminal and typing

```
sudo aptitude install compizconfig-settings-manager
```

Now you can access it from your System-->Preferences menu

Here you can modify all the plugins to your hearts content, Click on the General options and select the desktop size tab, here you can add and remove desktops for the switcher.

Ahh thank you. I had the manager installed but the only panel option I didn't check was the General Options, because that would make too much obvious sense. I knew there had to be something stupid and obvious I was missing. Thanks a ton!

---

### Post by jesuisbenjamin on 2008-08-09
Hey there i have quite a similar problem:

I have installed Compiz and Compiz Setting Manager and have now 2 desktops. I need only one desktop and no matter what i try to do in Compiz or in the Panel item, two desktops remain.

How can i change this? Thanks

---

### Post by CyberDude4819 on 2008-08-09
> **jesuisbenjamin said:**
> Hey there i have quite a similar problem:

I have installed Compiz and Compiz Setting Manager and have now 2 desktops. I need only one desktop and no matter what i try to do in Compiz or in the Panel item, two desktops remain.

How can i change this? Thanks

Same solution that worked for me. Open the Compiz Panel and goto General Options - Desktop Size and then drop the Horizontal Virtual Size down from 2 to 1 et voila!

---

### Post by jesuisbenjamin on 2008-08-09
And i had to _reboot_ of course #-o

Thanks

---

### Post by CyberDude4819 on 2008-08-09
> **jesuisbenjamin said:**
> And i had to _reboot_ of course #-o

Thanks

No problemo

---

### Post by jesuisbenjamin on 2008-08-09
Errr wait a minute... Now all my effects are gone. It's all been reset!
:confused:

---

### Post by jesuisbenjamin on 2008-08-09
Hey i found my answer so i am happy again :)

---

### Post by CyberDude4819 on 2008-08-10
> **jesuisbenjamin said:**
> Errr wait a minute... Now all my effects are gone. It's all been reset!
:confused:

O.o And the only thing you changed was the Virtual Desktop size? Sounds like something else either got changed, or it may not have loaded properly at start up.

---

### Post by Hyper Tails on 2008-08-20
I have the same problem to in kubuntu 
i installed compiz and no more than 2 desktops will come

---

