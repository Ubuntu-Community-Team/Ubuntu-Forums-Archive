---
title: "Fsck and stream of numbers"
date: 2017-12-16
forum: General Help
---

### Post by girandolian on 2017-12-16
Hey everybody, new Ubuntu user here. 

Could you confirm if this endless stream of hex codes is a stage of the fsck process?

[IMG]https://i.imgur.com/Z0u4J06.png[/IMG]

It's been going on for several hours now and I couldn't find references about it by other users so far.

More info: I used my Ubuntu USB to run fsck -yes /dev/sdb2 from the Boot menu on my old laptop. It runs fine and then skips to this endless stream of numbers. Tho it's not recommended, I restarted the laptop mid-process once to confirm if the same thing would happen again.

 Thank you for any insight.

---

### Post by deadflowr on 2017-12-16
> Could you confirm if this endless stream of hex codes is a stage of the fsck process?
No, because I (and no one else either) cannot read what it actually says.
I don't think it's normal though, fwiw.

---

### Post by ajgreeny on 2017-12-16
What was the command you used, and was the partition your are checking unmounted? 

It should really be unmounted, or mounted as read-only, which I believe can work but I have no experience of that as I have only ever used fsck from a live system booted from USB.

I have never seen any output like that whenever I've used fsck, so like deadflowr, I think something is wrong with the fsck process, or your partition filesystem is completely corrupt.

---

### Post by girandolian on 2017-12-17
Just confirming for any other user that might Google this: I let it run and the fsck process finished fine a couple hours later.

---

### Post by ajgreeny on 2017-12-17
And did fsck report any faults that it had found or repaired, or did it just finish quietly?

You still did not tell us what command you used which might give a clue about what is going on here.

---

