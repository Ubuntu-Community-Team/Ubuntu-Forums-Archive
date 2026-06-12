---
title: "Autologin to Wrong User Account"
date: 2015-02-09
forum: General Help
---

### Post by Luxx on 2015-02-09
This isn't exactly a security issue for me, but could be if I shared my computer, and it isn't really a DE issue, so I didn't really know where to put this.

Whenever I reboot I am automatically logged into the secondary account on the computer. This seems to be Ubuntu's choice as I did not set that account as default.

I have the user accounts set up for different DEs. I only use the secondary account when updates break things and I need Unity to fix them. Unfortunately, this happens more frequently than I would like. I have gnome-session-fallback on my primary account. I need administrator priviledges on both accounts and prefer to have autologin on both accounts. This doesn't seem to create a conflict as one account has obvioulsy been selected as the default account, but how can I make it my primary account instead? It was booting into my primary account before. I don't know why this changed or how to get it back to the previous behavior.

I have looked for hours and found advice on changing usernames, user account images, changing session DE for the same user, etc. none of what I've found has really addressed my question and I'm not finding anything in the user accounts or groups settings that make a difference. Any help greatly appreciated.

---

### Post by ajgreeny on 2015-02-09
From the unity desktop use the Cog icon top-right ->System Settings ->User Accounts.
You will need to unlock the dialogue box, highlight the user in question, and turn off the automatic login there.

---

### Post by Luxx on 2015-02-10
Thanks. I'm not using Unity. Can't stand it. I have gnome-session-fallback in primary account and Gnome 3 in secondary account.
No cog, but I found system settings, but menu items were missing and I couldn't get to those settings. I had to do some gymnastics to get them back. I can't for the life of me remember what it was... 
That would actually be the "user accounts or groups settings" that I mentioned above that you were directing me to.

I was hoping there was a way to keep both accounts on autologin and have my primary account as the default instead of the secondary account, but maybe that isn't possible. I still don't know why it switched. Maybe it has something to do with GRUB. I keep losing my GRUB menu.

---

### Post by deadflowr on 2015-02-10
> I was hoping there was a way to keep both accounts on autologin and have my primary account as the default instead of the secondary account, but maybe that isn't possible. 

As you figured out, it isn't possible.
Only one user can be set to autologin at a time, typically it is which ever user is listed first alphabetically.

---

