---
title: "Os for server management/ultra portable and fast booting laptop"
date: 2013-11-14
forum: General Help
---

### Post by ads2996 on 2013-11-14
I have an oldish hp laptop lying around, in hope to use it as a quick boot, easy access laptop with decent battery life. I'm am trying to decide between running Ubuntu or something backtrack, or would unning both be a gd idea? I will also keep windows installed on it.

---

### Post by nerdtron on 2013-11-15
Put lubuntu on it. It may not be pretty but it will run pretty snappy.

---

### Post by ads2996 on 2013-11-15
I have used lubuntu before and I didn't really like the interface, the laptop is similar to my main laptop on specs, but with no dedicated graphics and only 2gb of ram rather than 4gb

---

### Post by nerdtron on 2013-11-15
2GB ram is good for a workstation. Even Unity or KDE will run smooth on that as long as you have a dual core processor.
As for me, I use XFCE on my main workstation. It's just a matter of personal preference.

---

### Post by ads2996 on 2013-11-15
I think I will got for Ubuntu, as I like the look of unity and it runs quick on my main laptop, however should also install backtrack for its pen testing programs that are built in

---

### Post by philinux on 2013-11-15
Moved to General Help.

---

### Post by nerdtron on 2013-11-15
Are you really going to do penetration testing on a "quick boot, easy access" laptop? But still though, no one stops you from installing backtrack. Just allocate another partition for it and ubuntu should be happy.

In case you want to triple boot I suggest the following layout of hard drive partitions:
1 partition for WinXP
1 partition for Backtrack
1 partition for Ubuntu 
1 swap partition shared for Ubuntu and backtrack.

And install the OSs in the following order: WinXP, Backtrack and then Ubuntu.

---

