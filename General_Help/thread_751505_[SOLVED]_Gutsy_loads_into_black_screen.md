---
title: "[SOLVED] Gutsy loads into black screen"
date: 2008-04-10
forum: General Help
---

### Post by mahasmb on 2008-04-10
I'm on Gutsy Gibbon (7.10)

Whenever I log into Ubuntu, all I get is a black screen, with a pointer and my two Gdesklets showing up. I have no terminal and I guess it's Gnome that's failing to load up. So I can't use my computer at all. I have to log out, and log in under "Fail safe GNOME" just to be able to use my computer as I am now. Any idea what my problem is and how I can fix this?

I have tried 

```
sudo dpkg-reconfigure gdm
```
and
```
sudo dpkg-reconfigure xserver-xorg
```

Neither have helped.

---

### Post by mahasmb on 2008-04-10
I'd also like to note that I can still move my mouse around, and I can tell that the computer connects to the internet because my GoodWeather Gdesklet displays the weather instead of "not connected."

I've had this problem for about two weeks now.

---

### Post by Crafty Kisses on 2008-04-10
> **mahasmb said:**
> I'd also like to note that I can still move my mouse around, and I can tell that the computer connects to the internet because my GoodWeather Gdesklet displays the weather instead of "not connected."

I've had this problem for about two weeks now.

Hmmm. while at the screen press the following: ```
Ctrl+Alt+F2
```
Then type: ```
startx
```
After that what happens?

---

### Post by mahasmb on 2008-04-11
IT WORKS AGAIN!

I'm not sure exactly what helped. But I read somewhere that if you logged into root and then logged out again (without rebooting) and then logged in again with your username that that should fix it for some reason.

So I restarted my computer and booted into one of the "recovery" kernels so I was logged in as root. I restarted Gnome as root. 

```
sudo /etc/init.d/gdm restart 
```

Gnome loaded up fine. Then I clicked Ctrl+AltF1 which took me back to the terminal. I typed in

```
exit
```

Which logged me out. Then I logged in as a normal user and it worked.

I may have done the above differently. Can't quite remember. But it should hopefully work for anyone else.

Also, I went to System > Preferences > Session (while logged in under "Fail Safe Gnome")

I clicked on the Session Options tab and UNCHECKED "Automatically remember running applications when logging out".

Also, I made sure that when I had abosulely no programs open that I clicked on "Remember currently running applications". So that it would save the currently running applications I had (which were none).

Like I said, I assumed the problem was because of scripts that were running or applications that were trying to open up as Gnome loaded. Which would explain why Failsafe Gnome still worked fine. Then again I could be wrong. It's been a while and I've learned quite a bit about Ubuntu, Gnome and Linux but I am no means an expert, yet.

I hope this'll help anyone who has the same problem I had. I don't know which of the above worked, but I suggest you try both.

Thank you for your help Codename. I really appreciate it :) .

---

