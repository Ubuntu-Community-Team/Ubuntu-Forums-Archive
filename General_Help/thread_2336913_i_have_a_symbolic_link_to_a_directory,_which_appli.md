---
title: "i have a symbolic link to a directory, which application should i choose to open with"
date: 2016-09-12
forum: General Help
---

### Post by dleghthikos on 2016-09-12
i feel like i am trying to do something i am not supposed to be doing:  in windows, there are 'shortcuts' to files and directories- are you not supposed to use some functional equivalent in ubuntu?  i have created a 'symbolic link' to a directory but when i try to open it, i am prompted with a 'choose application' dialog box.  am i doing something i'm not supposed to be doing?  how do day-to-day casual ubuntu users access their files/directories?  btw this question relates to a lubuntu install, specifically.

---

### Post by howefield on 2016-09-12
How have you created the link, can you share what you have done  ?

---

### Post by QIII on 2016-09-12
Hello!

How did you create the symlink?

Edit:  Great minds think alike.  Greater minds type more slowly.

---

### Post by dleghthikos on 2016-09-13
by holding ctrl + shift and drag and dropping the icon

by the way, by restarting the application i set as default (a file manager, pcmanfm specifically) started working as i expected, so symbolic links now work as expected for directories and files
(context: i had set it, but the setting didn't take effect until restarting)

---

### Post by howefield on 2016-09-13
> **QIII said:**
> ...Edit:  Great minds think alike.  Greater minds type more slowly.

I have no doubt about that :)

> **dleghthikos said:**
> ... so symbolic links now work as expected for directories and files context: i had set it, but the setting didn't take effect until restarting)

OK, glad you got it, I'd normally use ln -s in the command line but Ctrl + Shift and drag works well too.

---

