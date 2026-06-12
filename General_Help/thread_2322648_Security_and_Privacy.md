---
title: "Security and Privacy"
date: 2016-04-29
forum: General Help
---

### Post by Richard_Lorentz on 2016-04-29
Hi. Under Settings on my recently upgraded to 16.04 Ubuntu I only have Privacy (which has no tabs and only 4 switches -- Screen Lock, Usage & History, Purge Trash & Temporary Files, and Location Services) -- not Security & Privacy. Any thoughts as to why I only see Privacy and what I might do to get the Security part back?

Thanks!

---

### Post by QDR06VV9 on 2016-04-29
> **Richard_Lorentz said:**
> Hi. Under Settings on my recently upgraded to 16.04 Ubuntu I only have Privacy (which has no tabs and only 4 switches -- Screen Lock, Usage & History, Purge Trash & Temporary Files, and Location Services) -- not Security & Privacy. Any thoughts as to why I only see Privacy and what I might do to get the Security part back?

Thanks!
Can you be more specific?
```
sudo ufw enable
```
Will start and enable a firewall(iptables)
And this from [http://freerepublic.com/focus/news/3424292/posts?page=8](http://freerepublic.com/focus/news/3424292/posts?page=8)
> Perhaps the most exciting change in the newest iteration of Ubuntu is  that online search results in the dash — previously turned *on* by default — are now turned *off*  by default. This “feature” caused quite a bit of controversy when  Canonical introduced it in Ubuntu 12.10. It caused all searches — even  those where a user was searching for local files on his or her machine —  to return items from online searches. Since it was turned on by default  and without the express consent of the user, many considered it  spyware. Now that Canonical has, thankfully, turned online searches off by default, it is a non-issue. As *The Register* [described]("http://www.theregister.co.uk/2016/03/29/ubuntu_16_04_first_beta_review/") this change:

[INDENT]There  is one small tweak that will likely be getting a lot of attention in  this release – the online search features in Unity have been disabled by  default. 
[/INDENT]
And be sure you stay updated and current with security updates.

---

### Post by Richard_Lorentz on 2016-04-29
Indeed, the online search issue was the reason behind my post. Unfortunately, after running "sudo ufw enable", Settings still just shows me Privacy as described above. No Security & Privacy, no tabs, and therefore, no way to check the online search option.

---

### Post by deadflowr on 2016-04-29
Try reinstall unity-control-center:
```
sudo apt-get install --reinstall unity-control-center
```

---

### Post by Richard_Lorentz on 2016-04-29
I will give it a try. I'm 12 hours away from being in front of that machine again, but I will report back, hopefully with good news! Thanks for the suggestion!

---

### Post by mc4man on 2016-04-29
If previous suggestion doesn't work & assuming you're running Ubuntu - 
```
sudo apt purge activity-log-manager
```
```
sudo apt update
```
```
sudo apt install  activity-log-manager
```

---

### Post by Richard_Lorentz on 2016-04-29
I tried both and still just see "Privacy". Very strange and a little frustrating. Surely there are some other people seeing this?!

---

### Post by mc4man on 2016-04-29
> **Richard_Lorentz said:**
> I tried both and still just see "Privacy". Very strange and a little frustrating. Surely there are some other people seeing this?!
does seem odd, try logging out & into a guest session, then see whats in System Settings, ect.

Also try this way to open - 
```
gtk-launch unity-activity-log-manager-panel
```

A screenshot of System Settings may be helpful (focus on window, then Alt+PrtSc

---

### Post by Richard_Lorentz on 2016-04-30
Good detective work. The guest login showed Security & Privacy, so all is well there. Here is what I see with my usual login. What gives?

[added 2 minutes later]: Your command line approach also works! So it is possible to see Security & Privacy. I think you're getting close.  :)

---

### Post by mc4man on 2016-04-30
You are getting the control panel & privacy panel within for Gnome, not Ubuntu. So 1st. question is are you using, (ie. logging in to) Ubuntu (unity) or Gnome (gnome-shell or gnome-flashback)?

_If using Ubuntu/unity _then something didn't translate correctly during your upgrade. Just for a bit of info run & post this - 
```
ls /usr/share/applications |grep control-center
```

---

### Post by Richard_Lorentz on 2016-04-30
Yes, using Unity. Here is what [COLOR=#000000][FONT=Ubuntu Mono]ls /usr/share/applications |grep control-center gives:[/FONT][/COLOR]

gnome-control-center.desktop
unity-control-center.desktop

---

### Post by mc4man on 2016-04-30
> **Richard_Lorentz said:**
> Yes, using Unity. Here is what [COLOR=#000000][FONT=Ubuntu Mono]ls /usr/share/applications |grep control-center gives:[/FONT][/COLOR]

gnome-control-center.desktop
unity-control-center.desktop

So there are typically 3 ways to access the control panel or it's panels - 
Dash > search a panel name, like security, appearance, details, ect.
Right click on Desktop > Change Desktop Background
From the cog menu far right unity panel  > System Settings

So assuming the last one above is the biggest issue maybe try to remove what's it's opening. Then it'll either open the proper control panel or nothing will happen.
To test, in a terminal - 
```
sudo mv /usr/share/applications/gnome-control-center.desktop /usr/share/applications/gnome-control-center.desktop.bak
```
Then log out/in or reboot & see what happens..

---

### Post by Richard_Lorentz on 2016-04-30
You provided the necessary inspiration! I unlocked the cog icon from the launcher and then searched for Settings in Dash. Found Settings and System Settings. Settings is what I had. System Settings is what I wanted. Locked it to the Launcher and all is great now.

Thank you very much for your help. Now where is that "solved" button....

P.S. Forgot to mention: I loved your Alt+PrntScr trick. Never knew that one.

---

