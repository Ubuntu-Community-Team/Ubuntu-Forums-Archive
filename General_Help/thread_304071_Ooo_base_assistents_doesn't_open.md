---
title: "Ooo base assistents doesn't open"
date: 2006-11-21
forum: General Help
---

### Post by mxsteini on 2006-11-21
Hi there,
I'm running edgy with jre1.5 or blackdown java-linux 1.4.
When I'm trying to open an assistent in Ooo-base nothing happens.
The form-assistent and the report assistent doesn't open.


Need any help

Thanks, Michael

---

### Post by gunksta on 2006-11-21
As you clearly understand, Java is necessary for many of the OOBase functions. *Let's make sure you have Java installed*.

Using Synaptic, or the command line, make sure you have the following packages installed.

sun-java-bin
sun-java-jre

*Now let's make sure OOo can find your java installation.*

Open up OOWriter, OOSpread, or whatever and go to 

Tools --> Options

Now, on the left hand side of the dialog box you should see a column with lots of choices in it. "Java" is near the middle of the dialog box under OpenOffice.org. See Below.

OpenOffice.org
    User Data
    General
    Memory
    View
    Print
    Paths
    Colors
    Fonts
    Security
    Appearance
    Acessibility
    **JAVA**

Load/Save
Language Settings
etc.

Click on Java and make sure "Use a Java runtime environment." is checked. My installation of OOo also lists which version(s) of java are installed and recognized by OOo. For the record, I find gcj to be useless and I do not install it on my machines. I like the idea, but it's not ready yet, IMHO. If OOo is trying to use gcj, tell it to use Sun Java. If it hasn't found Sun Java, help it. You will need to ADD a java installation and you will want OOo to look at 

/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre

After that, OOo should be able to do everything you expect it to.

--andy

---

### Post by mxsteini on 2006-11-22
Hi andy,
I have java still running - tryed different versions.
Didn't found sun-java-bin but sun-java5-bin and this version was already installed and activated.
I also tried java-1.5.0-sun-1.5.0.09 the newest sun-version.
Doesn't work.
But I found another Ooo-version at [http://www.prooo-box.org](http://www.prooo-box.org)
This version show the version-nummber 2.0.4-5 instead of 2.0.4-0ubuntu2.
And this works. Seems this is a problem with the ubuntu-version.

Michael

---

### Post by gunksta on 2006-11-22
Oops, sorry for the typo, sun-java5* is what you want.

But did you look to see if OOo recognizes your java installation? If OOo hasn't seen your java installation for some reason, it won't use it.

I would look at the second half of my post, because I don't have any problems at all with OOo.

--andy

---

### Post by mxsteini on 2006-11-23
Hi andy,
I did everything you wrote.
But I would give it a second chance if you would do something for me:
open file-new-database
follow the wizzard and create a new database.
1. Then click on forms and select forms with assistent (maybe wizzard, I have only a german version) it is the second point under tasks.
Do you realy get a wizzard which helps you?

2. Click on reports.
Select report with wizzard. What happens now?

My old OOo worked all day long. This is the only point which is not working.

Michael

---

### Post by mxsteini on 2006-11-25
Hi andy,
thanks for the konversation. But I found my problem in bug-tracker:
[https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/72539](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/72539)

I think you have the same problem.
If not, please help the others.

Michael

---

### Post by gunksta on 2006-11-25
You are 100% correct. I don't normally use the Wizards, and I had not noticed this until today.

Interesting.

Perhaps this is a good time to learn how to make OOo databases by hand?  :mrgreen:


Good Luck! Databases are pretty easy in OpenOffice.org, even without the wizards, but I agree it's an annoying bug.
--andy

---

### Post by guhpraset on 2007-07-22
Arghhh, the same problem with me. So it is a bug!!  I am using Feisty.

I was trying to follow the tutorial [here]("http://sheepdogguides.com/fdb/fdb1simpleform.htm") and i cant load the wizard.

Now i need to look for tutorial that doesnt involve the dead wizard.

---

### Post by mxsteini on 2007-07-30
I'm not shure about the new things about this bug and I don't have the time to check it out again.
One thing worked last time:
Use the newest javathings from sun AND download Ooo direct from openoffice.org.
For german version I know a script that runs very pretty:
[http://www.glasen-hardt.de/index.html](http://www.glasen-hardt.de/index.html)
Maybe you can change it to your language.

---

### Post by Hagar Delest on 2007-08-01
To install the official OOo version, see here : [[Ubuntu] Installing OOo on Debian and Co.](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

---

