---
title: "itools"
date: 2007-04-08
forum: General Help
---

### Post by embeemb on 2007-04-08
In order to get prayer time notifications, I ran
>  sudo apt-get install itools and managed to install the utility from the repositories.

However, upon completing installation, I couldn't run the applicaiton. >  embee@embee-lappie:~$ itools  gave back >  bash: itools: command not found .

I know for a fact this is a command line utility. What am I doing wrong? I'm quite new to Ubuntu, so my question might be a little off-beat.

Thanks for the help anyway :)

---

### Post by ihavenoname on 2007-04-08
If you are on gnome then install minbar. THe deb can be found here

[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fm%2Fminbar%2Fminbar_0.1-6_i386.deb&md5sum=5223e0789ae85a03c48e2bc51dee78e9&arch=i386&type=main]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fm%2Fminbar%2Fminbar_0.1-6_i386.deb&md5sum=5223e0789ae85a03c48e2bc51dee78e9&arch=i386&type=main")

here's a direct link.
[http://http.us.debian.org/debian/pool/main/m/minbar/minbar_0.1-6_i386.deb](http://http.us.debian.org/debian/pool/main/m/minbar/minbar_0.1-6_i386.deb)
install that and type alt+F2 and then type minbar and hit enter. You should see a prayer time utility. If you want it to start everytime you login then click on System-->Preferances-->Session and add minbar to your list of start-up programs.


Edit: If you don't want to install minbar (the graphical utility). You can use the following commands at the cli.

ical 
idate 
ipraytime 
ireminder

I hope this helps.

Look at [http://www.ubuntume.com/](http://www.ubuntume.com/) for more info on these types of tools.

---

### Post by embeemb on 2007-04-08
I downloaded the .deb package and tried to install. Got an error message >  Dependency is not satisfiable: libatk1.0-0

I tried >  sudo apt-get install libatk1.0-0 and it confirmed that I have the newest version. I also changed the permission for the .deb package to be executable by owner. I still get the same error message.

Any ideas?

---

