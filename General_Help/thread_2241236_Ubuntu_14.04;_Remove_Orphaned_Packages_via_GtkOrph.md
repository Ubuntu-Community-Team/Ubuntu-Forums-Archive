---
title: "Ubuntu 14.04; Remove Orphaned Packages via GtkOrphan"
date: 2014-08-25
forum: General Help
---

### Post by tegelstom on 2014-08-25
Hello Everyone! :)
I use GtkOrphan for regular maintenance and here is my situation:
[https://plus.google.com/u/0/photos/112478144887851328209/albums/5736976833890696177/6051394378103329010?pid=6051394378103329010&oid=112478144887851328209](https://plus.google.com/u/0/photos/112478144887851328209/albums/5736976833890696177/6051394378103329010?pid=6051394378103329010&oid=112478144887851328209)
7 orphaned packages with extra priority... Plus that (I'm not very sure) all these packages installed, after the [COLOR=#000000]linux-generic-lts-trusty installation.[/COLOR]
What priority means in this tool? Should I remove them all?
Thanks in Advance
Thomas

---

### Post by ibjsb4 on 2014-08-25
Your running Trusty so The one marked trusty could still apply to you.  Myself I run xorg, but do not have this package installed, but thats my system, not yours.

The final decision is of course yours to make.  I have been bitten by deborphan in the past, so like me, use at your own risk :)

---

### Post by grahammechanical on 2014-08-25
Am I right in guessing that you started with Ubuntu 12.04 and over time by running update manager you progressed thought the point releases of 12.04.1; 12.04.2; 12.04.3; 12.04.4; 12.04.5? If you did then you got the hardware enablement stacks of later releases of Ubuntu, Quantal, Raring, Saucy and even Trusty.

Have you now upgraded to 14.04.1? Then you may not need those packages. Run

```
sudo apt-get update
sudo apt-get upgrade
```

You may find those same packages listed as not needed and a recommendation to use autoremove to remove them. You could think of that as a double confirmation.

Regards.

---

### Post by tegelstom on 2014-08-25
I was using 12.04 only and I did a clean installation of 14.04.

---

### Post by tegelstom on 2014-08-25
@[[COLOR=#000000]ibjsb4[/COLOR]]("http://ubuntuforums.org/member.php?u=1729120")[COLOR=#000000]  & @[/COLOR][COLOR=#DD4814][COLOR=#000000][grahammechanical]("http://ubuntuforums.org/member.php?u=1087323"), [/COLOR][/COLOR]Thanks for your answers! :)

---

### Post by tegelstom on 2014-08-29
My bad, I installed [COLOR=#000000]the [/COLOR][COLOR=#000000][COLOR=#000000]linux-generic-lts-trusty a t[/COLOR][/COLOR][COLOR=#111111][FONT=Verdana]ransitional package for upgrades from 12.04 to 14.04 (Precise to Trusty) with no reason since I did a clean installation of 14.04, that caused all these orphaned packages! I removed them via GtkOrphan plus that [/FONT][/COLOR][COLOR=#000000]linux-generic-lts-trusty and everything works nice and clear!!![/COLOR]

---

