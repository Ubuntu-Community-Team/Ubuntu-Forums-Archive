---
title: "Login trouble"
date: 2007-08-24
forum: General Help
---

### Post by Speshec on 2007-08-24
I've installed Ubuntu using wubi ( russian language) , but I can't login. I enter login but it inputs with arabic letters from right to left. I've changed language (F10...) but it dosen't  works, layout is still arabic, and I can't change it.
What should I do?

---

### Post by tuxcantfly on 2007-08-24
Try going into a console with Ctrl-alt-F2, and you should be able to login from there. Then, choose the russian locale using this guide:  [http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html](http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html)

---

### Post by Speshec on 2007-08-26
I can't login even using console, all input simbols shows as vertical arrows... Strange

---

### Post by tuxcantfly on 2007-08-26
> **Speshec said:**
> I can't login even using console, all input simbols shows as vertical arrows... Strange

That really does sound strange... However, even despite the symbols, I believe the input is the same; just memorize your username and password, and all the commands you need to enter (see my previous post), then just type them in, and despite the symbols, you should still be able to login.

However, if you still can't log in, try using recovery mode (Select Ubuntu on the boot menu, then hammer away at the ESC button right afterwards, that should give you an option of selecting recovery mode, if it gives you only "Ubuntu", just press enter and hammer away at ESC again, then select the "Ubuntu (original kernel)" option, find the line that starts with "kernel", press e to edit, and add to the end of the line "single", then press enter to save, then press b to boot), that'll log you in as root, then type in the commands listed in the link above to change your locale.

---

### Post by tlinsenm on 2007-09-28
Hello,
I'm having exactly the same problem:
I installed (German) Ubuntu via Wubi 7.04.04 on my (German) Thinkpad R51 and only get Arabic at the login prompt.
The solutions suggested here do not work: Ctrl-Alt-F2 gets me to console all right, but there I get the same triangles as Speshec - tuxcantfly's assumption that these are only a mask to cover the password is unfortunately incorrect. Booting to recovery mode does not help either: at the login prompt (not in grub, though!), the only keys that work are dot and slash, pressing all other keys just results in a beep - presumably they're still Arabic. Any more suggestions? Thanks!

---

