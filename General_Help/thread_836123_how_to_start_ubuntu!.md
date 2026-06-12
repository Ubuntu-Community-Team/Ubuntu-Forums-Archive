---
title: "how to start ubuntu!"
date: 2008-06-21
forum: General Help
---

### Post by ramadan on 2008-06-21
I've ubuntu installed along with windows Xp, ( Grup loader)
1. how to make xp as  default boot system
2. how to start ubuntu in low graphics mode( failed to boot due to display drivers problem)
everyhelp is appreciated

---

### Post by geo909 on 2008-06-21
For your #1 question.

Make a backup of your grub menu configuration file:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_BACKUP
```

Then change it:

```
sudo gedit /boot/grub/menu.lst
```

Copy-paste the lines for XP over the ones for ubuntu.
That makes it default.

---

### Post by ajgreeny on 2008-06-21
> Copy-paste the lines for XP over the ones for ubuntu.
That makes it default.

That's a bit confusing to someone who perhaps doesn't know the intricacies of grub!  It makes it sound as though you overwrite the ubuntu entry with the windows entry.  That would have removed the ubuntu entry totally.  It would have been safer to say

"Copy-paste the lines for XP **above** the ones for ubuntu.
That makes it default."

---

### Post by steveneddy on 2008-06-21
> **ajgreeny said:**
> That's a bit confusing to someone who perhaps doesn't know the intricacies of grub!  It makes it sound as though you overwrite the ubuntu entry with the windows entry.  That would have removed the ubuntu entry totally.  It would have been safer to say

"Copy-paste the lines for XP **above** the ones for ubuntu.
That makes it default."

Seems right to me.

Is it full of gas?

---

### Post by geo909 on 2008-06-21
> **ajgreeny said:**
> That's a bit confusing to someone who perhaps doesn't know the intricacies of grub!  It makes it sound as though you overwrite the ubuntu entry with the windows entry.  That would have removed the ubuntu entry totally.  It would have been safer to say

"Copy-paste the lines for XP **above** the ones for ubuntu.
That makes it default."

Gee, you're right! "Over" would be normally taken as "overwrite". "Above" is the right word.

So sorry, hope I didn't create any problems..

It's that I'm not an English speaker and I often make such mistakes.

---

### Post by ramadan on 2008-06-21
thanks to all of you, I'll try this soon and keep you informed

---

### Post by ramadan on 2008-06-21
i pressed Esc >.there is no way to copy and paste, just e to edit and b to boot,
so  i choosed e and give me choices : make active, savedefault, so i tried to choose savedefault( cos xp was highlited) prssing enter but no response.
so did i miss anything? i cant boot into ubuntu

---

### Post by ajgreeny on 2008-06-21
You need to edit the menu.lst file.  In terminal type ```
gksudo gedit /boot/grub/menu.lst
``` give your password when asked, which will not show in the terminal, and the file will open with root permissions so you can edit and save it.  Now add the windows entry at the bottom of the file to the top position in the file, not right at the top, but at the top of the listed operating systems.  You should now boot straight into windows but ubuntu will be at the second entry in the grub menu.

---

