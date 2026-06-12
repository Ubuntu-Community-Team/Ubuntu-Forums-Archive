---
title: "Problems in/with Feisty"
date: 2007-07-05
forum: General Help
---

### Post by greentiger on 2007-07-05
i recently installed feisty 7.04 on my system using wubi and the alternate iso.

i cannot for the life of me get my realtek microphone to work with anything--and frustratingly with skype.

i've read a few suggestions on how to fix this but none of them make any sense to me.

also, i cannot get wine to connect starcraft to battle.net. i tried adding some keys to HKCU for direct3d rendering and deleting fonts like a guide i found on the internet says, and i've seen people say it "just works", but when i use apt-get to check to see if i have the latest version of wine, it says that i do. when i try to connect to battle.net i get a black screen saying searching for fastest server (that message is normal), but then it just crashes to a green screen (emulated desktop) and then close wine.

some places on the net says wine doesn't work with battle.net and some says it works just fine. for whatever reason my 7.04 does NOT work with battle.net and i would like it to. any ideas or suggestions?

i have thought about going to 6.06 because at least my microphone worked.

---

### Post by kuja on 2007-07-05
Having the newest version of wine may not always be the best thing. Perhaps what you should really look for is an old version in which battle.net is known to work.  Hope this idea helps.

---

### Post by greentiger on 2007-07-05
Ok, so if i "mark for complete removal" and then reinstall the ubuntu wine package, that should work then?
i'll try it tonight and see what happens. thanks for the suggestion.

also, any ideas on the microphone issue?
as i said,i have a realtek (i guess integrated) sound card--the microphone worked in 6.06 but doesn't seem to work at all in 7.04. hopefully this will be rectified in 7.10.

as far as solutions i've looked in the forums here and can't seem to figure out a solution.

thanks

---

### Post by greentiger on 2007-07-06
i tried all the .deb versions for 7.04 and none of them work.

any hints for the microphone? or am i just screwed until 7.10?

---

### Post by fredj on 2007-07-06
Double click on the speaker icon in the taskbar this will bring up the alsa mixer. Go to Edit -> Preferences
and make sure the mic volume control is present and selected. See if you can also add a mic boost volume control or switch. Add and other controls or switches that you think you might need.

---

### Post by greentiger on 2007-07-09
> **fredj said:**
> Double click on the speaker icon in the taskbar this will bring up the alsa mixer. Go to Edit -> Preferences
and make sure the mic volume control is present and selected. See if you can also add a mic boost volume control or switch. Add and other controls or switches that you think you might need.

fine, skype still doesn't work.

---

### Post by greentiger on 2008-01-23
i figured it out by using a mic boost.
thanks for the replies.

---

