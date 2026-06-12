---
title: "Zenity script help"
date: 2016-11-27
forum: General Help
---

### Post by zvlo on 2016-11-27
Hello I am trying to make a zenity program that has to answer these questions. 
[IMG]http://i67.tinypic.com/2qwmvx5.jpg[/IMG]


Here is the code (I am really confused):
```

#!/bin/bash
 


start=1
while [ $start=1 ]
do
P1=$(zenity --forms --text "Employment Information" --title= "Employment Information" --add-entry="Employee Full name" --add-entry="Employee Username" --add-calendar="Date of Birth" --add-list="Select Department" --list-values="HUMAN RESOURCE|FINANCE|SALES|INFOTECH|LOGISTICS" --add-password="Password:" --add-combo="Select Education" --combo-values="Grade 12|Diploma|Adv. Diploma|Graduate|Masters" --separator=: >> emplist.txt)


P2=$(zenity --list --checklist  --title="Technicial Certifications" --text="Select cerifications achieved:" --column="Acquired" --column="Certifications" FALSE "RHCSA" FALSE "RHCSE" FALSE "MCSA" FALSE "CCNA" FALSE "CCNP" FALSE "ITIL" FALSE "PMP" >> emplist.txt)


P3=$(zenity --list  --title "Drivers License" --text "Select Drivers License level: " --radiolist  --column "Acquired/Passed" --column "License level" FALSE "G1" FALSE "G2" FALSE "G" >> emplist.txt)


P4=$(zenity --question --title " " --text "Make another account")


P5=$(zenity --text-info --filename="emplist.txt")


done



```
In short I need to:


-Make the name inputted in the first entry of the first zenity form prompt appear on the question prompt (P4)
-When I say No on the question prompt(P4) it should redirect me to P5 to show emplist.txt
-When I say yes on the question prompt(P4) it should redirect back to P1 to make another account
-Ok/Cancel should close P5 when pressed
-P2 and P3 should stdout to emplist.txt WITHOUT making a new line and adding to P1s line


Thank you so much

---

