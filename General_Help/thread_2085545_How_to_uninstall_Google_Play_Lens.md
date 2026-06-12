---
title: "How to uninstall Google Play Lens"
date: 2012-11-18
forum: General Help
---

### Post by NBPX on 2012-11-18
How to uninstall this lens? 

[http://www.omgubuntu.co.uk/2012/11/new-lens-lets-you-search-google-play-from-the-unity-dash](http://www.omgubuntu.co.uk/2012/11/new-lens-lets-you-search-google-play-from-the-unity-dash)

It's easy to install, but unclear about how to remove.

---

### Post by Vaphell on 2012-11-18
try ```
sudo apt-get remove googleplaylens
```
remove that ppa from software sources as a bonus.

---

### Post by aliddell on 2012-11-18
Open up a terminal and
```
sudo apt-get remove unity-lens-xxx
```where xxx is probably going to be googleplay. If you don't see that, try typing

```
sudo apt-get remove unity-
```WITHOUT PRESSING ENTER and then hitting tab twice to see what you get. You'll probably find what you're looking for.

---

### Post by raja.genupula on 2012-11-18
> **Vaphell said:**
> try ```
sudo apt-get remove googleplaylens
```remove that ppa from software sources as a bonus.


+1 .

Above post deals with CLI way . I will give you about the GUI way .
you can perform that operation from the Software center and Synaptic package manager with clicks .

---

### Post by NBPX on 2012-11-18
I did not find the application in the Software Center before searching for "Google" and "Play". But now I searched by "lens" and goddamn was there hidden among the other lenses.

It's removed! I removed through command line. Thanks!

I uninstalled it because I did not returned any results to me.

---

