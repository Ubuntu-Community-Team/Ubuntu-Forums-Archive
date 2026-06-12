---
title: "Eclipse not working in Ubuntu 8.04"
date: 2008-04-30
forum: General Help
---

### Post by adilbaig on 2008-04-30
I have downloaded the **PDT eclipse** from eclipse.org. I have also installed **sun-java6-jre** from synaptics. This is what **"java -version" ** shows

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

I have downloaded eclipse to ~/Programs/eclipse

Problem is when i go to the folder in command-line and type **"./eclipse"** , i get this error message 

"bash: ./eclipse: No such file or directory"

And, here's the funny part[B]

"adil@adil:~/Programs/eclipse$ ls
about_files  configuration  eclipse.ini   features  libcairo-swt.so  plugins
about.html   eclipse        epl-v10.html  icon.xpm  notice.html      readme
"[/B]

Needless to say, HELP!!!

---

### Post by ibutho on 2008-04-30
What happens if you use the full path name e.g.
```
~/Programs/eclipse/eclipse
```

---

### Post by adilbaig on 2008-05-01
Nope.

```

adil@adil:~$ ~/Programs/eclipse/eclipse
bash: /home/adil/Programs/eclipse/eclipse: No such file or directory

```

That wouldn't work as expected. Neither does this

```
adil@adil:~/Programs/eclipse$ ./eclipse
bash: ./eclipse: No such file or directory

```

:(

---

### Post by adilbaig on 2008-05-01
I am using Ubunto 8.04 for AMD 64 architechture. I dont know if that has anything to do with this problem

---

### Post by zhark1 on 2008-05-03
I have the same problem, only way I can get an Eclipse working for PHP development is by downloading the newest Eclipse (Europa) from Eclipse.org and using the PHPEclipse nightly software update, even then it crashes every once in a while. PHPEclipse doesn't work at all in with the Eclipse in Synaptic, and the PDT Eclipse package from the PDT project homepage doesn't work either (1.0.2).

I'm running Ubuntu AMD64 desktop.

---

### Post by jamesstansell on 2008-05-05
There is a problem with 64bit Java and Eclipse.  A lot of people are recomming to use sun-java5 to run eclipse, but configuring eclipse to use either sun-java6 or openjdk-6 for running/debuggin your application.  There are several bug reports on launchpad about this.

---

### Post by adilbaig on 2008-05-06
I can get Eclipse working now, but not without its issue.

First, for those who can't get Eclipse running. Download the 32-bit version of Europa, and download the latest JRE V6 32bit from sun's site. 

Put the JRE inside the eclipse folder and in eclipse.ini, point the vm to that jre like so

```
-vm jre/bin/java
```

This works fine, including the new version of PDT. 

BUT! the "Find and Install" feature fails for all sites. Its gives an error like 

> premature end of file 

Dont know what to do about that?!

I can download plugins from the the browser and "unzip" them in eclipse, but that's not how i want it. Any suggestions?

BTW, my Eclipse does not crash, because its 32bit. The rest of my system uses the 64bit version of JDK6

---

### Post by ftaylor on 2008-05-06
You could always try **sudo apt-get install eclipse**
Maybe the mighty terminal will know what to do. My eclipse works fine from this.

---

### Post by jamesstansell on 2008-05-06
> **adilbaig said:**
> I can get Eclipse working now, but not without its issue.

First, for those who can't get Eclipse running. Download the 32-bit version of Europa, and download the latest JRE V6 32bit from sun's site. 

Sun's 32 bit JRE is packaged for Hardy:

[http://packages.ubuntu.com/hardy/ia32-sun-java6-bin](http://packages.ubuntu.com/hardy/ia32-sun-java6-bin)

Hmmm ... apparently if you needed the 32-bit JDK you would have to download it.  Because Eclipse includes its own compiler I'm not sure that the JDK is actually needed.

> 
BUT! the "Find and Install" feature fails for all sites. Its gives an error like 

Dont know what to do about that?!


"premature end of file" I don't think I've heard of so far with Eclipse.  It sounds like a site.xml file might not be downloading properly. (Might not be on the server properly.)  Does it let you change the server to do the update from?

---

### Post by LosButch on 2008-05-08
I have the exact same problem with eclipse. I have used the 32 bit standalone version of Eclipse and 32 bit version of the jvm for quite some time.
Yesterday I upgraded Ubuntu to version 8.04, and now my software updates doesn't work. I get the same error message as adilbaig.
I seem to have trouble with the Subclipse plugin as well, as I cant update any of my projects. I searched around and found some info about a JavaHL adapter, but I cant really make much sense of it, and cant seem to get it installed properly, as I use a standalone version of Eclipse. 
Oh, and SVN works fine from the command line.

Has there been some major, SSL / Java / Something important for Eclipse, update in the latest Ubuntu release?

---

### Post by LosButch on 2008-05-08
BTW, I just remembered that after the upgrade to 8.04, my PSI had no SSL/TLS plugin installed, so I needed the package 'libqca2-plugin-ossl' for it to work. If some standard SSL has been removed / changed in the latest version of Ubuntu, this might has something to do with the problem, as Eclipse update might use SSL as well?

---

### Post by LosButch on 2008-05-09
I give up, I cant get it to work. So now ill have to use the 64 bit version of Eclipse, which seems to work, although it usually crashes a bit too often. But rather that, than not being able to use Subclipse and being able to install plugins.

---

### Post by adilbaig on 2008-05-10
@ftaylor . Problem is, thats Eclipse3.2 . I've tried that and it works like a charm. Except that i want to try using Eclipse3.3 (Europa) with the latest updates for PDT and Descent, and several other plugins.

I may need to revert back to that if things don't improve soon.

@jamesstansell. All update sites don't work. I checked them on my windows version of Eclipse, and they work fine. Its a problem with this install.

Any clues?

---

### Post by ulgor on 2008-06-03
I had the same problems, using 32 Bit Hardy (fresh install), Eclipse 3.3, and Sun_6_JRE to run eclipse / sun_jdk_6 for compiling projects. 

First, eclipse only crashed randomly after some time. After installing subclipse and using it to download some sources, it would not even start, giving me the "error code = 1..." message!

my solution (a little stupid but it seems to work):
I read that its a bug in the new Sun 6 JRE... Now I simply use the sun_jre_5 just to run eclipse, but still the newest version (sun_jdk_6) that I installed earlier to compile projects, run other apps etc.

1. synaptic: just installed the sun-jre-5 
2. "sudo gedit /etc/eclipse/java_home": uncomment the first few entries before sun1.5, like:

#/usr/lib/jvm/java-7-icedtea
#/usr/lib/jvm/java-gcj
#/usr/lib/kaffe/pthreads
#/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-1.5.0-sun
...

3. if I run "java -version" I still get the version 1.6.0_06 as default Java, which is good.

4. Eclipse running quite stable now... (needs more testing)

Does anyone know if this solves the problem permanently?

---

### Post by Kintar1900 on 2008-07-08
For what it's worth, this is almost certainly an issue with the JVM.  I was having this very same problem, and in a fit of frustration, I changed my IntelliJ IDEA install to use the 32-bit 1.6 JVM.  After doing so, IDEA's plugin manager was no longer able to update the plugin list or successfully perform any other network-related tasks.  I'm in the process of trying ulgor's suggestion now.  Thanks, ulgor! :)

---

### Post by ngothean on 2008-12-03
I can't open PHP file 
I use ubuntu 8.04 and follow literally word by word the instruction in [https://help.ubuntu.com/community/PHPEclipse](https://help.ubuntu.com/community/PHPEclipse) 

Thank you

---

### Post by ngothean on 2008-12-04
> **ngothean said:**
> I can't open PHP file 
I use ubuntu 8.04 and follow literally word by word the instruction in [https://help.ubuntu.com/community/PHPEclipse](https://help.ubuntu.com/community/PHPEclipse) 

Thank you
I reinstall Ubuntu and don't install PHPEclipse from repositories. Instead I download JRE directly from Sun (jre 6u11) and Eclipse directly from eclipse (PDT 1.0.3 all in one). The direct download is must faster (not through package manager) and so is the installation. Now it works fine for me

---

