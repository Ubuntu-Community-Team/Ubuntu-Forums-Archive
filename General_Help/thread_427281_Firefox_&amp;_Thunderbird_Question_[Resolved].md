---
title: "Firefox &amp; Thunderbird Question [Resolved]"
date: 2007-04-29
forum: General Help
---

### Post by CheeseQueen452 on 2007-04-29
I would like to run Firefox & Thunderbird from root all the time by using this command: gksudo thunderbird &/gksudo firefox &. However, it asks for my password. Is there a way to prevent that?

---

### Post by coxy on 2007-04-29
Is there a way to prevent it asking for you root password? Yes, but it's not a good idea or secure. Do a search for enabling root and logging in as root. Be aware, neither are recommended.

Why do you want to run them as root anyway?

---

### Post by CheeseQueen452 on 2007-04-29
I'm not worried about security, I'm the only one using this computer. Why is it not a good idea? I installed both programs manually, & by running them as root, they allow me to check for updates to the program as well as themes & add-ons. This way, I can get new versions as soon as they are released, instead of waiting a week or 2(maybe more) for the update manager to upgrade them for me.

> **coxy said:**
> Is there a way to prevent it asking for you root password? Yes, but it's not a good idea or secure. Do a search for enabling root and logging in as root. Be aware, neither are recommended.

Why do you want to run them as root anyway?

---

### Post by ashz on 2007-04-29
yes why the need to run root?

---

### Post by ashz on 2007-04-29
Whoops...u beat me to it..

Okay addons/themes will update regardless so no probs there, so really u only have to sign into root to upgrade to a new version (which is about once every 2 months ish)

But by being in root all the time u let ur external security compromised....not a good idea

Anyways u can click on...

System > Administration > Login Window > Security

Then check the "Allow local system administartor login"

Then on ur GDM signon page instead of putting in ur normal user id, type in root then ur root password.

(BTW if u have never signed in root before u will have to change ur password, by doing the following..

System > Administration > User & Groups...

Then click on root and then properties...

Set password by hand...

Cheers
Ash

---

### Post by CheeseQueen452 on 2007-04-29
Once again, I don't care about security. I'm the only one that uses this computer. I just want to run FF & TB as root, not log in as root. I have "Allow local system administrator login" checked. I merely want to run FF & TB as root without entering my password everytime. However, as you pointed out, new versions aren't released very often so I suppose I can live with it the way it is. But then I have to keep checking mozilla.com to see when updates are released.... Oh well, I'll just put it in my bookmarks & hopefully I'll remember to check from time to time....

> **ashz said:**
> Whoops...u beat me to it..

Okay addons/themes will update regardless so no probs there, so really u only have to sign into root to upgrade to a new version (which is about once every 2 months ish)

But by being in root all the time u let ur external security compromised....not a good idea

Anyways u can click on...

System > Administration > Login Window > Security

Then check the "Allow local system administartor login"

Then on ur GDM signon page instead of putting in ur normal user id, type in root then ur root password.

(BTW if u have never signed in root before u will have to change ur password, by doing the following..

System > Administration > User & Groups...

Then click on root and then properties...

Set password by hand...

Cheers
Ash

---

### Post by ashz on 2007-04-29
lol well if u aint worried about security then u wont need to worry about firefox or thunderbird being up to date :P

---

### Post by CheeseQueen452 on 2007-04-29
I see your point.... While I'm not worried about security, I do like to keep my programs up to date. The security is just a bonus, but as a Linux user the risk is negligible.....

> **ashz said:**
> lol well if u aint worried about security then u wont need to worry about firefox or thunderbird being up to date :P

---

### Post by OffHand on 2007-04-29
> **CheeseQueen452 said:**
> The security is just a bonus, but as a Linux user the risk is negligible.....
No it's not. Your plan is dumb.

---

### Post by aysiu on 2007-04-29
If you installed them manually to the /opt directory, you can just change ownership of those folders to you--that's better than running them as root all the time: ```
sudo chown -R cheesequeen:cheesequeen /opt/firefox
sudo chown -R cheesequeen:cheesequeen /opt/thunderbird
``` Then just launch them regularly as ```
firefox
``` and ```
thunderbird
``` and you should be able to check for updates without any problems.

---

### Post by GuitarRocker2562 on 2007-04-29
for firefox, "sudo chown -R <username> /usr/lib/firefox"

then find your thunderbird folder (check /usr/lib/mozilla-thunderbird) and type "sudo chown -R <username> <thunderbird directory>"

---

### Post by CheeseQueen452 on 2007-04-30
Thankyou!!

> **aysiu said:**
> If you installed them manually to the /opt directory, you can just change ownership of those folders to you--that's better than running them as root all the time: ```
sudo chown -R cheesequeen:cheesequeen /opt/firefox
sudo chown -R cheesequeen:cheesequeen /opt/thunderbird
``` Then just launch them regularly as ```
firefox
``` and ```
thunderbird
``` and you should be able to check for updates without any problems.

---

### Post by CheeseQueen452 on 2007-05-02
Ok, for some reason, Firefox doesn't give me the "check for updates" option again. I used the command posted above, but it only worked temporarily. What do I do?

---

### Post by CheeseQueen452 on 2007-05-02
Well, I used the command again, then went to about:config & changed "app.update.enabled" to true. Hope that works.... I'll keep you posted.

---

### Post by CheeseQueen452 on 2007-05-03
Ok, Firefox still does NOT allow the "check for updates" option. It seems to only work for one computer session at a time. Simply restarting FF doesn't disable it, but rebooting does for some reason. Any ideas? There's one other thing I'll try, but I'm not hopefull.... Stay tuned.....

---

### Post by CheeseQueen452 on 2007-05-04
Well, I'm not sure what I did(if anything), but the "check for updates" option seems to be sticking... so far.... I hope it stays that way!

---

