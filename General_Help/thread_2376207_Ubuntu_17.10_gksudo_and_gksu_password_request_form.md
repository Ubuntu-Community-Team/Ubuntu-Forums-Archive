---
title: "Ubuntu 17.10 gksudo and gksu password request form not working"
date: 2017-10-31
forum: General Help
---

### Post by saladriel on 2017-10-31
Hi all, noted this thing yesteday on my 17.10 installation: whenever I run gksudo or gksu from system shell, the password request form is shown, but I can't manage to shift the focus and write the password on it. 
Is it a common issue?
What could I do to make it work?

Thanx in advance for your time

---

### Post by Impavidus on 2017-10-31
Seems to be a known bug.
[https://ubuntuforums.org/showthread.php?t=2375077](https://ubuntuforums.org/showthread.php?t=2375077)

---

### Post by saladriel on 2017-11-02
Uh, ok. Thanx

---

### Post by bilekbp on 2018-01-02
Hell, I'm having the same problem, and I can't find a workaround noted in the linked thread. Am I missing something?

---

### Post by #&amp;thj^% on 2018-01-02
> **bilekbp said:**
> Hell, I'm having the same problem, and I can't find a workaround noted in the linked thread. Am I missing something?

Perhaps I can Re-Quote cariboo from that link:
Quoted:
 You can use either Xorg or Wayland when you log in, but you should be aware that Wayland will not work with proprietory drivers (Nvidia) you need to run the Nouveau drivers if you want to use it.

Using Wayland causes problems with authentication. Synaptic, or using application as a root will not work unless you open a terminal and type the following command:

```
xhost +si:localuser:root
```

**This will only work for the current session**, so after a reboot you'll have to run the command again.

So far there isn't any other work-a-round to make the setting stick.

Automatic login not working:

---

### Post by bilekbp on 2018-01-02
Thank you for the response. I had tried the xhost command, but it did not work for me (I still couldn't change focus to the password prompt), which is why I was confused.

Logging in under Xorg did work, however, so I guess that's my workaround.

Thanks again!

---

