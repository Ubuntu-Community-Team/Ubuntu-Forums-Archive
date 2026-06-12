---
title: "Internal error [x]Show Details -&gt; Apport"
date: 2015-01-29
forum: General Help
---

### Post by Unterseeboot_234 on 2015-01-29
Using Ubuntu 14.04 LTS with Gnome Classic Desktop and lately every boot / re-boot gives me the "Sorry, Ubuntu has an internal Error" panel. In fact I get a staircase of those panels. All panels point to Apport as the cause. Further the Upgrades Notifyer gets disabled. I have to open Terminal and key in the commands to sudo apt-get update && sudo apt-get upgrade.

Is Apport the problem? And if I disable Apport will the Ubuntu Upgrades start working again? Do you recommend disabling Apport?

---

### Post by ibjsb4 on 2015-01-30
You can disable apport.  I do not have it installed.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+apport&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+apport&sa=Search&cof=FORID:9)

You can also reset apport by removing the /var/crash/ reports.

---

