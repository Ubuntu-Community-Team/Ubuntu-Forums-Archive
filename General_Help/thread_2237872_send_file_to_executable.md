---
title: "send file to executable"
date: 2014-08-04
forum: General Help
---

### Post by ken18 on 2014-08-04
I'm trying to set up an automated way to run an executable against a text input file (in my specific case, generate pdf files using pdflatex) without typing into a terminal window or editing a shell script.  

Right now I either open a terminal and type in 'pdflatex inputfilename.tex' or do the equivalent in a shell script.  What I want to do is accomplish this by double or right-clicking on the input file and indicating that the file is to be opened by a particular executable (pdflatex in this case) or a shell script.  I really don't want to type commands in a terminal window or edit my existing shell script each time I want to use a different input file.  I'm an avid mouse click kind of guy.

Appreciate any suggestions.

---

### Post by sisco311 on 2014-08-04
You can create a .desktop file for your script/command, place it in the ~/.local/share/applications/ directory and make it executable. Then right click on a .tex file select **Properties** -> **Open With**. Select the name of your .desktop file from the list. Set it as default or just add it to the Open With menu. 

 .desktop file example: 

~/.local/share/applications/pdflatex.desktop:

```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
NoDisplay=true
Exec=prdflatex %f 
Name=pdflatex
Comment=Create .pdf from .tex

```

---

### Post by ken18 on 2014-08-07
Thanks for your help!  After of number of iterations I finally got it to work, but have a couple of questions:

(1) once I rename the file to .desktop and change execute permissions, how can I then edit the file with gedit to make changes?  I tried removing the execute permissions but was unable to rename the file back to .txt.  I ended up deleting the file and starting over.

(2) I used desktop-file-install command to install the file in /usr/share/applications, but how would I remove it in the future if I wanted to?  mv command?

---

### Post by Vaphell on 2014-08-07
.desktop files are kind of treated specially by the GUI but commandline couldn't care less.
*gedit file.desktop* should work, as should *mv file.desktop file.txt*

---

### Post by ken18 on 2014-08-08
Thanks, command line version worked!!

---

