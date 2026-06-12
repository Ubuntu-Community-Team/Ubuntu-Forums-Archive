---
title: "Eliminate Sign In Password Can't Be Done?"
date: 2020-06-23
forum: General Help
---

### Post by mawil10132 on 2020-06-23
I've been using Ubuntu off and on for several years as common user. About a year ago installed on a new Dell for daily use.  I'm retired, have no children in the house, just I and my wife, I have no valuable data on my laptop. Simply use the laptop for social media and reading articles. I go back to the laptop many, many times per days, as I get up for this and that. What I finding is I'm spending a massive amount of time entering the initial password to get Ubuntu going again.  It is a tremendous waste of time. Through the years I've followed the multitude of advice on how to terminate the Sign In request for password and yet none have worked.  So what I'm asking is for a reply from an highly knowledgeable programmer of Ubuntu to tell me if it's really possible to have a PC that isn't locked after it sits idle too long and or after reboot.  To clarify I'm not talking about the master user password required to make major changes to the systems. So, is there a simple way through reinstalling Ubuntu or is there a way to modify the existing installed ubuntu 20.04?  Please don't guess, if you have actually done it I want to hear from you please.

---

### Post by ActionParsnip on 2020-06-23
Your "contemplating going back to Win10" threat, gives absolutely zero value to the question and doesn't make anyone want to help you any more or any less.

If you install an addon/extension like LastPass (free) to your browser and tell it to autologin for the session it will automatically fill in forms for you. You will need to teach it credentials initially through normal use but this will reduce as time goes by.

You will need a password set to log in as well as use for installing updates. You can enable autologin but you will need to authenticate to install updates. This will happen rarely once the system is setup (once a week) which is minimal.

---

### Post by mawil10132 on 2020-06-23
More of an obvious feeling of angst, with zero meaning of threat. Why you took it so personally confuses me. Who in their right mind would want to revert back to Win10!?  Ubuntu is the best thing to happen to computing since the keyboard, obviously. And thank your for you suggestion, which seems to indicate that it is impossible to do within ubuntu of not being forced into security that isn't wanted nor needed.

---

### Post by TheFu on 2020-06-23
Nobody here works for Canonical. Everyone is just a volunteer.  There aren't any "highly knowledgeable programmer of Ubuntu" here.  I did earn a living writing code for about 15 yrs, but was never paid to work on Ubuntu.  Heck, Ubuntu didn't exist for most of that time and we weren't allowed to use Linux at all in th

For the stated purposes, perhaps a ChromiumOS solution would be better? [https://www.neverware.com/](https://www.neverware.com/) is an option. There are a few others. These are browser-centric OSes like a chromebook, but will run on your existing laptop/desktop. They are fast.  The negatives for ChromiumOS based solutions is that most people would choose the easy way and give up all their privacy to google.  To each their own.  I used the "guest account" for 3 months to avoid ever connecting a device to a gmail account.

I suppose the Win10 stuff would make me less inclined to volunteer my effort to find a solution for anyone planning to dabble with Linux.  I've been trying to help people for 25 yrs. There was a period long ago when I'd try to convince them all the reasons why a Linux-based system was in their own interest, but that would fail 98% of the time.  Now I believe you can take a nightsider to the pond, but you can't force him to spawn.

It is unclear to me what ActionParsnip's suggestions have to do with automatic login and disabling the screen saver password prompt? Would love to understand that.

Anyways, the correct answer to your 2 questions are completely dependent on the Ubuntu Release being run 3 possible versions and the DE used. There are about 8 flavors per release.  Probably the easiest way to convey correct, accurate data to us about those things is by installing and running a program, inxi.

```
$ inxi -b
```

If you'd like to self-service, there is an "ubuntu desktop guide" for people using the main/default/pushed-by-Canonical Gnome3 desktop here: [https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)  look for automatic login for the password login solution and look for the screen saver settings for the system already running and logged into, but asking for password after lunch solution.  If you allow the system to hibernate or use standby, those may have specific settings around entering a password too.

[https://help.ubuntu.com/stable/ubuntu-help/user-autologin.html.en](https://help.ubuntu.com/stable/ubuntu-help/user-autologin.html.en) for 20.04
[https://askubuntu.com/questions/1117025/how-to-disable-screensaver-lock](https://askubuntu.com/questions/1117025/how-to-disable-screensaver-lock)  ... screen saver lock for 18.04.

The login, screen saver, standby and hibernation requests for passwords appear to be different settings.  But the DE and release you run may change that answer.

---

### Post by sudodus on 2020-06-23
If you install a program package, you get a tool that I think will help do what you want.

```

sudo apt update
sudo apt install gnome-system-tools

# and then run

users-admin

```

You get a line with [SIZE=3]'Password: **Asked on login**                 Change...'[/SIZE]

Click on Change... (It is actually a button, and after you enter your password you can change the setting, so that you will no longer need the password to get to the desktop environment.)

---

### Post by GhX6GZMB on 2020-06-23
@mawil, you'll need to be a bit more specific about which password challenges you'd like to eliminate:
1: the first login PW at boot/restart. This can be removed - you'll actually be asked about this feature when installing 20.04.
2: the PW after suspend or screensaver. This can also be removed by disabling the "Lock computer" feature.
3: the PW when issuing system commands (sudo). This will stay.

---

### Post by TheFu on 2020-06-23
> **ml9104 said:**
> @mawil, you'll need to be a bit more specific about which passwords you'd like to eliminate:

**Each of those is the same password, stored in the same DB.**  Only the purpose changes based on the current program.  

The login password is the only one, unless whole disk encryption is used or some program like a password manager demands something else.

---

### Post by GhX6GZMB on 2020-06-23
> **TheFu said:**
> **Each of those is the same password, stored in the same DB.**  Only the purpose changes based on the current program.  

The login password is the only one, unless whole disk encryption is used or some program like a password manager demands something else.

Agreed, my phrasing was not optimal. But we're talking about the purposes, not the PW itself. I've edited my post accordingly; it read as if there are different passwords.

And if the OP is annoyed about where and when to enter the PW, it's solvable in cases 1 and 2.

---

### Post by kneutron on 2020-06-23
BEGIN $HOME/bin/noscreensaver # don't forget to chmod +x it

```

#!/bin/bash


killall xscreensaver
xset s off 
xset dpms 0 0 0


if [ "$1" = "" ]; then
 setterm -blank 0 -powerdown 0 -powersave off
else
 setterm -blank $1 -powerdown $1 -powersave on
fi

exit;

```

--I also end up uninstalling xscreensaver and modifying the Power settings to Never turn screen off and Never suspend when plugged in.  HTH

---

### Post by HermanAB on 2020-06-24
Everyone find passwords to be a pain in the neck and if you are the sole user of a machine, then it can feel like a useless burden.

The main problem is what happens when your machine is stolen.  At that point, you are suddenly not the only user anymore.

I had a laptop stolen about 20 years ago and since then I encrypt everything and use very long passwords...

---

### Post by TheFu on 2020-06-24
BTW, solving the 3rd "password problem" is also possible, though about the worst idea in the universe of Unix security.

---

