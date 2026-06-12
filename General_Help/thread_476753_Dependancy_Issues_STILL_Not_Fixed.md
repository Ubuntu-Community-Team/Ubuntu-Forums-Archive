---
title: "Dependancy Issues STILL Not Fixed"
date: 2007-06-17
forum: General Help
---

### Post by CheeseQueen452 on 2007-06-17
I still have libavutilcvs49, libquicktime0, & mozilla-mplayer listed as upgradable, but there are broken dependancies preventing the upgrades. I've been waiting almost 2 months for these issues to be resolved. When will they be fixed? Is there anything I can do?

---

### Post by 5-HT on 2007-06-17
Two months, ouch. That shouldn't be. Which repos are you using and what are the broken packages?

---

### Post by CheeseQueen452 on 2007-06-26
I'm using almost every repo listed in "software sources". The mplayer plugin can't be upgraded because it wants libc6 to be installed... but it is installed. I'm still having this problem & it's driving me nuts! SOMEONE PLEASE FIX THIS!!!

The broken packages are libc6, libavcodec1d, & libavutil1d.

> **5-HT said:**
> Two months, ouch. That shouldn't be. Which repos are you using and what are the broken packages?

---

### Post by Shazaam on 2007-06-26
Stab in the dark here but have you looked at this? Depending on your version of Ubuntu it may not be applicable.

[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

---

### Post by CheeseQueen452 on 2007-06-26
I'm using Feisty.

> **Shazaam said:**
> Stab in the dark here but have you looked at this? Depending on your version of Ubuntu it may not be applicable.

[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

---

### Post by CheeseQueen452 on 2007-07-27
Ok, this is really annoying..... When will these dependencies be fixed? Can someone PLEASE do something about this? I've been waiting for months to see these issues resolved! JUST FIX IT ONCE & FOR ALL!!!!!

---

### Post by CheeseQueen452 on 2007-08-02
This is rediculous, I've been waiting for months!! I can't even upgrade the mplayer plugin until they're fixed. PLEASE FIX THESE PACKAGES!!!!

---

### Post by rbmorse on 2007-08-02
> **CheeseQueen452 said:**
> I still have libavutilcvs49, libquicktime0, & mozilla-mplayer listed as upgradable, but there are broken dependancies preventing the upgrades. I've been waiting almost 2 months for these issues to be resolved. When will they be fixed? Is there anything I can do?

On my feisty I have libquicktime0 and mozilla-mplayer installed, no problem.  I cannot find a file in the Ubuntu Feisty or Gutsy repositories + medibuntu.sos-sts.com named libavutilcvs49 (or anything even close).  

From where are you trying to obtain this?

---

### Post by CheeseQueen452 on 2007-08-02
I've FINALLY had a break through! I managed to install a new version of libc6, which was needed to upgrade the mplayer plugin. I also got libavutilcvs49 installed. Now, I just have to get libquicktime0 upgraded....

> **rbmorse said:**
> On my feisty I have libquicktime0 and mozilla-mplayer installed, no problem.  I cannot find a file in the Ubuntu Feisty or Gutsy repositories + medibuntu.sos-sts.com named libavutilcvs49 (or anything even close).  

From where are you trying to obtain this?

---

