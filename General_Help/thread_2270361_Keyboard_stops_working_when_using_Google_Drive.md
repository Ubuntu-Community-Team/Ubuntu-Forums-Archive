---
title: "Keyboard stops working when using Google Drive"
date: 2015-03-22
forum: General Help
---

### Post by temporos on 2015-03-22
Every time I use Google Sheets (the spreadsheet function in Google Drive) my keyboard will suddenly stop working entirely. Sometimes, this happens immediately after loading the spreadsheet. Other times, it takes up to a couple minutes to happen. The only way to get the keyboard working again is to close out of all Chrome/Chromium-based applications, and then restart them. Since the keyboard doesn't work, I lose any unsaved data when I close (online forms, anything in Docs, etc.).

Possibly due to the same issue, I've noticed that sometimes when I type in the Chrome browser (outside of Google Docs), the things I type will come out scrambled. For example, if I type "hello," it might appear on the screen as "elhol." O_o

Has anyone else experienced this? I have searched both these forums as well as Google, and I can't find anything even remotely similar to this issue.

OS: Lubuntu 14.04
Browser: Google Chrome [COLOR=#000000][FONT=monospace]41.0.2272.89[/FONT][/COLOR][COLOR=#000000][FONT=monospace] ([/FONT][/COLOR][COLOR=#000000][FONT=monospace]Official Build[/FONT][/COLOR][COLOR=#000000][FONT=monospace])
Hardware: ASUS EeePC 1005HA[/FONT][/COLOR]

---

### Post by temporos on 2015-03-28
Anyone?

---

### Post by temporos on 2015-04-09
Last bump. Anyone know anything about this?

---

### Post by tjiagoM on 2015-04-10
Have you tried a different browser? Maybe could be some problem with the browser specifically in Lubuntu...

---

### Post by patrick.gruetter on 2015-04-11
Hi

I had a similar problem in Kubuntu. I now switched my keyboard model from "generic-something..." to "Logitec generic" as I have a Logitech keyboard.
So far, I was able to edit in Google drive again. I also experienced keys getting mixed up, especially when I type fast and the system is under load. After switching the keyboard type, this problem also seems to be gone.

Hope that solves it for you too ?

Cheers

---

### Post by peryton6 on 2015-05-29
Sorry, what do you mean by "I switched my keyboard model?" Did you make the switch in firefox settings? System settings?

I just installed ubuntu and in trying to use gchat and drive am having the same issues as OP.

---

### Post by peryton6 on 2015-05-29
Ok, actually I did a little searching and found this thread:
[http://askubuntu.com/questions/360696/keyboard-not-working-100-after-ubuntu-13-10-upgrade](http://askubuntu.com/questions/360696/keyboard-not-working-100-after-ubuntu-13-10-upgrade)

The solution within worked for me and is as follows:
GO TO:
  1) System Settings > Language Support, or you can hit Super (Windows key) to open the Dash, then type Language Support
  2) At the bottom part find "Keyboard input method system"
  3) Switch between "Default", "IBus" and "None". It may be different in your case, so try each one out. Start with option None.
  4) After making the change, you need to restart for the settings to take effect.
  Below is a screenshot.
  [IMG]http://i.stack.imgur.com/StKfW.png[/IMG]

Hope this helps!

---

