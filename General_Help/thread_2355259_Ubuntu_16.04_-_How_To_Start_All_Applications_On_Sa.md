---
title: "Ubuntu 16.04 - How To Start All Applications On Same Screen, On Dual Screen Setting"
date: 2017-03-10
forum: General Help
---

### Post by AngelOfNorath on 2017-03-10
I was using my laptop, until I decided to connect it to my "old" (it's not really that old...) screen. At first, while I was using only the laptop, I had the problem where my launched applications appeared on top left side of the screen. Using CompizConfig Setting Manager I fixed that, or at least I thought I did. Now that I've  connect the second monitor another problem appeared, my applications, appear on the wrong screen.

Let me give you some details:


The Monitors Settings is:  External Monitor on the left [Full HD 1920x1080 - 23"], Laptop on the right[1366x768 - 15"]. (and there is no way this can change, consider it default)

Ubuntu from the old days until now (16.04, as other said in the many posts I searched) doesn't have an option of setting a default screen. It (Ubuntu) considers default the left screen no matter what.
The thing is, that I mainly work with my laptop which it is infront of me. That's my "main" screen. The other one is on the left, leveled up. So having to look up and drag the program to the laptop screen everytime I open a applications, it's really annoying and non-practical. The only "tricky" way I found is setting in >Displays my laptop screen on the left and the big one on the right. But the dragging and moving through the two monitors becomes tiring, since i have to move the mouse in reverse... I hope you understand what I am saying.

So even using compiz (Window Management > Place Windows > Mutli Mode Output) I can't find a solution. Am I missing something out? I would prefer a solution without extra scripts. But if I cannot avoid it...

---

### Post by vanadium on 2017-03-11
Strangely enough, there is no possibility to define your right monitor as your primary monitor in the graphical interface. It may however be possible to change your primary display using a command that configures xorg, see [here](http://askubuntu.com/questions/760942/set-primary-monitor-on-16-04). The simplest form of the command is "xrandr --output DP-4 --primary". You need to adapt DP-4 in this command by the actual code of your monitor. You can tell the codes of your connected (and not connected) outputs from the command "xrandr" without arguments. This command can be added in your autostart applications. 
I see, however, that you may also need to adapt the file .config/monitors.xml for this to work reliably. You may want to do some testing first without touching this file.

---

