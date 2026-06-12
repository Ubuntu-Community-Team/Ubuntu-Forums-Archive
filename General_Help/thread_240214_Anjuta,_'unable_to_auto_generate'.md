---
title: "Anjuta, 'unable to auto generate'"
date: 2006-08-20
forum: General Help
---

### Post by ehoffman on 2006-08-20
Hello

I'm trying to build a small program, and when clicking 'auto generate', I get an error message:

'Unable to auto generate.  Check Settings->Commands'

I can't see what's the problem.

Help!

---

### Post by baldy1324 on 2006-08-20
since im guessing you are a newbie to programming in c/c++ and you are probably doing single-source code programs i would use something like gedit to create the document and then use gcc or g++ to compile it on the command line. this method dosen't use IDE's that try to simply build projects with lots of files. i find using the command line easier for programming.

---

### Post by ehoffman on 2006-08-20
Actually, I'm a newbie at Linux programming.  I come from Windows (caugh) where I do have a strong programming experience, but I'm still learning my way aroung in Linux.

I found out though that if I start a new project, from scratch, and then move the existing source file to it, it work.

The problem occured when I created a new project from import...  It seem that Anjuta does not like it (hence the 'experimental' notice displayed when importing projects :rolleyes: ).

I managed to get going by creating a new project, as explained above.

I tried eclipse first, and then Anjuta.  I do preffer the simplicity and lightweightness of Anjuta compared to eclipse, especially when I want to build console apps (though with several sources/includes and external shared objects).

Thanks.

---

### Post by baldy1324 on 2006-08-21
ok here is what i recommend for console apps- open gedit applications-->accessories-->text editor or type ALT-F2 and the type gedit. type the code in there... then fire up a console (ALT-F2 type gnome-terminal) and then navigate to the directory you saved it in (cd ~/Desktop for desktop or if you saved it your regular directory just leave it there). (if this dosen't make since to you search google for how to use the console. then g++ (for c++) or gcc (for c) filename and it will compile. then just ./filename.
and its a lot better than IDEs.

---

