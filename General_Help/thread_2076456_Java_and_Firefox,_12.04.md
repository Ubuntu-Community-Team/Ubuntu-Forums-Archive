---
title: "Java and Firefox, 12.04"
date: 2012-10-26
forum: General Help
---

### Post by d3fau1t on 2012-10-26
Hi, I'm having a lot of trouble getting Java to work with my browser in 12.04. I currently have version 7 JDK installed from the repos. 

```
$java -version
java version "1.7.0_07"
OpenJDK Runtime Environment (IcedTea7 2.3.2) (7u7-2.3.2a-0ubuntu0.12.04.1)
OpenJDK 64-Bit Server VM (build 23.2-b09, mixed mode)

$javac -version
javac 1.7.0_07
```

I deleted the links in the firefox and mozilla folders following a tutorial. Now there is no libnpjp2.so or libjavaplugin_oji.so to link to -- which hadn't worked when they were there.

Any idea how to get this working with Firefox?

---

### Post by d3fau1t on 2012-10-26
It is so annoying!

---

### Post by Twilk73 on 2012-10-27
In 12.10 this worked for me. 

First I uninstalled all the java programs I could find in the ubuntu software center. Then after searching the web I found this info. Ad bam java works on the browser now. Reason I uninstalled all the java programs was because you cant have to java programs they will conflict with one another. 

To install JRE 7:
1. Open a terminal window.
2. Type in the following commands then hit Enter after each.
sudo sh -c "echo 'deb [http://www.duinsoft.nl/pkg debs](http://www.duinsoft.nl/pkg debs) all' >> /etc/apt/sources.list"
sudo apt-get update
sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 5CB26B26
sudo apt-get update
sudo apt-get install update-sun-jre

Edit: Hope this helps man.

[COLOR="Red"]If this is not working for you.[/COLOR]

Ok so after crashing ubuntu and starting back fresh I went to install this and I could not get it to work. I searched the ubuntu store looking for java instalations but couldnt find any. So recalling what I did last time i just retraced my steps. I first installed iced tea plugin. Once installed I then searched java on my installed tab and then procceded to uninstall all the java's taht where checked off. Then I tried this task and it work just fine. In conclusion if this is not working its because there is some form of java already installed on your system. 

I am a total newb so this retarded step is all because I still learning a lot lol.

---

### Post by d3fau1t on 2012-10-28
Thank you very much! 

It worked perfectly, other than me having to change the url to "deb [http://www.duinsoft.nl/pkg](http://www.duinsoft.nl/pkg) debs all".

---

### Post by jcoles on 2012-10-28
Success here too, Twilk73.

Perhaps you could edit your message. It appears that the '*'s should be spaces.
Can you explain what your commands do? It looks like you are adding a repository in the Netherlands and updating Java from there. Is that right? 

Without this, Ubuntu's java installation is rather lame. The Iced-Tea plugin fails to work, even though java -version shows "1.7.0_09-b05". Sometimes Firefox completely locks up trying to load an applet. Now it works fine. 

Thanks again.

---

### Post by dee119 on 2012-10-28
Many thanks for your excellent input regarding #java

Success here as well.

Thank you ;)

---

### Post by d3fau1t on 2012-10-28
Just a note, I was also able to get the JDK working great with this, by going to [http://www.oracle.com/technetwork/java/javase/downloads/jdk7u9-downloads-1859576.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk7u9-downloads-1859576.html), downloading the Linux X64 tarball, issuing this command:

```
sudo mkdir -p /usr/lib/jvm/jdk1.7.0 
```

Then, after extracting, moving the contents of the tarball to the jdk1.7.0 folder:

```
sudo mv jdk1.7.0_09/* /usr/lib/jvm/jdk1.7.0/
```

Then entering:

```
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.7.0/bin/java" 1
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.7.0/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jdk1.7.0/bin/javaws" 1
```

... which I read about [here]("http://www.liberiangeek.net/2012/04/install-oracle-java-jdk-7-in-ubuntu-12-04-precise-pangolin/").

And that's it!

---

### Post by d3fau1t on 2012-12-11
This also works in Debian Wheezy/Sid.

---

