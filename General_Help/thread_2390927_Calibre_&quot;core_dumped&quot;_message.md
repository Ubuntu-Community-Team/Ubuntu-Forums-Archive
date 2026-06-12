---
title: "Calibre &quot;core dumped&quot; message"
date: 2018-05-03
forum: General Help
---

### Post by Jorhel on 2018-05-03
Hi,
I have a few other thread related to Calibre installation...
I tried installing it from the website and reinsatlling it more recently after putting the problem in the too hard basket for a while hoping that an update either at my end or theirs would have solved the problem, no such luck. Everything seems to install properly but when I try to run it I get illegal operation, core dumped.
So I tried installing it from Synaptic (not recommended by the sofware developper) and got an older version that seems to work well except for the small but vital detail of finding my Kobo Ereader...
It connects properly to the computer, I can find it via the file manager in Media, but Calibre does not acknoledge it.
ANY IDEAS???

---

### Post by Impavidus on 2018-05-04
If you run Xubuntu 16.04 (as your profile says), you get the old Calibre 2.55 from the repos. That's the disadvantage of running LTS releases and the reason why I'm on the interim releases nowadays (currently running 17.10, with Calibre 3.7. 18.04 has Calibre 3.21). So upgrading to the latest Ubuntu release could help, but that may not be necessary.

You could try a PPA, which is an alternative repository where you can find a more recent version and install it using the package manager. Ask your favourite search engine for a Calibre PPA. I think that would be the best solution. This one looks decent, but I can't guarantee it's safe to use: [https://launchpad.net/~jonathonf/+archive/ubuntu/calibre](https://launchpad.net/~jonathonf/+archive/ubuntu/calibre)

Or try it the dirty way: your file manager sees your ereader and can mount it. You can try and drop the book in, but risk missing some metadata or having to push the factory reset switch on the ereader. That wouldn't be my first choice.

---

### Post by oldos2er on 2018-05-05
Moved to General Help.

---

