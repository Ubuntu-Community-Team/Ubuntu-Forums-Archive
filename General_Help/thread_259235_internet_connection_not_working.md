---
title: "internet connection not working"
date: 2006-09-17
forum: General Help
---

### Post by bananasareformonkeys on 2006-09-17
I installed Ubuntu 6.06 tuesday i think on a 6 year old G4 cube i had.  I worked until late thursday night, and i think there was actually a temporary internet outage from time warner cable.  Everything is working fine now, and i can connect to the internet with my winxp comp, but ubuntu still doesnt connect.  after fiddling with it for a little to no avail i tried loading up from the live cd.  It worked.  Since i've only been using it a couple days i reinstalled, but after reboot it cant connect to the internet.

i disabled ipv6 in firefox but its still not working.

---

### Post by TLE on 2006-09-17
> **bananasareformonkeys said:**
> I installed Ubuntu 6.06 tuesday i think on a 6 year old G4 cube i had.  I worked until late thursday night, and i think there was actually a temporary internet outage from time warner cable.  Everything is working fine now, and i can connect to the internet with my winxp comp, but ubuntu still doesnt connect.  after fiddling with it for a little to no avail i tried loading up from the live cd.  It worked.  Since i've only been using it a couple days i reinstalled, but after reboot it cant connect to the internet.

i disabled ipv6 in firefox but its still not working.

There is a bug in the internet-connection software, that MAY be what's affecting you. Try in a terminal to type:
```
sudo ifdown eth0
sudo ifup eth0
```
If that brings up your internet I can help fix it, otherwise there's something else wrong and we'll have to hope somebody else drops by.

---

### Post by bananasareformonkeys on 2006-09-17
well the first time i tried that i got an error on the 
sudo ifup eth0
timestamp too far in the future.
that's when i realized my clock is set 4 hours off.  So i changed it.  when i tried that again the last thing it says is:
mv: cannot move '/etc/resolv.cong.dhclient-new' to '/etc/resolv.conf': Operation not permitted

so, it didnt work

---

### Post by TLE on 2006-09-17
Weel then I'm afraid I can't help you. I hope somebody else is reading along.

---

### Post by bananasareformonkeys on 2006-09-17
so i got it working after installing ubuntu from the beginning again.  I think there may be a problem with the hardware clock.

---

### Post by TLE on 2006-09-17
Ok great. Have fun with it.

---

### Post by bananasareformonkeys on 2006-09-19
i'm still having some problems with the internet connection, but the sudo ifdown / ifup makes it work.  So what is the bug?  and how do i fix it?

by the way, my clock always resets to four hours too early when i restart... any ideas why?  I thought maybe it was the hardware clock, but it's always exactly 4 hours too slow.

---

### Post by TLE on 2006-09-19
> **bananasareformonkeys said:**
> i'm still having some problems with the internet connection, but the sudo ifdown / ifup makes it work.  So what is the bug?  and how do i fix it?

by the way, my clock always resets to four hours too early when i restart... any ideas why?  I thought maybe it was the hardware clock, but it's always exactly 4 hours too slow.

I don't know what the bug is, i think, (as in I think, this is pure speculation) that something is wrong with the order in which things are started at boottime, and that's why I haven't been pushing trying to find the real reason since Edgy will have a brand new startup deamon. Anyway what works for me is to put those two commands in the ```
/etc/rc.local
``` file, so that it it'll look somthing like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo ifdown eth0
sudo ifup eth0

exit 0

```
remember to use sudo when you open the file in an editor or you wont be allowed to write to it.

As for whats wrong with your clock, I don't know, maybe somebody else have an input, otherwise try to search the forum for it, I think I once read something similar.
Regards TLE

---

### Post by bananasareformonkeys on 2006-09-20
unfortunately it didnt quite work.  I think its because i actually have to type in:

sudo dhclient
sudo ifdown eth0
sudo ifup eth0

to make the internet work.
do i need to put password permission into it somehow?


and does any know why my clock sets itself four hours back when i restart? it's only when i restart, not when i turn off the computer.

---

### Post by TLE on 2006-09-20
> **bananasareformonkeys said:**
> do i need to put password permission into it somehow?
No, just add the extra line and see if it works

---

### Post by x1a4 on 2006-12-22
Try this:  

As root, create a file called 

/etc/modprobe.d/bad_list

with the following content

alias net-pf-10 off

then reboot.

---

