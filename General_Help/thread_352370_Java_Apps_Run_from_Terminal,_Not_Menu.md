---
title: "Java Apps Run from Terminal, Not Menu"
date: 2007-02-03
forum: General Help
---

### Post by LaneLester on 2007-02-03
Although java apps (jedit, gfp) will run fine when started from the terminal, they won't as Gnome menu items. I have this at the bottom of .bashrc, and I confirmed that the path is OK:

export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.00
export PATH=${JAVA_HOME}/bin:${PATH}

Lane

---

### Post by Ramses de Norre on 2007-02-03
If you give in a path you need to specify the class path for java, like this:```
java -cp /home/user/java/ /home/user/java/main
``` Or you can write a script and cd to the right directory first.

---

### Post by LaneLester on 2007-02-03
Thanks, Ramses. I tried this script:
#!/bin/bash
cd /opt/GFP
java -jar gfd.jar
which works fine in the terminal, but not from the menu.

I just tried this for jedit in the menu and it didn't work (I probably have the syntax wrong... there is no main folder):
java -cp /usr/lib/jvm/java-6-sun-1.6.0.00/ /usr/lib/jvm/java-6-sun-1.6.0.00/bin -jar /usr/share/jEdit/jedit.jar

Gnome gives the error: Failed to execute child process "java" (no such file or directory)

Lane

---

### Post by pseudonym on 2007-02-03
Drop a symlink to your script in /usr/local/bin . Then just use the name of the link as the command in your menu entry/panel launcher.

---

### Post by LaneLester on 2007-02-03
> **pseudonym said:**
> Drop a symlink to your script in /usr/local/bin . Then just use the name of the link as the command in your menu entry/panel launcher.

There must be something wrong with my system. That makes perfect sense, and indeed it works fine when executed from the terminal... just not from the menu. Neither "gfp" by itself nor "/usr/local/bin/gfp". Both work from the terminal while in any directory.

Perhaps a related observation, Gnome Commander provides an execution field at the bottom. When in /usr/local/bin, ./gfp does not work, although it does work in the terminal.

Lane

---

### Post by phossal on 2007-02-03
Eclipse exhibits the same behavior depending on how you download it and try to launch it. When you download eclipse from the repositories for example, the command line calls /usr/bin/eclipse (in most cases), which is actually a shell script that tests for things like the environment variable JAVA_HOME.  The package manager also updates the gnome menu, and *that* icon is actually a link to the executable included in the package. 

Just because you have JAVA_HOME set, and even though you can launch it from the terminal, it doesn't lauch from the menu. That's because the *packaged* version doesn't use the script (from the menu link), but looks for a JVM in /usr/lib/jvm...  It's often necessary to manually update the jvm list file.

If you happen to download eclipse from eclipse.org, you can (again) launch it using the startup.jar, or using the "executable" (by double clicking) once you've run chmod +x.

I don't know how you aquired the packages that won't run, or how you got Java, or how you've configured your system, but it's likely a *little* thing that's tripping you up. If you've installed the Java JDK directly from SUN, for example, you have everything you need to run *all* java programs that don't require additional extensions. 

Good luck

---

### Post by LaneLester on 2007-02-03
> **phossal said:**
> Just because you have JAVA_HOME set, and even though you can launch it from the terminal, it doesn't lauch from the menu. That's because the *packaged* version doesn't use the script (from the menu link), but looks for a JVM in /usr/lib/jvm...  It's often necessary to manually update the jvm list file.
Where is the jvm list?

Lane

---

### Post by pseudonym on 2007-02-03
I think what's meant is to register your Java version system-wide by running - ```
sudo update-alternatives --config java
``` and choosing your default Java version (you'll likely have only one).

---

### Post by phossal on 2007-02-03
> **pseudonym said:**
> I think what's meant is to register your Java version system-wide by running 
I'm not sure if you're referring to my post or not, but that isn't at all what I mean. Depending on how you acquire a program, there can be multiple ways of launching it, and multiple *sources* that the launch mechanism looks to in order to determine whether dependencies exists.

My example about eclipse below is that there are three ways to launch the thing, and using update-alternatives resolves only *one*.

I just don't personally know where the JEdit menu icon launches from. I'm not sure how the package was acquired and if it was a *package* that put the icon in the menu, or the user. The first thing I would do is try to determine what the menu icon is doing. Is there *something* at /usr/bin/jedit  ? Is it a script? A symlink? An executable? What's the mechanism?

---

### Post by LaneLester on 2007-02-04
> **pseudonym said:**
> I think what's meant is to register your Java version system-wide by running - ```
sudo update-alternatives --config java
``` and choosing your default Java version (you'll likely have only one).
Actually, I see that I have *three* by using that command:
[INDENT]  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
 +        3    /usr/lib/jvm/java-6-sun/jre/bin/java[/INDENT]

The command said:
[INDENT]Press enter to keep the default[*], or type selection number:[/INDENT]

Since a "+" isn't a "*," I entered "3," and the problem was solved! Both jedit and gfp now work by having simply "jedit" or "gfp" in the menu field.

Thanks to everyone who responded to my plea for help.

Lane

---

### Post by phossal on 2007-02-04
That was a disappointingly (although I correctly anticipated) easy fix. I learned something useful here, too. I've become so used to helping people fix certain kinds of problems that I only look for those kind of solutions. I'll have to get out of that rut. You could've gotten *around* that problem another way, but I'm glad you didn't.

Glad you're up and running! Cheers!

---

