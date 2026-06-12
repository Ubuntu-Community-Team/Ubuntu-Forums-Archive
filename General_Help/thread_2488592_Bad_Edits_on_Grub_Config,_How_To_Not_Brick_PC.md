---
title: "Bad Edits on Grub Config, How To Not Brick PC?"
date: 2023-07-10
forum: General Help
---

### Post by despondent-aviator on 2023-07-10
Relatively new to Linux. Ran **sudo vi /etc/default/grub** through terminal, was met with my config as expected, but when I attempted to make edits to my **GRUB_CMDLINE_LINUX=""** my arrow keys only made text inputs, and I couldn't delete alterations. I closed the terminal at this point since I couldn't delete the gibberish lines I made. Opening the config again I was met with a E325 code warning me that a swap file for the config already existed, and was likely (2) due to an edit session crashing. Ignoring this and continuing I ran into the same issue over again. I don't believe I can post images yet for a visual example, but anyone answering on how to actually make edits to my Grub Config would be appreciated. I was following a guide for a different Distro, so perhaps using the **vi **command was in error?

EDIT: Tried looking for how to edit tags, but this is Ubuntu 23.04.

---

### Post by Rubi1200 on 2023-07-10
Hi and welcome to the forums :-)

Are you able to post the results of this command

```
cat /etc/default/grub
```

Or do you get errors?

---

### Post by tea for one on 2023-07-10
> **despondent-aviator said:**
> Relatively new to Linux.
> **despondent-aviator said:**
> I was following a guide for a different Distro, 
Well, that probably wasn't a good idea ;)
Just curious, which guide were you using?

To edit grub files, I would suggest:-
```
sudo nano /etc/default/grub
```

---

### Post by despondent-aviator on 2023-07-10
That's it, thank you!

For your curiosity, it was [https://www.youtube.com/watch?v=eTWf5D092VY](https://www.youtube.com/watch?v=eTWf5D092VY)

---

### Post by yancek on 2023-07-11
You now likely have a file:  /etc/default/grub.swp which you will need to delete (use sudo) before you can do an edit of that file with vi.  You first need to hit the i key to insert and then properly close the file or this will happen.  To close a file, one way to do it is to hit the Esc key then type in :wq  and hit the Enter key to save changes.  If you continue to use nano, it won't matter.

---

