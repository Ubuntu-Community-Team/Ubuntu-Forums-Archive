---
title: "Java help needed"
date: 2006-10-18
forum: General Help
---

### Post by fordy on 2006-10-18
I am a refugee from Windows and new to Ubuntu.  I need some help getting started with installing a Java aplication.  I have already downloaded and installed the Sun JRE through Add/Remove applications and believe the installation was successful.

Now, I have a Java application comprising a main jar file and sub directories containing a raft of other jar files and resources.  My questions are these:

[LIST=1]
[*]Where in the file structure should I place the application files for ease of access?
[*]How do I go about running the application - preferably through the GUI?
[/LIST]

Oh BTW, I'm a bit of a Java novice too.:-? 

Many thanks.

---

### Post by _Pete_ on 2006-10-18
> **fordy said:**
> 

[LIST=1]
[*]Where in the file structure should I place the application files for ease of access?

[*]How do I go about running the application - preferably through the GUI?
[/LIST]

Oh BTW, I'm a bit of a Java novice too.:-? 

Many thanks.

1)
I think this is pretty much up to your liking. Personally I have in my home directory code/ subdir which then again have java/ and  C/ and other subdirs for different kind of projects.

2)
Find out how to launch the Java application from then command line. Then do a launcher to your desktop using the same command line. How this is done depends which desktop system you use (Gnome/KDE/someother) .


Hope that help!

---

### Post by fordy on 2006-10-18
Thanks Pete,

I think I have got most of the way there.  In the end I found an rpm file (rather than the binary archive) and converted that to deb using alien and then let it install in the directory of its choice (which was /home)

The launcher it installed didn't seem to do anything so I took the commands in the launcher and entered them through terminal (my GUI BTW is Gnome).  What I got was a bunch of error messages about libraries not being found (though the jar files all seem to be in place).

Now, i am running the commands starting "java ..."  Is there a chance that this is running the java implementation that came with Ubuntu rather than the Sun java that I installed?  Should this matter and if it does how do I ensure that I run the Sun JVM?

Thanks again.

---

### Post by _Pete_ on 2006-10-19
> **fordy said:**
> Thanks Pete,

I think I have got most of the way there.  In the end I found an rpm file (rather than the binary archive) and converted that to deb using alien and then let it install in the directory of its choice (which was /home)

The launcher it installed didn't seem to do anything so I took the commands in the launcher and entered them through terminal (my GUI BTW is Gnome).  What I got was a bunch of error messages about libraries not being found (though the jar files all seem to be in place).

Now, i am running the commands starting "java ..."  Is there a chance that this is running the java implementation that came with Ubuntu rather than the Sun java that I installed?  Should this matter and if it does how do I ensure that I run the Sun JVM?

Thanks again.

Yes indeed it is possible that the default java points to gcc java which is the default after installation. Install Sun's java:

sudo apt-get install sun-java5-jre

after that configure java to point this one:

sudo update-alternatives --config java

on the list select the one pointing to Sun's java...

sun-java5-jre package is on multiverse repo so that must be in your /etc/apt/sources.list

---

### Post by ATAQ on 2006-10-19
I have mine located in /usr/share/java because One or two programs that I ran requested the files from there, so I think that may be the best possible place for you to install the files to, t ensure that it works.

Regards,
Ant,
Eire

---

### Post by _Pete_ on 2006-10-19
> **ATAQ said:**
> I have mine located in /usr/share/java because One or two programs that I ran requested the files from there, so I think that may be the best possible place for you to install the files to, t ensure that it works.




Best place is to install where package automatically installs files. If there are some odd programs which expects the java program found some certain place then do symlinks for them.

---

### Post by fordy on 2006-10-20
> **_Pete_ said:**
> Yes indeed it is possible that the default java points to gcc java which is the default after installation. Install Sun's java:

sudo apt-get install sun-java5-jre

after that configure java to point this one:

sudo update-alternatives --config java

on the list select the one pointing to Sun's java...

sun-java5-jre package is on multiverse repo so that must be in your /etc/apt/sources.list

Thanks for that Pete.  I already had Sun's Java installed so all I needed to do was set it as the default.  Now the Java app works correctly - which also solves another question I had on the forum about a Ubuntu compatible desktop content management package - that's what the Java app was.  So, double thanks.:D

---

