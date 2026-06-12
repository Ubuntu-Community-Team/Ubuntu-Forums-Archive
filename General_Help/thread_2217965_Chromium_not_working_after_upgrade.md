---
title: "Chromium not working after upgrade"
date: 2014-04-19
forum: General Help
---

### Post by rdh61 on 2014-04-19
Hi, 

After upgrading from Lubuntu 13.10 to 14.04, Chromium is not working. Sometimes it will not let me type anything in the address/search box, or in the search engine search box on the page. Sometimes I can the first time but then I cannot delete and retype another entry. I have installed and updated the new pepper flash plugin, but this does not help.

What can I do?

Many thanks.

---

### Post by bapoumba on 2014-04-19
So I understand you had Chromium on 13.10 and it got upgraded to 14.04 with all the other packages, am I correct ?
I had to reinstall it, the panel icon was not even working. I did not loose my profile settings.
I do not recall how I got it reinstalled, but that probably was with apt-get as I rarely use the GUI for package managers, I like when it talks to me in the terminal.

I would run:
```
sudo apt-get update
sudo apt-get remove chromium-browser
sudo apt-get install chromium-browser
```
and see if it helps getting Chromium back on tracks.

One thing, you did restart Chromium after installing the pepperflash plugin, right ?

---

### Post by 21miki21 on 2014-04-19
Probably known Ibus bug.  I experienced this bug too, few days ago with daily Lubuntu 14.04 build with Slovak keyboard.

Read know issues. 
**Known Issues**

**Installation**


[LIST]
[*]Some keyboard layouts may have problems (such as UK ones). You can workaround the problem by removing all the ibus-* packages (see [1284635]("https://bugs.launchpad.net/bugs/1284635")))
[/LIST]

---

### Post by rdh61 on 2014-04-20
Reinstalling did not work. Re the known issue, I have a somewhat more direct approach: Chromium doesn't work, Chrome does, Chromium out, Chrome in! Thank you.

---

### Post by bapoumba on 2014-04-20
> **rdh61 said:**
> Reinstalling did not work. Re the known issue, I have a somewhat more direct approach: Chromium doesn't work, Chrome does, Chromium out, Chrome in! Thank you.
Use and do what works for you, that is the most important :)

---

### Post by Jonathan_Traill on 2014-04-20
Experienced similar after upgrade to 14.04, but I converted Chromium to SRWare Iron, and it went away.

---

### Post by rdh61 on 2014-04-24
Hi Jonathan_Traill,

When opening Iron did you repeatedly get the following message:

"Your profile can not be used because it is from a newer version of Iron.
Some features may be unavailable. Please specify a different profile directory or use a newer version of Iron."

I do. Any idea what to do about it?

Thanks.

---

### Post by bapoumba on 2014-04-27
Just to follow up as I had forgotten to do so (and got the bug on a fresh install) : [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648)
Use as a temp fix :
```
ibus exit
```

Edit : following up on post #1.

---

### Post by ezekiel3 on 2014-05-30
Hi! bapoumba
I follow up your last post and it work for me.
Any way, in the link you left it said that in Im-config change ibus to xim, I really do not understand what does it do. But in [here ]("http://askubuntu.com/questions/449361/keybord-input-not-work-in-chromium-34-ubuntu-14-04-aura-260972-using-fcitx-wo")he said to change iBus to Fcitx. Now which is the difference? or which will be more appropriate?

Thanks

---

### Post by kowloon2 on 2014-05-30
Try to download Chrome from Google. I have similar problem before after the upgrade to 14.04 from 13.1.

---

### Post by bapoumba on 2014-05-30
> **ezekiel3 said:**
> Hi! bapoumba
I follow up your last post and it work for me.
Any way, in the link you left it said that in Im-config change ibus to xim, I really do not understand what does it do. But in [here ]("http://askubuntu.com/questions/449361/keybord-input-not-work-in-chromium-34-ubuntu-14-04-aura-260972-using-fcitx-wo")he said to change iBus to Fcitx. Now which is the difference? or which will be more appropriate?

Thanks

Hello !
I have not changed anything for now to have a standard setup and test any update that would solve that bug.
So either I use Firefox (that I had not used in some years) or I exit ibus at each reboot which has got me into hard freezes when playing with keyboard configs.. If at some point I get bored, I'll play around with different options.

---

