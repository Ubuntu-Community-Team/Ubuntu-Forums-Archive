---
title: "Ubuntu does not start anymore.!!! Weird Problem...please help"
date: 2007-05-01
forum: General Help
---

### Post by Abhijit_T on 2007-05-01
I had a perfectly working installation of Ubuntu Feisty until yesterday night....no problems at all....i used synaptic to download Java Runtime Environment 6 and the Java plugin. While it was downloading i used 'shutdown' to set the computer to shutdown at a specific time(i gave enough time to finish downloading and installing)

```
sudo shutdown -P 01:30
```

I went to bed after this...waking up today i saw that the laptop had indeed shutdown. I booted up the laptop thinking nothing was wrong. The login screen appeared normally. I entered username and password...and then.....nothing!!!
The background which is displayed behind the splash screen just appears and then nothing happens. No splash screen....no desktop...nothing. The hard disk does not load anything...it just sits there. I hit Ctrl+Alt+Bkspace to get to the login screen again....tried it without XGL this time....same thing. Tried it in Failsafe Gnome...same thing.
I tried Failsafe Terminal, and atleast it showed the terminal window at the bottom right corner. But since this is such a random sort of problem, i have no idea what to do.

I need help really fast, because i'm going kind of crazy here....typing this from Windows...

PS: One thing i noticed what that if i let the screen stay for a minute or two after logging in, a greay window shows up at the top left...no titlebar or anything...just a grey box. When i move my mouse over it, it changes to a text select cursor

System Info-
Dell Inspiron 6400
Ati Radeon X1400
1GB Ram
Ubuntu 7.04 Feisty Fawn
fglrx+glx+beryl

Guys, I need help fast....please help me!!!

---

### Post by Abhijit_T on 2007-05-01
ok,fixed it myself...
 it was because i added this line to my /etc/network/interfaces-
```
pre-up ifconfig eth0 mtu 1450
```
removed it and it starts now, but turns out without that line half my pages don't load, so i added it again, and restarted, and it still loads :)

EDIT: i just started synaptic, and it told me i had a broken package....turns out it was java...so i installed it again....i was an ***, and had thought yesterday it would install without prompting, but it asks for license agreement....so maybe tht was the problem...

---

