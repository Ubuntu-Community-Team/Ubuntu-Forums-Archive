---
title: "Browser launched from Okular (14.04)"
date: 2015-01-12
forum: General Help
---

### Post by jotacebusta2 on 2015-01-12
Hi all,

I am wrting the slides for a presentation, using LaTeX (beamer class). I include links to other files, and to external links. My viewer is Okular, and everything is fine for the links to the files. Nevertheless, when the lonk is an internet address,okular does not launch firefox, which is my default browser. Instead it launches "Ubuntu web broser", I think it'es Epiphany  (I have Gnome 3 also installed). 
The LateX command used is \href{http:..... my link}{here}. What do I do?

Thanks!

JC

---

### Post by yancek on 2015-01-12
I'm not familiar with Latex, but if it is an a href link, just precede it with firefox.

---

### Post by jotacebusta2 on 2015-01-12
I tried what you mention, but it does not work. Once I complile my LaTeX document, Okular shows it, but upon clicking the link I obtain an error, since the *file* firef http... is not there.

JC

---

### Post by Holger_Gehrke on 2015-01-12
Perhaps okular is calling one of the generic names for a browser set through the debian alternatives system. Try 
```
update-alternatives --get-selections|grep www-browser
``` If one of those points to the wrong program, you can correct this with 
```
update-alternatives --config "groupname"
``` (replace"groupname" with the generic name the first command printed in the first column of it's output)

---

### Post by ajgreeny on 2015-01-12
Are you using gnome, unity, kde or something else as your DE?

I think, whichever you use, it is probably easy to set Firefox as your default browser in one or other of the settings dialogues.

---

### Post by jotacebusta2 on 2015-01-12
Thanks, I've got the solution. From the kde control panel the application associated to Okular needed to ve changed . I closed my tab and don't have the link anymore :-(

---

