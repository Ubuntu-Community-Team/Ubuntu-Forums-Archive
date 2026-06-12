---
title: "Acid rip does not find my dvd player or file path is wierd"
date: 2014-09-07
forum: General Help
---

### Post by patrikmellq on 2014-09-07
Hello i try to rip some dvd's that i have ...
But i don't know how to write the file path to my dvd ...

This is how it looks like, my dvd is at my "media" folder ...

[IMG]http://i61.tinypic.com/2qc36u0.jpg[/IMG]


The name of the dvd is "UDF Volume" or is it the cd device ... not sure

[IMG]http://i57.tinypic.com/2hd44qq.png[/IMG]

Now i try to write /media/UDF Volume as file path for "acid rip" to find and rip my dvd, but there is no such file path.
When i click on UDF Volume so comes the dvd files up ...

[IMG]http://i58.tinypic.com/2aion42.png[/IMG]

And when i click on VIDEO_TS i can see the files that i want to rip with "acid rip"

[IMG]http://i61.tinypic.com/2dspwyv.jpg[/IMG]

But i don't know the search or file path to the dvd?
That is what i need help with.

[IMG]http://i59.tinypic.com/2s79amq.png[/IMG]

[IMG]http://i57.tinypic.com/sm3b86.png[/IMG]

I test the following file path.

/media/UDF Volume/VIDEO_TS and it does not work

I also try with terminal to try to find the search path or file path to my dvd
When i write cd /media i come to that folder
Then i write ls to list files in that folder and can see UDF Volume

**So i have no clue how i got to get the right file patch to my dvd to tell acid rip to load it!!!**

[IMG]http://i62.tinypic.com/2podzxc.png[/IMG]

---

### Post by mc4man on 2014-09-07
run
```
sudo lshw -c disk
```
Look under the *-cdrom section for your dvd drive, use one of the dev links shown, usually /dev/sr0 or /dev/sr1

---

