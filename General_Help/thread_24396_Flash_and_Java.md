---
title: "Flash and Java"
date: 2005-04-06
forum: General Help
---

### Post by chili on 2005-04-06
Does anybody have the steps to follow to get flash and java working properly??  I have tried following the steps for java off of sun's website but it never installs correctly.  Never shows in about:plugins either.

And my flash is in the about:plugins but seems to lock my browser now everytime i visit a flash site.

Thanks,
chili

---

### Post by bored2k on 2005-04-06
a ) [http://ubuntuforums.org/showthread.php?t=22646&highlight=automatic+script](http://ubuntuforums.org/showthread.php?t=22646&highlight=automatic+script)

b ) Enable multiverse. then
> "Also, if you don't already have it, you'll need the build-essential package:

apt-get install build-essential

Then do this:

$ sudo apt-get update
$ sudo apt-get install java-package java-common fakeroot

download the sun jdk from java.sun.com
** edit /usr/share/java-package/sun-j2sdk.sh to reflect the actual JDK 1.5 release version.

$ fakeroot make-jpkg jdk-1_5_0-linux-i586.bin
$ sudo dpkg -i sun-j2sdk1.5_1.5.0_i386.deb (this reports an error but is completed in next step)
$ sudo apt-get install sun-j2sdk1.5debian
$ sudo update-alternatives --config java (see next step for dependancy errors)
$ sudo apt-get -f install (fix dependancy errors if required)" (change the java package with the correct name) .

---

### Post by Nis on 2005-04-06
[QUOTE=chili]Does anybody have the steps to follow to get flash and java working properly??  I have tried following the steps for java off of sun's website but it never installs correctly.  Never shows in about:plugins either.

And my flash is in the about:plugins but seems to lock my browser now everytime i visit a flash site.

Thanks,
chili[/QUOTE]
 You can try the HAIH (click in my signature) or ubuntu-geek's [automate script](http://www.ubuntuforums.org/showthread.php?t=22646).

And by the way, wrong forum.  This is for guides on how to do things, not for questions.

---

### Post by bored2k on 2005-04-06
[QUOTE=Nis]You can try the HAIH (click in my signature) or ubuntu-geek's [automate script](http://www.ubuntuforums.org/showthread.php?t=22646).

And by the way, wrong forum.  This is for guides on how to do things, not for questions.[/QUOTE]
 Thank you Nis, I hadn't noticed.

---

### Post by dataw0lf on 2005-04-07
Man, Nis is like the Grandmaster Ninja of thread reporting.  He reminds me of the Soup Nazi.  But in a good way.

---

