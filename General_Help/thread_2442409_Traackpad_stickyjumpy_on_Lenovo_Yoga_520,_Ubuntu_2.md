---
title: "Traackpad sticky/jumpy on Lenovo Yoga 520, Ubuntu 20.04"
date: 2020-05-03
forum: General Help
---

### Post by bjohas on 2020-05-03
[COLOR=#242729][FONT=Arial][FONT=inherit]Ubuntu 20.04 has thankfully resolved a lot of issues with my Lenovo Yoga 520, such as WiFi. So that's amazing!
[/FONT]
[FONT=inherit]However, there's a new intermittent issue, which is to do with the trackpad. When I move my finger over the trackpad, the pointer initially sticks. Then when I release, it jumps (to what I assume is the right position). For longer moves, the pointer catches up several times. So basically, continuous movement is not possible (unless I do lots of very small swipes, which approximates normal behaviour).[/FONT]
[FONT=inherit]
I installed 20.04 about a few days ago, and the issue first arose yesterday, then went away again, and has now returned. Rebooting doesn't make a difference: Just after a reboot, just into the desktop, with no apps running, the issue is apparent.[/FONT]
[FONT=inherit]
[/FONT][FONT=inherit]Also, this does only affect single finger swipes. With two fingers (e.g. to scroll) the response is immediate (or at least seems so).

Same behaviour occurs with USB mouse.
[/FONT]
[/FONT][/COLOR]After some more testing, I think this is a display issue. For example, my top bar is hidden. If I quickly move the pointer into the top bar, the top bar actually opens BEFORE the pointer gets there visually. So it appears that the issue is not with the trackpad driver etc, but actually with the display of the pointer.

---

### Post by bjohas on 2020-05-03
Solution: Turn off 'zoom' in the accessibility options.


I have no idea why that was causing problems, but perhaps I accidentally turned it on using a keyboard shortcut which explains the intermittent behaviour!


(Perform this test: Create a new account? Does the problem persist? No. -> clearly not a hardware problem. So I systematically started turning settings on/off and finally found the issue.)

---

