---
title: "Problem With Crash Plan"
date: 2014-03-08
forum: General Help
---

### Post by Jacob_M on 2014-03-08
Installed Crashplan using instructions from this link;

[http://support.code42.com/CrashPlan/Latest/Getting_Started/Installing_CrashPlan](http://support.code42.com/CrashPlan/Latest/Getting_Started/Installing_CrashPlan)

Everything went fine but now I have no idea how to launch the GUI. 

Any suggestions?

I have a file called 'crashplan' on my desktop now but when i launch it it says "there was an error launching the application details: failed to execute process Details: Failed to execute child process "yes/bin/CrashPlanDesktop" (No such file or directory)

---

### Post by Jacob_M on 2014-03-08
Shouldn't Crashplan just put their software in the Ubuntu software center?

---

### Post by bluefrog on 2014-03-08
"yes/bin/CrashPlanDesktop" doesn't look like a valid path for the executable file.

you should reinstall the software or at least correct the path. right click on the desktop icon, properties and correct the path

---

### Post by fbugnon on 2014-06-06
You might want to try the solution on [this]("http://ubuntuforums.org/showthread.php?t=2199698&p=13043124#post13043124") post, regarding editing the run.conf located on /usr/local/crashplan/bin/ as per the [solution]("http://support.code42.com/CrashPlan/Latest/Troubleshooting/CrashPlan_Client_Closes_In_Some_Linux_Installations") provided by the software developer.

---

