---
title: "HOW TO set the PATH"
date: 2004-11-24
forum: General Help
---

### Post by Green on 2004-11-24
Hi, all
   I have a question about post installation of Java. I want to set the JAVA_HOME in the PATH. Where is the properiate place to add the script? For instance, In /etc/profile, i can add the JAVA_HOME, and export $JAVA_HOME etc to ensure every time boot up, i have JAVA_HOME at the PATH.
   Is this the right way to do it? Or you have another solution.
   Can you recommand an article about the linux booting sequence?

THX

---

### Post by TravisNewman on 2004-11-24
This section in the forum is for people WRITING HowTo articles, not people requesting help. This question would be better suited for General Help. Can a mod with power here move this to General?

---

### Post by qstone on 2004-11-24
I'm having the same problem...
I found docs saying that it can be changed in /etc/profile (globally) or ~/.bash_profile

I add the following (to BOTH files, just to be sure) :
EXPORT JAVA_HOME="/usr/local/jdk"
EXPORT JDK_HOME="${JAVA_HOME}/bin"
EXPORT PATH="${JDK_HOME}/bin:${PATH}"

After a complete reboot, my PATH remains unchanged, and the other variables are not defined. 
I'm not a shell expert, but these lines look ok to me, so what ? Is the PATH defined elsewhere in ubuntu ???

---

### Post by jiyuu0 on 2004-11-24
i assume your java folder is at /usr/java/jre1.5.0

$ sudo gedit /etc/bash.bashrc

Append the following lines at the end of file:
  JAVA_HOME=/usr/java/jre1.5.0
  export JAVA_HOME
  PATH=$PATH:$JAVA_HOME/bin
  export PATH

reboot

$ echo $JAVA_HOME
$ echo $PATH

[http://kitech.com.my/ubuntu/4.10/#jre](http://kitech.com.my/ubuntu/4.10/#jre)

---

