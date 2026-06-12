---
title: "Program List. What's installed, what isn't, etc."
date: 2006-11-20
forum: General Help
---

### Post by Roasted on 2006-11-20
I kinda always assumed that everything, as far as programs, would be under applications.

But I downloaded the linux aim client to see if I could use that to direct connect with someone since GAIM lacked that capability. I noticed there's no icon for it anywhere... and the only way I could launch it is to type "aim" in terminal. No big deal, but I just wanted to know WHERE the program is stored. Why isn't it under the applications list in the top left corner? Where is it stored in the file system? What folder? Etc.

---

### Post by scxtt on 2006-11-20
it wasn't "packaged" to do that (install the icon, etc.) or ubuntu (gnome/kde) isn't setup in a way that particular install 'requires' to do it automatically ...

do a **whereis gaim** from the CLI, that will tell you where it is, and you can make your own launcher in your menu ...

---

### Post by Roasted on 2006-11-20
jason@jason:~$ whereis aim
aim: /usr/bin/aim /usr/lib/aim /usr/bin/X11/aim


Why three places?

---

### Post by scxtt on 2006-11-20
/usr/bin/aim == executable file
/usr/lib/aim == library files
/usr/bin/X11/aim == GUI files (maybe /usr/bin/aim **ln -s** to this?)

you're really only concerned w/ the 1st one for your link ...

---

