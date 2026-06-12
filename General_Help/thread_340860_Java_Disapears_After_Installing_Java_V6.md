---
title: "Java Disapears After Installing Java V6"
date: 2007-01-17
forum: General Help
---

### Post by chr1831 on 2007-01-17
ok, i installed java 6 (or atleast try to) and now i no longer have a java command :/, how can i get it back?

---

### Post by taurus on 2007-01-17
Applications -> Accessories -> Terminal
```
sudo update-alternatives --config java
```

---

### Post by chr1831 on 2007-01-17
ive tried that 5times :/


root@chris-laptop:/home/chris/Desktop# update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/bin/gij-wrapper-4.1
 +        2    /usr/lib/j2se/1.4/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          4    /usr/lib/jvm/java-6-sun/bin/java

Press enter to keep the default[*], or type selection number: 4
Using `/usr/lib/jvm/java-6-sun/bin/java' to provide `java'.
root@chris-laptop:/home/chris/Desktop# java
bash: java: command not found
root@chris-laptop:/home/chris/Desktop#

---

### Post by taurus on 2007-01-17
What happens to this command?

```
java -version
```
Where did you install java 6 anyway?

---

### Post by chr1831 on 2007-01-17
/usr/lib/jvm and i edited my post above to show the output of update-alts

root@chris-laptop:/home/chris/Desktop# java -version
bash: java: command not found
root@chris-laptop:/home/chris/Desktop#

---

### Post by taurus on 2007-01-17
Well, you have two options.

1.  Link the latest version, 6.0, to /usr/bin/java.
```
sudo ln -s /usr/lib/jvm/java-6-sun/bin/java  /usr/bin/java
```

2.  Modify your ~/.bashrc and add the path to it.
```
gedit ~/.bashrc
```
Add these two lines to it.
```
PATH=$PATH:/usr/lib/jvm/java-6-sun/bin
export PATH
```

Log out and back in again (reboot if you wish) and see if you get the right version with this command.

```
java -version
```

---

### Post by chr1831 on 2007-01-17
i just did the ln :D but uhhh yeah :/

chris@chris-laptop:~/Desktop$ java -version
Error: could not open `/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/jvm.cfg'

---

### Post by taurus on 2007-01-17
Can you print out these two commands?

```
ls -la /usr/bin/java
ls -la /usr/lib/jvm
```

---

### Post by chr1831 on 2007-01-17
chris@chris-laptop:~/Desktop$ ls -la /usr/bin/java
lrwxrwxrwx 1 root root 32 2007-01-17 18:17 /usr/bin/java -> /usr/lib/jvm/java-6-sun/bin/java
chris@chris-laptop:~/Desktop$ ls -la /usr/lib/jvm
total 79904
drwxr-xr-x   4 root  root      4096 2007-01-17 17:47 .
drwxr-xr-x 126 root  root     61440 2007-01-17 16:44 ..
lrwxrwxrwx   1 root  root        23 2007-01-16 23:17 java-1.5.0-sun -> java-1.5.0-sun-1.5.0.08
drwxr-xr-x   8 root  root      4096 2007-01-16 23:18 java-1.5.0-sun-1.5.0.08
-rw-r--r--   1 root  root      2361 2006-08-17 16:49 .java-1.5.0-sun.jinfo
lrwxrwxrwx   1 root  root        19 2007-01-17 17:30 java-6-sun -> java-6-sun-1.6.0.00
drwxr-xr-x   6 root  root      4096 2007-01-17 17:33 java-6-sun-1.6.0.00
-rw-r--r--   1 root  root      2522 2006-12-23 02:45 .java-6-sun.jinfo
-rw-r--r--   1 chris chris 62678298 2007-01-17 16:39 jdk-6-linux-i586.bin
-rwxr-xr-x   1 chris chris 18964005 2007-01-17 16:55 jre-6-linux-i586.bin
chris@chris-laptop:~/Desktop$

---

### Post by taurus on 2007-01-17
```
ls  /usr/lib/jvm/java-6-sun-1.6.0.00/bin
```

---

### Post by chr1831 on 2007-01-17
chris@chris-laptop:~/Desktop$ ls  /usr/lib/jvm/java-6-sun-1.6.0.00/bin
ControlPanel  java    jcontrol  orbd     policytool  rmiregistry  tnameserv
i386          javaws  keytool   pack200  rmid        servertool   unpack200
chris@chris-laptop:~/Desktop$

---

### Post by taurus on 2007-01-17
```
ls -la /usr/lib/jvm/java-6-sun-1.6.0.00
```

---

### Post by chr1831 on 2007-01-17
chris@chris-laptop:~/Desktop$ ls -la /usr/lib/jvm/java-6-sun-1.6.0.00
total 24
drwxr-xr-x 6 root root 4096 2007-01-17 17:33 .
drwxr-xr-x 4 root root 4096 2007-01-17 17:47 ..
drwxr-xr-x 3 root root 4096 2007-01-17 17:30 bin
drwxr-xr-x 2 root root 4096 2006-12-23 02:45 ext
drwxr-xr-x 7 root root 4096 2007-01-17 17:33 jre
drwxr-xr-x 4 root root 4096 2007-01-17 17:30 man
lrwxrwxrwx 1 root root   10 2007-01-17 17:33 .systemPrefs -> /etc/.java

---

### Post by taurus on 2007-01-17
```
ls -la /usr/lib/jvm/java-6-sun-1.6.0.00/bin
```

---

### Post by chr1831 on 2007-01-17
chris@chris-laptop:~/Desktop$ ls -la /usr/lib/jvm/java-6-sun-1.6.0.00
total 24
drwxr-xr-x 6 root root 4096 2007-01-17 17:33 .
drwxr-xr-x 4 root root 4096 2007-01-17 17:47 ..
drwxr-xr-x 3 root root 4096 2007-01-17 17:30 bin
drwxr-xr-x 2 root root 4096 2006-12-23 02:45 ext
drwxr-xr-x 7 root root 4096 2007-01-17 17:33 jre
drwxr-xr-x 4 root root 4096 2007-01-17 17:30 man
lrwxrwxrwx 1 root root   10 2007-01-17 17:33 .systemPrefs -> /etc/.java
chris@chris-laptop:~/Desktop$ ls -la /usr/lib/jvm/java-6-sun-1.6.0.00/bin
total 12
drwxr-xr-x 3 root root 4096 2007-01-17 17:30 .
drwxr-xr-x 6 root root 4096 2007-01-17 17:33 ..
lrwxrwxrwx 1 root root   23 2007-01-17 17:30 ControlPanel -> ../jre/bin/ControlPanel
drwxr-xr-x 3 root root 4096 2007-01-17 17:30 i386
lrwxrwxrwx 1 root root   15 2007-01-17 17:30 java -> ../jre/bin/java
lrwxrwxrwx 1 root root   17 2007-01-17 17:30 javaws -> ../jre/bin/javaws
lrwxrwxrwx 1 root root   19 2007-01-17 17:30 jcontrol -> ../jre/bin/jcontrol
lrwxrwxrwx 1 root root   18 2007-01-17 17:30 keytool -> ../jre/bin/keytool
lrwxrwxrwx 1 root root   15 2007-01-17 17:30 orbd -> ../jre/bin/orbd
lrwxrwxrwx 1 root root   18 2007-01-17 17:30 pack200 -> ../jre/bin/pack200
lrwxrwxrwx 1 root root   21 2007-01-17 17:30 policytool -> ../jre/bin/policytool
lrwxrwxrwx 1 root root   15 2007-01-17 17:30 rmid -> ../jre/bin/rmid
lrwxrwxrwx 1 root root   22 2007-01-17 17:30 rmiregistry -> ../jre/bin/rmiregistry
lrwxrwxrwx 1 root root   21 2007-01-17 17:30 servertool -> ../jre/bin/servertool
lrwxrwxrwx 1 root root   20 2007-01-17 17:30 tnameserv -> ../jre/bin/tnameserv
lrwxrwxrwx 1 root root   20 2007-01-17 17:30 unpack200 -> ../jre/bin/unpack200
chris@chris-laptop:~/Desktop$                               


is there like a deb that will redo the java for me and fix this?

---

### Post by taurus on 2007-01-17
```
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/java -version
```

---

### Post by chr1831 on 2007-01-17
chris@chris-laptop:~/Desktop$ /usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/java -version
Error: could not open `/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/jvm.cfg'

---

### Post by taurus on 2007-01-17
There is something wrong with your version of java!  How did you install it anyway?  

[https://sdlc4b.sun.com/ECom/EComActionServlet;jsessionid=72CBE9A361D6FB1B57F71C50ECBF5E77](https://sdlc4b.sun.com/ECom/EComActionServlet;jsessionid=72CBE9A361D6FB1B57F71C50ECBF5E77)

Except the license.  Then click on the "Linux self-extracting file" and download it.  It will probably  be saved in your $HOME/Desktop, jdk-6-linux-i586.bin.  

Now, move it to /opt and unpack it there.

```
cd ~/Desktop
chmod 755 jdk-6-linux-i586.bin
sudo mv jdk-6-linux-i586.bin /opt
cd /opt
sudo ./jdk-6-linux-i586.bin
sudo rm /usr/bin/java
sudo ln -s /opt/jdk1.6.0/bin/java  /usr/bin/java
source ~/.bashrc
java -version
```

---

### Post by chr1831 on 2007-01-17
im just going to re install, ile wait for an official release of java6, java hates me i hate it i guess but its just so nice :-/

---

### Post by taurus on 2007-01-17
I just wrote you a step by step but I guess I just wasted my time here then!  ](*,)

---

