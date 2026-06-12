---
title: "Fogger not appearing in Software Center"
date: 2012-11-29
forum: General Help
---

### Post by danbrownlow on 2012-11-29
Hey,

I read about Fogger and wanted to try to install it, but when I read that it can be installed via Software Center, I can't find it.

When I search for, "Fogger", nothing appears.. Has it been removed or am I doing something wrong?

---

### Post by Elfy on 2012-11-29
I believe you'd need to use a PPA for it - if you are using 12.10 then 

[http://ubuntuforums.org/showthread.php?t=2073647](http://ubuntuforums.org/showthread.php?t=2073647)

specifically

> **loneowais said:**
> Hi, 

I'm the developer of Fogger. Fogger is not going anywhere. It's just that I'm too busy with things in my personal life. I'll get back to working on Fogger soon (~1-2 months)

Thanks for the patience.

---

### Post by danbrownlow on 2012-11-29
Oh, sorry, didn't see that. Sad, but understandable. Guess I should have checked it out when I first saw it, not 2 months later :)

Thank you.

---

### Post by Elfy on 2012-11-29
Keep an eye on it I guess :)

---

### Post by testa101 on 2013-02-27
However, fogger is still not in the Ubuntu Software Center (I've seen a couple posts saying that the developer is moving his residence and some stuff and have it up again in a couple months...)

anyway, I've had success with this: [https://launchpad.net/~loneowais/+archive/fogger/+packages]("https://launchpad.net/~loneowais/+archive/fogger/+packages")

either one of two ways: 1) add the ppa and install

[HTML]sudo add-apt-repository ppa:loneowais/fogger ; sudo apt-get update ; sudo apt-get install fogger[/HTML]

or 2) download the deb file and install (I prefer GDebi) [https://launchpad.net/~loneowais/+archive/fogger/+files/fogger_0.2.4ppa1-0~236~precise1_all.deb]("https://launchpad.net/~loneowais/+archive/fogger/+files/fogger_0.2.4ppa1-0~236~precise1_all.deb")

---

