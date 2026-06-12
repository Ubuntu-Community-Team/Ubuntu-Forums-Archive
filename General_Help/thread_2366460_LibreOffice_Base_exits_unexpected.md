---
title: "LibreOffice Base exits unexpected"
date: 2017-07-18
forum: General Help
---

### Post by lumaja2 on 2017-07-18
Ubuntu 16.04 LTS
 LibreOffice Base 5.1.6.2
 Start  LibreOffice Base *Create new Database > Finish *page opens to save the file name Click on Save and  LibreOffice Base shuts down.
 Restart Base screen opens with *LibreOffice document recovery *and there with file name written on  
 LO Writer that was open.
 Uninstall Base, restart Ubuntu  then install Base again go through same process it still does the same.
  Can some one help to Correct this.
  Thank you

---

### Post by unityforever on 2017-07-18
hi
i don't know how to solve this problem, but i would like to recommend you to use another software.

im an ordinary user and a reliable office application is essential to keep my efficiency even my job
(one day i almost lose my job because Liberoffice, the pptx it created cannot be read by MicrosoftOffice which is installed on conference room
don't mentioned while its saving pptx, it will drop many elements, and liber will crashed so often.)

there is an office application called WPS ,it is made by chinese, and is good.
im not their advertiser, im just really like this software.
it can show Microsoft pptx completely and nicely including animation and effects.
it can recover the important files which is damaged on your remote disk.
when it is saving the pptx, almost everything can be saved, if something has to be drop, it will tell you which staffs will be lost.

and its free

---

### Post by lumaja2 on 2017-07-19
WPS doesn&#8217;t have Data base application.
  
 
  I still need LO Base to be fixed can anyone help please.

---

### Post by amanchesterman on 2017-07-20
I too have 16.04, but my version of LO is 5.3.4.2 -- I have the PPA enabled and it updates automatically. So as a first step you may want to update yours to the latest version.

I've gone through the steps you describe and have no problem, it all works fine in my installation -- which is no help to you, I know, except that it tells us the software is OK.

LibreOffice advice is 'When noticing strange behavior in LibreOffice the first thing to do is to reset the user profile.' That's from
[https://wiki.documentfoundation.org/UserProfile](https://wiki.documentfoundation.org/UserProfile)
where you'll find instructions on how to do it.

That's all the help I can offer, I'm afraid: reset your profile and/or update LO. I hope you get it sorted!

---

### Post by lumaja2 on 2017-07-20
My version of LO is 5.1.6.2 it was working correctly until an update, I only have a problem on LO Base Not with Calc or Writer. I Follow the advice to reset the user profile but it dint work LO Base still the same. Should I update to ver. 5.3.4.2?   If Yes how I  do this update Please explain. Thank you

---

### Post by speartip on 2017-07-20
Before you update and start adding ppas, I would first off delete the user profile in your Home folder.
Its in your Home/.config folder. You will see the Libreoffice folder. With LO closed delete it, and see if the crash still persists.

---

### Post by lumaja2 on 2017-07-21
I Follow your advice to delete the profile but still the same.

---

### Post by speartip on 2017-07-21
OK. Well in that case you may want to install the latest version via the ppa. In a terminal run the following commands, one at a time:
```
[COLOR=#333333]sudo add-apt-repository ppa:libreoffice/libreoffice-5-3[/COLOR]
```
```
sudo apt update && sudo apt upgrade
```
You may be best deleting your LO profile again before upgrading.
See how you go.

---

### Post by lumaja2 on 2017-07-21
I install the latest version of LO following your advice, start LO Base Create a New Database and Save on Saving still crashes, other time on saving an window opens with “LibreOffice 5.3 Document Recovery” Title with a note “LibreOffice Base exits unexpected”, Click Start Recovery > Finish, and LO Base crashes. Is this a bug with Ubuntu?

---

### Post by alaric-cundy on 2017-07-25
I have reported the same problem in another thread.  I am using 32-bit Ubuntu 16.04 LTS.  In fact, my problem is even worse in that Writer also crashes, though Calc, Draw, and Impress all work OK.  I have a work-around in that if I reboot my system in an older version of the Linux kernel -  4.4.0-79, or older - everything works fine.  I am perhaps lucky in that I use Grub on boot-up, hence I am able to choose 'Ubuntu - Advanced Options', and then 'Linux 4.4.0-79' and then everything works fine.  It is an awful nuisance having to do this though.  I have tried the ideas in this thread, to no avail.  The problem definitely started with the update from 4.4.0-79 to 4.4.0-81, and subsequent updates to -83, -85, and -87 have not solved the problem.  I am running - or, at least, trying to run - version 5.3.4.2 of LibreOffice.

Does anyone have any other ideas - _***please!***_

---

### Post by alaric-cundy on 2017-07-26
I have found that if I switch off Java, as suggested above, then I can actually open a LibreOffice Base document, I can look at lists of queries, reports, forms, but as soon as I either try to look at the list of tables or try to execute a query I get this error message:

[I][COLOR=#0000ff]The connection to the data source "Accounts" could not be established.

The connection to the external data source could not be established. No SDBC driver was found for the URL 'sdbc:embedded:hsqldb'.[/COLOR]

[/I]However, bizarrely, the sample database called biblio.odb will open happily.  Is anyone able to help, given this extra bit of information, please?  What is an SDBC driver?

With Java switched off, I am at least able to open Documents (odt, doc, or docx) in Writer. If  re-enable Java, then any attempt to open any document using LibreOffice Writer causes all active components of LO to crash out, without giving any error messages at all.

---

### Post by lumaja2 on 2017-07-27
Ubuntu 16.04 LTS 32 bit
 Thak you to give some explanation on this.
 I download and install LO ver. Ver. 5.3.4.2 and has the same problem (Witer and Base crashes.
 Calc, Draw and Impress work).
 Very disapointed with Ubuntu on this one never expected to come to this and not get fixed  
 for more that two weeks.
 My big problem is am working with an DataBase project I use Writer every day.
 I will try to boot with Linux kernel  4.4.0-79 please explain I to get into Grub and what should
 I do if dont have this Grub version.
 Thank you

---

### Post by alaric-cundy on 2017-08-18
[FONT=Arial, sans-serif]I have been tearing my hair out with this issue ever since I first posted it. I have followed various suggestions I have found elsewhere on the forums and in the LibreOffice forums, but to no avail. If, via the Grub menu, I boot under kernel version 4.4.0.79 or older everything is absolutely fine, but under any more recent version it crashes out as soon as I attempt to access the list of tables. Help! Surely someone out there can help? Please!!!!!!!!! What happened with 4.4.0.81 that caused Base to go wrong?

**POST-SCRIPT:** I have found something that might help someone to help those of us who are suffering from this problem. And, by the way, in different threads and in different forums, I have found loads of people experiencing the same effect. I found two copies of a system database called biblio.odb. 

The one located at usr/lib/libreoffice/presets/database is shown as owner 'root'; I can happily open that document and I can access the single table that it contains, though I can't make any changes to the table because I am not the owner. 

There is also a copy at home/username/.config/libreoffice/4/user/database. 'Properties' then 'Permissions' shows that I am the owner of that copy; that version crashes as soon as I try to access the list of tables - just as is the case with my own databases. 

However, if I copy the root-owned version to, say, Documents, the ownership of the copy changes to 'Me', but I find that if I open this copy, not only can I access the table, I also have full read / write access so I can add new tables and update the existing one - i.e., it behaves perfectly.

Do these observations throw any light on the matter? [/FONT] 
 
 
 **[FONT=Arial, sans-serif]A POST-SCRIPT to the POST-SCRIPT[/FONT]**

 
 
 [FONT=Arial, sans-serif]Further to my previous update: the biblio database - that is the one that works fine - is a dbase file; all of those that crash are HSQLDB embedded files. [/FONT]

---

### Post by alaric-cundy on 2017-08-19
I think I have an explanation for these woes, but not a solution.

HSQLDB format databases as created by LibreOffice depend on Oracle Java.  I found this comment on another Forum: "**Oracle  Java (JVM/JDK) will not be available in the Debian / Ubuntu   repositories anymore because Oracle retired the "Operating System   Distributor License for Java" (JDL) and the only release available in   the repositories will be OpenJDK**."  My system update logs show  multiple recent failures of the installation of Java.  So we need to  remove Oracle Java and use OpenJDK instead, but I can't anywhere find  out how to do that.

---

### Post by speartip on 2017-08-19
There are 2 threads running on this issue, and as far as I can see the problem only seems to be related to the 4.4.xxx kernel.
Has anyone tried installing the latest 4.10.xxx kernel that's in the repos, to see if this problem still persists?

Alternatively if someone could upload a non-confidential file that crashes, then others could maybe try it on their system to see what happens and give feedback.

---

### Post by alaric-cundy on 2017-08-21
Thank you, Speartip.

I upgraded my test PC to kernel 4.10... manually, as (presumably) that kernel version only normally arrives with later versions of Ubuntu (later than 16.04.LTS).  Everything works fine.....  Just to be clear - that is it works under Ubuntu 16.04.3 with Kernel 4.10.1.  So it seems that Base works happily on Kernel version 4.4.79 or anything older than that, but not on any version from 4.4.81 through to 4.4.92.  But then it does work on kernels 4.10 onwards.  I'm not sure how safe it is to run 16.04 / 4.10 on a live 'production' computer, so presumably best advice would be to upgrade from 16.04 to 17.04 (and soon to 17.10) whilst awaiting the release of 18.04?

---

### Post by speartip on 2017-08-21
@alaric-cundy.
The 4.10 kernel is in the 16.04 repos, and is default in the 16.04.3 isos. It is perfectly safe to use on production machines.
It's not necessary to upgrade to 17.04 or 17.10. Stick to 16.04 for stability and support.

---

### Post by alaric-cundy on 2017-08-22
Thank you again, Speartip.  I have some further insight:

My main 'live' computer currently runs 16.04.03 LTS, LO version 5.4.0.3, kernel 4.4.0-92-generic.  As described previously, under this configuration LO Base does not function.

Development computer 1 runs 16.4.3 LTS, LO 5.4.0.3, kernel 4.10.1-041991-generic.  As described previously, under this configuration, LO Base runs perfectly.

I have upgraded development computer 2 to 17.04 with LO 5.4.0.1, kernel 4.10.0-32 generic.  Under this configuration, LO Base does not work.  I'm not sure which difference between development computers 1 and 2 is causing the different performance for LibreOffice Base, but I intend to follow speartip's advice NOT to upgrade any other computers to 17.04!.

---

