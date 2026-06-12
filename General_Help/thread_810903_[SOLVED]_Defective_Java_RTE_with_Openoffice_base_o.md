---
title: "[SOLVED] Defective Java RTE with Openoffice base on 8.04"
date: 2008-05-28
forum: General Help
---

### Post by panorack on 2008-05-28
After installing openoffice base I get the following error message when trying to open an existing database:

*'The selected JRE is defective.Please select another version or install a new version and select it under Tools - Options - Openoffice - Java.  Please install the openoffice.org-java-common package for this functionality.'*

The next error dialoge box tells me that 'No Java Installation could be found.' A check with Synaptic shows that openoffice.org-java-common is installed. I have tried a complete removal and reinstallation with no effect.

I'm at a loss to know what to try next. Any ideas anyone??

Panorack

---

### Post by SyL on 2008-05-31
Not really sure but i guess that openoffice.org-java-common is using a JRE. 

So check if you have one installed, and which version is it. If you have different version use update-java-alternatives for the select the one OOo needs.

---

### Post by roida on 2008-06-05
How can i check if there is a JRE installed?

---

### Post by SyL on 2008-06-05
> **roida said:**
> How can i check if there is a JRE installed?



Try some Java related commands on a terminal.
Like java, javac and you will see if you have any JRE installed.

---

### Post by SyL on 2008-06-05
You could also use the command **update-java-alternatives** the see which version are installed and choose the one you want to use.

---

### Post by panorack on 2008-06-05
Thanks for the help SyL. I assumed that the openoffice.org-java-common package would have included the JRE but apparently not. 

However, I downloaded java-6-sun from their site and it installed ok but I am still getting the same error messages from Openoffice-base. The JRE is installed and Openoffice is pointing to the directory where it is installed, so is this a bug or am I missing something????:confused:

panorack

---

### Post by SyL on 2008-06-06
You are welcome :)
But i'm not sure i'll be of a great help, for this problem.

From your answer i understand that when you go into Tools - Options - Openoffice - Java
you can see the sun JRE1.6 that you installed and this JRE is selected, correct?

Are you still getting the error "No Java Installation could be found"?

---

### Post by panorack on 2008-06-06
Yes, I installed JRE1.6.0_06 and that is the one that is showing in Tools-Options-Java. It even shows the location of that file, which is correct. 1.6 is the correct version of JRE for Ubuntu 8.04 so I am assuming it is correct for OOo-Base, which is version 2.4. 

Very frustrating as it worked perfectly under Ubuntu 7.10. I really don't know what to try next.

panorack

---

### Post by SyL on 2008-06-10
Are you still getting the error "No Java Installation could be found"?     

Do you get the same error with another DB?

Could you try to load this DB within a 7.10 live CD, and see if this DB file could be corrupted?



it just some hints, sorry that i cannot help more efficiently.

---

### Post by panorack on 2008-06-12
Thanks for your time and help SyL but I have found that there is a problem with OO.o-Base detecting Java when running under Ubuntu 8.04. I looked on the OpenOffice forum site and found the following solution:

Close OOo then delete the file ~/.openoffice.org2/user/config/javasettings_Linux_x86.xml file.

Details of the thread where I found the above can be found at:

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=5463&sid=2aaa85f198394bd5fc834cf1c80d218a](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=5463&sid=2aaa85f198394bd5fc834cf1c80d218a)

---

### Post by SyL on 2008-06-12
Hi Panorack,

good to know you could get it work properly!
and thanks for the details :-)

---

