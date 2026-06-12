---
title: "jedit installation problems"
date: 2005-04-17
forum: General Help
---

### Post by clippyhater on 2005-04-17
I have Sun's SDK installed, and java -version gives me the expected output.

However, when I attempt to run my just-installed jedit, I get the following output:

```

dave@maximus:~$ jedit
[error] main: Exception in thread "main"
[error] main: java.awt.AWTError: Cannot load AWT toolkit: gnu.awt.gtk.GtkToolkit not found in [file:/usr/share/jedit/jedit.jar, core:/]
[error] main:    at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.4.0.0)
[error] main:    at java.awt.Component.getToolkit() (/usr/lib/libgcj.so.4.0.0)
[error] main:    at java.awt.Component.getFontMetrics(java.awt.Font) (/usr/lib/libgcj.so.4.0.0)
[error] main:    at org.gjt.sp.jedit.gui.SplashScreen.SplashScreen() (Unknown Source)
[error] main:    at org.gjt.sp.jedit.GUIUtilities.showSplashScreen() (Unknown Source)
[error] main:    at org.gjt.sp.jedit.jEdit.main(java.lang.String[]) (Unknown Source)

```

Any ideas, pointers, etc., to help get me up and running?

Thanks!

---

### Post by fubar2k1 on 2005-05-05
Install the J2SE Runtime Environment (JRE) as explained in [http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

------------
wget -c [http://frankandjacq.com/ubuntuguide/jre-1_5_0_03-linux-i586.bin](http://frankandjacq.com/ubuntuguide/jre-1_5_0_03-linux-i586.bin)
sh jre-1_5_0_03-linux-i586.bin
sudo mkdir /usr/java
sudo mv jre1.5.0_03/ /usr/java/
sudo chown -R root:root /usr/java/jre1.5.0_03/
sudo ln -s /usr/java/jre1.5.0_03/bin/java /usr/bin/java
sudo ln -s /usr/java/jre1.5.0_03/bin/java_vm /usr/bin/java_vm
---------------

then 

$ sudo gedit /etc/bash.bashrc

and add the following lines

--------------------------------------------------
JAVA_HOME=/usr/java/jre1.5.0_03
export JAVA_HOME
#PATH=$PATH:$JAVA_HOME/bin
PATH=$JAVA_HOME/bin:$PATH
export PATH
------------------------

test it with (probably you'll have to logout and log-in)

java -version

That should do it

---

