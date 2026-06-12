---
title: "Aptana on 8.04 problem"
date: 2008-05-08
forum: General Help
---

### Post by somethingkindawierd on 2008-05-08
I just downloaded Aptana Studio 1.1 and tried to start it on Ubunbu 8.04.  I get an error message as seen in the attached screen shot.  The JVM exits with error code of 1.

Any ideas?  Thanks!

---

### Post by bilbo.san on 2008-05-08
Hey,
Well... I have not installed it yet. But I think that you should not install Aptana directly onto Ubuntu.
You see... the problem is that Aptana is not based on GNOME... So to make it work, you have to install it as a 'plug-in' on Eclipse.
I would suggest you to go to Add/Remove programs... look for Eclipse and install it.
Then, you can add the plug-in on Eclipse.

Now, I am not sure, I am still searching for info... but I think that you have to install the JAVA RUNTIME before installing Eclipse.

in the Terminal:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

Let me know if it works for you!!!
Good luck

b.

---

### Post by somethingkindawierd on 2008-05-09
I have Aptana Studio running on Ubuntu 8.04 on my 24" iMac.  All I did was download it, unzip it to the Desktop, and click on the Application.  On my laptop that is not the case.  I get a Java error.  I much prefer Aptana to Eclipse and I want to stay away from the Eclipse plugin if I can.

---

### Post by bilbo.san on 2008-05-09
OK... So you had success on running Aptana on your Desktop?... 
I suppose that it just requires the Java Scripts (JRE & JDK) installed on the Ubuntu before installing Aptana.
Have you installed those in your laptop yet?

I understand that there are plans for a .deb version in the near future... I hope!.

Meanwhile, I guess I will stick with Kompozer and Blueflish Editors... but unfortunately, they do not work the PHP verywell.

b.

---

### Post by somethingkindawierd on 2008-05-12
Yes.  On the desktop I installed Aptana and it just worked.  On my laptop, which I experiment with more, I installed a java app that installed/tweaked java in some way when installed.  I think it broke something.  I used the synaptic package manager to uninstall all java packages and reinstall them back to what I thought was default (including JRE and JDK), but that did not work either - I still get the same EXIT 1 error.  All other java apps work on my system.  So I am just wondering where to begin looking to debug this problem.

---

### Post by ceaseoleo on 2008-07-14
> **somethingkindawierd said:**
> I just downloaded Aptana Studio 1.1 and tried to start it on Ubunbu 8.04.  I get an error message as seen in the attached screen shot.  The JVM exits with error code of 1.

Any ideas?  Thanks!


I'm getting this same issue, I tried to increase memory, and no luck.. any other ideas.. did you ever get this fixed ?

---

### Post by somethingkindawierd on 2008-07-16
I reinstalled Ubuntu and everything works now. 

The original problem began when I tried to install some other app that messed with my Java engine. I never figured out what it did.

I know this is not an ideal solution, but Aptana works splendidly now :)

---

