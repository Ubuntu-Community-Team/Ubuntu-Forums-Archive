---
title: "How to access repository for Ubuntu 12.04 LTS"
date: 2021-07-27
forum: General Help
---

### Post by lu333031 on 2021-07-27
We would like to experiment with installing/updating some tools on our ubuntu 12.04 LTS based appliance but Synaptic fails while reloading the package information with an error in it being unable to find the repository.

**We understand that 12.04 LTS is a really old version of Ubuntu.**

However, upgrading ubuntu is neither required for our needs, nor practical given the deployment of the appliances around the world and many other practical considerations. It appears that the repository has been moved in the past few months as we had been able to reload package information in Synaptic before that.
Where do I find the repository so that I can update a tool (e.g. tzdata).

Thank you.

Lu

---

### Post by Bashing-om on 2021-07-27
lu333031 - Hello

Try as : [http://old-releases.ubuntu.com/ubuntu/dists/precise/](http://old-releases.ubuntu.com/ubuntu/dists/precise/)

Hope this helps

---

### Post by guiverc on 2021-07-27
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

The primary focus is upgrading an EOL system, but it tells you what needs to be done to allow package installs.

Ubuntu 12.04 ESM is (*or has*) reached the end of it's life; thus the move (mirrors will drop 12.04; move applies to main archive).  Ubuntu 12.04 reached it's end of *standard support* life long ago - [URL="https://fridge.ubuntu.com/2017/03/15/ubuntu-12-04-precise-pangolin-reaches-end-of-life-on-april-28-2017/"]https://fridge.ubuntu.com/2017/03/15/ubuntu-12-04-precise-pangolin-reaches-end-of-life-on-april-28-2017/

[/URL]FYI:  *I can't imagine you'd still be using pentium III type hardware?  as I  used pentium 4, pentium M & pentium D hardware in testing 18.04 (& later actually until i386 was dropped).  12.04 is a rather different system due to it's age.*

---

### Post by QIII on 2021-07-27
Hello.

When you say "around the world", are they connected?  If they are exposed in any way to the web, then upgrading to a newer release is far beyond a question of practicality and well in the realm of imperative.  

Unless you want to be pwned all around the world, do not expose your current systems in any way, shape or form.

It would be the height of irresponsibility for us to provide assistance if any of these appliances is exposed.

---

### Post by scorp123 on 2021-07-28
> **lu333031 said:**
>  However, upgrading ubuntu is neither required for our needs, nor practical given the deployment of the appliances around the world ...

You're basically begging to be hacked at this point.

---

### Post by Impavidus on 2021-07-28
> **lu333031 said:**
> 
Where do I find the repository so that I can update a tool (e.g. tzdata).

Nowhere, as no more updates for Ubuntu 12.04 are created. Not only standard support, but even extended support has ended. The repositories may still be present on some servers (like the old-releases server), but are no longer maintained and haven't been for years.

---

