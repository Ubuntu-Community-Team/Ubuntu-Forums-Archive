---
title: "lubuntu 18 CPU usage 100% using browsers"
date: 2018-07-12
forum: General Help
---

### Post by darthgollo on 2018-07-12
I have a old desktop using lubuntu, everything runs perfect, but if I surf in internet my cpu usage increase super high all the top to 100**%  **:(, I dont know how to decrease it to runs better in some websites, I use for browser falkon, is good but is not enough speed for some websites, im pretty new in linux and all this new community, im asking for some help.

some details, in task manager says QtWebEngineProcess is eating most of my cpu even at 70 porcent, and falkon increase pretty high enough some time to 45 ir 50 and then both decrese but gt high again with more activities online, what should I do ? is this normal? 

my desktop has:
2gb ram
intel celeron R 2.80 GHz 1 physical processor, 1 core, 1 thread
lubuntu 18.04
motherboard  3.0/945GCT-M3 ELITEGROUP COMPUTER SYSTEM CO.,LTD
harddrive 160gb
graphics 1024x768 the X.org fundation.


THANK YOU a lot by the way for read this.

---

### Post by TheFu on 2018-07-13
Disable javascript and don't allow flash or any other media to run.   Also, perform some ad blocking so all those tiny extra javascript things aren't allowed or even downloaded.

Many websites are graphics heavy, so if you can put in a modern GPU ($40 would be enough), you'll likely get much better performance, though for $90 you can get a used Core2Duo desktop off lease lots of places with better specs than the machine you have now and probably 9x faster.  2100 passmark for this type of system.
Found this locally for $89 at a national computer chain: 
> Lenovo ThinkCentre M57 Desktop Computer Refurbished; Intel Core 2 Duo Processor 3.06GHz; Microsoft Windows 10 Home; 4GB RAM; 250GB Hard Drive

BTW, I couldn't find any performance data about a "intel celeron R" CPU, so we don't really know how bad it is.  /proc/cpuinfo should provide the full, official name. If this [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+2.80GHz&id=644](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+2.80GHz&id=644) is what you have. OUCH! 250 passmarks is the lowest I've ever seen.   Might be fine for a home webserver or for nextcloud,  but I would probably just use a Raspberry Pi v3+ ($35) instead.

Do you realize that falkon is based on Qt?  That is NOT the main toolkit used by LXDE/Lubuntu systems.  On a computer with limited RAM, which 2G is today, you should avoid mixing main libraries between Qt and GTK.  Effectively, using falkon means having all the libraries for Qt and GTK loaded concurrently.  It looks like it is based on Chromium. Why not just use Chromium (which is also heavy) instead? At least then you wouldn't load Qt libs too.

---

### Post by darthgollo on 2018-07-14
im going to try with Chromium to see how it runs,  thank you by th way im going to do some of your tips.

---

### Post by HermanAB on 2018-07-14
In my experience, the worst power hog is Firefox, followed by Chrome.  The best is Safari on a Mac, which is specifically designed to save power.  For Linux there are many other browsers that you can try.  

The best one will be Links, which is a text mode browser - no useless power sapping features!

---

### Post by darthgollo on 2018-07-14
:guitar: falkon works well for me, surfing in the web, but youtube is a mess or other website with videos repoduction like Khan Academy, thanks for the recomendations im going to chek out and let you know how it works.](*,)

---

### Post by darthgollo on 2018-07-14
I dont see the name or the download link in the website, can you help me with that  Herman? im new with linux and lubuntu

---

### Post by TheFu on 2018-07-14
> **darthgollo said:**
> I dont see the name or the download link in the website, can you help me with that  Herman? im new with linux and lubuntu

```
sudo apt install lynx
```

In Linux, you shouldn't download programs to be installed. Always use the package manager.  But Lynx probably isn't all that useful for most people.  If you want a VERY light browser that has a GUI, dillo is one.  But don't use it for sites where you expect security or privacy.    Dillo doesn't validate HTTPS certs.

---

### Post by darthgollo on 2018-07-14
ok thank you

---

### Post by HermanAB on 2018-07-14
And the other one that sounds the same:
$ sudo apt install links

---

