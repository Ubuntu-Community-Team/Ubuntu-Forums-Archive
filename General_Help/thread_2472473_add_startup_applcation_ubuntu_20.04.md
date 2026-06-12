---
title: "add startup applcation ubuntu 20.04"
date: 2022-02-28
forum: General Help
---

### Post by nzer2022 on 2022-02-28
adding a startup application doesnt work, or save when i add it ? i add it here press close and then it disappears?? also add manually to systemctl startup service but doersnt startup ,, im on ubunutu 20.04LTS

---

### Post by vanadium on 2022-03-01
Expected behavior is that the entry you added appears in the list after you filled the data. Any data, in fact: the only required field is "Command", and there is no checking on whether the command is valid or not. The tool should automatically create a .desktop file in ~/.local/share/applications.

Difficult to assess what might be wrong in your case. Perhaps you do not do it the right way, perhaps permissions of your ~/.local/share are not correct?

---

### Post by mIk3_08 on 2022-03-01
> **nzer2022 said:**
> adding a startup application doesnt work, or save when i add it ? [IMG]https://ubuntuforums.org/attachment.php?attachmentid=290104&stc=1[/IMG]
i add it here press close and then it disappears?? also add manually to systemctl startup service but doersnt startup ,, im on ubunutu 20.04LTS
> **vanadium said:**
> command is valid or not.  I agree with  the command that is valid or not. You should better know the running  application name command is correct. for verifying it, try using the  terminal to verify it. Good Luck and Cheers

---

### Post by GhX6GZMB on 2022-03-01
If login as the main user, the menu items (.desktop files) are stored in /usr/share/applications

---

