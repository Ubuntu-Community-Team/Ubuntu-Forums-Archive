---
title: "Connection to Ext Data Source Could Not be Established"
date: 2015-10-05
forum: General Help
---

### Post by Rick St. George on 2015-10-05
Sorry if wrong thread, please inform where to post or move!

In LibreOffice Base; I get this message when attempting to create new Table.

   " The connection to the external data source could not be established. 
     No SDBC driver was found for the URL 'sdbc:embedded:hsqidb'. "

Any ideas? 
Thanks!
Rick
):P

---

### Post by QDR06VV9 on 2015-10-05
See if this get's you sorted out.
```
sudo apt-get install libreoffice-sdbc-hsqldb
```
Dont know why they don't include it with the installation?
Regards

---

### Post by Rick St. George on 2015-10-05
Thanks, here is the output;

```

stephen@stephen-evo-5723:~$ sudo apt-get install libreoffice-sdbc-hsqldb
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libreoffice-sdbc-hsqldb is already the newest version.
libreoffice-sdbc-hsqldb set to manually installed.
The following packages were automatically installed and are no longer required:
  hyphen-en-us libcuda1-331 libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-l10n-en-gb libreoffice-l10n-en-za mythes-en-au mythes-en-us
  nvidia-331-uvm nvidia-libopencl1-331 nvidia-opencl-icd-331
  openoffice.org-hyphenation
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
stephen@stephen-evo-5723:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  hyphen-en-us libcuda1-331 libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-l10n-en-gb libreoffice-l10n-en-za mythes-en-au mythes-en-us
  nvidia-331-uvm nvidia-libopencl1-331 nvidia-opencl-icd-331
  openoffice.org-hyphenation
0 upgraded, 0 newly installed, 12 to remove and 15 not upgraded.
After this operation, 100 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 255516 files and directories currently installed.)
Removing hyphen-en-us (2.8.6-3ubuntu2) ...
Removing libcuda1-331 (340.93-0ubuntu0.0.1) ...
Removing libreoffice-help-en-gb (1:4.2.8-0ubuntu1) ...
Removing libreoffice-help-en-us (1:4.2.8-0ubuntu1) ...
Removing libreoffice-l10n-en-gb (1:4.2.8-0ubuntu1) ...
Removing libreoffice-l10n-en-za (1:4.2.8-0ubuntu1) ...
Removing mythes-en-au (2.1-5.4) ...
Removing mythes-en-us (1:4.2.1-0ubuntu1.1) ...
Removing nvidia-331-uvm (340.93-0ubuntu0.0.1) ...
Removing nvidia-libopencl1-331 (340.93-0ubuntu0.0.1) ...
Removing nvidia-opencl-icd-331 (340.93-0ubuntu0.0.1) ...
Removing openoffice.org-hyphenation (0.7.1) ...
stephen@stephen-evo-5723:~$ 


```

But still get same Error. Base will open, but when clicking on TABLES or FORMS / CREATE or USE WIZARD, I get the Error.

Any ideas?
Thanks!
Rick

---

### Post by QDR06VV9 on 2015-10-05
Did you install from an outside PPA?
I have not seen this yet?
```
[COLOR=#000000][FONT=Ubuntu Mono]Reading state information... Done[/FONT][/COLOR]libreoffice-sdbc-hsqldb is already the newest version. 
**libreoffice-sdbc-hsqldb set to manually installed**.
```

For certain features of the software - but not most - Java is required. Java is notably required for Base.

---

### Post by Rick St. George on 2015-10-05
No- I used Ubuntu Software Center.  Noticed your reference to Java.
I am currently running OpenJdk 7 (see below)

```


stephen@stephen-evo-5723:~$ sudo update-alternatives --config java
[sudo] password for stephen: 
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-8-oracle/jre/bin/java          1076      auto mode
* 1            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1071      manual mode
  2            /usr/lib/jvm/java-8-oracle/jre/bin/java          1076      manual mode

Press enter to keep the current choice
[*], or type selection number: 


```

Does this help?  Does it matter which version - Oracle or Open JDK?
Thanks!
Rick

---

### Post by QDR06VV9 on 2015-10-05
This is how mine is
```
* 2            /usr/lib/jvm/java-8-oracle/jre/bin/java          1074      manual mode


```
And I am not having any issues with Libre Base.

---

### Post by Rick St. George on 2015-10-05
Still get same Error, perhaps I need to restart JAVA. How do I do that in Terminal?
Thanks!

---

### Post by QDR06VV9 on 2015-10-05
The way i have always understood JAVA it only runs with the applications as needed.
I would try to to close Libre Base and and re-open see if the error is still there.
This in your post above has me scratching my head though
> **libreoffice-sdbc-hsqldb set to manually installed**[COLOR=#000000][FONT=Ubuntu Mono].[/FONT][/COLOR]

If you would see if libreoffice-base-drivers are installed?
```
apt-cache policy libreoffice-base-drivers 
```

---

### Post by Rick St. George on 2015-10-05
It was closed when I made the JAVA switch. Reopened and .. same message!

Now my head is scratching ! ! !

---

### Post by QDR06VV9 on 2015-10-05
This is what they tell me.
> [COLOR=#323232][FONT=Myriad Pro] &#8220;No [/FONT][/COLOR][COLOR=#323232][FONT=Myriad Pro]SDBC[/FONT][/COLOR][COLOR=#323232][FONT=Myriad Pro] driver was found&#8230;&#8221; indicates that Base could not find the [/FONT][/COLOR][COLOR=#323232][FONT=Myriad Pro]JRE[/FONT][/COLOR][COLOR=#323232][FONT=Myriad Pro] driver to make the connection.[/FONT][/COLOR]
I am lost ATM:-k
Just to cover all Bases here have you restarted yet? Stranger things have worked.
Regards

---

### Post by QDR06VV9 on 2015-10-05
Ok lets see if Libre can even see java.
Open Libre Office
Then Select >Tools then >Options, click on that.
Then on the left go down to >Advanced, click that now, in the window on the right it should show >Use a Java runtime enviroment, Enabled.
I attached a screen shot for mine, yours should show similar.

---

### Post by Rick St. George on 2015-10-05
WOW - After restart .. same thing. Then I noticed another window popped up, something like - "Base needs JRE running. Do you want to start a JVE?" I clicked YES, and it worked. 

Thanks a Million and SORRY for the Trouble!
Solved and Case Closed.
Rick
:popcorn:

---

### Post by QDR06VV9 on 2015-10-05
It is never any trouble to help out, Just takes me a while to kick in sometimes..:grin:
Good Job!!

---

