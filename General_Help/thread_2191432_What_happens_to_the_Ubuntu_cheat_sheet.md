---
title: "What happens to the Ubuntu cheat sheet?"
date: 2013-12-02
forum: General Help
---

### Post by monkeybrain20122 on 2013-12-02
I remember in 12.04 if you press the super key long enough there will be a list showing all the keyboard shortcuts. I notice that feature appears to be gone in 13.10. What happens? I think it is a good way to help new users, or do they believe that new users should only use LTS?

---

### Post by coffeecat on 2013-12-02
Works for me in 13.10.

---

### Post by monkeybrain20122 on 2013-12-02
When I hold the super key in 13.10 I see numbers on the launcher icons in the unity bar.

---

### Post by coffeecat on 2013-12-02
I see both. Have you changed any of the Unity plugin settings in ccsm, or have you installed another desktop?

---

### Post by monkeybrain20122 on 2013-12-02
I have change some settings in ccsm. And it seems that it happens rather consistently for my two 13.10 and one 13.04 install. May be I have disabled the setting in the unity plugin that is responsible for this feature because of conflicts with other plugins. I am wondering which one.. 

Edited: strange. With my 13.04 installation I just open ccsm to go to Unity plugin then close ccsm, **without doing anything** and now the cheat sheet shows up. Will check the 13.10 installations when I go home..

---

### Post by monkeybrain20122 on 2013-12-02
It doesn't work for me in 13.10. I checked ccsm's unity plugin and I didn't find  anything unusual, a short press of the dash still brings up the dash  but holding it only brings up number in the launcher but no help  overlay. This guy has the same problem  [http://askubuntu.com/questions/363882/after-upgrading-from-13-04-to-13-10-holding-super-no-longer-brings-up-the-help](http://askubuntu.com/questions/363882/after-upgrading-from-13-04-to-13-10-holding-super-no-longer-brings-up-the-help)

---

### Post by cariboo on 2013-12-03
The cheat sheet works for me on Trusty, except for setting the icon size to 28px and setting the launcher to auto-hide, it's a bone stock installation.

---

### Post by monkeybrain20122 on 2013-12-03
I believe it has to do with my workaround to fix the scale and edge flip plugins from this thread. [http://ubuntuforums.org/showthread.php?t=2156531](http://ubuntuforums.org/showthread.php?t=2156531)
After disabling automatic sorting I have re-arranged the order of the plugins. I have no intention of putting my theory to the test and risk the frustration of setting it up again. :) I am just curious where the cheat sheet has gone. This workaround is not needed in 13.04 so the help overlay still loads (yeah one wonders what new workarounds would be required when 14.04 comes out. I doubt that the Compiz bugs will ever get fixed now that they are moving to Mir and Unity8)

---

### Post by philinux on 2013-12-03
Not working here either just numbers in launcher. This was an upgrade to 13.10 not clean install.

I've only enabled wobbly windows nothing else tweaked.

I'll try resetting unity and compiz to default.

[edit] yep that fixed it.

```
dconf reset -f /org/compiz/
```

Then

```
setsid unity
```

(Moved to General Help forum)

---

### Post by monkeybrain20122 on 2013-12-03
So does it still work if you re-enable wobbly windows?

---

### Post by philinux on 2013-12-03
> **monkeybrain20122 said:**
> So does it still work if you re-enable wobbly windows?

Hi yes it does I just tried it. :D

I just resized my launcher icon size back to size 38. 

Enabling wobbly was a bit weird - desktop all froze and a crash report generated. I left it alone and it all unfroze and all worky.

---

