---
title: "How to know the binary name of an application to run it from the Terminal??"
date: 2013-03-11
forum: General Help
---

### Post by aayus on 2013-03-11
I want to run all the applications through the terminal rather than double clicking on its icon. 
For that i need to know the binary name of the applications. 
eg. gedit text1.txt
     evince mytext.pdf
how can one know the binary name of all the applications to be able to run from the terminal??

---

### Post by iMac71 on 2013-03-12
what you wish is very easy to get: simply do these steps:
[LIST]
[*]enter the name of your desired application in the search field of the ubuntu software center; 
[*]when the icon of that application appears, click on "more info"; 
[*]scroll the window until you see the "Version" field: here you find the name you're looking for. 
[/LIST]

---

### Post by aayus on 2013-03-12
In the end it turned out to be a silly question.
Thanks!!

---

### Post by iMac71 on 2013-03-12
I'm not so sure that your question be really silly.
For instance, I used the above procedure for creating my own installation script, where there are the binary names of all the applications I want to install after having installed a new release of Ubuntu.

---

### Post by Vaphell on 2013-03-12
package names you install and names of binaries you run are not necessarily the same.

To browse available packages you can use ```
apt-cache seach <keyword>
```
and to get the list of installed ones ```
dpkg --get-selections
```
To get the actual command of gui programs you can look in .desktop files located in /usr/share/applications

```
grep ^Exec= /usr/share/applications/*.desktop
```

---

### Post by vasa1 on 2013-03-12
@Vaphell, if you don't mind, please look at this laborious code that I came up with to relate **.desktop files**, **Name=** and **Exec=**. I'm sure you'll boil it down to a line or two!

```
grep '^Name=' /usr/share/applications/*.desktop > ~/Desktop/mgtl1.txt && grep -h '^Exec=' /usr/share/applications/*.desktop > ~/Desktop/mgtl2.txt && paste -d':' ~/Desktop/mgtl1.txt ~/Desktop/mgtl2.txt > ~/Desktop/mgtl3.txt && perl -p -i -e 's/\/usr\/share\/applications\///'g ~/Desktop/mgtl3.txt && perl -p -i.bak -e 's/\n/\n\n/'g ~/Desktop/mgtl3.txt && perl -p -i.bak -e 's/:/\n/'g ~/Desktop/mgtl3.txt
```

Also, see this: [http://ubuntuforums.org/showpost.php?p=12282576&postcount=6](http://ubuntuforums.org/showpost.php?p=12282576&postcount=6) and [http://ubuntuforums.org/showthread.php?t=2067629&p=12473245#post12473245](http://ubuntuforums.org/showthread.php?t=2067629&p=12473245#post12473245)

---

### Post by schragge on 2013-03-12
@**vasa1**
:?: Would this do what you want? [highlight]Edit.[/highlight] Corrected to work for any order and number of Name=/Exec= lines in a .desktop
```
sed -nrs '/^\[Desktop Entry\]/d;/^(\[|Name=|Exec=)/p;${g;p}' /usr/share/applications/*.desktop
```

---

### Post by Cheesemill on 2013-03-12
You could also just launch the program normally and then use...
```
ps ax
```
to list all running processes. The application you have just launched will be near the bottom.

---

### Post by vasa1 on 2013-03-12
> **schragge said:**
> @**vasa1**
:?: Would this do what you want
```
sed -n '/^Name=/p;/^Exec=/{G;p}' /usr/share/applications/*.desktop
```

Hi, please redirect that to a file and then look for the ones involving LibreOffice. The problem there is that the LibreOffice .desktop files (and a few others) don't always have Name= first and Exec= second. Also, there are instances of Name=, Exec=, Exec=, Name in **one** .desktop file. And those .desktop files are why I took a long route. I've referred to that problem in the links I provided.

---

### Post by schragge on 2013-03-12
@**vasa1**
I've edited my post, please take another look.
[highlight]PS.[/highlight] I don't have LibreOffice installed, so cannot test it.

---

### Post by vasa1 on 2013-03-12
> **schragge said:**
> @**vasa1**
I've edited my post, please take another look.
[highlight]PS.[/highlight] I don't have LibreOffice installed, so cannot test it.

It's nearly perfect. Could you also incorporate the name of the .desktop file?

BTW, now this is how the LibreOffice ones look like:
```

Exec=libreoffice3.6 --base %U
Name=LibreOffice 3.6 Base
Name=New Database
Exec=libreoffice --base %U

Exec=libreoffice3.6 %U
Name=LibreOffice 3.6 Legacy StarOffice 5 Binary Format Importer

Exec=libreoffice3.6 --calc %U
Name=LibreOffice 3.6 Calc
Name=New Spreadsheet
Exec=libreoffice --calc %U

Exec=libreoffice3.6 --draw %U
Name=LibreOffice 3.6 Draw
Name=New Drawing
Exec=libreoffice --draw %U

Exec=libreoffice3.6 --impress %U
Name=LibreOffice 3.6 Impress
Name=New Presentation
Exec=libreoffice --impress %U

Exec=libreoffice3.6 --writer %U
Name=LibreOffice 3.6 Small Device Format Importer

Exec=libreoffice3.6 --math %U
Name=LibreOffice 3.6 Math
Name=New Formula
Exec=libreoffice --math %U

Exec=libreoffice3.6-printeradmin
Name=LibreOffice 3.6 Printer Administration

Exec=libreoffice3.6 %U
Name=LibreOffice 3.6 

Exec=libreoffice3.6 --writer %U
Name=LibreOffice 3.6 Writer
Name=New Document
Exec=libreoffice --writer %U

Exec=libreoffice3.6 %U
Name=LibreOffice 3.6 XSLT based filters


```

---

### Post by schragge on 2013-03-12
@**vasa1**
From what I can see all Exec= lines from the same .desktop file are identical. I could output only the last of them after all Name= lines, like this:
```
sed -ns '/^Name=/p;/^Exec=/h;${g;s/$/\n/p}' /usr/share/applications/*.desktop
```
To get filenames you probably should use awk instead of sed as it has FILENAME variable. The latest GNU sed version 4.2.2 [includes](http://lwn.net/Articles/530460/) new command **F** just for this, but it's not yet in Debian. In awk, it's something like
```

awk '
 /^Name=/;
 /^Exec=/  {x=$0}
 NR!=1&&FNR==1 {printf "%s\nIn: %s\n\n",x,FILENAME}
 END {printf "%s\nIn: %s\n\n",x,FILENAME}
' /usr/share/applications/*.desktop

```
or, if written in one line
```
awk -vfmt='%s\nIn: %s\n\n' '/^Name=/;/^Exec/{x=$0}NR!=1&&FNR==1{printf fmt,x,FILENAME}END{printf fmt,x,FILENAME}' /usr/share/applications/*.desktop
```

---

### Post by Vaphell on 2013-03-12
LO has 2 sections in .desktop files: standard [Desktop Entry] and [X-new Shortcut Group]. I'd ignore the latter completely.
Similar thing with transmission (+2 sections), totem (+5) and probably many others.

in let's say awk i'd switch matching on when [[]Desktop Entry[]] and off when any other [[].*[]]


edit: something like this should work
```
for f in /usr/share/applications/*.desktop; do sed -rn '/^\[Desktop Entry\]/,/^\[.*\]/{/^(Name|Exec)=/p}' "$f" | sort -r; echo; done
```

---

### Post by efflandt on 2013-03-12
One other command that I don't think anyone mentioned here yet is **apropos**. That lists man pages related to a search term which would likely commands and man pages explaining how to use them (command line arguments, etc.).  Although, sometimes that can result in a long list and if you want to browse through it, you may want to pipe it to less:```
apropos file | less
```

---

### Post by schragge on 2013-03-12
> **Vaphell said:**
> in let's say awk i'd switch matching on when [[]Desktop Entry[]] and off when any other [[].*[]]
Then probably something like this would be enough
```

awk '
 FNR==1{pf=0;printf "\nFile: %s\n", FILENAME}
 /^\[Desktop Entry\]$/{pf=1;next}
 /^\[/{pf=0}
 pf>0&&/^(Name|Exec)=/{sub(/=/,": ");print}
' /usr/share/applications/*.desktop

```
Or, with GNU sed 4.2.2 (hopefully to be included in Ubuntu after *raring*):
```
sed -ns '1F;/^\[Desktop Entry\]/,/^\[/{/^Name=/p;/^Exec=/h};${z;x;G;p}' /usr/share/applications/*.desktop
```

[highlight]Update.[/highlight]
I also converted the output format to dctrl ([Debian control file]("http://www.debian.org/doc/debian-policy/ch-controlfields.html")). This allows for interesting effects when e.g. piping the result into [dctrl-tools]("http://packages.ubuntu.com/quantal/dctrl-tools"). Consider something like
```
sed -nrs '/^\[Desktop Entry\]/,/^\[/{s/^(Name|Exec)=/\1: /p};${z;p}' /usr/share/applications/*.desktop|sort-dctrl -kName|tbl-dctrl -cName:30 -cExec:43
```

---

