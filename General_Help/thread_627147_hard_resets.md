---
title: "hard resets"
date: 2007-11-29
forum: General Help
---

### Post by raichle on 2007-11-29
Occasionally I have to do a hard reset on my laptop running 7.10.   I think it's a memory issue, but occasionally it will lock up and there is nothing I can do but hold the power button down till it shuts down.   This happens on my windows partition as well.   

Is there anything I should be worried about?  Is there any cleaning up I need to do after this happens?

It's a temporary situation as a I wait for another laptop so I don't want to fork out the money for new RAM.


thanks!

---

### Post by PmDematagoda on 2007-11-29
I believe that the problem is memory oriented (as do you), I fixed it by simply cleaning the memory modules out and switching their locations a little.

If you want a good way of safely restarting Ubuntu when it is frozen so that your data and Hard Drive would be intact, I advise you to look [here]("http://ubuntuforums.org/showthread.php?t=617349").

---

### Post by teryowen on 2007-11-29
Just make sure when and if it lags dont start pressing even more buttons to see if it works as this overloads it further at first sign of lag take a pause, other its lag see if you can limit the amoung of process running. Thats all the ideas i have.

---

### Post by raichle on 2007-11-29
so I tried following the directions linked to above and I held alt+print screen and then typed in order r s e i u b  and that only served to lock things up.  What am I doing wrong?

---

### Post by PmDematagoda on 2007-11-29
Sorry, could you be a little more clearer?

You said that you did the sequence and it froze, but in what way?

---

### Post by atlfalcons866 on 2007-11-29
hard resets can sometimes corrupt file systems but i doubt that is the reason if your using a jorunaled file system (ext3t,reiserfs,xfs,jfs)

---

### Post by PmDematagoda on 2007-11-29
> **atlfalcons866 said:**
> hard resets can sometimes corrupt file systems but i doubt that is the reason if your using a jorunaled file system (ext3t,reiserfs,xfs,jfs)

Actually they can occur on journaled file systems as well, especially if data was being written to the HDD when you cold restarted the PC, so it is safer to first unmount all the drives and then go for the cold reboot.

---

