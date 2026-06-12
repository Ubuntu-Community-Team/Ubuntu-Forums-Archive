---
title: "Java app problem"
date: 2013-03-13
forum: General Help
---

### Post by cscj01 on 2013-03-13
I am running Ubuntu 12.04 x64 and Oracle Java 1.7.0_04.  I recently upgraded a Java application that does something odd.  This app has Help in the Menu Bar, and there are two choices under Help that are supposed to show a particular file path: one being an archive path and the other a documents path.  Trouble is, when I chose Help>Show Archive Folder or Help>Show Documents Folder, it launches Easytag, an audio file tagging application.  If I remove (uninstall) Easytag, the Java app presents an Information window with the correct path in either case.  When Easytag is installed, the Java app launches Easytag, and the Directory Tree window in Easytag is positioned at the location that should be shown in the Information window, not in Easytag.

I have been in communication with the developers of the Java app, and, to date, they have not offered any reason for this behavior.  I have tried to use the Java Console to determine what is happening, but I do not know Java, and I don't seem to be getting anywhere.  I used the Java Control Panel to set tracing and logging on, but there doesn't seem to be much useful information in the only file I could find with trace information in ~/.java/deployment/log.  I have started the Java app from a terminal to try to get information in the terminal, but that does not give any information when I chose one of the two options mentiuoned above.  The Java app has an option Help>Console Window, but that also gives no information about the particular selections mentioned above.  Does anyone know of any method to isolate what this Java app is doing when it launches Easytag?

---

### Post by cscj01 on 2013-03-19
bump

---

### Post by cscj01 on 2013-04-02
bump

---

