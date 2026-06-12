---
title: "Merging multiple csv files"
date: 2013-12-07
forum: General Help
---

### Post by Marcello49 on 2013-12-07
Hi
I need help to solve the following problem: I have multiple (from 2 to 6) files. The first three columns identify a student the fourth is the results of an exam that can be taken more then once in different moments. They are of the form


"MATRICOLA";"COGNOME";"NOME";"01_2012"
"5108932";"ABBATE";"LINO";"respinto"
"5129960";"ANTONELLI";"STEFANO";"Assente"
"5078925";"BONO";"GIULIA";"24/30"


They have different fourth columns


"MATRICOLA";"COGNOME";"NOME";"02_2012"
"5135682";"MARTI";"FRANCO";"Assente"
"5129960";"ANTONELLI";"STEFANO";"23/30"


I would like to merge them in order to obtain


"MATRICOLA";"COGNOME";"NOME";"01_2012";"02_201 2"
"5108932";"ABBATE";"LINO";"respinto"; " "
"5129960";"ANTONELLI";"STEFANO";"Assente"; "23/30"
"5078925";"BONO";"GIULIA";"24/30"; " "
"5135682";"MARTI";"FRANCO";" ";"Assente"


In other words a want to add the new column without duplicating the students.
Thanks for your help
Marcello

---

### Post by amanchesterman on 2013-12-07
Hi Marcello, the experts on this forum may be able to tell you a quick and clever way of doing this -- but I'm no expert so I can only suggest a slow process of copying-and-pasting:

1) Open your spreadsheet application (LibreOffice Calc or whatever you use) and import each .csv file as a separate worksheet, converting them to .ods format.
2) Sort all the records on each sheet so that they are in the same order top to bottom: I would use the student record number as the unique identifier for doing this.
3) Create a new blank sheet and copy all the columns from all the sheets into that, left to right across the page: this of course will produce a sheet in which several of the columns contain duplicate data.
4) Delete the columns which contain duplicate data and move the remaining columns until they are in the order you want, left to right.

Long-winded I know, but I've had to do this kind of thing myself on several occasions so I know it works!
Good wishes
John

---

### Post by bluefrog on 2013-12-08
a quick and dirty answer which would need that all your files have the same students on the same line numbers

let's name your files 1 2 3 4 5 6
cat 2 | awk 'BEGIN{FS=";"} { print $4 }'> tmp2 would produce an output file tmp2 as following:
"02_2012"
"Assente"
"23/30"

then 
paste -d ";" 1 tmp2 > result
would give the following in the result file

cat result
"MATRICOLA";"COGNOME";"NOME";"01_2012";"02_2012"
"5108932";"ABBATE";"LINO";"respinto";"Assente"
"5129960";"ANTONELLI";"STEFANO";"Assente";"23/30"
"5078925";"BONO";"GIULIA";"24/30";

---

### Post by bluefrog on 2013-12-08
could also use join which would be better. sry long time didn't use any command line.

need the files to be sorted. you can sort them on the fly or before hand.

join -a 1 -t ";" -o 1.1 1.2 1.3 1.4 2.4 <(sort 1) <(sort 2)

which means: join sorted file 1 and sorted file 2 on the first field (delimitered by ";") and print (-o 1.1 1.2 1.3 1.4) the 4 fields from file 1 and the fourTH field from file 2 ( 2.4 ) and also print unpairable lines from file 1 (-a 1). you could print unpairable lines from file 2 with -a 2 after -a 1 but in that case as we only print the fourth field from file 2 it would be useless to do that...
"5078925";"BONO";"GIULIA";"24/30";
"5108932";"ABBATE";"LINO";"respinto";
"5129960";"ANTONELLI";"STEFANO";"Assente";"23/30"
"MATRICOLA";"COGNOME";"NOME";"01_2012";"02_2012"

(unpairable lines from file 2 are not printed here)

have a look at the fourth line wich is an unpairable line from file 2 in the following command (-a 1 -a 2)
join -a 1 -a 2 -t ";" -o 1.1 1.2 1.3 1.4 2.4 <(sort 1) <(sort 2)
"5078925";"BONO";"GIULIA";"24/30";
"5108932";"ABBATE";"LINO";"respinto";
"5129960";"ANTONELLI";"STEFANO";"Assente";"23/30"
;;;;"Assente"
"MATRICOLA";"COGNOME";"NOME";"01_2012";"02_2012"

---

