---
title: "Shift wont work alongside alt or ctrl"
date: 2007-02-21
forum: General Help
---

### Post by Vegiemaster on 2007-02-21
Hi,
I've been a Edgy user for some time now, and I love using workspaces and being able to move windows back and forth with ctrl alt shift right/left.  However, for some reason this combination will not work anymore.  Note: It is definitely set up correctly in Gnome Keyboard Shortcuts.  Trust me, it's set up as far as that goes.  But I've discovered that My shift key will not function alongside alt or ctrl.  I can use shift + whatever, but if I throw in alt or ctrl, nothing happens at all.  It's like it cancels it out.  I've tried searching both Google and these forums, but find nothing.  Some help would be greatly appreciated.

I believe it stopped working around when I installed XGL/Beryl and used xmodmap .../xmodmap.us.  Could that be it?  I've stopped using Xgl but the problem still exists.

Thanks

---

### Post by highneko on 2007-02-21
Is this both sides of your keyboard? Do the left shift+alt+ctl keys work together?

---

### Post by Vegiemaster on 2007-02-21
Same behavior on both sides.

---

### Post by Vegiemaster on 2007-02-22
Bump.

Has anyone seen this before?  Is there a way for me to just blow away my current keyboard configuration?

---

### Post by VCSkier on 2007-03-09
this just happened to me too, today...  its really annoying.  for me, my shift key stopped working altogether.  arg.  i'm trying to use exclaimation points, but i can't...  no...  shift...  please help....  ahhh.... [/mild-but desperate-sarcasm]  seriously though, whats going on[question-mark] :)

---

### Post by VCSkier on 2007-03-19
My problem was linked to Beryl somehow.  I did an aptitude purge beryl, deleted my ~/.beryl, and then reinstalled it, and everything is fine again.  I don't know how that happened, but I'm glad to have my shift back!  :)

---

### Post by larytet on 2008-02-17
Left Ctrl + Left Shift stopped working for me after one of the updates

Rigth Ctrl+left shift+Arrow Left/Right do the work - select word
Left Ctrl+Left Shift+Left/Right Arrow do not work


Also I using xkeymaps I discovered that Ctrl-Y and Ctrl-T do not work either

I reinstalled Ubuntu to 7.10, did not help

i tried xkeymaps (GUI front end for xmodmap - indeed Left Ctrl+Left SHift does not produce codes

wireless desktop Logitech S510, works perfectly with WinXP.

i will appreciate any tip


[Update]in the xkeycaps when i click Left Ctrl + Left shift only LeftCtrl is colored by yellow on the virtual keyboard. I am using PC101 wide Delete tall Enter layout. this layout produces correct mapping when i click every key alone.

---

### Post by larytet on 2008-02-17
i tried to follow this thread 

[http://ubuntuforums.org/showthread.php?t=610302](http://ubuntuforums.org/showthread.php?t=610302)

no result

regular HP wired keyboard works just fine
so the problem is specific to the Logitech S510. Something is got killed in that patch for S510

Logitech S510 has a receiver connected to the USB
the wired keyboard i am using is an old USB 105 keys keyboard from HP. PC i am working with does not have PS2 connector

---

### Post by larytet on 2008-06-04
> **Vegiemaster said:**
> Bump.

Has anyone seen this before?  Is there a way for me to just blow away my current keyboard configuration?

yes, same here - Logitech S 510 used to work just fine
upgrade to 8.04 does not help
clean install of 8.04 does not help

---

