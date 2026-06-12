---
title: "Why is Unity dash search so inefficient?"
date: 2014-01-28
forum: General Help
---

### Post by faust99 on 2014-01-28
I hate to be so obviously subjective in my criticism, but I cannot understand the massive regression that seems to have affected the Unity dash search power since 13.04. Most of the time search is unable to find files which have been accessed regularly and often and despite having found them on other occassions. It is as if the search is reindexed after every reboot. How can this be the case when it was so powerful in 12.10??

---

### Post by Frogs Hair on 2014-01-28
I don't share that experience with 13.10 and suspect there may be another  problem . 13.04 reached end of life yesterday , so please included the Ubuntu version you are using and how you installed.

---

### Post by faust99 on 2014-01-28
> **Frogs Hair said:**
> I don't share that experience with 13.10 and suspect there may be another  problem . 13.04 reached end of life yesterday , so please included the Ubuntu version you are using and hoe you installed.

Thanks for replying. As an aside, I had the same issue with 13.04. ATM I'm on 13.10 and did a fresh install via live DVD 64bit.

---

### Post by Frogs Hair on 2014-01-28
The thread is tagged Lubuntu , is this correct ? If so then the conclusion would be you installed Unity and all recommended packages on Lubuntu.

---

### Post by faust99 on 2014-01-28
> **Frogs Hair said:**
> The thread is tagged Lubuntu , is this correct ? If so then the conclusion would be you installed Unity and all recommended packages on Lubuntu.

I'm sorry - I tagged it Lubuntu by mistake. It is actually Ubuntu. As far as I know, all of the recommended packages have been installed. However, I just ran the Software Updated and it has informed me that not all updates can be installed, so there may be some issues....

---

### Post by Frogs Hair on 2014-01-28
If you have a partial update run check for updates by closing and opening the software updater.  This  will update the package system by connecting to the ubuntu servers. =```
sudo apt-get update
```  If you are still getting partial update message wait for a while and try again . Partial updates can break the package system and are usually seen when not connecting to the server / software sources.

---

### Post by dnemcanin2 on 2014-01-28
sudo apt-get -f install  
-f -> fix-broken

---

### Post by faust99 on 2014-01-28
> **Frogs Hair said:**
> If you have a partial update run check for updates by closing and opening the software updater.  This  will update the package system by connecting to the ubuntu servers. =```
sudo apt-get update
```  If you are still getting partial update message wait for a while and try again . Partial updates can break the package system and are usually seen when not connecting to the server / software sources.

Yes, there seem to be connectivity issues at the moment....

> **dnemcanin2 said:**
> sudo apt-get -f install  
-f -> fix-broken

Is this meant to be one command or two?

Sorry, duh I get it...

> **faust99 said:**
> Is this meant to be one command or two?

The output is 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. So I'm guessing nothing's actually broken...

---

### Post by dnemcanin2 on 2014-01-28
just
```
 sudo apt-get -f install
```
nothing after install

---

### Post by faust99 on 2014-02-03
So all updates have completed but the Dash search is still frustrating

---

### Post by vasa1 on 2014-02-03
Maybe you need to turn off the "scopes" especially if you have a slow net.

---

### Post by faust99 on 2014-02-03
> **vasa1 said:**
> Maybe you need to turn off the "scopes" especially if you have a slow net.

I've got online search results disabled so that should not be an issue. The most basic and obvious search results sometimes fail to come up in the Dash. For instance, one would imagine that typing "Documents" would result in the Documents folder coming up as a result, since its such a top level folder. But in my case this never happens, even when I use the specific files lense (i.e. Super+F).

---

### Post by monkeybrain20122 on 2014-02-03
I just type "Documents" and it does come up. It is actually working quite well in my experience The only thing I don't like is that it is not very flexible in terms of what directory to include or exclude. e.g I edit some config file in /etc /blah blah and it is not like I do this everyday, why does that get logged? And say if you try to exclude a folder like Downloads, then it shows right up in the dash even though its contents won't. My chief problem since 13.10 is the dash is too full of clutters consisting of random accessed files instead of something useful (which I want to keep in the dash). It would be a lot easier if it is opt in rather than opt out: in other words all folders are excluded by default and you decide what to add to the search path instead of the other way around.

---

### Post by faust99 on 2014-02-03
Yes, other's have commented that it works of for them. In my case I have to use Nautilus for the searches to be meaningful.

---

### Post by Gordonbp531 on 2014-02-12
I agree.
I'm on 13.10 and the Dash search doesn't find files that Nautilus search finds immediately....

---

