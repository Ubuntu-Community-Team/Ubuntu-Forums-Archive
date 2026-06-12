---
title: "hdfview won't start"
date: 2015-07-14
forum: General Help
---

### Post by necbot on 2015-07-14
I'm running Ubuntu 12.04 (I have to run this version, don't ask....) and I installed HDFview from the official repos.  When I tried to start it I get....

```
Exception in thread "main" java.awt.HeadlessException
    at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:207)
    at java.awt.Window.<init>(Window.java:535)
    at java.awt.Frame.<init>(Frame.java:420)
    at javax.swing.JFrame.<init>(JFrame.java:218)
    at ncsa.hdf.view.HDFView.<init>(HDFView.java:175)
    at ncsa.hdf.view.HDFView.main(HDFView.java:2162)

```

On the HDFview page in the troubleshooting section it says...

```
[COLOR=#383D44][FONT=Arial]**Linux:**[/FONT][/COLOR]

[LIST]
[*]1. Edit the hdfview.sh file
2. Find the line with "export JAVABIN="
3. Change the value to the right of the "=" to the location of the system installed Java.
4. Save the changes.
[/LIST]

```

So my file looks like this....

```
#!/bin/sh
# Shell script wrapper around the hdfview program,
# Copyright 2009 by Sylvestre Ledru <sylvestre@debian.og>
#
export JAVABIN="/usr/bin/java"
# Include the wrappers utility script
. /usr/lib/java-wrappers/java-wrappers.sh


# We prefer to use openjdk or Sun's java if available
find_java_runtime openjdk sun  || find_java_runtime


find_jars jhdf jhdf5 jhdfobj jhdf4obj jhdf5obj jhdfview jgraph
JAVA_ARGS="-Djava.library.path=/usr/lib/jni/ -Dswing.systemlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel "


run_java ncsa.hdf.view.HDFView -root /usr/share/doc/libjhdf-doc/ $*

```


When I do this it still gives me the same error message.  How do I run this program?  Thanks

---

### Post by Vladlenin5000 on 2015-07-14
What java version have you installed?

```
# We prefer to use openjdk or Sun's java if available
```


*Openjdk* is the one in Ubuntu repositories.

---

