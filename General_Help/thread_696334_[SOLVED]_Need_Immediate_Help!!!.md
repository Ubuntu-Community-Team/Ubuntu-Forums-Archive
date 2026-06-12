---
title: "[SOLVED] Need Immediate Help!!!"
date: 2008-02-13
forum: General Help
---

### Post by lovhorror on 2008-02-13
You can tell I need immediate help immediately because it's in capslock and has three exclamation points.

My problem is severe.

First I have to inform you that I installed ubuntu only a week ago, and I love it. I do not, however, know how to run ubuntu without graphics (I don't know what term to use, but it's similar to microsofts dos screen).

Unfortunately that's the pickle I'm in. I turned off the graphical login (for reasons I'll state in  a minute) so now when I login it stays in this dos-like state. I don't know commands, or how to run things. What I need is a solution, a way to start the login with graphics and pictures, so I can get to my desktop and re-enable this feature.

Now, the reason I disabled it to begin with is that I switched the login screen to kubuntu, which I then realized I didn't like. So I went to system->administration and there was no login window option. I thought I could fix it somehow by disabling the login, I don't know what I was thinking.

Right now I'm running ubuntu from my install disk. Please, please help me.

---

### Post by lovhorror on 2008-02-13
Please?

I really don't want to have to reinstall ubuntu. Someone help me.

---

### Post by lovhorror on 2008-02-13
C'mon!

---

### Post by lovhorror on 2008-02-13
tl;dr How do I load the GUI from the CLI?!

---

### Post by seventhc on 2008-02-13
ok, boot up to where you get the black screen, type your user name hit enter
type your password ( you won't see any ***** or circles, it will appear as you arent typing, don't worry) just type your password then hit enter.
You will have a command prompt, when there type
```
startx
```that should get you back to your desktop. Then need to get it back to normal.

---

### Post by lovhorror on 2008-02-13
Oh thank you so much. I'm about to try it, if it works you're my new hero.

---

### Post by seventhc on 2008-02-13
well, then I hope it works :guitar:

---

### Post by lovhorror on 2008-02-13
Worked.

I love you.

---

### Post by seventhc on 2008-02-13
OK, but it isn't fixed yet, now we need to re enable the graphical login.
Do you remember where you went to disable it?
If we don't set it back you always have to run startx to get to your desktop.

---

### Post by lovhorror on 2008-02-13
Already re-enabled. System -> Administration -> Services

I thought disabling one of them would still let me login.

Do you think you could help solve my missing-application problem though. I have no option to change login screens any more.

---

### Post by seventhc on 2008-02-13
does your name show in the top panel?
If not right click on the panel and choose *Add to Panel* then add [I]Switch User.
[/I]Once thats there, you can right click on your name to get login options
Or were you using a different app for that?

---

### Post by lovhorror on 2008-02-14
"User Switcher" has quit unexpectedly.

Every time.

---

### Post by seventhc on 2008-02-14
Does this happen when you are trying to click on it? Please tell me what you are doing when this happens.
Also since enabling the graphical login you might want to log out, then back in, or do a reboot. Unless you've already done that, if so just let me know when that msg pops up.

---

### Post by lovhorror on 2008-02-14
when I go to add to panel and have add user switcher highlighted and click add it gives me that report.

I restarted/logged out and everything's working fine.

---

### Post by seventhc on 2008-02-14
OK, if everything is working fine, maybe mark this thread as solved.
Up top you will see Thread tools, click on that and there is an option to mark thread as solved.
:)

---

### Post by lovhorror on 2008-02-14
No, I still can't change the screen, but the GUI is working fine.

---

### Post by seventhc on 2008-02-15
tell me when you'll be on.
It's to hard to troubleshoot when your gone for the day/night.
I will try to help if I can, but it will be much more difficult if you only post once a day.
By that I mean it will be easier if everything is fresh in our minds.
(errors, what we tried, results, etc.)

---

### Post by lovhorror on 2008-02-15
I'm still in highschool so I'll be on 2:30pm - 4:30pm then work and I won't be back 'till 10-10:30.

---

### Post by seventhc on 2008-02-15
OK, No problem, I'll try to be here. :)

---

### Post by lovhorror on 2008-02-15
Okay, I'm here. I'll be on 'till 4-4:30.

"User Switcher has quit unexpectedly"
If you reload a panel object, it will automatically be added back to the panel.

If I click reload it does the same thing.

This happens when I try to add a user switcher to my taskbar.

---

### Post by lovhorror on 2008-02-15
Also, when I try to turn off my computer there's no option to turn off or restart. I'm so confused here.

---

### Post by lovhorror on 2008-02-15
Okay, I've got to go now. I'll be back sometime around ten. If there's a way I can contact either you or someone else who can help that'd be really nice because I've got a couple of other problems too. Perhaps send me your AIM, thanks.

---

### Post by strabes on 2008-02-15
What happens when you run the following command in a Terminal? (Applications > Accessories > Terminal)```
gksu /usr/sbin/gdmsetup
```

You should probably go into System > Preferences > Main Menu, and then in that window click on "Administration" and see if the "Login Window" option has been disabled. (it's disabled if it is unchecked).

---

### Post by airtonix on 2008-02-15
are you sure : 

> startx

 is the proper way to start the GDM?

ive always used and been told this is the proper way to start up the Xserver.

> sudo /etc/init.d/gdm restart

nd since you didnt use sudo before the orginal usage of startx, it probably means the xserver didnt start with proper access to the system

---

### Post by seventhc on 2008-02-15
> **airtonix said:**
> are you sure : 



 is the proper way to start the GDM?

ive always used and been told this is the proper way to start up the Xserver.



nd since you didnt use sudo before the orginal usage of startx, it probably means the xserver didnt start with proper access to the system
Well, startx is what I use in FreeBSD(not linux), Red Hat, and every other linux distro to get into the desktop environment. If I was wrong in saying so, sorry for passing along wrong info. It may very well be different in ubuntu, I just wanted him to be able to get to a desktop. But it would explain the errors.

I never even thought about using sudo or gksudo but thats a good point. Again it isn't something I've ever needed in other systems.
Sorry if I messed up:confused:

---

### Post by lovhorror on 2008-02-15
gksu /usr/sbin/gdmsetup

leads to it saying gnome manager is not running. Is that the issue?

---

### Post by lovhorror on 2008-02-15
sudo /etc/init.d/gdm restart

That says GNOME isn't the default display

---

### Post by lovhorror on 2008-02-16
Okay, I can login normally if I start in CLI and type sudo gdm but when I restart it starts in CLI again. I have gdm graphical login enabled, but the kdm is disabled. All I think I need now is to change gdm to default. If anyone knows how to do that you're my hero.

---

### Post by Shippou on 2008-02-16
Hello there...

Seems you like CLI (Command-User Interface)? Just joking... :)

Congratulations you have settled the problem. I was about to suggest startx but then it was already said,,, hehehehe...:)

Have a nice day... :)

---

### Post by lovhorror on 2008-02-16
Alright, I fixed everything. Thanks for your help everyone, it's much appreciated. Now, the quest to add music to my zen v plus. Haha.

---

