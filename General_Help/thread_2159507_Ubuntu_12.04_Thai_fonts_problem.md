---
title: "Ubuntu 12.04 Thai fonts problem"
date: 2013-07-03
forum: General Help
---

### Post by sathitth on 2013-07-03
I accidentally rename /usr/share/fonts into /usr/share/.fonts. After I recovered it, I had problem viewing Thai fonts in many application.
 
I also attached print screens of some applications with Thai fonts problem.
1) Font Manager
2) Thunderbird
3) Nautilus

Thank you.
SATHIT T.

---

### Post by sathitth on 2013-07-08
$ sudo chmod 644 /usr/share/fonts/*
$ sudo fc-cache -fv
The above two instructions solved he problem in "Font Manager", and thunderbird. However, the Nautilus still have the problem.

Please let me know if I should post may question  in different forum. 

Thank you.
SATHIT T.

---

### Post by sathitth on 2013-07-08
After I reboot, the problem came back again. There are problems in
[COLOR=#000000]1) Font Manager[/COLOR]
[COLOR=#000000]2) Thunderbird[/COLOR]
[COLOR=#000000]3) Nautilus

and 
4) Login page

Should I reinstall Ubuntu 12.04 or move to Windows 7?

Thank You.
SATHIT T.[/COLOR]

---

