---
title: "During update keep the present grub or install the new grub"
date: 2014-07-22
forum: General Help
---

### Post by Sherman_Willden on 2014-07-22
I just updated Ubuntu and it installed some new grub files. It stopped and presented a new window asking about the grub. Should I have installed the new grub? A line in the window stated that the present grub was changed and do I want to keep it.

Thank you;

Sherman

---

### Post by oldfred on 2014-07-22
I have had similar questions back when doing full version updates.

It is a lose, lose question.
But if you have modified your grub, then your settings may not work with the new version or if you accept the new one any changes you made will be lost. 

Did you use grub customizer or make any manual changes to grub configuration.

If you did not modify grub then you should select the maintainers version or the updates.

Best to always backup your changes and always accept new version. You may have to reapply your changes, but that can be easier than finding & fixing entries that do not work with a new version.

---

### Post by Bashing-om on 2014-07-22
Sherman_Willden; Hi !

+1 to oldfred's recommendation to "  always accept new version " . I too had that grub update this AM. It is minor to go back and re-edit grub to what you desire.

Remember to update-grub once the changes have been made.
```

sudo update-grub

```

[INDENT][INDENT]all will be well
[/INDENT][/INDENT]

---

### Post by Sherman_Willden on 2014-07-23
Thank you;

Sherman

---

