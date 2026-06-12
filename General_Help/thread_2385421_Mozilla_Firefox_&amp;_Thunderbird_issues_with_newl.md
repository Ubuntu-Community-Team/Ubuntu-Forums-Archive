---
title: "Mozilla Firefox &amp; Thunderbird issues with newly installed 16.04"
date: 2018-02-20
forum: General Help
---

### Post by Richard_York on 2018-02-20
I've just installed Ubuntu 16.04 to dual boot alongside Windows10 on a new-to-us desktop built in 2011. I've kept W10 just in case things go wrong, also because I'm not confident how I'd reinstall Windows if I wipe it. Ubuntu's still settling down, at least I hope it is, but then I hope to transfer our massive collection of emails on Thunderbird from the previous desktop machine, likewise our profiles and settings on Firefox.

The source machine is 32-bit, running 14.04, the newer one's a 64-bit machine.

 When I originally moved from Windows XP to Ubuntu 14, I re-formatted the whole disc and installed on single boot,  I was able to pick up  and save the relevant profile details in Thunderbird, save them on an external drive, and drop them into the new Thunderbird profile folder, re-named to match what was already there. I've now forgotten the route by which I did this, but it felt gratifyingly simple at the time, given I was very nervous and unsure of the whole procedure. I'm still very tentative about it all.

So (i) will it work taking these from a 32-bit system and dropping them into a 64-bit?
(ii) please will some kind person remind me where they are found now?

Can I still do the same with Firefox, importing all the bookmarks etc.? And if so, where do I find the relevant folder and files?

With thanks for any help, the less technically written the better!

---

### Post by ajgreeny on 2018-02-20
All should be fine if you simply copy the two hidden folders, **~/.mozilla** (for firefox) and **~/.thunderbird**, from your old 32 bit system's home folder and paste them into your new home folder in the 64 bit system.
If you have already started firefox and thunderbird in the new system you will first have to delete those two hidden folders before pasting the new ones in.

The different architectures will not matter for those configuration folders so just go ahead and copy them over.

Just in case you're not aware of this, you need to press Ctrl+H to show all hidden files and folders in the file manager.

---

### Post by Richard_York on 2018-02-20
Thank you, that's very helpful and reassuring. So it's the whole** /.mozilla**  folder to copy in, then? Last time, following instructions, I isolated just a specific profile folder buried somewhere within that main folder. This seems much easier. No need to change folder names to match the system's expectations, either?
Thanks again.

---

