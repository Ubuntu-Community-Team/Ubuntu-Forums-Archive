---
title: "ant is broken!"
date: 2005-07-29
forum: General Help
---

### Post by DamnDirtyApe on 2005-07-29
I'm getting an error when trying to use ant:

```
doug@aragorn:~$ sudo apt-get -qq install ant

Preconfiguring packages ...
Selecting previously deselected package ant.
(Reading database ... 99797 files and directories currently installed.)
Unpacking ant (from .../ant_1.6.2-2ubuntu2_all.deb) ...
Setting up ant (1.6.2-2ubuntu2) ...

doug@aragorn:~$ ant
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/tools/ant/launch/Launcher
doug@aragorn:~$
```

Can anyone suggest what's gone wrong here?

---

### Post by Xian on 2005-07-29
Try using the install session below.
It should be suffcient to get Ant installed properly.

You can probably shortcut this by the second example.
However, I have not tested this method.
Be sure you have the [Extra Repos](http://ubuntuguide.org/#extrarepositories) added to your source list.

```
$ sudo apt-get install sun-j2sdk1.5 antlr classpath classpath-common cpp-4.0 ecj-bootstrap fastjar g++-4.0 gcc-4.0 gcj-4.0 gij-4.0 gjdoc java-gcj-compat junit jython libbcel-java libbsf-java libcommons-logging-java libcommons-net-java libedit2 libgcj-common libgcj6 libgcj6-awt libgcj6-common libgcj6-dev libgnucrypto-java libgnuinet-java libgnujaf-java libgnujaxp-java libgnujaxp-jni libgnumail-java libjaxp1.2-java libjdepend-java libjessie-java liboro-java libreadline-java libregexp-java libstdc++6-4.0-dev libxalan2-java libxerces2-java libjsch-java
```

```
$ sudo apt-get build-dep ant
```
Now you should be set and ready to run ant.
Be _certain_ to read the [Ant User Manual](http://ant.apache.org/manual/running.html#commandline).
Here is an excerpt:

[i]"If you've installed Ant as described in the Installing Ant section, running Ant from the command-line is simple: just type ant.

When no arguments are specified, Ant looks for a build.xml file in the current directory and, if found, uses that file as the build file and runs the target specified in the default attribute of the <project> tag. To make Ant use a build file other than build.xml, use the command-line option -buildfile file, where file is the name of the build file you want to use.
If you use the -find [file] option, Ant will search for a build file first in the current directory, then in the parent directory, and so on, until either a build file is found or the root of the filesystem has been reached. By default, it will look for a build file called build.xml. To have it search for a build file other than build.xml, specify a file argument. Note: If you include any other flags or arguments on the command line after the -find flag, you must include the file argument for the -find flag, even if the name of the build file you want to find is build.xml."[/i]

---

