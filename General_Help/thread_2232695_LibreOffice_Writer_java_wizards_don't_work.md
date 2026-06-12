---
title: "LibreOffice Writer java wizards don't work"
date: 2014-07-03
forum: General Help
---

### Post by Tom_ZeCat on 2014-07-03
I can't seem to get all the wizards working in LibreOffice writer.  The ones that don't work are Letter, Fax, and Agenda.  All the other ones do work.  I searched the web and found this post on the topic: 

[http://ubuntuforums.org/showthread.php?t=1778814]("http://ubuntuforums.org/showthread.php?t=1778814")

In that thread, they advocate installing libreoffice-java-common with this command: 

```
sudo aptitude install libreoffice-java-common
```

I tried that and got a message that something was wrong, the process was interrupted, and that I needed to do this: 

```
sudo dpkg --configure -a
```

Instead, I went into Synaptic Package Manager, and it burped.  It told me the same thing.  So I ran: sudo dpkg --configure -a.  It fixed Synaptic Package Manager so that I could open it and look to see if I had libreoffice-java-common installed or not.  Turns out I do.  There it was right on the Synaptic list near LibreOffice.  I figured I would mark it for a complete uninstall.  However, when I tried that, it also marked LibreOffice for a complete uninstall.  I didn't want that, so i cancelled. 

Back in the terminal, I went ahead and ran: 

```
sudo aptitude install libreoffice-java-common
```

This time it ran fine.  However, the wizards STILL won't run in LO Writer.  In Writer, I went to Tools ==> Options ==> Advanced and verified that “Use a Java runtime environment” was checked.  There were two choices, Sun Microsystems and Oracle, and Sun was the one chosen.  I switched to Oracle to see if that would make a difference.  The wizards still would not work.  Finally, in  Tools ==> Options ==> Advanced I selected “Enable experimental features” to see if that would help.  Still no luck.  

I've done everything I know to do.  I've looked in old posts.  Why aren't these wizards working and how can I make them work?

---

