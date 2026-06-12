---
title: "trouble updating java6 w/JVM 1.5 in Kubuntu"
date: 2008-03-21
forum: General Help
---

### Post by harryliddic on 2008-03-21
I need JVM 1.5 to run eclipse. My java file sits on my desktop under jre-6u5-linux-i586.bin. I have tried **'sudo aptitude upgrade'** then **'sudo aptitude install sun-java6-jre'** etc.Then I tried** apt-get **the same way always to get the error: cannot locate the file. I tried moving the file by drag-and-drop
and lost everthing. Is there a way I can add this file to the Synaptic? Is there any way for apt-get to see this file. why do I have the feeling that this is the first in a long string of problems getting this to work?

---

### Post by dabang on 2008-03-22
You cannot install jre-6u5-linux-i586.bin via apt. apt, respectively dpkg can only handle Debian packages (*.deb). If you have a local Debian package, you can install it by typing:
```
sudo dpkg -i /path/to/<package_name>.deb
```

As far as I know, Ubuntu provides jre6 update 2, wich is installed by:
```
sudo apt-get install sun-java6-jre
```
And check if it's default:
```
sudo update-alternatives --conig java
```

If you really need update 5, you may install jre-6u5-linux-i586.bin like this:
Make it executable:
```
chmod +x jre-6u5-linux-i586.bin
```
If you need to install it system wide for all users, you could copy the file to /opt (this way it won't conflict with Ubuntu's java) and run it:
```
sudo cp jre-6u5-linux-i586.bin /opt
cd /opt
sudo ./jre-6u5-linux-i586.bin
```
If it's done:
```
sudo rm /opt/jre-6u5-linux-i586.bin
```

Now set your JAVA_HOME to /opt/jre...:
```
export JAVA_HOME= /opt/jre...
```
(of course replace "..." with corect path)
And add it's "bin" to your PATH:
```
export PATH=$JAVA_HOME/bin:$PATH
```

By the way:
```
sudo apt-get install eclipse
```
should take care of everything.

---

### Post by harryliddic on 2008-03-22
you solved a very knotty problem.




thanks a lot!

---

