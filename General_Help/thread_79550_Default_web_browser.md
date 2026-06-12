---
title: "Default web browser"
date: 2005-10-20
forum: General Help
---

### Post by binome-x on 2005-10-20
Hi,
I can't configure my default web browser, no "choosing components" in my systemsettings
Does anyone know how to do that ?
Thx

---

### Post by treris on 2005-10-20
hi there, 

I went ahead and used the older system, the one of Hoary, you can for example use it by using the link to settings in the taskbar's system menu.
this should get you where you want to go

---

### Post by binome-x on 2005-10-20
How do you install the old system ?

---

### Post by shakin on 2005-10-20
[QUOTE=binome-x]Hi,
I can't configure my default web browser, no "choosing components" in my systemsettings
Does anyone know how to do that ?
Thx[/QUOTE]

I have it in kcontrol -> KDE Components -> Component Chooser

Are you missing that option? I haven't tried Breezy with KDE 3.4, but it's there with 3.5 beta 2

---

### Post by binome-x on 2005-10-20
I have KDE components but no components chooser

---

### Post by treris on 2005-10-20
somehow in breezy with kde 3.4.3 there is no kcontrol center, but probably if you enter 

(sudo) kcontrol in the terminal it should open up just like you're used to in Hoary

and then you should be able to just open

KDE components -> Component Chooser and voilá

hope this works for ya

---

### Post by Rumo on 2005-10-22
[QUOTE=treris]
(sudo) kcontrol in the terminal
[/QUOTE]

That will only work if kcontrol is installed (which is probably the case for all upgraded systems but not for a fresh installedbreezy).

Of course it is possible to install kcontrol with a simple
```

sudo apt-get install kcontrol

```

---

### Post by jeremy on 2005-10-22
My fresh install of Kubuntu breezy has kcontrol by default.

---

### Post by B.B on 2005-10-22
[QUOTE=jeremy]My fresh install of Kubuntu breezy has kcontrol by default.[/QUOTE]
Mine too..

Alt + F2 > kdesu kcontrol > KDE Components > Component chooser

But it does'nt work for me though, iIt's still Konqueror that open links from Kontact. :( 

Anyone with a better idea ?

---

### Post by treris on 2005-10-23
are you sure that you have changed the preferences for all website related extensions to open with firefox? because that's how I did it so I'm assuming it should also work for you

BTW kcontrol was installed by default on my fresh install of breezy, I was actually somewhat surprised to see basically two ways of changing your overall settings, one being kcontrol and the other the new system settings

---

### Post by B.B on 2005-10-24
[QUOTE=B.B]Mine too..

Alt + F2 > kdesu kcontrol > KDE Components > Component chooser

But it does'nt work for me though, iIt's still Konqueror that open links from Kontact. :( 

Anyone with a better idea ?[/QUOTE]
Figured it out.

instead of 'kdesu kcontrol' type 'settings:/' and do it from there.

What is the difference between 'kcontrol' and  'settings:/' and why are there two places to change your setting in the first place ? And what about 'system settings' from the start menu, why the lack of options compared to the other two  possibilities 
? :confused: :confused:

---

### Post by dc2447 on 2005-11-14
I am having similar issues - I use Thunderbird as my mail client but on this fresh install of breezy when I click hyperlinks in thunderbird firefox doesn't do anything even though it is set as default browser.

Anyone help?

---

### Post by barosl on 2007-04-27
Try installing kde-systemsettings.

---

### Post by dc2447 on 2007-04-27
> **barosl said:**
> Try installing kde-systemsettings.

The thread is 18 months old and you answer is wrong 

sudo update-alternatives --config x-www-browser

---

