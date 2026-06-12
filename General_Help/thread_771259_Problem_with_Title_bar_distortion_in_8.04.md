---
title: "Problem with Title bar distortion in 8.04"
date: 2008-04-27
forum: General Help
---

### Post by toolfreakuna on 2008-04-27
Hey guys,

This is a problem I have actually had with all releases of Ubuntu, and I wanted to know if anyone had a clue what is going on. After installing Ubuntu and enabling the Nvidia restricted drivers through System -> Administration -> Hardware Drivers, I can get Compiz effects up as high as I want. The only problem I have is that sometimes the title bars flicker, as I have shown in the below screenshot. Any suggestions?

EDIT: This problem seems to disappear as long as the window isn't maximized. Just a side note.

---

### Post by enchantedsky on 2008-04-27
I have the same problem with my Nvidia card, and there is a fix in Compiz-Fusion for Window titlebar problems:

1) Go into Add/Remove programs, get a program called "Advanced Desktop Effects Settings". Install it, it lets you control Compiz-Fusion

2) Go into System --> Preferences --> Advanced Desktop Effects Settings

3) On the left side of the window for Advanced Desktop Effects Settings, click on Utility

4) Click on Workarounds

5) The panel which pops up helps you fix various window problems you might be having with Compiz-Fusion. For instance, to fix your window titlebar problem, you'd want to check off "Firefox Windows Fix" and "OpenOffice Menu Fix". Experiment with different settings to see how your window behavior changes, and see if it fixes your problem.

Now, I mentioned in the first line of my post here that I have the same problem as you. What I've found is that this solution only *reduces* window titlebar distortion, but doesn't completely remove it. Once in a blue moon, you may see your titlebar distort, which I hope is fixed in a future Compiz update.

---

### Post by FuturePilot on 2008-04-27
Known bug
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508")
It only effects the Human, Clearlooks, and Glossy Metacity themes. Look here for a workaround.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508/comments/114]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508/comments/114")

---

### Post by toolfreakuna on 2008-04-27
Okay, I did both of these, but the problem persists. I guess it's just a bug. Oh, and I'm using Blubuntu look, by the way, but it does the same in Human, Clearlooks, etc.

---

### Post by FuturePilot on 2008-04-27
The workaround that someone posted will only work for the Human Metacity theme. I'm pretty sure the Blubuntu Metacity theme is almost identical to the Human Metacity theme.  You can probably perform the same tweak on Blubuntu also.

---

