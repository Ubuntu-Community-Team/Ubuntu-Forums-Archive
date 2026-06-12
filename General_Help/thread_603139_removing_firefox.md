---
title: "removing firefox"
date: 2007-11-04
forum: General Help
---

### Post by Angelbeast on 2007-11-04
I'm wanting to just use Swiftwasel...Is there ANY way to remove firefox without also removing the desktop stuff?

---

### Post by wieman01 on 2007-11-04
What desktop stuff? You should be able to remove it through Synaptic. Search for the main package and simply remove it.

---

### Post by Angelbeast on 2007-11-04
> **wieman01 said:**
> What desktop stuff? You should be able to remove it through Synaptic. Search for the main package and simply remove it.

I tried but when i go to do it like that a window comes up with all of the other stuff it's going to remove along with firefox...take a look at the screenshot...

---

### Post by wieman01 on 2007-11-04
> **Angelbeast said:**
> I tried but when i go to do it like that a window comes up with all of the other stuff it's going to remove along with firefox...take a look at the screenshot...
Ah... alright. Better not in that case. ;-) Strange though. I have no idea why it does that.

What about installing the new browser and replacing all shortcuts and icons?

---

### Post by TuxTwig on 2007-11-04
Seems like removing Firefox will cripple your system, I'm not sure why that's happening, as my remove Firefox option works without all that. :(

EDIT: Perhaps it's because you installed Firefox 3.0?? Try removing Firefox 3.0 first.

---

### Post by Angelbeast on 2007-11-04
> **wieman01 said:**
> Ah... alright. Better not in that case. ;-) Strange though. I have no idea why it does that.

What about installing the new browser and replacing all shortcuts and icons?

i do have swiftweasel set as the default...i just wanted to remove anything i'm not using...ah well...that seems kind of microsoft like...forcing me to keep firefox haha ...

---

### Post by Angelbeast on 2007-11-04
> **TuxTwig said:**
> Seems like removing Firefox will cripple your system, I'm not sure why that's happening, as my remove Firefox option works without all that. :(

evolution was doing that too but i just disabled the alarm thing in the start up list then i was able to uninstall it...i don't know what ll i would have to disable for the firefox though

---

### Post by wieman01 on 2007-11-04
Seems you don't have a choice. No clue why it does that. Looks kind of odd to me.

---

### Post by Angelbeast on 2007-11-04
> **wieman01 said:**
> Seems you don't have a choice. No clue why it does that. Looks kind of odd to me.

yeah...oh well though...i guess i can live with it *LOL*

---

### Post by wieman01 on 2007-11-04
I borked my system once while I removed "orphaned" packages... Seriously it's good that you maintain your system but I figured out that it's just not worth it sometimes. ;-) I probably spent 24 hours fixing it last time I did it. Haha...

---

### Post by Angelbeast on 2007-11-04
> **wieman01 said:**
> I borked my system once while I removed "orphaned" packages... Seriously it's good that you maintain your system but I figured out that it's just not worth it sometimes. ;-) I probably spent 24 hours fixing it last time I did it. Haha...

yeah i have a few things that were removed that other stuff uses...nothing too serious as far as i know...i ran kleen sweet last week and it sended up removing stuff like  

file:///usr/share/ubuntu-artwork/home/index.html

so firefox when it's looking for it's default start page can't find it but little stuff like that i guess doesn't hurt anything

---

### Post by Sparky222B on 2007-11-04
I'm not sure why, but Firefox seems to be a dependency of ubuntu-desktop :\

---

### Post by wieman01 on 2007-11-04
...perhaps so because Gnome does not come with its own browser in contrast to KDE (Kubuntu). Kubuntu'ers have a choice.

---

### Post by FuturePilot on 2007-11-04
It's because there's a lot of things that use the Gecko rendering engine. But since at this time there is no stand alone Gecko engine those things will depend on Firefox to provide Gecko. And since Webkit hasn't matured yet, even Epiphany depends on Firefox for Gecko. Perhaps once Webkit matures Firefox will no longer be a dependency of so many things.

---

### Post by stchman on 2007-11-04
> **Angelbeast said:**
> I'm wanting to just use Swiftwasel...Is there ANY way to remove firefox without also removing the desktop stuff?

Do the following:

```

sudo apt-get -y autoremove firefox
```

---

### Post by robrmd9 on 2007-11-05
> **Sparky222B said:**
> I'm not sure why, but Firefox seems to be a dependency of ubuntu-desktop :\

Why wouldn't it be?  It's the official internet browser of Ubuntu, so it should be included in the ubuntu-desktop metapackage, which includes all the packages of the base Ubuntu install.

---

### Post by Angelbeast on 2007-11-06
> **stchman said:**
> Do the following:

```

sudo apt-get -y autoremove firefox
```

now will this way break any of the gecko dependencies?

---

### Post by gh23l on 2007-11-18
I was also quiete concerned to destroy my ubuntu when i removed firefox, but I tried and it's no problem at all. Ok, I can't use yelp and the ubuntu-docs anymore, but who care's.

As webbroswer I use epiphany, but still with a gecko-engine, but not dependable on firefox. I found a package called epiphany-gecko in the debian-sid-repositories which really works fine. There's also a epiphany-webkit package available but that's kind of buggy until now.

---

### Post by GavinZac on 2008-01-15
you guys need to know the answer before you go telling the guy incorrect information.

Most of those packages are dependant upon firefox. The one that looks out of place is "ubuntu-desktop".

Ubuntu-desktop is a **meta-package** which installs all the normal applications that come with Ubuntu Desktop edition. If you remove firefox, you no longer have all those normal applications so you no longer have the standard Ubuntu Desktop package.

You can safely remove firefox, and Ubuntu-desktop without affecting anything other than firefox.

---

### Post by wieman01 on 2008-01-16
> **GavinZac said:**
> you guys need to know the answer before you go telling the guy incorrect information.
What makes you think people spread incorrect information? This thread is about removing Firefox which apparently had not been done before by a lot of people, apparently so because nobody with the right answer posted a reply. If you know the answer, good for you. Perhaps you could post earlier next time?

---

### Post by 6205 on 2008-03-23
I don't know how you, but i am unable to remove Firefox only, without loosing Epiphany or Yelp..

---

