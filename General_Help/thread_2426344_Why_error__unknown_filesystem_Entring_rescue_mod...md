---
title: "Why error : unknown filesystem Entring rescue mod.. grub rescue&gt;  always happen"
date: 2019-09-07
forum: General Help
---

### Post by agungprawira on 2019-09-07
[FONT=trebuchet ms]firsty i have to say that this is a mainstream topic, but seriously i have no idea to fix this
i have just installed ubuntu 18.04, everytime when i start or restart my notebook, this problem always happen
[B]error : unknown filesystem
[/B][/FONT][INDENT][FONT=trebuchet ms]Entring rescue mod..
grub rescue> 
[/FONT][/INDENT]
[FONT=trebuchet ms]
but i always can fix this problem by[/FONT][INDENT][FONT=trebuchet ms][B][B]set boot=(hd0,msdos5)/grub
set prefix=(hd0,msdos5)/boot/grub
insmod normal
normal[/B]
[/B][/FONT][/INDENT]
[FONT=trebuchet ms]so the question is how i can fix this problem ? i mean i don't want this error always happen when i start to use my notebook.
[/FONT]

---

### Post by Rubi1200 on 2019-09-07
Hi and welcome to the forums :-)

If you can boot back into Ubuntu using those commands, then you need to reinstall GRUB to sort the problem out.

Open a terminal:

```
sudo grub-install /dev/sda
```

followed by

```
sudo apt-get update
```

and

```
sudo apt-get upgrade
```

Note that this assumes you have only one HD called sda. If you are dual-booting or have some other setup please let us know before you change anything.

Good luck!

---

### Post by agungprawira on 2019-09-07
no, i use linux as my main os.
thank you for your help sir, it's really work. thank you

---

### Post by Rubi1200 on 2019-09-07
Well, to fix the problem you definitely need to reinstall GRUB.

Run the first 2 commands and everything should be fine again.

---

### Post by Rubi1200 on 2019-09-07
> **agungprawira said:**
> no, i use linux as my main os.
thank you for your help sir, it's really work. thank you

Glad to hear you got it sorted out.

Please mark the thread Solved using Thread Tools at the top of the first post so others can also find the solution.

Good luck!

---

