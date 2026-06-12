---
title: "The greater application appears to be crashing. Attempting to use another one."
date: 2008-05-25
forum: General Help
---

### Post by newagelink on 2008-05-25
[COLOR="Indigo"]Recently, I've been letting my laptop idle itself to sleep, to let KTorrent seed more. Trying to start it back up the next morning, I get a black screen with some USB errors -- with small resolution, as if it's some DOS prompt thing -- and the computer turns off. I press the power button again and it starts up, but I receive an error message a millimeter in height (and barely legible.) Copied [from another thread]("http://ubuntuforums.org/showthread.php?t=138350"), it appears to be:[/COLOR] > The greater application appears to be crashing. Attempting to use another one. [COLOR="Indigo"]That thread was for 6.06, and I'm using 7.10. I tried [his recommended solution]("http://ubuntuforums.org/showpost.php?p=783585&postcount=11"), but received the following error messages:[/COLOR] > daniel@daniel-laptop:~$ wget [http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.13-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.13-1ubuntu1_i386.deb)
--07:47:55--  [http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.13-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.13-1ubuntu1_i386.deb)
           => `libgtk2.0-0_2.8.13-1ubuntu1_i386.deb'
Resolving archive.ubuntu.com... 91.189.88.46, 91.189.88.31, 91.189.88.45
Connecting to archive.ubuntu.com|91.189.88.46|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
07:47:55 ERROR 404: Not Found.

daniel@daniel-laptop:~$ dpkg -i libgtk2.0-0_2.8.13-1ubuntu1_i386.deb
dpkg: requested operation requires superuser privilege [COLOR="Indigo"]The second command was basically to see if anything would happen; it seemed clear that the file wasn't found. I held down the power button until it forcefully shut itself off -- what does that do? -- and it started (third time now) without a problem.

Thanks for reading. Any thoughts?[/COLOR]

---

### Post by dasunst3r on 2008-05-25
Firstly, on the *dpkg -i* command you issued, you forgot to tack on *sudo* to execute the command as root.  Package installations require root privileges.  Secondly, since libgtk2.0-0 is in the repositories, you can type in *sudo apt-get install libgtk2.0-0* in the terminal.

Also, why are you letting your computer go to sleep if you want KTorrent to seed?

---

### Post by newagelink on 2008-05-25
> **dasunst3r said:**
> Firstly, on the *dpkg -i* command you issued, you forgot to tack on *sudo* to execute the command as root.[COLOR="Indigo"]I saw its response, that I lacked superuser privileges, so I understand that much (now.) As I said, I only decided to go ahead and press enter (the command was copy/pasted) because it said it didn't find the file, and I was wondering if anything would happen anyway.[/COLOR]
> **dasunst3r said:**
> Secondly, since libgtk2.0-0 is in the repositories, you can type in *sudo apt-get install libgtk2.0-0* in the terminal.[COLOR="Indigo"]Ah! Thanks![/COLOR]
> **dasunst3r said:**
> Also, why are you letting your computer go to sleep if you want KTorrent to seed?[COLOR="Indigo"]Because my computer's typically on roughly ten hours each day, and I don't want to waste energy. ... Problem:[/COLOR] > daniel@daniel-laptop:~$ sudo apt-get install libgtk2.0-0
[sudo] password for daniel:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**libgtk2.0-0 is already the newest version.**
The following packages were automatically installed and are no longer required:
  xchat-gnome-common planetpenguin-racer-data libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[COLOR="Indigo"]I already have the latest version![/COLOR]
> daniel@daniel-laptop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
daniel@daniel-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xchat-gnome-common planetpenguin-racer-data libsmpeg0
The following packages will be REMOVED:
  libsmpeg0 planetpenguin-racer-data xchat-gnome-common
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 12.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 117786 files and directories currently installed.)
Removing libsmpeg0 ...
Removing planetpenguin-racer-data ...
Removing xchat-gnome-common ... [COLOR="Indigo"]So ... I guess something else is now causing the same error message...[/COLOR]

---

### Post by dasunst3r on 2008-05-25
Just checking: Are you using Ubuntu or Kubuntu?

---

### Post by newagelink on 2008-05-25
[COLOR="Indigo"]Ubuntu; thus the prefix to the thread title that ubuntuforums requires.[/COLOR] ;)

---

### Post by dasunst3r on 2008-05-26
This seems to most closely resemble the issue you have been facing.  Try that solution and tell us what happens.

---

### Post by chinaxmsink on 2008-05-26
Now I know.Thanks you very much.---------------------------------------------------------------->We are the creators of beautiful handmade [copper sinks](http://www.china-sinks.com).

---

### Post by newagelink on 2008-05-26
> **dasunst3r said:**
> This seems to most closely resemble the issue you have been facing.  Try that solution and tell us what happens.[COLOR="Indigo"]Was there supposed to be a hyperlink in your post somewhere?[/COLOR]

---

