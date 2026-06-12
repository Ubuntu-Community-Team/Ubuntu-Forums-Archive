---
title: "FileSync between Hard Disks"
date: 2007-08-30
forum: General Help
---

### Post by gavinjb on 2007-08-30
Hi,

I am looking at Syncing Files between my internal Hd and external (backup) drive, in Windows I used FullSync from Sourceforge, which is available for Linux as well, I have run the installer, but when I run the app I get the following error

```

FULLSYNC_HOME = /home/gavin/FullSync
Error: JAVA_HOME is not defined correctly.
  We cannot execute java

```

This seems strange as the installer is Java and is run with installer

```

java jar FullSyncInstaller.jar

```

You are meant to be able to run FullSync by executing the following script

```

#! /bin/sh

PRG="$0"
progname=`basename "$0"`
saveddir=`pwd`
dirname_prg=`dirname "$PRG"`

while [ -h "$PRG" ] ; do
  ls=`ls -ld "$PRG"`
  link=`expr "$ls" : '.*-> \(.*\)$'`
  if expr "$link" : '/.*' > /dev/null; then
      PRG="$link"
  else
      PRG=`dirname "$PRG"`"/$link"
  fi
done

FULLSYNC_HOME=`dirname "$PRG"`/..
FULLSYNC_HOME=`cd "$FULLSYNC_HOME" && pwd`

echo "FULLSYNC_HOME = $FULLSYNC_HOME"

cd $FULLSYNC_HOME

if [ -z "$JAVACMD" ] ; then
  if [ -n "$JAVA_HOME"  ] ; then
    if [ -x "$JAVA_HOME/jre/sh/java" ] ; then
      # IBM's JDK on AIX uses strange locations for the executables
      JAVACMD=$JAVA_HOME/jre/sh/java
    else
      JAVACMD=$JAVA_HOME/bin/java
    fi
  else
    JAVACMD=java
  fi
fi

if [ ! -x "$JAVACMD" ] ; then
  echo "Error: JAVA_HOME is not defined correctly."
  echo "  We cannot execute $JAVACMD"
  exit
fi

if [ -n "$CLASSPATH" ] ; then
  LOCALCLASSPATH=$CLASSPATH
fi

# add in the dependency .jar files
DIRLIBS=$FULLSYNC_HOME/lib/*.jar
for i in ${DIRLIBS}
do
    # if the directory is empty, then it will return the input string
    # this is stupid, so case for it
    if [ "$i" != "${DIRLIBS}" ] ; then
      if [ -z "$LOCALCLASSPATH" ] ; then
        LOCALCLASSPATH=$i
      else
        LOCALCLASSPATH="$i":$LOCALCLASSPATH
      fi
    fi
done

if [ -n "$JAVA_HOME" ] ; then
  if [ -f "$JAVA_HOME/lib/tools.jar" ] ; then
    LOCALCLASSPATH=$LOCALCLASSPATH:$JAVA_HOME/lib/tools.jar
  fi

  if [ -f "$JAVA_HOME/lib/classes.zip" ] ; then
    LOCALCLASSPATH=$LOCALCLASSPATH:$JAVA_HOME/lib/classes.zip
  fi

else
  echo "Warning: JAVA_HOME environment variable is not set."
  echo "  If build fails because sun.* classes could not be found"
  echo "  you will need to set the JAVA_HOME environment variable"
  echo "  to the installation directory of java."
fi

$JAVACMD -classpath "$LOCALCLASSPATH" -Djava.library.path="$FULLSYNC_HOME/lib" net.sourceforge.fullsync.cli.Main "$@"

```

But as you can see from the error above this doesn't work, I have installed the sun-java6-jre package and as far as I know this should be ok, has anyone got any ideas.

Thanks,

Gavin,

---

### Post by bmorency on 2007-08-30
try typing this before you run your script and see how that works.


export JAVA_HOME="/path/to/java/home"
export PATH="/path/to/java/bin:$PATH"

---

### Post by tszanon on 2007-08-30
I don't know if this is the cause of your problem, but it should be:
```
java **-jar** FullSyncInstaller.jar
```

---

### Post by gavinjb on 2007-08-30
> **bmorency said:**
> try typing this before you run your script and see how that works.


export JAVA_HOME="/path/to/java/home"
export PATH="/path/to/java/bin:$PATH"

Thanks,

One question though, how do I find the path to my java bin folder

---

### Post by vanadium on 2007-08-30
which java

---

### Post by gavinjb on 2007-08-30
I don't know, I know is the app is java based and from the error it is looking for java, but not sure how to find the path

---

### Post by Krydahl on 2007-08-30
He meant if you type "which java" into a terminal it will return the path you need.

---

### Post by tszanon on 2007-08-30
> **gavinjb said:**
> One question though, how do I find the path to my java bin folder
Try:
```
locate java
```
It's usually /usr/local/jre<version>/bin or /usr/local/jdk<version>/bin.

---

### Post by bmorency on 2007-08-30
to find the actual path of where java is installed type

```
update-alternatives --config java
```

the file /usr/bin/java is just a sym link to another location. if you have multiple versions of java installed for some reason it will let you pick which one you want to use.

---

### Post by gavinjb on 2007-08-30
Thanks, I changed the path in the .sh file to the correct path and it now works fine, thanks for all the help.

---

### Post by gavinjb on 2007-09-29
Hi,

I have just re-installed my PC with Kubuntu and I have tried to get FullSync to work again, but can't workout what I need to do to get the FULLSYNC_HOME path to work, the script has the following 2 lines to set this up

```

FULLSYNC_HOME=`dirname "$PRG"`/..
FULLSYNC_HOME=`cd "$FULLSYNC_HOME" && pwd`

```

and when I run which java, I get /usr/bin/java, can someone please tell me what I need to edit on this, 

Thanks.


Gavin,

---

### Post by gavinjb on 2007-09-29
figured it out, I was trying to change the wrong entry, all I needed to do was add an line at the end of settinh the Java path which was JAVACMD=/usr/bin/java

---

