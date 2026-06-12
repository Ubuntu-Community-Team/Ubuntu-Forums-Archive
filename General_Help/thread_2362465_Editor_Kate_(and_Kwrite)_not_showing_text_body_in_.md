---
title: "Editor Kate (and Kwrite) not showing text body in Lubuntu"
date: 2017-05-29
forum: General Help
---

### Post by xinuzi on 2017-05-29
Maybe I'll send Kate-development a bugreport, or maybe someone here knows the solution to a problem I have with the Kate editor on Lubuntu 16.04 LTS X64.

This problem:

When I choose to open a .txt file with Kate or with Kwrite, the file loads, but without body text.
The same in case of 'Always Open with'.
A small popup with 'new file' appears and disappears within Kate and thereafter: nothing.

Other (text) editors: no problem.

---

### Post by vasa1 on 2017-05-29
Do you see any messages when you run these programs from a terminal window?

---

### Post by oldos2er on 2017-05-29
Here's a silly thought: If you swipe or mark where the text should be, does it show up?

---

### Post by #&amp;thj^% on 2017-05-29
Just one more thing to check also...Under Tools>>at the top of kate,
Be sure the Read Only is un-ticked.

---

### Post by xinuzi on 2017-06-02
I see I'll have to check a few things concerning Kate in Lubuntu 16.04 LTS X64.

I'll do that when I'm at the location where that computer is situated ;)

Thanks for the tips already!

---

### Post by martin3d on 2017-09-13
I have this problem too. It worked with Lubuntu 14.04 and does not work with Lubuntu 16.04.
Kate version is 15.12.3. I did not change any settings. Leafpad (the standard Lubuntu text editor)
works fine).

When a file is opened, the text-window is empty. A message says: "Neue Datei" (= "New file",
I have german Kate)

[ATTACH=CONFIG]276705[/ATTACH]

---

### Post by martin3d on 2017-09-13
No. There are no messages in the terminal.

---

### Post by martin3d on 2017-11-29
I have a solution. You have to change the .desktop-Shortcut from:
kate -b %U
to:
kate -b %F

this worked for me with Ubuntu 16.04 and Kate 15.12.3

---

