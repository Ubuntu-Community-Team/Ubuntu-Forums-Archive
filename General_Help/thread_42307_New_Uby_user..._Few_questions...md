---
title: "New Uby user... Few questions.."
date: 2005-06-16
forum: General Help
---

### Post by Bandit on 2005-06-16
Hello Everyone,
Some of you may reconize me from the SuSE forums.
I have been running SuSE for the past 5 years.
I decided to run Ubuntu 5.04 for a while and expand my knowledge more.
I have the 2 or 3 questions.

How do I login as Root?
I go to put my PW in and all I get is Sorry??

Is it good to install the new nVIdia drivers 1.0-7664 for my FX5200?
I play UT2004 often.

Does Unreal Tourney 04 install well and stable.

Thanks,
Joey :grin:

---

### Post by intangible on 2005-06-16
I play UT2004 quite often with the nvidia drivers from ubuntu and so far, no problems here.  Here's a tutorial: [https://wiki.ubuntu.com//BinaryDriverHowto](https://wiki.ubuntu.com//BinaryDriverHowto)

To enable root, just assign it a passwd: **sudo passwd root**.
In Ubuntu, most tasks should be handled by just prefixing the command with **sudo** instead of logging in as root, it's a good habit to use.  (Don't worry, sudo will cache the password so you don't have to type it everytime if doing multiple commands).

 I usually just use **sudo sh** if I need to perform a quick little task instead of enabling root.  You can find a root terminal under **Applications->System Tools->Root Terminal**

---

### Post by tread on 2005-06-16
>  sudo will cache the password  for about 15 minutes. I was a bit annoyed at the no-root business initially, but I kept it and now I much prefer using sudo.

---

### Post by Bandit on 2005-06-17
Kewl thanks,
I got the video card working good.
I really wanted to install the newest drivers cuz I am trying to figure out why UT2004 keeps crashing on me. It crashes even with updates on both SuSE 9.3 and Uby 5.04. The only thing I havent did was try the newest drivers.
I tried to install them the other day on SuSE 9.3 like I always do, but for some reason the driver install didnt take. Which was weird cuz I never had any problems before doing this.
So I decided to take adavatage of the situtation and use it as a excuse to install Ubuntu again. So far I am very very impressed.

I got UT2004 installed. It was pretty easy. I just had to do it just like I do on SuSE.
export SETUP_CDROM=/media/cdrom0 <--I think this is right anyway. I keep it wrote down :)

One more question.
How can I drop down to straight console mode from the GDM login and leave xwindows. On SuSE I would just set it to boot into console in YaST.

Thanks again,
Joey

---

### Post by bored2k on 2005-06-17
[QUOTE=Bandit]
One more question.
How can I drop down to straight console mode from the GDM login and leave xwindows. On SuSE I would just set it to boot into console in YaST.

Thanks again,
Joey[/QUOTE]
Press ALT+CTRL+F1 (through F6).

---

### Post by Bandit on 2005-06-17
[QUOTE=bored2k]Press ALT+CTRL+F1 (through F6).[/QUOTE]
 That still leaves X running. The install script will still tell you to shut it down befor continuing and will cuase the install script to stop. 
I tried that before :D

---

### Post by wylfing on 2005-06-17
Do like bored2k says. Hit Ctrl+Alt+F1 to drop to a console, then kill X with
```
sudo killall gdm
```
When you want to start X again, just
```
sudo /etc/init.d/gdm restart
```
Rebooting your computer is for Windows. Don't do it.  :)

---

### Post by desdinova on 2005-06-17
Actually the best method is

init 1

then to get back

init 2

---

### Post by desdinova on 2005-06-17
to the OP 

you want to bookmark

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

