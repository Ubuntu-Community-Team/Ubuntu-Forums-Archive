---
title: "console language"
date: 2005-10-19
forum: General Help
---

### Post by myha on 2005-10-19
Hi all!

I really need a help on this one... It's bothering me for quite a while now...

I cant set keyboard language in console to slovenian.... And this is really annoying, cause I have slo language in gnome and englist in console, so all the keys are diffrent... :???: 

I tried dpkg-reconfigure locales but it doesnt help...

Can anyone help me plese?

Thanks,
Miha

---

### Post by kairu0 on 2005-10-19
You probably have to edit /etc/environment (LANG and LANGUAGE variables to be safe.)

---

### Post by NiN on 2005-10-20
Hi!

if you want to change the keyboard language in console just type

dpkg-reconfigure console-data

then you can choose your preferred layout.

[edit]
of course you have to do that with sudo ;)
[/edit]

---

### Post by myha on 2005-10-20
Yes! Finally....  :)  Thanks, Nin, it works now...
Thank you very much!

@kairu0: I did edit the /etc/environment and it changed language but not in console...

regard,
Miha

---

