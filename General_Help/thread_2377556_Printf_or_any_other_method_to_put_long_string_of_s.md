---
title: "Printf or any other method to put long string of spec characters - passing passwords"
date: 2017-11-14
forum: General Help
---

### Post by alex346 on 2017-11-14
Hello,


I am looking for a method to use in my bash script which allows me to use long strings with all special characters. 


I have found that printf method could be helpfull for me but unfortunately, when I trying
```
root@machine:~# tevar=`printf "%s%c" "'``fF/0,g_V/Y)>^.(a0(,%<A.`8N:q*Rd|lCy0t9N'FDPs|S,$2(^$/*>5Ush*w87L#m@t~:[Ple+=Od633Z3m3xGV.zX+a-N%x1K=J7gOO=?1c$HZU78iVtJG1N[s@-eH#DwH]V5l}??XWI.YJ;4%:LmAEML9%4jm'Y6GXTc{DT7Iia$!+/[x.),b]5`iO3E,-+,44+9Fke45Z=m^ba.EP^)+GqZ.uQNF*sU9'Kxq6i19+ie*6rZjjCC.2`rSYVqlmHlHqeFBCapXXSxXROXUrljMWGsicEdCdPJuvbXnPXlENaBzpMBnRgtGsFtTYbHsyilugLrTSTMvGDGqSIhXhJISqnIuBwxfqr`'" ; echo $tevar
-bash: b&#322;&#261;d sk&#322;adni przy nieoczekiwanym znaczniku `)'

```
I am getting error


-bash: b&#322;&#261;d sk&#322;adni przy nieoczekiwanym znaczniku `)'


What is important - I need to pass different length strings, I don't know the lenght, and the positions of special characters.
This is a password from my password list and I need find working pass to archive.
[B]
What can I do to pass very long stream with any special character as a string and put it as variable in bash script?


Or - maybe I can make it outside the bash ? I am using 7 zip command line tool where I need to put the password as paramater like
[/B]
7z t -pP@55w0rd!


where P@55w0rd! is my password. 


What was my fault before (long time ago)- I have had used almost 5000 characters in passwords. I have lot of possible passes in my dictionary, and I am sure, that one of them will be correct.

---

### Post by untrustytahr on 2017-11-14
I'm not sure why you want to use printf but...
```
while IFS= read -r line; do printf '%s\n' "$line"; done < password_file.txt
```

would print the line.  you obviously would want to remove the '\n' in a script.

you could just redirect the line into 7z:

```
while IFS= read -r line; do 7z t -p{"$line"} archive_file.7z; done < password_file.txt
```

That would produce a very verbose output, so i would just output the 'current' password and the success code.

---

### Post by Holger_Gehrke on 2017-11-15
What you're probably looking for is called a "Here Document". Search the manual page of bash for it.

Holger

---

