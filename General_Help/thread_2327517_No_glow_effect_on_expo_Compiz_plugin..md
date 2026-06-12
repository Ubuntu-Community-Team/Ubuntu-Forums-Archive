---
title: "No glow effect on expo Compiz plugin."
date: 2016-06-11
forum: General Help
---

### Post by acutbal on 2016-06-11
Hello!!


I have a problem with Compiz and Ubuntu 16.04, it's silly but it bothers me a lot. The problem is with Expo plugin, for whatever reason doesn't load well when the session starts so the orange frame indicating the active workspace doesn't appear.


I've tried everything, reset compiz with different commands, reset unity, reinstalling compiz, change some settings in CCSM, nothing works. The most I get is activate it for the current session by disabling/enabling the Expo and Unity plugins from CCSM, but if I log out or reboot again fails.


The strange thing is that for a few weeks I had installed Ubuntu 16.04 Mate and had the same issue, then there was a Compiz update which seemed that fixed it. Back to Ubuntu 16.04 and again the same issue...:(  From Ubuntu 11.04 until 15.10 I've never had this problem.&#65279; That's because I think that's a occasional issue.

I've also opened a bug in Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1575183](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1575183)


Thanks and regards!!&#65279;

---

### Post by acutbal on 2016-06-13
[COLOR=#333333][FONT=monospace]Hi!![/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I've done two little videos where you can see what I mean:
[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace][https://youtu.be/Oz_qtyYTTMw](https://youtu.be/Oz_qtyYTTMw)
[https://youtu.be/GgrLlwR3Zls](https://youtu.be/GgrLlwR3Zls)
[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Apologize for its quality, I only have my phone...[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Best regards!![/FONT][/COLOR]

---

### Post by CantankRus on 2016-06-13
Does the same happen in the guest account or a newly created user account?
Does running "compiz --replace",  fix when outline disappears?

---

### Post by acutbal on 2016-06-13
> **CantankRus said:**
> Does the same happen in the guest account or a newly created user account?
Does running "compiz --replace",  fix when outline disappears?

Thanks for your response!

Yes, the same happens with the guest account. The command fix the issue but it's only temporal, after logout and login again or reboot the laptop the issue is still there.

Regards! :D

---

### Post by CantankRus on 2016-06-13
It's hard to pin down these little compiz issues.
Perhaps in startup applications you can add....
```
sh -c "sleep 10 && compiz --replace"
```
to reload the window manager.

---

### Post by acutbal on 2016-06-13
> **CantankRus said:**
> It's hard to pin down these little compiz issues.
Perhaps in startup applications you can add....
```
sh -c "sleep 10 && compiz --replace"
```
to reload the window manager.

I'm going to try now, I'll let you know quickly.

Best regards! :D

---

### Post by acutbal on 2016-06-13
> **CantankRus said:**
> It's hard to pin down these little compiz issues.
Perhaps in startup applications you can add....
```
sh -c "sleep 10 && compiz --replace"
```
to reload the window manager.

PD: I apologize for my English, it's not my language... :redface:

It works more or less... :D  After this command plugin Expo works as expeected but now seems that the desktop doesn't start well, I've to open Nautilus to see "Ubuntu Desktop" in the status bar:

[IMG][IMG]http://i.imgur.com/VeKqDYs.png[/IMG][/IMG]


Best regards and 1.000.000 thanks for your help!! :D

---

### Post by CantankRus on 2016-06-13
About the best I can suggest. 
Compiz has always had these little glitches. 
Clicking on the top ubuntu icon in the launcher brings back "Ubuntu Desktop" text here.

---

### Post by acutbal on 2016-06-13
> **CantankRus said:**
> About the best I can suggest. 
Compiz has always had these little glitches. 
Clicking on the top ubuntu icon in the launcher brings back "Ubuntu Desktop" text here.

Yes, and I really appreciate your help, I prefer your solution rather than do a Compiz --replace every time I boot my laptop. It's weird because with Ubuntu 14.04.x and 15.10 I hadn't had any problems with Compiz.

Anyways, thank you very much again!! :D

---

### Post by mc4man on 2016-06-13
Seems like a bug, it's 100% repeatable here, but not on an install I've never really used. So maybe it comes about thru use of some sorts.
What's odd is the glow always returns here if I log out/in, then is gone on a fresh boot or restart. (and a log out/in returns it.
I blame everything inexplicable in 16.04 on systemcrapd.

---

### Post by acutbal on 2016-06-14
> **mc4man said:**
> Seems like a bug, it's 100% repeatable here, but not on an install I've never really used. So maybe it comes about thru use of some sorts.
What's odd is the glow always returns here if I log out/in, then is gone on a fresh boot or restart. (and a log out/in returns it.
I blame everything inexplicable in 16.04 on systemcrapd.

Yes, it's a weird bug... Please, if you have this bug, could you mark as affected in Launchpad? It would be useful:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1575183](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1575183)

Thank you very much!! :D

---

