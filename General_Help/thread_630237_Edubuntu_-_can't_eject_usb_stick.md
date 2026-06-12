---
title: "Edubuntu - can't eject usb stick"
date: 2007-12-03
forum: General Help
---

### Post by peterroots on 2007-12-03
There seem to be many posts on this, none seem to give an answer that works so here goes with another try!

Using Edubuntu
we can insert a flash drive and it mounts and displays fine, and seems to be owned by the user that plugged it in.
The problem is there is no unmount or eject option on the right click menu so how do we get them out again (short of turning off the computer or crossing your fingers and yanking it out)?

File -> unmount volume announces that the volume is not in fstab and you are not root
using a terminal for eject volume does not work
using a terminal and umount volume does not work but sudo umount volume does work (but who in their right mind would give a hundred students access to administrator privileges)

A post pointed me to a file /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi and suggested changing the reference for safe eject to true - it already was set to true
(on my own computer running kubuntu 7.04 there is an eject option on right click it is just a problem on the school Edubuntu computers)

Any bright ideas out there?

---

### Post by peterroots on 2007-12-10
still not fixed it but the problem is with the client computers not the terminal server - if I log in on the terminal server and plug a usb stick into this machine, everything works as expected/as it should.  The problem arrises when a usb is plugged physically into any of the client cmoputers.
Any ideas anyone?

---

