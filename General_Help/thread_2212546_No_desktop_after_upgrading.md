---
title: "No desktop after upgrading"
date: 2014-03-21
forum: General Help
---

### Post by Chris62 on 2014-03-21
Hi,

I have just done an online upgrade of my installation of Lubuntu 12.04 to the latest version and although everything ran without any error messages or other problems, I found when I rebooted at the end of the process   that I did not have a desktop anymore. However, when I right-click on the space that should be the desktop that appears after boot up I get a menu which includes thing like the internet and file manager and system if I select 'internet' and then 'Firefox' it runs correctly and I can access the net. I can get a terminal by doing CTRL+ALT+T. So, it appears that I have a functioning system that just lacks the desktop.

Could someone suggest a way of getting the desktop back, please?

---

### Post by Dreamer Fithp Apprentice on 2014-03-21
Sounds like you've booted to Openbox rather than Lubuntu.  Lubuntu runs on top of Openbox so Openbox is always there as an option in Lubuntu. Try typing in a terminal```
openbox --exit
``` and then the enter key. That should log you out without the trouble of completely rebooting from scratch. Then study the login screen. I forget what graphical login manager (usually somewhat misleadingly called a "display manager") Lubuntu uses by default but somewhere on that screen should be a dropdown menu that lets you choose the session type. Choose "Lubuntu" and you should get the UI you were expecting when you log in. You can choose either when you log in. Try the openbox some. It takes some getting used to but I like it better. I'm an ex-Lubuntu user, now using plain openbox.

---

### Post by Chris62 on 2014-03-22
Hi and thanks for your message. I did what you said > openbox --exit but it didn't work; nothing happens at all when I do that. Something seems to have happened to the system since I shut the computer down last night in that I can only log on now as a guest. If I try and log on as me then it will  not accept my password but the guest account accepts my password instead.

There is a drop down list at the top right of the screen and Lubuntu has a dot beside it but selecting anything else does nothing. I can't see what else to do other than delete Lubuntu and re-install it, which I am reluctant to do. Have you any other ideas, please?

---

### Post by steeldriver on 2014-03-22
Does it reject your password with a message (such as "login incorrect" or whatever), or just silently return to the login screen?

---

### Post by Chris62 on 2014-03-23
It does not give any message; it just silently returns me to the login screen

---

