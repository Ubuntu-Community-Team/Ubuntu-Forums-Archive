---
title: "Trouble executing Azureus"
date: 2007-01-14
forum: General Help
---

### Post by Absurd on 2007-01-14
So I am using the latest version of java (1.6.0) and other java apps. (especially Open Office) work fine, but I am having trouble running Azureus.

First of all, the directory where I have java install is /usr/lib/jvm/jre1.6.0

If I go into the bin director and attempt to run azureus with java ($./java azureus %u) I get an error that says

```
Exception in thread "main" java.lang.NoClassDefFoundError: azureus
```

How can I fix this problem? With symlinks, right? Where would they go?

Btw, if I attempt to run Azureus normally I get the following error.

```
/usr/bin/azureus: line 36: exec: java: not found
```

---

### Post by taurus on 2007-01-14
What's the output of this command from a terminal?

```
java -version
```

---

### Post by Absurd on 2007-01-14
If I go into the directory where java is installed and enter $./java -version I get

> java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

If I just do "$java -version" I get a BASH output that java was not found.

---

### Post by taurus on 2007-01-14
You either need to put **/usr/lib/jvm/jre1.6.0/bin** on your path (in ~/.bashrc) or you need to configure it with

```
sudo update-alternatives --config java
```
Then, see what happens when you run this command from anywhere?

```
java -version
```

---

### Post by Absurd on 2007-01-14
when I run 

```
sudo update-alternatives --config java
```

I get 

> There is only 1 program which provides java
(/usr/bin/gij-wrapper-4.1). Nothing to configure.

Well, the latest java was shown there before.

I installed it manually by the way.

What now?

---

### Post by taurus on 2007-01-14
From a terminal, run
```
gedit ~/.bashrc
```
Add the following two lines to the end of it.

```
PATH=$PATH:/usr/lib/jvm/jre1.6.0/bin
export PATH
```
Save it and then run

```
source ~/.bashrc
java -version
```
What's the output of the last command from above?

---

### Post by Absurd on 2007-01-14
> java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

[EDIT]Nevermind, I can get azureus running fine from konsole (by just entering "$azureus"), but I can't get it to run by clicking an icon on the desktop.

And azureus exits after being executed

> 
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=5861, tid=3085204384
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid5861.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#


---

### Post by Absurd on 2007-01-15
Update

Ok, I finally got azureus to work properly. The problem was that I was installing Azureus from a repository instead of grabbing it from sourceforge and manually installing.

Now you can add the [Resolved] tag. :P

---

### Post by pointym5 on 2007-01-16
So you're saying that the Azureus package in Edgy simply does not work? Have you (or has anybody) logged a bug?

---

### Post by Absurd on 2007-01-16
Well, in my experience, the Azureus package in Edgy did not work ***because*** I had manually installed the Java Runtime Environment manually.

---

### Post by schio on 2007-01-16
Check this:

[http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus](http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus)

---

### Post by Absurd on 2007-01-16
> **schio said:**
> Check this:

[http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus](http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus)
That's actually the guide I used to install it.

---

### Post by skynexus on 2007-01-17
I can confirm the exact same problem on my system. Oddly, Azureus appeared to work fine for some time (with Java 6 installed) until a few weeks ago. Re-installed Java but that did not help. Followed the above guide after reading the post and it solved the problem. Has anyone filed a bug report on this one?

---

### Post by Absurd on 2007-01-17
I don't see the bug going away until the latest jre makes it into the repos. (Perhaps in Feisty?)

---

### Post by mahiyar on 2007-01-25
I had the same problem and was about to take a deep plunge, when I read somewhere here in the forums that you just need to replace ~.azureus, that solved my problem.

---

