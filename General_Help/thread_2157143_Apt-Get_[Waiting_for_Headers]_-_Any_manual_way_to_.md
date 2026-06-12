---
title: "Apt-Get [Waiting for Headers] - Any manual way to force an update?"
date: 2013-06-24
forum: General Help
---

### Post by Affrikka on 2013-06-24
Hello all,

Ultimately I'd like to upgrade to 13.04, because my laptop (amoung many other things) were just stolen from my house and my desktop is very old/has little memory. I've read 13.04 is much easier on memory with Unity than 12.04, so if this is wrong please let me know.

Anyway, I noticed my Update Manager won't show the convenient "There is an upgrade available," even after I checked in the settings to show upgrades for all new versions, not just LTS ones. I looked at ways to do this from the command line and saw they all had me do sudo apt-get update first; this is where I get stuck.

Firstly, in the past an apt-get update wouldn't take too long, but this takes literally forever. Then it gets stuck at about 23% without continuing further (I let it sit for a whole night) saying that connection to one of the servers is failing. 

Is there any other way around this? I could do the easier route of burning 13.04 to a CD, I don't have anything really to lose, save $10 on a pack of new blank CDs.

Thanks!

---

### Post by plucky on 2013-06-24
> I've read 13.04 is much easier on memory with Unity than 12.04, so if this is wrong please let me know.

12.04 has unity 2D mode,which allows lower spec systems to use Ubuntu.

13.04 does not have the ability to use unity 2D mode and your system will have to be capable of running compiz.

> Firstly, in the past an apt-get update wouldn't take too long, but this takes literally forever. Then it gets stuck at about 23% without continuing further (I let it sit for a whole night) saying that connection to one of the servers is failing.

Is there any other way around this? 

Try changing the download server you are using to the Main server in your **Software Sources**.

>  I could do the easier route of burning 13.04 to a CD, I don't have anything really to lose, save $10 on a pack of new blank CDs.


You might need to use a DVD.

Good Luck

---

### Post by Affrikka on 2013-06-24
If that's the case, I'll probably stick to 12.04, I think my desktop currently only has 512MBs of RAM, I gave most of it to another desktop which I no longer have. Thanks for the help!

---

### Post by CaptainMark on 2013-06-24
512mb is pushing it for some of the new versions of Ubuntu, you would be better off switching to a version of Ubuntu with more lightweight software, I would strongly recommend Lubuntu, 512 would run quite well with that.

---

