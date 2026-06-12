---
title: "How To Install Areca Backup"
date: 2018-03-14
forum: General Help
---

### Post by rbscairns on 2018-03-14
So far, I have:

1. Downloaded areca-7.5-linux-gtk-32.tar.gz into my Downloads folder.

2. Extracted areca-7.5-linux-gtk-32.tar.gz into my Home Folder.

3. In Home Folder/Areca, I have checked that all .sh files (including those in sub-directories) have the following access controls:

[INDENT]View content = Anyone
Change content = Only owner
Execute = Anyone[/INDENT]

4. In my Home Folder/Areca, I opened areca.sh in leafpad and it reads:
```
#!/usr/bin/env bash
####################################################################
#
# This script launches Areca's Graphical user interface.
#
####################################################################

PROGRAM_DIR=`dirname "$0"`
"${PROGRAM_DIR}"/bin/areca_run.sh com.application.areca.launcher.gui.Launcher "$1" "$2" "$3" "$4" "$5" "$6" "$7" "$8" "$9" "${10}" "${11}" "${12}"
```
5. I checked the contents of my Home Folder/Areca/bin and it contains a file areca_run.sh.

6. In my Home Folder/Areca, I then opened areca.sh and click on Execute. Nothing happens.

7. In my Home Folder/Areca, I then opened areca.sh ans click on Execute in Terminal. The terminal screen flashes open and then closes immediately.

How do I get Areca to work?

---

### Post by VMC on 2018-03-14
It shows that "[COLOR=#000000][FONT=&amp]areca_run.sh" should be in the "/bin" directory.

edit:unless [/FONT][/COLOR][FONT=Ubuntu Mono, monospace][COLOR=#000000]"${PROGRAM_DIR}" is pointing to your home dir. Their web page for installation is sparse.[/COLOR][/FONT]

---

### Post by monkeybrain20122 on 2018-03-14
[https://sourceforge.net/p/areca/bugs/563/](https://sourceforge.net/p/areca/bugs/563/) 

Ubuntu comes with backup tool, why do you need some random java app which apparently has not had any development since 2015?

---

### Post by speartip on 2018-03-14
> **monkeybrain20122 said:**
> Ubuntu comes with backup tool, why do you need some random java app which apparently has not had any development since 2015?

IMO Areca is one of, if not the best Backup tool there is for Linux.
To get it to run isn't straight forward though. To start with you will need to install Oracle Java 8. The best way to do that is by using the ppa from here:
[https://launchpad.net/~webupd8team/+archive/ubuntu/java](https://launchpad.net/~webupd8team/+archive/ubuntu/java)
If you want to use the openjdk from Ubuntu repos instead, then you'll need to change some lines in the ~areca/bin/areca_run.sh file as shown here in the Stefan Willinger post:
[https://sourceforge.net/p/areca/bugs/563/](https://sourceforge.net/p/areca/bugs/563/)
Then its just a simple case of opening a terminal inside the extracted areca folder and running:
```
./areca.sh
```
To configure areca a good tutorial can be found here:
[http://www.areca-backup.org/tutorial.php](http://www.areca-backup.org/tutorial.php)
If you need any more help please post back.

---

