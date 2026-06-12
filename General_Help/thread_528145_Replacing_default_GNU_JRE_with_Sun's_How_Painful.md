---
title: "Replacing default GNU JRE with Sun's: How Painful?"
date: 2007-08-17
forum: General Help
---

### Post by Peter108 on 2007-08-17
Howdy.

I have just used dpkg to install a Subversion client called SmartSVN.  However when I try to execute the client I'm told that "an unsupported Java version has been detected. Please install a JRE from SUN (java.sun.com).  Indeed the JRE I have is 1.4.2 "gij (GNU libgcj version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)"

When I go over to java.sun.com, I find two options for their latest JRE
```
 
Linux RPM in self-extracting file       jre-6-linux-i586-rpm.bin       17.60 MB
Linux self-extracting file              jre-6-linux-i586.bin           18.09 MB
```

I'm pretty noob, so I have a couple of problems:
[LIST=1]
[*]Are there serious risks to using one of these versions of Sun's JRE over GNU's.  I mean, Sun's is so widely used, I'd be surprised, but I don't know?
[*]Are either of the above files installable via the two methods I'm familiar with: apt-get install and dpkg -i.  If so is there some sort of pre-massage step I need to apply?
[*]If neither of the 2 above install methods would work on these files, is there anything that would?  If so, is there a link to the method?
[/LIST]

Thanks.

---

### Post by Gremlinzzz on 2007-08-17
jre-6-linux- is in synaptic package manager
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Java_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Java_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by gobbles414 on 2007-08-17
Hi all,

It is also important to make sure that Sun's Java is your system default, as some programs will not run with other versions (e.g. Mercury Messenger). One method for selecting your default Java is discussed [here]("https://help.ubuntu.com/community/Java"). I'm sure there are other methods as well.

---

### Post by IcemanV9 on 2007-08-17
At least, you're familiar with apt-get. And, like Gremlinzz said, it is in repo.

```
apt-cache search sun-java
```

You'll get the list of sun-java. Install java, then do what gobbles414 said, to set sun-java as your system default.

```
sudo update-alternatives --config java
```

To check if sun-java is default, then do

```
java -version
```

Then, you should be all set with SmartSVN installation.

---

### Post by Peter108 on 2007-08-19
Just read the man page for update-alternatives.  Very cool feature.   That answers my final question about whether I need to update remove gnu jre.  Apparently not.  Thanks, everybody.

---

