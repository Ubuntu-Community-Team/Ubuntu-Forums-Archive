---
title: "stupid stupid mouse gestures"
date: 2007-10-23
forum: General Help
---

### Post by audunmb on 2007-10-23
yeah, I want to get rid of them or at least control them. It some kind of shortcut connected to the scrolling on my touchpad which gives browsers(both Opera and Firefox) commands like Back, Forward, Home and trying to connect to non-existing links. I can't figure out exactly how to do any of the commands, it just happens when I touch the scrollbar. 

I've never installed anything to get it, it came with gutsy and it's just annoying. I use the scrollbar to scroll! 

I tried qsynaptics and gsynaptics, and looked at the xorg.conf-file, but couldn't figure out any way to turn it off. Neither Opera nor Firefox had any options to turn it off, or any indication that this should happen at all. 

When it's bugging me, I consider it a bug, not a feature.

---

### Post by kidders on 2007-10-24
> **audunmb said:**
> Neither Opera nor Firefox had any options to turn it offThat's not true. What you're describing sounds like the normal behaviour of what would be button #2 & a horizontal scroll wheel on a conventional mouse, not mouse gestures. Your trackpad is presumably just emulating these functions, which is a typical enough approach to their design. Both Opera & Firefox do allow you to override or remove most of these buttons' functionality, from their advanced settings.

If you'd like to file a bug, check out Opera & Firefox's bug databases.

---

### Post by audunmb on 2007-10-29
Thanks for replying. 

I really can't find these options in Firefox or Opera, Not under the Advanced tab at least. 
You're probably right that this isn't mouse gestures... but button 2 and scrollbar. So with Gutsy there suddenly is a button 2 in the upperleft corner of my touchpad and also a button 3 behaviour somewhere else on the touchpad. I really prefer my previous setup with button 3 on two finger-click and button 2 on three finger-click (which still works), but these *new* buttons.

How do I get rid of them?

---

### Post by audunmb on 2007-10-29
Ah, I did find it. synclient does this

---

### Post by kidders on 2007-10-29
> **audunmb said:**
> Thanks for replying.No worries. :-)

Advanced settings like these are most easily accessible by visiting "about:config" in Firefox, for example ... but these would be application-specific settings only. If you prefer your mouse buttons to work differently (in terms of how you trigger them, rather than what application functions are bound to them), xorg.conf is the thing to fiddle with. Within reason, your mouse buttons & virtual scrollwheels can be made to work any way you want, once you know the hardware- & driver-specific configuration changes to make.

I can see where you're coming from though ... trying to cram too much functionality into a touchpad just makes it hard to use imo. Personally, I _hate_ the way browsers bind history navigation to horizontal scrolling, and always disable it. On the other hand, other application-specific functionality (eg desktop switching) can be handy.

Anyhow, it seems like you're all sorted out now.

---

### Post by Dr.Noodle on 2008-05-05
> **audunmb said:**
> Ah, I did find it. synclient does this

Could you explain in a bit more detail how you resolved this issue?

I have the same problem with my wireless mouse which every time i scroll up and down it triggers firefox's navigation.

---

### Post by Dr.Noodle on 2008-05-05
> **Dr.Noodle said:**
> Could you explain in a bit more detail how you resolved this issue?

I have the same problem with my wireless mouse which every time i scroll up and down it triggers firefox's navigation.

I've trawled through the about:config in ff to no avail. Synclient in terminal i have no idea what im doing with it. however it just flags up the following when i enter this command...

```

Linux:~$ synclient -l
Can't access shared memory area. SHMConfig disabled?
```

Im also not sure on how to alter my xorg.conf!


Dont you just love new guys eh! :)

---

