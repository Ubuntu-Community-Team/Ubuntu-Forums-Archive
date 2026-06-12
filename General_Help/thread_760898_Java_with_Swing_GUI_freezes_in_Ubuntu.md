---
title: "Java with Swing GUI freezes in Ubuntu"
date: 2008-04-20
forum: General Help
---

### Post by Jojan on 2008-04-20
When I run the following program (and all others I've tried) in Ubuntu they tend to freeze up. It should quit when I press OK, but nothing happens. What could be wrong?

```
[COLOR="DarkOrchid"]import[/COLOR] javax.swing.*;
[COLOR="SeaGreen"]**public class**[/COLOR] temp {
    **[COLOR="SeaGreen"]public static void[/COLOR]** main(String args[]) {
        JOptionPane.showMessageDialog([COLOR="Magenta"]null[/COLOR], [COLOR="Magenta"]"Hello World!"[/COLOR]);
        System.exit(0);
    }
}
```

I'm using Ubuntu 7.10 32 bit with 512 MB RAM.

---

### Post by FluffyElmo on 2008-04-21
It works fine here, what version of Java do you have installed? Try *java -version* at the command line to make sure you are using the Sun JVM. The default JVM is GCJ and that may be your problem. You can find lots of guides on installing the Sun JDK but a quick version is:
```
sudo apt-get install sun-java6-jdk
sudo update-alternatives --config  
```

Hope this helps, for reference* java -version *returns the following on my system:
```
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
```

And after saving your class in the file *temp.java* the following commands ran your program as expected:
```
javac temp.java
java temp
```

---

### Post by Jojan on 2008-04-21
Fixed it! thank you!

---

### Post by FluffyElmo on 2008-04-21
Sorry, the command to change the default version is:
```
sudo update-alternatives --config java
```

You may also have to run it with javac if you have multiple jdks installed:
```
sudo update-alternatives --config javac
```

---

### Post by Jojan on 2008-04-21
Works fine, but I cant find how to fix this in Eclipse.

---

### Post by FluffyElmo on 2008-04-21
You have to get Eclipse to use the correct JVM. You can change the JVM the command line using something like this:
```
eclipse -vm /usr/lib/jvm/java-6-sun/jre/bin/java
```

There is a config file somewhere where you can make the change permanent. You can also set different JVMs for different projects in the project settings.

I can't be any more specific than that because it's been a long time since I used Eclipse and I don't have it installed anymore. I'm a Netbeans guy now:)

---

### Post by Jojan on 2008-04-22
I found where. Thank you!

---

### Post by new_at_linux on 2008-05-29
Sorry to revive thread, but I'm having the same problem.  When I used Ubuntu, everything worked.  I couldn't find the eclipse config file, but since I don't use eclipse all that much, I just ran it from the terminal with the command "eclipse -vm /usr/lib/jvm/java-6-sun/jre/bin/java".

Now I switched to Kubuntu and the command won't work.  I installed java6 OK and set it as the default, but when I use the command my program still freezes (its the same program as I used in ubuntu).

Can anyone help?

---

