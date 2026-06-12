---
title: "sun java 6 install problem"
date: 2008-04-06
forum: General Help
---

### Post by boardrfolife on 2008-04-06
so i started from scratch and downloaded sun-java6-plugin it requires sun-java6-bin so i downloaded the bin the bin then says it needs sun-java-jre. I then proceed to download that and when that finishes it says it needs bin to install. So if bin needs jre and jre needs bin its quite a dependency loop. Any Recommendations?

---

### Post by Bubba64 on 2008-04-06
Did you install from synaptic which is accessible from system administration if you install from there your work will be done. It sounds like you down loaded java 6 instead. All my computers are on the Hardy release but I assume java 6 is on other distributions it was in my last Gutsy dist.

---

### Post by TWO on 2008-04-06
> **boardrfolife said:**
> so i started from scratch and downloaded sun-java6-plugin it requires sun-java6-bin so i downloaded the bin the bin then says it needs sun-java-jre. I then proceed to download that and when that finishes it says it needs bin to install. So if bin needs jre and jre needs bin its quite a dependency loop. Any Recommendations?

It might be surplus to your needs but the following link is to a forum how-to thread with instructions on how to install all the codecs necessary for any flavour of Ubuntu:

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

I'd uninstall whichever java packages you have installed and just follow the instructions on the page.

Hope that helps

TWO

Edit: Like Bubba64 said, installing it via Synaptic Package Manager should do the trick and doing so via the Terminal/ Konsole should be fine as I think 'apt' also installs other required package dependencies.

---

### Post by Bubba64 on 2008-04-06
> **TWO said:**
> It might be surplus to your needs but the following link is to a forum how-to thread with instructions on how to install all the codecs necessary for any flavour of Ubuntu:

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

I'd uninstall whichever java packages you have installed and just follow the instructions on the page.

Hope that helps

TWO

Edit: Like Bubba64 said, installing it via Synaptic Package Manager should do the trick and doing so via the Terminal/ Konsole should be fine as I think 'apt' also installs other required package dependencies.

Good job with a better link and instructions, I sometimes wonder if I am actually making things harder than easier.

---

### Post by warp99 on 2008-04-06
Open a terminal and type the following command:

```
sudo apt-get remove --purge sun-java*
```
then
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts
```

If this does not work then you don't have the multiverse repositories enabled.

---

### Post by TWO on 2008-04-06
> **Bubba64 said:**
> Good job with a better link and instructions, I sometimes wonder if I am actually making things harder than easier.

Oh no, that was just lucky! Having only used K(U)buntu for a couple of months myself, I was faced with a similar problem and someone who posted on an old thread of mine happened to have started that how-to guide, which has turned out to be really useful.

:)

---

### Post by boardrfolife on 2008-04-06
you all were helpful, my only problem is that my college doesn't allow us to access the internet untill java is installed. Most ridiculous thing ever.

---

