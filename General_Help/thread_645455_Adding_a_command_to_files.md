---
title: "Adding a command to files"
date: 2007-12-20
forum: General Help
---

### Post by Helgiks on 2007-12-20
Hi, I am trying to add a command to files so I won't always have to open the terminal, find the file and than write the command. To be precise I want to be able to right-click ".tex" files and click an option that will do "pdflatex" to the file. I first figured clicking Properties->Open with->Add->Use custom command, there I typed "gnome-terminal -x pdflatex "

That seemed to work but the output goes to "/home/USER/" which is not what I want, than I tried to figure out what I can do, to change the working directory to the one the specific file is in, without success. So I ask you is their a better way of doing this?  Or can I simply change the working directory so the output goes to the right place?

P.S. Would be better if it said something like "Convert to PDF" along with the "Rename, Copy, Cut etc.".

---

### Post by aJayRoo on 2007-12-20
I think what you want will be a nautilus script (assuming you are using the nautilus file manager that is). A quick google search brought up [this blog](http://stochasticflux.com/blog/?p=10) that seems to do what you want, of course if you are not totally happy with the solution then it would be very easy to modify the script.

EDIT: you may need to log out after doing this for the scripts menu to show up on right click.

---

### Post by Helgiks on 2007-12-20
Yeah, that seems to be what I was looking for, thanks allot.

---

