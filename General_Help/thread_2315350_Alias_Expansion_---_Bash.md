---
title: "Alias Expansion --- Bash"
date: 2016-02-27
forum: General Help
---

### Post by vasa1 on 2016-02-27
If I run *acse pandora* and paste the output in a forum, people may not figure out what *acse* is.

Pressing *control+alt+e* after typing *acse pandora*, expands *acse* to *apt-cache search*. This has been around for years, but I just learned about it. Works for Bash. I don't know about other shells.

---

### Post by Habitual on 2016-02-28
That is Great to know!
I usually use
```
type acse
``` or
```
alias acse
```

but that sorta rocks!

Thanks.

---

### Post by vasa1 on 2016-05-11
I just encountered a problem with using Ctrl+Alt+E.

I have this alias:```
alias 5m='find ~/ ! -path "/home/vasa1/.config/kupfer/*" ! -path "/home/vasa1/.mozilla/*" ! -path "/home/vasa1/.cache/*" ! -path "/home/vasa1/.config/google-chrome/*" ! -path "/home/vasa1/.config/libreoffice/4/user/*" ! -path "/home/vasa1/.dropbox/*" ! -name "recently-used.xbel" ! -path "/home/vasa1/Public/Backups/*" -mmin -5 -type f -ls'
```

If I expand it using Ctrl+Alt+E, I get this:```
09:00 AM ~ $ find ~/ ! -path /home/vasa1/.config/kupfer/* ! -path /home/vasa1/.mozilla/* ! -path /home/vasa1/.cache/* ! -path /home/vasa1/.config/google-chrome/* ! -path /home/vasa1/.config/libreoffice/4/user/* ! -path /home/vasa1/.dropbox/* ! -name recently-used.xbel ! -path /home/vasa1/Public/Backups/* -mmin -5 -type f -ls
```
And then *find* isn't happy:```
find: paths must precede expression: /home/vasa1/.config/kupfer/config-kupfer.plugin.triggers-v1.pickle
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec|time] [path...] [expression]
09:00 AM ~ $ 
```If I compare the alias and the expansion, it's clear that the expansion has removed all the double quotes.

---

### Post by sudodus on 2016-05-12
Interesting to learn more about bash :-)

---

### Post by vasa1 on 2016-05-12
It was fun while it lasted ;) but Habitual's use of *type* or *alias* is the way to go for convoluted aliases.

---

### Post by sudodus on 2016-05-12
Maybe I can contribute with a small script, that helps identify the package, that was used to install a certain program, or tell that it is an own script or alias.

It is useful when I want to [help people at our forums, to] find which package to install to get a particular program.

```
#!/bin/bash

#http://www.debianhelp.co.uk/findfile.htm

if [ "$1" == "" ]
then
 echo "Descr: PAckage  of  Installed PRogram"
 echo "Usage: $0 <name-of-installed-program>"
else
 param=$(which "$1")
 if [ $? -eq 0 ]
 then
  wout=$(wajig whichpkg "$param")
  if [ "$wout" != "" ]
  then
   echo "$1  is installed as a program in system PATH"
   echo 'package: /path/name'
   echo "$wout"
  else
   echo "$param  is a program or script in private PATH"
  fi
 else
  echo "$1  is *not* installed as a program in system PATH"
  help -s "$1" 2>/dev/null
  if [ $? -eq 0 ]
  then
   echo "#------------------------------------"
   echo "$1  is [part of] a bash command"
  fi
 fi
fi
wout=$(grep "^alias $1=" $HOME/.bashrc)
if [ $? -eq 0 ]
then
 echo "#------------------------------------"
 echo "$wout"
fi

```

I call the script ***paipr***, and it uses ***wajig*** behind the curtain.

***Example:*** A user wants to use ***add-apt-repository*** in a mini system made from the Ubuntu mini.iso.

Then I run (in my main computer, where I have it installed)

```
$ paipr add-apt-repository
add-apt-repository  is installed as a program in system PATH
package: /path/name
INSTALLED MATCHES (x1)
----------------------
software-properties-common: /usr/bin/add-apt-repository
```

and I can tell the user to install **software-properties-common**.

---

