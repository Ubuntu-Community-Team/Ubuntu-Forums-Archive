---
title: "howto install sun java 5/6/beta &amp; eclipse manually replacing gcj (gnu java)"
date: 2006-11-11
forum: General Help
---

### Post by zadax on 2006-11-11
Ok, I searched these forums and everywhere else but couldn't find a difinitive solution to installing Sun's Java - manually.  I found bunches of pieces here and there, but all that I found had an issue or two.  Yes, I know how to enable it in the synaptic package manager but here is the thing...as a Java developer, I can't use the 1.5.0_06 version that Ubuntu supplies due to a nasty bug with that version.  Also, I need eclipse 3.2.1 not 3.1.2 - WAY too old of a version - and I hate that Ant/Xerces target bug.  And I want all of my stuff to use Sun's Java because the GNU Java is not fully developed and many apps have features that won't run with it. 

So, here is how I found to fix these issues.  Also, by following the concept, you should be able to do things like download and unzip Mozilla/SeaMonkey, etc. and not have to worry about having a debian package just to get teh 'alternative' stuff to work.

As the following works, I would appreciate any feedback from people that know Ubuntu better (I understand other Linux distros better, so this alternatives, multiple jvm's and gcj stuff is new to me).  I am used to running sun's .bin file, changing some links and being done with it, but whatever.

Wherever 'java-sun' exists you can name it to anything of your choice (e.g. i also have one called java-beta for my 1.6 beta version).

1.  upack sun jdk (e.g. /opt/jdk1.5.0_09) - from the sun site
2.  ln -s /opt/jdk1.5.0_09 /usr/lib/jvm/java-sun 
3.  edit /etc/jvm
4.  add "/usr/lib/jvm/java-sun" as first line
5.  cp /usr/lib/jvm/.java-gcj-jinfo /usr/lib/jvm/.java-sun-jinfo 
6.  edit .java-sun.jinfo so that all java-gcj are now java-sun
7.  install galternatives
8.  ln -s /usr/lib/jvm/java-sun/ /etc/alternatives/java-sun
9.  run galternatives
10. select javac from the index
11. click 'add'
12. set path to /etc/alternatives/java-sun/bin/javac
13. set priority to 301 (or the just one higher than the gcj priority)
14. repeat steps 10 through 13 for all the java items below, setting the priority just one higher than the highest priority in the galternative list
	- javac (301)
	- java (1000)
	- jar (1000)
	- javadoc (351)
	- javah (301)
	- javap (301)
	- rmiregistry (1000)
	- rmic (301)
	- serialver (301)
	- native2ascii (301)
15. (because galternatives maxes out at 1000 for priority) for each of the above that you set a priority of 1000, edit each of their files under /var/lib/dpkg/alternatives/ (e.g. /var/lib/dpkg/alternatives/jar) and change the 1000 to 1042 (or one higher than the highest value)
	- /var/lib/dpkg/alternatives/java
	- /var/lib/dpkg/alternatives/jar
	- /var/lib/dpkg/alternatives/rmiregistry
---

to update java, merely unpack the new sun's java into /opt (or wherever) and change the link /usr/lib/jvm/java-sun to point to the new /opt/[sun java] version

to revert back to gnu java, run galternatives and select the original options
(you could also run 'update-alternatives --all' and change it that way)

---

for java developers that want to run eclipse with sun java's version...

using the aforementioned method all you will have to do is unpack the eclipse from eclipse.org and run it. It will automatically pickup and use whatever option you have set in galternatives.

---

notes:
I chose galternatives over the command line because the command line kept throwing an error that it could not find /usr/lib/jvm/java-sun/bin/java et al.  Updon checking logs, this appears to be caused by a lack of a .deb package install or something.  
	
HTH!

Please feel free to critisize or comment on feedback (spelling and grammar excluded -because i don't care about those when posting to forums), because if something I did is just plain 'bad' I would like to know so that I can learn from the mistake. Thanks.

As far as I can tell this fixes all java programs to use sun's java.  Now to see if i can remove the gcj all together without breaking Ubuntu, as gcj is slow and incomplete...

---

### Post by jhickey on 2006-11-27
I found this easier.  Not sure if it is 100% right but it changes the main Java used by the system.

Download the jdk-1_5_0_09-linux-i586.bin move it to /opt and run it

sudo ./jdk-1_5_0_09-linux-i586.bin
  hit space a few time and type yes

update-alternatives --install /usr/bin/java java /opt/jdk1.5.0_09/bin/java 500

Finally run:
update-alternatives --set java /opt/jdk1.5.0_09/bin/java
  OR
update-alternatives --config java

the --set option will not prompt you while the --config option will present you with a list of option.

Rinse and Repeat for all the other java tools you need (javac, jar, javadoc and so on)

---

### Post by 0815user on 2006-11-27
Well, to do it the real debian way, you could also try:

"make-jpkg java_bla.bin".

That shoudl give you handy .debs you can install easily via dpkg.

---

### Post by spayced on 2007-01-25
the update-alternatives command was giving errors for unknown arguments but galternatives was gold, thanks much for the fix. :D
I don't know why the original JRE was even in there it was so useless ;/

---

### Post by joeloh on 2007-11-06
While trying to follow Sun Micro Java Installation guide, each time I type in SU at the terminal I am prompt to enter password, But when I type in my password the cursor don't seem to more. and when I press the enter key the request for password keep coming up.  I cannot go beyond this point. Pleas help, I completely new to Ubuntu and Linux.  Regards and mand thanks

---

