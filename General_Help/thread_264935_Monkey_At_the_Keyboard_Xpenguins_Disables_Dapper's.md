---
title: "Monkey At the Keyboard: Xpenguins Disables Dapper's GUI!"
date: 2006-09-25
forum: General Help
---

### Post by mac57 on 2006-09-25
It is true that a monkey at the keyboard is the best tester of all. In this case, I am the monkey. I am new to Ubuntu and new to Gnome, but certainly not new to Linux - I have been using it for years, running under IceWM, KDE and of late, XFCE. However, when Ubuntu Dapper Drake came out, I decided to try it just like the designers intended - with Gnome. And since I am a Gnome newbie, I could be counted on to make every beginners mistake in the book, and I have. BUT, I did not expect any of those to totally screw up the GUI. BUT, one of them did. 

Dapper Drake comes with xpenguins, a classic bit of Linux silliness, which draws little animated penguins wandering all over your desktop. I used to use it a lot in my older Linux releases - it worked great under IceWM and was just fun. However, it really doesn't work worth a darn under KDE or XFCE. When I saw it included in Ubuntu, AND there was even a panel applet I was really pleased - xpenguins back again. Since there was a panel applet, I assumed it was fully supported.

WRONG! I downloaded both xpenguins and the xpenguins-applet and then right clicked on the panel, selected Add To Panel, and selected xpenguins-applet from the presented list. Instant freeze! Ubuntu was still happily chugging away in the background (I could click on the desktop and get a response, double click on icons I had on the desktop and so on, and all was well there) but the panel was frozen, hard. Of course the panel is where ALL the program launchers are, and critically, where the shutdown button is! I was stuck. The monkey had successfully frozen out the shiny new GUI simply by doing something that certainly LOOKED supported. 

I had to resort to a hardware reset to regain control. Now happily I am only an Ubuntu and Gnome newbie, not a Linux newbie. When I restarted, and the panel STILL froze, this time on startup, presumably as it tried to do whatever it was trying to do with xpenguins that froze it the first time, I hit CTL-ALT-F1 to get to a virtual terminal, and used apt-get to remove xpenguins. One reboot later and the panel started up with an error, offering to remove xpenguins from it, since it could not find it. I selected "OK" and all was well.

Two morals to this story. (1) stay away from xpenguins unless you REALLY know what you are doing, and (2) Gnome has a few critical weaknesses, and this is one of them! As the first of my newbie experiences with Gnome, I am somewhat put off. I have screwed up KDE and XFCE many, many times, but NEVER have I succeeded in completely killing the panel, or anything else, such that I had to resort to a restart. I think that Gnome may yet need some more robustness work.

This is NOT an attempt to start a flame war. Please do not write in to defend Gnome. I *am* a Gnome newbie, and I plan on sticking it out with Ubuntu as it came to me, Gnome and all, for a while, so as to get more experience with it. When I have used Gnome for a few months, then I will make an educated decision on whether I like it or not. For now, this is just a heads up for the user community.

---

