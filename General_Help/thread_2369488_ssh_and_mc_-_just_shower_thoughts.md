---
title: "ssh and mc - just shower thoughts"
date: 2017-08-23
forum: General Help
---

### Post by marchello_lippi2 on 2017-08-23
Hi all, 
Just shower thoughts about ssh and mc... ) 
Let's say, I connect to remote computerA using ssh and start mc there. 
Then I connect to the computerB on the left panel using ssh. 
Next I connect to the computerC on the right panel using ssh. 
(why? let's say, it is just convenient as ssh keys for both computerB and computerC are stored at computerA)

Now I copy file from computerB to computerC. 
Does computerA work as mediator and the traffic goes through it?

---

### Post by SeijiSensei on 2017-08-23
I haven't used mc in quite a while, but regardless, yes I believe the copy will not go directly from B to C, but through A.  Midnight Commander has no way to make a direct connection between the two machines.

You might look into [sshfs]("https://help.ubuntu.com/community/SSHFS") which will let you map remote filesystems with SSH.  Then you could mount B and C to directories on each other.  Connect with SSH to either machine from A and copy files directly between B and C.

---

### Post by marchello_lippi2 on 2017-08-24
Now it is not only shower thoughts. 
Transferred file was stored at computerA in /tmp/mc-[username] folder. As it was huge, it filled all available space. 
Just FYI if someone will try to repeat this...

---

