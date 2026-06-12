---
title: "new to this"
date: 2008-02-18
forum: General Help
---

### Post by Adam105 on 2008-02-18
[LEFT]Ok so i am completely new to this Ubuntu. I went to do updates a while ago and it frose or went to a black screen so i had to close it down manually and then restart. any ways when i restarted and went back into the updates i got this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


So i wen to to some other forums and asked what to do and was told to enter this into the termanil or command line in my case the termanil cause im using gnome.

$sudo dpkg --configure -a 

So i did i opened the termanil and i entered the above information and got this:

adambalan@ubuntuAdam:~$ $sudo dpkg --configure -a 
dpkg: requested operation requires superuser privilege

 

So What am i suppose to do?
I have tried entering a password and it tells me the bash file is not reconised or something...I need detailed steps to fix this please

Oh and I am the only one who uses this computer so i am like admin[/LEFT]

---

### Post by Adam105 on 2008-02-18
Ok so i really need some help with this....
If any one has suggestions?

---

### Post by knutschr on 2008-02-18
Were you asked for your password?

You could try this:
```
]sudo bash
```

After typing your password it should change to root account.
Then try without sudo
```
dpkg --configure -a
```
```
su adambalan
```

---

### Post by strabes on 2008-02-18
Your problem is that you put a "$" in front of the command. When people tell you to run something and it has a dollar sign in front of it, the "$" just indicates that what follows is a command to be entered into terminal. (Notice the $ after the terminal's prompt). The actual text you should enter/paste into a terminal is:```
sudo dpkg --configure -a
```

Hope this helps.

---

