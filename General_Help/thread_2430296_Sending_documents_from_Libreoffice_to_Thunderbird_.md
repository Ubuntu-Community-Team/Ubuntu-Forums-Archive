---
title: "Sending documents from Libreoffice to Thunderbird pop3 (ubuntu 18.04)"
date: 2019-10-30
forum: General Help
---

### Post by Robbyx on 2019-10-30
I have reinstalled Thunderbird, which I use via pop3 mail.

I can not get documents in LibreOffice to be sent to Thunderbird. Does any one know why? It has been suggested that the sending into thunderbird needs SimpleMapi, that is not supported by Ubuntu. Is this the real reason?

Within Ubuntu and Libreoffice the default email program is set as Thunderbird.

---

### Post by uRock on 2019-10-30
Is your Thunderbird installed as a Snap or from deb? I see both listed in Software. **Thunderbird Mail** is from deb and **Thunderbird** is Snap. Snaps have issues integrating with other apps.

---

### Post by SeijiSensei on 2019-10-30
If I choose File > Send > Email Document in LibreOffice, it opens my Thunderbird email composer with the document included as an attachment.

---

### Post by uRock on 2019-10-30
> **SeijiSensei said:**
> If I choose File > Send > Email Document in LibreOffice, it opens my Thunderbird email composer with the document included as an attachment.

[s]I am going to jump on my 19.10 machine and see if it works like this with the Snap.[/s]
Never mind, Gmail refuses to even authenticate the snap. This method is working properly for the deb.

---

### Post by Robbyx on 2019-10-30
I think the best way to understand why I can not send docs from Libreoffice to TB would be to check the log files. Which ones should I look at?

---

### Post by Skaperen on 2019-10-30
i think that snap applications are looking for other applications to also be snaps.  the simple solution is to have LibreOffice save the document on disk as a file in your Documents folder or somewhere else of your choosing then have Thunderbird browse that folder and attach that one when you see it in there.

---

### Post by Skaperen on 2019-10-30
> **Robbyx said:**
> I think the best way to understand why I can not send docs from Libreoffice to TB would be to check the log files. Which ones should I look at?

these kind of applications generally do not produce log file output.

---

### Post by Robbyx on 2019-10-30
I have been saving the file to disk and then adding it to an email address. It is a bit chunky as a method and I would have liked to use the send method instead.

I can not use snap because I use xanmod's kernel.

---

### Post by Skaperen on 2019-10-30
is this expected to be a means in LibreOffice to "mail this document" and it would launch the mail client with the document already attached, ready for you to enter the to:, cc:, and bcc: email addresses and either send now or edit a message?

---

### Post by uRock on 2019-10-30
> **Skaperen said:**
> is this expected to be a means in LibreOffice to "mail this document" and it would launch the mail client with the document already attached, ready for you to enter the to:, cc:, and bcc: email addresses and either send now or edit a message?

It should open the typical window for creating an email, with the document attached.

---

### Post by Robbyx on 2019-10-31
In my case using send as email  does not do anything in TB: no new message and therefore no attachment. That is why I thought I might pick up an error in the logs.

---

### Post by SeijiSensei on 2019-11-01
Have you specified Thunderbird as the default mail program in the operating system? Take a look in System Settings.

---

### Post by Robbyx on 2019-11-01
yes it is the default

---

### Post by uRock on 2019-11-01
Robbyx, try launching libreoffice via terminal and going through the process. We may get a workable error out of it.

---

### Post by ajgreeny on 2019-11-01
What happens if you right click the doc in file manager? Do you then get an option to send by email in any way? 

I'm not on my Xubuntu system at the moment but I seem to remember that is an option in my system, though it may simply be my memory that's playing tricks on me.

---

### Post by Robbyx on 2019-11-01
> **uRock said:**
> Robbyx, try launching libreoffice via terminal and going through the process. We may get a workable error out of it.

```
und
robins@robins-desktop:~$ libreoffice
Failed to open display
javaldx: Could not find a Java Runtime Environment!
Please ensure that a JVM and the package libreoffice-java-common
is installed.
If it is already installed then try removing ~/.libreoffice/3/user/config/javasettings_Linux_*.xml
Warning: failed to read path from javaldx
Unable to init server: Could not connect: Connection refused
/usr/lib/libreoffice/program/soffice.bin X11 error: Can't open display: 
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)
robins@robins-desktop:~$ 



```


I have searched in Synaptic  and note of options for Java Runtime Environment are installed. Which version should I choose?

Geany

libraoffice: meta package but I have LO installed
> This is taken from the about in my installed version:
Version: 6.0.7.3
Build ID: 1:6.0.7-0ubuntu0.18.04.10
CPU threads: 4; OS: Linux 5.3; UI render: default; VCL: gtk3; 
Locale: en-GB (en_GB.UTF-8); Calc: group



OpenJDK Java runtime, using Hotspot JIT

IBM Java(TM) Runtime Environment (JRE) 8.0

---

### Post by Robbyx on 2019-11-01
> **ajgreeny said:**
> What happens if you right click the doc in file manager? Do you then get an option to send by email in any way? 

I'm not on my Xubuntu system at the moment but I seem to remember that is an option in my system, though it may simply be my memory that's playing tricks on me.

Yes there is the option and it does open TB and show an email with the file attached. I used pcmanfm to do it.

---

### Post by ajgreeny on 2019-11-03
You also may need to go into the ***Libreoffice ->Tools ->Options ->Libreoffice ->Advanced*** and make sure that your version of java is enabled; just having it installed on the system may not be sufficient for Libreoffice to use the send-mail system.

---

### Post by Robbyx on 2019-11-03
I now have the JRE installed but still the send does not work. 

> java -version
openjdk version "11.0.4" 2019-07-16
OpenJDK Runtime Environment (build 11.0.4+11-post-Ubuntu-1ubuntu218.04.3)
OpenJDK 64-Bit Server VM (build 11.0.4+11-post-Ubuntu-1ubuntu218.04.3, mixed mode, sharing)


Please suggest how to repair this latest error on terminal startup

> robins@robins-desktop:~$ libreoffice
Failed to open display
Unable to init server: Could not connect: Connection refused
/usr/lib/libreoffice/program/soffice.bin X11 error: Can't open display: 
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)


---

### Post by ajgreeny on 2019-11-04
Having now looked at my Libreoffice settings I wonder if your problem is related to java as it is disabled in my LO settings but I can send mail from the LO File menu without a problem.

I'm not sure where to look further but will see what else I can find.

---

### Post by Robbyx on 2019-11-07
As I still can not send a file directly from Libreoffice to Thunderbird this is the current state of play:

> libreoffice
Failed to open display
Unable to init server: Could not connect: Connection refused
/usr/lib/libreoffice/program/soffice.bin X11 error: Can't open display: 
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)
 

> robins@robins-desktop:~$ libreoffice --display
Failed to open display

(soffice:31790): Gtk-WARNING **: 22:49:07.874: Missing argument for --display
Unable to init server: Could not connect: Connection refused
/usr/lib/libreoffice/program/soffice.bin X11 error: Can't open display: --display
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)


What should I do next? This all has arisen since a clean install. Previously I could send files to email. I think I have missed out an app  that should be installed, but I do not know which. 
I only reinstalled the system partition. The home partition is as it was.

---

