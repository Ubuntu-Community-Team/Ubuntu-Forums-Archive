---
title: "i seriously cocked up!"
date: 2007-06-16
forum: General Help
---

### Post by kadafi69 on 2007-06-16
in my infinite wisdom when im drunk, i decided to try and format an old partition on my hard drive last nite. something must have gone wrong. when i rebooted i was greeted with the glorious message 'missing NTLDR' 
so ive popped in my live cd, my main hard drive seems to have disappeared.

any ideas or suggestions? or am i just buggered?

---

### Post by bigken on 2007-06-16
missing NTLDR is a windows xp error you could try and boot from a win xp cd and use 
chkdsk /r in the repair console

---

### Post by kadafi69 on 2007-06-16
ok, tried that (not that has been a windows installation on my pc for months)
it failed to check the hard drive i mentioned and checked all the others.
looks like a re-installation job for me

---

### Post by bigken on 2007-06-16
the demon drink eh 

must say I do a gallon or 2 my self LOL

---

### Post by stefansjs on 2007-06-21
if you boot from your winXP cd and load the recovery console, you should be able to run a command called "fixboot"  (type help to see the list of commands).  This might fix your problem (assuming that your hard drive isn't blank).  I do think it is unlikely that everything is gone, because you're still getting errors from windows, so it's likely that windows is still there

---

### Post by bigken on 2007-06-22
in the repair console type fixmbr enter then fixboot enter exit enter you should now reboot into windows

---

