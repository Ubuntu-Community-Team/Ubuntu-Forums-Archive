---
title: "Weblogic Server Running Issue"
date: 2014-04-26
forum: General Help
---

### Post by kiran_majumder on 2014-04-26
Hi friends, I have sucessfully installed "Open JDK Java 7 Runtime" and "Weblogic Server" in Ubuntu 14.04. I have configured domain for the server also.
I have set the JAVA_HOME, by adding 
"[B]JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64/jre/
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH[/B]" 
to bash.bashrc file.
Now the problem is, when I am trying to start the weblogic by running "startWebLogic.sh". I am getting the error :
"[B]Please edit your environment and set the JAVA_HOME
variable to point to the root directory of your Java installation[/B]."
But when I run the command "**echo $JAVA_HOME**", it gives the output "**/usr/lib/jvm/java-7-openjdk-amd64/jre/**". I can't recognize the problem. Please help me in this regard.

---

