---
title: "virtual box shared folders"
date: 2012-11-15
forum: General Help
---

### Post by whynot23 on 2012-11-15
hey guys

I've been running on my ubuntu a win xp from the virtual box. The question is how to put some ubuntu directory or file to the virtual xp?

---

### Post by Mr_JMM on 2012-11-15
You need to ensure the following have been done:

1. Instal extention pack
2. Install guest additions
3. Add your Ubuntu user to the VB group (vboxsf or vboxusers).

Then you can share folders.

Also, this should probably have been asked in the Virtualisation forum - [http://ubuntuforums.org/forumdisplay.php?f=308]("http://ubuntuforums.org/forumdisplay.php?f=308")

---

### Post by dannyboy79 on 2012-11-15
nevermind

---

### Post by whynot23 on 2012-11-15
i'm sorry sorry i'm still a total noob in the ubuntu and virtual box can you describe me how to check that

can i ask the admins to move it to the right folder?

---

### Post by Mr_JMM on 2012-11-15
> **whynot23 said:**
> i'm sorry sorry i'm still a total noob in the ubuntu and virtual box can you describe me how to check that

The virtualbox website / help manual has detailed instrunctions.

In short:
Go to vb website, download extension pack for your version (if you installed VB from repos then use the second ext pack on list). Once downloaded simply click on it and it will self install.

You can install guest additions from the drop down menu in VB.

To add your user type ```
sudo adduser [your username] vboxusers
```.

> **whynot23 said:**
> can i ask the admins to move it to the right folder? Yes, you can.

---

