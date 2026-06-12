---
title: "Problems executing .jar"
date: 2008-01-30
forum: General Help
---

### Post by FleetAdmiral74 on 2008-01-30
Behold, ```
ed@ed-desktop:~/java$ java -jar /home/ed/al/gloria050/tedv091/ted.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at javax.swing.JFrame.<init>(libgcj.so.81)
   at ted.TedMainDialog.<init>(TedMainDialog.java:112)
   at ted.TedMain.main(TedMain.java:32)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannotopen shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...6 more
```

But what does it all mean?

Following instructions from [http://www.ted.nu/wiki/index.php/Running_ted](http://www.ted.nu/wiki/index.php/Running_ted)

---

### Post by jcwmoore on 2008-01-30
based on your output and the link you provided, you are not running the correct version of java,you are running the GNU java (gcj) and not the sun version of java.  The ted web site said it needs the java run time from java.com (that is the sun version...) give me a minute and i'll link you to a guide to install sun java...

EDIT:
ok look here

[http://ubuntu-tutorials.com/2006/11/21/how-to-install-suns-java-development-kit-jdk-v50-ubuntu-6061-610/]("http://ubuntu-tutorials.com/2006/11/21/how-to-install-suns-java-development-kit-jdk-v50-ubuntu-6061-610/")

now i think you want to replace java5 with java6 as that is the current version avaliable...

you can also install it via Synaptic,

make sure all repositories (it's in the multiverse repository think....) are enabled and search for "sun java" and select the sun java 6 SDK, that should get you set up

---

### Post by pointone on 2008-01-30
```
sudo apt-get install libgcj7-1-awt
```

You're missing the AWT toolkit; specifically, the file libgtkpeer.so. This is found the the above package. It may be just libgcj7-awt on your system.

---

### Post by FleetAdmiral74 on 2008-01-30
Ok. I actually just managed to complete the official java install guide from [http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)

Still does not verify on the website though, when it asks to check...

Working on that last command now

Could the two versions i have come into conflict? as in, should I remove the gnu version i have?

edit: keep in mind, we are kinda working on two different fronts here, so it can get confusing. one is with the ted command java thing, and the other is getting java installed correctly and working in firefox. granted, there is some overlap, but it kinda complicates things when I think about it :)

after running that last command, still getting the same thing (i think). Im posting the output incase it actually is different, but if it is the same sorry for taking up more space!```
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at javax.swing.JFrame.<init>(libgcj.so.81)
   at ted.TedMainDialog.<init>(TedMainDialog.java:112)
   at ted.TedMain.main(TedMain.java:32)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannotopen shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...6 more
```

---

### Post by jcwmoore on 2008-01-30
> 
Could the two versions i have come into conflict? as in, should I remove the gnu version i have?

no, not really, i have both version installed on my machine, the issue is, what happens with you type the command, "java" does that mean the gcj java or the sun java...  That link i gave tells you how to update which version of java to run when you type "java"

```
sudo update-java-alternatives -s java-1.5.0-sun
```

but you downloaded version 1.6.0 so just type java-1.6.0-sun... it has been a while sense I have done this myself though

---

### Post by FleetAdmiral74 on 2008-01-30
huh, command is not found.

ah ha! you edited your post, i was wondering what link you spoke of. let me take a few min to peruse that...

---

### Post by jcwmoore on 2008-01-30
> after running that last command, still getting the same thing (i think). Im posting the output incase it actually is different, but if it is the same sorry for taking up more space!

run the command 
```
java -version
```

what does it say?

> 
ah ha! you edited your post, i was wondering what link you spoke of. let me take a few min to peruse that...

it looks like we are about 5 minutes out of sync....

---

### Post by FleetAdmiral74 on 2008-01-30
Yay, the program is starting up fine now! 

Now, we must pray I can actually get the program itself to work properly!

Oh, and ill keep this open for a while, but since the issue of java not verifying in firefox properly is not very important (since i can use most sites), ill just mark it as solved in a little while.

Thank you, gracias, and arigato!

---

