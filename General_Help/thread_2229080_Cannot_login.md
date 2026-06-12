---
title: "Cannot login"
date: 2014-06-11
forum: General Help
---

### Post by kakadu90 on 2014-06-11
Dear Fellow Ubuntu Users.

I cannot login to my Computer anymore.

I think this does not apply to me since I do not have a graphics card:
[http://ubuntuforums.org/showthread.php?t=2228650&highlight=login](http://ubuntuforums.org/showthread.php?t=2228650&highlight=login)

When I login, it shows a scrambled screen (has been this way since i upgraded to 14.04) and then throws me back to login.

I can login via Ctrl,Alt and F1.

I apparently didnt have a Xorg.conf and I tried chmod -R $User... as it was proposed in other Threads, doesnt work.

Here is the pastebinit: paste.ubuntu.com/7627717.

I am running 14.04 with the latest updates on a Thinkpad X201t (Tablet-Version with Wacom Pen...).

Any help will be appreciated, I need that computer. I am currently writing my Bachelors Thesis and am running a VM-XP on it for programming PLCs.
(All Data backed up three times over, dont worry).

I have partitioned the drive to separate /usr, /home partitions. When I try to cd them, I get a permission denied error.

EDIT:
I noticed I get thrown back to login screen only because my wwan prompts for the pin.

Wwan-card removed gives a screen with the default background which is rotated.

After about a minute I get thrown back to login screen.
EDIT end

Thanks in Advance
kakadu90

---

### Post by nknwn on 2014-06-11
The problem:
"everytime when i write my username and password,it will take me back to the username prompt"

The solution offered:
[http://ubuntuforums.org/showthread.php?t=2226406&p=13034505#post13034505](http://ubuntuforums.org/showthread.php?t=2226406&p=13034505#post13034505)

---

### Post by kakadu90 on 2014-06-11
This does not work, thank you though.

I noticed I get thrown back to login screen only because my wwan prompts for the pin.

Wwan-card removed gives a screen with the default background which is rotated.

After about a minute I get thrown back to login screen.

Any other suggestions?

---

### Post by steeldriver on 2014-06-11
Well... "can login, but desktop session dies almost immediately and returns me to the login screen" is a bit different from "cannot login"

What happens if you log in to a guest session? does that crash too? If not, it suggests something specific in your session (perhaps a corrupted ~/.config/monitors.xml file, based on the rotated input that you observed?)

---

### Post by kakadu90 on 2014-06-11
When trying to log in to guest the same thing happens.

---

### Post by nknwn on 2014-06-18
"Wwan-card removed gives a screen with the default background which is rotated." I don't understand that at all.
and no answers forthcoming on this forum.


Graphics drivers, Wwan-card drivers Maybe?

I'd be inclined to save my files and abandon Ubuntu 14 and reinstall the previous version.
In my experience Ubuntu 14 needs a higher specification of hardware than Ubuntu 12 for example.
Also, the Dash search in 14 is awful. Who wants all those 'opportunities to make a purchase' when you are looking for something on your own hard drive?

---

