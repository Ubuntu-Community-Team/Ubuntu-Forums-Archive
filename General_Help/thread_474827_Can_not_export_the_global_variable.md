---
title: "Can not export the global variable"
date: 2007-06-15
forum: General Help
---

### Post by kensonman on 2007-06-15
Dear All,

I write a script that will setup some environment variables. But it can not setup/export the environment correctly.

The script:
```
#!/bin/bash
## Create Date: 2007-06-13, Kenson
## The script to setup the environment variables.

DEBUG="DEBUG"

if test $DEBUG; then echo "Current JAVA_HOME=$JAVA_HOME"; fi

if test -z $JAVA_HOME; then
	if test $DEBUG; then echo "Setting up JAVA_HOME..."; fi
	JAVA_HOME=/usr/java/jdk
	if test $DEBUG; then echo "JAVA_HOME=$JAVA_HOME"; fi

	if test $DEBUG; then echo "Setting up ANT_HOME..."; fi
	ANT_HOME=/usr/java/ant
	if test $DEBUG; then echo "ANT_HOME=$ANT_HOME"; fi

	if test $DEBUG; then echo "Setting up the PATH..."; fi
	PATH="$JAVA_HOME/bin:$ANT_HOME/bin:$PATH"
	if test $DEBUG; then echo "PATH=$PATH"; fi

	if test $DEBUG; then echo "Exporting the environment(s)..."; fi
	export JAVA_HOME ANT_HOME PATH
else
	if test $DEBUG; then echo "The environment variables is already setup!"; fi
fi

if test $DEBUG; then echo "Finished the \"$0\""; fi
```

The output:
```
$ ./setupEnvironmentVariable.sh ; ./setupEnvironmentVariable.sh 
Current JAVA_HOME=
Setting up JAVA_HOME...
JAVA_HOME=/usr/java/jdk
Setting up ANT_HOME...
ANT_HOME=/usr/java/ant
Setting up the PATH...
PATH=/usr/java/jdk/bin:/usr/java/ant/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
Exporting the environment(s)...
Finished the "./setupEnvironmentVariable.sh"
Current JAVA_HOME=
Setting up JAVA_HOME...
JAVA_HOME=/usr/java/jdk
Setting up ANT_HOME...
ANT_HOME=/usr/java/ant
Setting up the PATH...
PATH=/usr/java/jdk/bin:/usr/java/ant/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
Exporting the environment(s)...
Finished the "./setupEnvironmentVariable.sh"
```

Is there have anything I forgot? Or how can I setup the environment variables in a script instead of ~/.bashrc (because I need to startup my glassfish server when startup computer)

---

### Post by croto on 2007-06-15
So let me see if I got that right.... you want to run the script at boot time? The problem I think is that when you "export" an environment variable, all processes children of  *that* bash session are going to see the newly set variables. 
I guess you'd have to set the variables in the script that runs the glassfish server....

---

