---
title: "Trouble with ArgoUML launcher"
date: 2007-10-11
forum: General Help
---

### Post by tdb1001 on 2007-10-11
Tried creating a launcher for ArgoUML but it won't launch the app. Opening a console and typing:

java -jar ~/ArgoUML/argouml.jar

works fine and the app begins loading in a few seconds. But if I create a desktop launcher with that as the command, the app never seems to load. If I run a system monitor (genome-system-monitor) it shows java running with the aforementioned command yet nothing happens and I eventually have to kill the process. I've tried adding CLASSPATH to my .bashrc file:

CLASSPATH=~/ArgoUML-0.24:~/ArgoUML-0.24/ext
export CLASSPATH

but that makes no difference either. JAVA_HOME is set to:
JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.00

Any ideas as to why it will run fine in a console but not run as a launcher? I have a limited understanding of java and am at a loss as to what the problem might be.

Thanks!

---

### Post by mick8985 on 2007-10-12
I can't even get it to run from terminal, if you can help me in any way to get it to run from terminal that would be appreciated. 

It might be an idea to follow the instructions in argouml.sh, ie create a symlink from bin to the argouml.sh file and launch that instead (I obviously cant test this myself as I cant even run from terminal, perhaps its because I am running gutsy)

Out of interest have you just started a computer science course, if so at which university?

---

### Post by tdb1001 on 2007-10-15
Thanks for the idea I'll give it a try. As for your question, no I'm not attending any university. Most of my time is spent working #-o

As for getting it to run in a terminal window, I'd say make sure you have the PATH set to point to the bin directory of your java installation. My PATH looks like this (from env):

PATH=/usr/lib/jvm/java-6-sun-1.6.0.00/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

and when you open a terminal the command-line I gave in the first post should work. I didn't have to setup anything else.

Good luck!

---

