---
title: "Firefox 3 released?"
date: 2008-06-09
forum: General Help
---

### Post by LittleLORDevil on 2008-06-09
I just updated my fresh install of Ubuntu and I noticed a Firefox update.  I was curious and check the about Firefox in the browser and didn't find any beta or RC around it?  Anyone else updated?

---

### Post by FFighter on 2008-06-09
It was the update to RC2. FF3 has not been released yet.

---

### Post by Bubba64 on 2008-06-09
> **LittleLORDevil said:**
> I just updated my fresh install of Ubuntu and I noticed a Firefox update.  I was curious and check the about Firefox in the browser and didn't find any beta or RC around it?  Anyone else updated?

Is FF running, look in synaptic to see whats marked if it is.

---

### Post by FuturePilot on 2008-06-10
It was not Firefox 3 final
```
apt-cache policy firefox-3.0
firefox-3.0:
  Installed: 3.0~rc1+nobinonly-0ubuntu0.8.04.1
  Candidate: 3.0~rc1+nobinonly-0ubuntu0.8.04.1
  Version table:
 *** 3.0~rc1+nobinonly-0ubuntu0.8.04.1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     3.0~rc1+nobinonly-0ubuntu0.8.04.0mt1 0
        500 http://ppa.launchpad.net hardy/main Packages
     3.0~b5+nobinonly-0ubuntu3 0
        500 http://us.archive.ubuntu.com hardy/main Packages

```

---

### Post by isaacj87 on 2008-06-10
Strange though...I was wondering about this as well. I know it's RC1, but if you look in the "About Mozilla Firefox" it says Firefox 3.0...not Firefox 3.0 RC1...

---

### Post by Bubba64 on 2008-06-10
If you want rc2 go to launchpad.
[http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html](http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html)
It says rc1 but rc2 is in the repository downloads keeping all previous stuff intact (overwrites)

---

### Post by LittleLORDevil on 2008-06-10
> **isaacj87 said:**
> Strange though...I was wondering about this as well. I know it's RC1, but if you look in the "About Mozilla Firefox" it says Firefox 3.0...not Firefox 3.0 RC1...
That is what got me confused.

---

### Post by Bubba64 on 2008-06-10
> **LittleLORDevil said:**
> That is what got me confused.

I'm sure it says rc1 in synaptic though.

---

### Post by LittleLORDevil on 2008-06-10
> **Bubba64 said:**
> I'm sure it says rc1 in synaptic though.
When it doubt, check synaptic I guess.

---

### Post by SunnyRabbiera on 2008-06-10
Well at the RC phase its practically final, as the official release is normally not much different then the RC unless something really goes wrong.

---

### Post by gmc on 2008-06-10
Anyone missing the status bar in the newly updated firefox? Or am I just lucky.  G.

---

### Post by Bubba64 on 2008-06-10
> **gmc said:**
> Anyone missing the status bar in the newly updated firefox? Or am I just lucky.  G.

Do you mean the navigation tool bar right click in the bookmark, tools files, etc bar and click navigation.

---

### Post by gmc on 2008-06-10
> **Bubba64 said:**
> Do you mean the navigation tool bar right click in the bookmark, tools files, etc bar and click navigation.

 Nope, I'm talking about the status bar at the bottom of the firefox window. I've attached an image to illustrate.  G.

---

### Post by bikeboy on 2008-06-10
Dumb question that needs to be asked - Is View > Status Bar checked?

---

### Post by gmc on 2008-06-10
> **bikeboy said:**
> Dumb question that needs to be asked - Is View > Status Bar checked?

 Definitely not a stupid question.   I never noticed that option before. I guess I either accidentally turned it off, or the update defaulted to off (probably me). Thanks for pointing out my over sight, and definitely a useful option for any eeepc users.  Again, Thanks  G.

---

### Post by aethralis on 2008-06-10
I it just me or has the rc1 become more unstable? FF has crashed (just closes itself without any notice) several times. Happens when selecting text, noticed no connection with flash pages.

---

### Post by melrom on 2008-06-10
> **aethralis said:**
> I it just me or has the rc1 become more unstable? FF has crashed (just closes itself without any notice) several times. Happens when selecting text, noticed no connection with flash pages.

someone was telling me this online last night as well. 

i wouldn't know because Hardy won't update for me. :(

---

### Post by barbedsaber on 2008-06-10
> **isaacj87 said:**
> Strange though...I was wondering about this as well. I know it's RC1, but if you look in the "About Mozilla Firefox" it says Firefox 3.0...not Firefox 3.0 RC1...

confused me as well, Oh well.

---

### Post by kripkenstein on 2008-06-10
I don't know if this is a new RC or the final, but regardless it's much more responsive. The older version was almost unusable on my (old) machine, it was so slow, but now things are very nice actually.

---

### Post by bikeboy on 2008-06-10
> **gmc said:**
> Definitely not a stupid question.   I never noticed that option before. I guess I either accidentally turned it off, or the update defaulted to off (probably me). Thanks for pointing out my over sight, and definitely a useful option for any eeepc users.  Again, Thanks  G.

Glad I could help. No idea how it became unchecked, the thought immediately came to mind though (most apps have View > Status bar).

---

### Post by victor.zamanian on 2008-06-10
So uhh...

```
$ firefox --version
Mozilla Firefox 3.0, Copyright (c) 1998 - 2008 mozilla.org
```

```
$ apt-cache policy firefox
firefox:
  Installed: 3.0+nobinonly-0ubuntu0.8.04.1
  Candidate: 3.0+nobinonly-0ubuntu0.8.04.1
  Version table:
 *** 3.0+nobinonly-0ubuntu0.8.04.1 0
        500 http://se.archive.ubuntu.com hardy-proposed/main Packages
        100 /var/lib/dpkg/status
     3.0~rc1+nobinonly-0ubuntu0.8.04.1 0
        500 http://se.archive.ubuntu.com hardy-updates/main Packages
     3.0~b5+nobinonly-0ubuntu3 0
        500 http://se.archive.ubuntu.com hardy/main Packages
```

```
$ aptitude show firefox | grep Version
Version: 3.0+nobinonly-0ubuntu0.8.04.1
```

mozilla.org offers 2.0.0.14. I don't know what's going on here.

---

### Post by Polygon on 2008-06-10
its still a release canidate. If no other problems show up, then mozilla will just take the RC2 build and label that as the final.

which is why it doesnt say RC in help>about firefox or anything.

---

### Post by victor.zamanian on 2008-06-10
> **Polygon said:**
> its still a release canidate. If no other problems show up, then mozilla will just take the RC2 build and label that as the final.

which is why it doesnt say RC in help>about firefox or anything.

That may very well be the case. I do not, however, consider that to be proper praxis. If it's RC2, the package name and about box should print the version name accordingly. If it's the final release, the package name and about box should print *that* accordingly. I don't consider it professional to just assume, "Meh, it's pretty much finished so let's just label it 3.0 since the guys at mozilla are so slow already. :D" No. That's not well done.

Note: this is not a personal attack against anyone, especially you, Polygon. Just in case anybody would think so. :-) But tell me, am I alone in believing this?

---

### Post by Ozor Mox on 2008-06-10
> But tell me, am I alone in believing this?

It confused me. I thought I was running FF3 final after checking the about page, and couldn't understand why it wasn't available on the Firefox website. Still, no biggie, it all works nicely.

---

### Post by K.Mandla on 2008-06-10
Moved to General Help.

---

### Post by BandD on 2008-06-10
When the updates showed up, I clicked on the firefox update in the update manager and clicked to show the description.  In there it clearly stated that it was RC1.  

I find it good practice to check and see what the updates actually are before installing them.

---

### Post by victor.zamanian on 2008-06-11
> **BandD said:**
> When the updates showed up, I clicked on the firefox update in the update manager and clicked to show the description.  In there it clearly stated that it was RC1.  

I find it good practice to check and see what the updates actually are before installing them.

I do that with nearly every package on every update. Especially on firefox nowadays since it's closing in on a major release, but also in general since it's an often-used program of mine, obviously. :-)

The latest update of firefox (I updated it yesterday) showed no sign of any RCX anywhere, including the actual names of the packages and descriptions for the updates, and that includes all of the firefox-* updates. Very odd. I can't find any indication that the version I'm running is a RC, other than the fact that mozilla.com hasn't announced a final version yet.

The thing for me isn't the fact that I "might be running the final version secretely :O". Obviously I'm not doing that since it's not released. My beef is with the fact that there should be proper branding of versions.

Regards,
Victor

---

### Post by Ameneon on 2008-06-11
I quite concur that it should show the exact version information even if it is likely borderlining certain that there will be no changes prior to the final version.

But at least, finally, FF is usable for me again. The ridiculous Beta 5 pushed me over to Opera but now I can start using FF again, no problems thus far.

---

