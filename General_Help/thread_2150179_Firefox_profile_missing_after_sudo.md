---
title: "Firefox profile missing after sudo"
date: 2013-05-31
forum: General Help
---

### Post by Garyu on 2013-05-31
Here's the thing: I am running Sage ([www.sagemath.org](www.sagemath.org)) and I installed it under /opt/ where it is run as the root user, and normal users logging on. Sage works great in itself, and when I log on it stores settings unique for each user logging on etc. However, when I start up Sage in the notebook mode, it automatically launches Firefox. And since Sage is run as root, this is equivalent as running sudo Firefox. Running Firefox as super-user is a common and known problem that then running it as a normal user will give an error message that the profile is missing or not accessible. There are a lot of answers on how to solve this, for example here: [http://ubuntuforums.org/showthread.php?t=2111189&highlight=firefox+profile+missing](http://ubuntuforums.org/showthread.php?t=2111189&highlight=firefox+profile+missing)

My problem is that I have tried all the suggested solutions. I have removed the ~/.mozilla directory. I have looked at the profiles.ini file. Nothing I do will result in anything else than this annoying error message. However, running "sudo firefox" works great, but I don't want to run firefox as a super-user. 

Normally, I use Chromium so it hasn't been an issue. But now I have a specific plugin (Zotero) that really wants to go through Firefox to run, and this is creating this problem that I have to make it work. **Every time I start my computer, firefox is started in sudo mode**, and then I shut it down, so I need to get a way to make it work regardless how often Firefox is started with sudo mode. 

What happens when I remove the .mozilla directory is a new one is created with a crash report, but without any new profile in it. The crash report is only a file with this number: 1369993322

---

### Post by dino99 on 2013-05-31
It seems to me that Sage should not be inside /opt, as it disturb the default ubuntu settings. Why not instead set the users/groups settings to deal with the admin/users rights ? (That is a genuine ubuntu config when not in server installation)

---

### Post by Garyu on 2013-05-31
> **dino99 said:**
> It seems to me that Sage should not be inside /opt, as it disturb the default ubuntu settings. Why not instead set the users/groups settings to deal with the admin/users rights ? (That is a genuine ubuntu config when not in server installation)

I followed the Sage installation instructions, and Sage works great. 

Firefox is the software that is causing problems. And even if I would move Sage somewhere else, or never start it at all, I still can't start Firefox currently because none of the proposed solutions seem to work for me.

---

### Post by steeldriver on 2013-05-31
are you saying firefox is autostarting with root privileges? or that when you start it manually it has root privileges?

if it's autostarting, maybe that's part of a saved session that you just need to find and delete

---

### Post by Garyu on 2013-05-31
> **steeldriver said:**
> are you saying firefox is autostarting with root privileges? or that when you start it manually it has root privileges?

if it's autostarting, maybe that's part of a saved session that you just need to find and delete

I'm saying that when Sage starts, that is scripted to autostart Firefox with root priviliges and it works fine. However, I always shut down Firefox instantly in that case.

When I try to start Firefox as my normal user, then I get that the profile is missing error, even though I have permissions on the profile with subdirs, and the profiles.ini is correct, and even if I delete the entire .mozilla directory then a new one isn't properly created.

---

### Post by HiImTye on 2013-05-31
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
try ```
sudo chown $USER:$USER $HOME
```
I'm not familiar with Sage, but if it is running FF as a root user and messing up your user's account, then it is definitely not FF's fault
can you configure Sage to run as another user?

---

### Post by Garyu on 2013-06-01
> **HiImTye said:**
> [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
try ```
sudo chown $USER:$USER $HOME
```
I'm not familiar with Sage, but if it is running FF as a root user and messing up your user's account, then it is definitely not FF's fault
can you configure Sage to run as another user?
aah... I'm an idiot. I did that for the ~/.mozilla/ directory, which didn't fix anything, but running it on home (with an additional -R for recursive) made Firefox work again. So I guess some other directory is altered. OK, thanks, this will help me figure something out. :)

---

### Post by HiImTye on 2013-06-01
right, -R, it was like 5am for me lol

---

