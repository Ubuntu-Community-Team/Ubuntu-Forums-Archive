---
title: "Odd Problem"
date: 2008-05-20
forum: General Help
---

### Post by Peter6218 on 2008-05-20
I have an odd problem. The image on the screen shakes sideways.

This is a dual boot machine running XP on the second HD. Image from XP is rock solid.

I've now had three different versions of Ubuntu on the system, all do the same. If you move the cursor or click on some link the screen shakes sideways.

The video card is an Nvidia GeForce 6 series.  I'm not running the restricted driver nor am I running Nvidia's driver.

Screen is an Acer LCD 19" wide.  Restricted driver only gives 800x600 resolution which is ridiculous on such a big screen. Experience with Nvidia's driver gave screen lock up so that's a no go either.

Currently I'm back to Feisty, had Gutsy and Hardy, no better.
Ideas ??

---

### Post by Cybergod on 2008-05-20
> **Peter6218 said:**
> I have an odd problem. The image on the screen shakes sideways.

This is a dual boot machine running XP on the second HD. Image from XP is rock solid.

I've now had three different versions of Ubuntu on the system, all do the same. If you move the cursor or click on some link the screen shakes sideways.

The video card is an Nvidia GeForce 6 series.  I'm not running the restricted driver nor am I running Nvidia's driver.

Screen is an Acer LCD 19" wide.  Restricted driver only gives 800x600 resolution which is ridiculous on such a big screen. Experience with Nvidia's driver gave screen lock up so that's a no go either.

Currently I'm back to Feisty, had Gutsy and Hardy, no better.
Ideas ??

I have a GeForce 6200 and sometimes this will happen to me.  I found that it only does this when compiz is enabled, if it's a problem for you then disable compiz and everything should be fine.

---

### Post by Peter6218 on 2008-05-20
Well that's interesting. Worth a try. How do I disable compiz, I'm no programmer.

---

### Post by Cybergod on 2008-05-20
> **Peter6218 said:**
> Well that's interesting. Worth a try. How do I disable compiz, I'm no programmer.

Click "System" > "Preferences" > "Appearance", then click the "Visual Effects" tab.  Make sure "None" is selected.

---

### Post by Znort_Ubern00b on 2008-05-20
You say you are using Feisty, have you got compiz running? As far as I know it is not a default package in Feisty. 

Open a terminal and type 
**metacity --replace**

that should turn off compiz if you have it running.

My guess is it is a driver problem, i have a 5200 nvidia card and no screen shake even when compiz running. i installed the nvidia drivers from synaptic, am usin feisty as well.

---

### Post by Cybergod on 2008-05-20
> **Znort_Ubern00b said:**
> You say you are using Feisty, have you got compiz running? As far as I know it is not a default package in Feisty. 

Open a terminal and type 
**metacity --replace**

that should turn off compiz if you have it running.

My guess is it is a driver problem, i have a 5200 nvidia card and no screen shake even when compiz running. i installed the nvidia drivers from synaptic, am usin feisty as well.

You are right, I didn't pay any attention that he/she was running Feisty.  My windows shake all the time when compiz is enabled on both Gutsy and Hardy.  It happens when I open a program, the windows will just start shaking and sometimes I can try to double click the title bar and it will stop.

---

### Post by Peter6218 on 2008-05-20
> **Cybergod said:**
> You are right, I didn't pay any attention that he/she was running Feisty.  My windows shake all the time when compiz is enabled on both Gutsy and Hardy.  It happens when I open a program, the windows will just start shaking and sometimes I can try to double click the title bar and it will stop.

That's the point. It happens on all three distros. Currently back to Feisty as I find wine runs my mail program better on it than the other two.

But it doesn't matter what distro I run, they all shake. Incidentally had Xandros on this system for a long time and no shake. So it isn't specifically a linux problem.

---

### Post by Znort_Ubern00b on 2008-05-21
> **Peter6218 said:**
> That's the point. It happens on all three distros. Currently back to Feisty as I find wine runs my mail program better on it than the other two.

But it doesn't matter what distro I run, they all shake. Incidentally had Xandros on this system for a long time and no shake. So it isn't specifically a linux problem.

Ok, do you have compiz running? Type the command I gave you earlier and see if shake stops. If not my guess is it is a driver problem and you need to look at installing the nvidia drivers. you'll need to install the correct one for your card, not sure which you'll have to ask but that should sort out your problem.

---

### Post by Peter6218 on 2008-05-21
> **Znort_Ubern00b said:**
> Ok, do you have compiz running? Type the command I gave you earlier and see if shake stops. If not my guess is it is a driver problem and you need to look at installing the nvidia drivers. you'll need to install the correct one for your card, not sure which you'll have to ask but that should sort out your problem.

Will get to try that later on today, thanks

---

### Post by Peter6218 on 2008-05-21
> **Znort_Ubern00b said:**
> Ok, do you have compiz running? Type the command I gave you earlier and see if shake stops. If not my guess is it is a driver problem and you need to look at installing the nvidia drivers. you'll need to install the correct one for your card, not sure which you'll have to ask but that should sort out your problem.

Tried the metacity --replace.

BINGO !!

Rock stable now.

Thanks a lot :)

---

