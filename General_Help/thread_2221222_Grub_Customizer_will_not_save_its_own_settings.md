---
title: "Grub Customizer will not save its own settings"
date: 2014-05-01
forum: General Help
---

### Post by 7o7YlUcb on 2014-05-01
Hi,
I recently reinstalled Windows7 and then had to run Boot Repair to restore grub. I then installed Grub Customizer. I launch it and press the arrows to change the List Configuration and then press save. If I then close Grub Customizer down and relaunch it, the List Configuration has gone back to the original. Why do you think it is ignoring my changes?

There are similar questions about the actual boot order being different to the list in GC, which they say may be due to multiple grubs installations. But I think this is not the same bug as I have, as GC just doesnt seem to be saving the changes. 

It does ask me for my pasword when I launch it.

Are there any logs or something I can look at?

Here is my output from Boot Repair...
[URL="http://paste.ubuntu.com/7359099/"]http://paste.ubuntu.com/7359099/

[/URL]Ubuntu 12.04.4 LTS

---

### Post by oldos2er on 2014-05-01
If you start grub customizer in a terminal with root privileges, does it save properly? If not, the terminal output may give some clue. ```
sudo grub-customizer
```

---

### Post by 7o7YlUcb on 2014-05-03
Thanks Ann,
Tried that but couldn't see anything.
However I noticed that some things were getting saved, but the suze entries seemed to be pushing the Ubuntu and Windows entries down.
There is about half a dozen entries for suze for some strange reason so I just reformatted the partition that suze was installed in and they went away and it seems to work now.

---

