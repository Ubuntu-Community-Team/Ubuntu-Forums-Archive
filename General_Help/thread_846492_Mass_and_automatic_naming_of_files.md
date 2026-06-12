---
title: "Mass and automatic naming of files"
date: 2008-07-01
forum: General Help
---

### Post by Adoran on 2008-07-01
Hello community! 

I'm building my very first set of shell scripts. Among some of the process I've got working I would like to name the output files with a pattern. Schematically like this -

"A NUMBER" + "A THREE LETTER ACRONYM" + "DATE dd/mm/yyyy"

An example of how I'd like the file to look is -

#1_DSI_27/04/1990.tar.gz

Preferably the three letter acronym should be asked for as a prompt. I have tried using the 'read' command for the three- letter-acronym and $date +d%/%mm/%yyyy for the date but I can't get it working. 

The program "[Metamorphose]("http://file-folder-ren.sourceforge.net/")" allows you to do this but I would like to have it embedded in a bash script so that it is more compact and more easily automated and runs in sequence with other processes.  I believe Metamorphose is written in Python. 

What sort of coding and coding structures in bash script do I need to achieve naming files in this fashion?

Many thanks all. :KS

---

### Post by spupy on 2008-07-01
```
read acronym
date=`date +%d/%m/%y`
filename=XYZ$acronym$date
echo $filename
```

Does this help?

EDIT: You have to checke "man date" to find the %codes for 4-digit year and 2-digit month numbers.

---

### Post by Adoran on 2008-07-03
It does! Thank you. It is that 'filename' command that seems to be key. Many thanks!

---

