---
title: "installed pipelight in 15.04 and its not compatible now want to remove but cant"
date: 2015-05-17
forum: General Help
---

### Post by eival on 2015-05-17
terminal isnt finding pipelight at all

what other codes could i run?

same goes for any wine implamentations

---

### Post by oldos2er on 2015-05-17
Please post the commands you ran.

---

### Post by efflandt on 2015-05-17
This shows what you have installed for a package, the wildcard * at the end picks up variations of it (-l is small L):```
efflandt@XPS-8100-1404:~$ dpkg-query -l pipelight*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-===========================================================
un  pipelight                   <none>             <none>             (no description available)
ii  pipelight-multi             0.2.8.1~ubuntu14.0 amd64              allows usage of Windows NPAPI plugins through Wine
```And since I could not get it to work in 14.04 for Silverlight (have not tried lately) I used these commands to remove it. Note that it will list a bunch of related packages that autoremove will remove, and you need the **ppa-purge** package installed to remove the ppa.```
sudo apt-get purge pipelight*
sudo apt-get autoremove
sudo ppa-purge ppa:pipelight/stable
```The only thing I was trying to do Silverlight for was Ceridian DayForce for scheduling vacation days, but I can do that with an app on my Android phone. I don't need Silverlight for Netflix because that works in Google Chrome (Netflix also works on Chromecast device using Chromecast Extension in Google Chrome or Netflix app on Android).

---

