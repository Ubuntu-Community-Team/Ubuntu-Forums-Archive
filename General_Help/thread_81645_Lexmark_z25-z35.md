---
title: "Lexmark z25-z35"
date: 2005-10-24
forum: General Help
---

### Post by issr7 on 2005-10-24
I tried installing my printer with the available drivers but there was none for the z25 model. I tried using another driver but it didn't work. Can someone suggest what i should do ?

---

### Post by aysiu on 2005-10-24
Have you seen this?

[http://www.ubuntuforums.org/showthread.php?t=49714&highlight=howto+lexmark](http://www.ubuntuforums.org/showthread.php?t=49714&highlight=howto+lexmark)

---

### Post by ecobuntu on 2005-10-24
[QUOTE=issr7]I tried installing my printer with the available drivers but there was none for the z25 model. I tried using another driver but it didn't work. Can someone suggest what i should do ?[/QUOTE]

d/l this driver, it works for z25 model [http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&os_group=Redhat&target=](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&os_group=Redhat&target=)

Then
1.  tar -zxvf CJLZ600LE-CUPS-1.0-1.TAR.gz
2.  sh z600cups-1.0-1.gz.sh -target temp_lex (ignore errors)
3.  cd temp_lex
4.  sudo alien *.rpm
5.  sudo dpkg -i *.deb
6.  Set up your printer either your the GNOME printer manager or the KDE manager.  Make sure you tell the printer to turn on as root.  

Good Luck!  
PS- This worked for me using the same driver with a z600

---

### Post by issr7 on 2005-10-25
help !

i got up to this point 

$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.

and im getting this error

ss@SS:~/Desktop/lexmark$ alien -t z600cups-1.0-1.i386.rpm
bash: alien: command not found
ss@SS:~/Desktop/lexmark$   

I tried using synaptic to install anything that has alien in it but the search came up with no results.

---

