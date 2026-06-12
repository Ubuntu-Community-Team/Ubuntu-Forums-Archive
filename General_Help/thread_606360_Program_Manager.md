---
title: "Program Manager"
date: 2007-11-07
forum: General Help
---

### Post by illuminaris on 2007-11-07
Does Ubuntu have a built in tab manager that I'm not aware of? It's extremely frustrating that programs just disappear when you minimize them and you have to go through all sorts of menus just to bring the window back. I've used three different tools that are supposed to supplement this, it seems, but haven't liked any of them.

Program Manager:
The tool "Program Manager" that I got from Add/Remove Programs is nice in some ways, but overall, having to pop it up every time i want to switch between windows is very frustrating and everytime a new window comes up you have to bring Program Manager back up by opening a whole new one, etc. It's a tad ridiculous.

Emerald/Avant:
I'm not sure which one of these gave you the little menu at the bottom that shows all your currently running programs, but, I didn't like that either. It constantly caused weird errors like changing the customization of my eye-candy and so on. Not to mention it made my usable screen a LOT smaller by about 10% which I wasn't too happy with.

AllTray:
This is closer to what I am looking for. Something that just places icons in a menu so you can click back and forth between the windows, except, you have to manually dock each window individually before it will show up, which means opening the Alltray program then clicking on the window every time you want to be able to control it. Also a lot of extra work that seems totally unnecessary.

If there are no better options, I'll live, and I realize this is a lot of complaining, but, I was really hoping there was something out there that's more applicable for just switching back and forth between multiple windows without all the hassle. Any ideas?

Thanks for your patience.

---

### Post by qamelian on 2007-11-07
Not exactly sure what you want because there is a task bar called window list that displays currently running programs on the bottom panel. Even when an app is minimized, there will be a button for it on the bottom panel unless you have removed the window list applet.

---

### Post by keyboardashtray on 2007-11-08
Well, I think you must mean the close button - that quits (most) programs.

You want the third button from the top right to minimize most. (like Windows)

UNLESS: like qamelian said, perhaps you removed the window list applet.

By default, it is on the bottom task bar, to the right of the show desktop button.

Go to your bottom panel (or where ever you want it) right click, select "add to panel" and  select "Window list" from under Desktop and Windows. This would be the style you are familiar with from windows. There is also ""Window Selecter" which is a little different, if you wanted to try that out intead.

So do that first, and see if that gets it the way you want it.

Alltray is more useful for getting something to not occupy a slot on your window list, for programs you want to run in the background (for example, an email client). They would shoot into your notification area, instead of your Window List. If you want an easier way to Alltray something, add alltray to the top panel. (Right click alltray in your menu and select add to panel). Then you would just click the alltray button then the window to put in the tray.

If you want a program to start *when you boot* and go directly to the notification area, you will need to set up a quick command in sessions. System>Preferences>Sessions

Then click the Add button, and type in the command: alltray program (and program is the program you want alltrayed)

---

### Post by illuminaris on 2007-11-14
I'm a tad bit confused. What bottom panel are you talking about? I have no bottom panel. I'm running 7.10 Gutsy and was previously running Fiesty. I have never seen a bottom panel except when using Emerald or whatever that program is.

Can you please explain how to create a panel at the bottom as well? I only have one at the top. Thanks.

---

### Post by keyboardashtray on 2007-11-14
Right click your existing panel and select "Add new panel".

You can drag your new panel around to wherever, and put whatever you want on it. It would seem you deleted the bottom panel somewhere along the way, but by default, it had the show desktop button, to quickly minimize your windows, the window list, which is what you are looking for now, a desktop switcher, and a trash can. You can put whatever you want there, but that is what is originally on if you want to set up what it would look like by default.

In case you want to know more about panels [https://help.ubuntu.com/7.04/user-guide/C/panels.html](https://help.ubuntu.com/7.04/user-guide/C/panels.html)

---

