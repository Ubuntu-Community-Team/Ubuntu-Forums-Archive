---
title: "A Java Problem"
date: 2007-06-25
forum: General Help
---

### Post by bertfallen on 2007-06-25
Right, I want to use Frostwire but it requires Java; Where can I get this from?

**The Error Message;**
> 
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)


---

### Post by MCSE_Crossover on 2007-06-25
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts

from [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by bertfallen on 2007-06-25
> **MCSE_Crossover said:**
> sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts

from [www.ubuntuguide.org](www.ubuntuguide.org)

Okay that sort of worked, but now I get this;

> Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)


---

### Post by MCSE_Crossover on 2007-06-25
You went though the whole installation, agreeing to the license agreements and everything? And you are still getting those errors? Did it pop up with that blue screen in the terminal window?

---

### Post by bertfallen on 2007-06-25
> **MCSE_Crossover said:**
> You went though the whole installation, agreeing to the license agreements and everything? And you are still getting those errors? Did it pop up with that blue screen in the terminal window?

I never got a License agreement O_o, it just said 
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      

//Some Other information that I can't get back.

Writing extended state information... Done


---

### Post by ThrobbingBrain66 on 2007-06-25
If you aren't using Feisty, you may have to use Sun Java 5, as I don't think Java 6 is in any repos earlier than Feisty.  Use the command that MCSE_Crossover gave you, but replace the '6' with '5'.  If that doesn't work, you maybe need to update your default Java selection:

```
sudo update-java-alternatives -l
```

Type in Java 5 or 6's corresponding number and hit enter.
Then try opening Frostwire again.

---

### Post by bertfallen on 2007-06-25
> **ThrobbingBrain66 said:**
> If you aren't using Feisty, you may have to use Sun Java 5, as I don't think Java 6 is in any repos earlier than Feisty.  Use the command that MCSE_Crossover gave you, but replace the '6' with '5'.  If that doesn't work, you maybe need to update your default Java selection:

```
sudo update-java-alternatives -l
```

Type in Java 5 or 6's corresponding number and hit enter.
Then try opening Frostwire again.

Well... I'm using 7.04 Thats Feisty, right?

---

### Post by ThrobbingBrain66 on 2007-06-25
> **bertfallen said:**
> Well... I'm using 7.04 Thats Feisty, right?

Yes, sir, it is.

Did the update-java-alternatives command work?

---

### Post by bertfallen on 2007-06-25
> **ThrobbingBrain66 said:**
> Yes, sir, it is.

Did the update-java-alternatives command work?

nope :(

> java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1041 /usr/lib/jvm/java-gcj
brett@Bretts-Desktop:~$ cd Desktop
brett@Bretts-Desktop:~/Desktop$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)


---

### Post by Damiel on 2007-06-25
Try this command:
```
sudo update-java-alternatives -s java-6-sun
```

You may also need to add this line on top of the JVM list in /etc/jvm :
```
/usr/lib/jvm/java-6-sun
```

---

### Post by bertfallen on 2007-06-25
Ah cheers, that worked.

Thanks all for your help.

---

