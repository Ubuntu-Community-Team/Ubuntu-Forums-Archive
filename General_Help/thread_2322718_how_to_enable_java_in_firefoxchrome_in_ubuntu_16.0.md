---
title: "how to enable java in firefox/chrome in ubuntu 16.04?"
date: 2016-04-30
forum: General Help
---

### Post by jen8 on 2016-04-30
Hi I installed the latest version ubuntu but can't get java to work in my browsers. many instructions I found online doesn't seem to relevant to this version
I am in Australia the business info management software on the government website is java 
so it has to be resolved.
Anyone knows an easy way of doing it? I use firefox most of the time

here is the software
[https://abr.gov.au/For-Business,-Super-funds---Charities/Updating-or-cancelling-your-ABN/Update-your-ABN-details/](https://abr.gov.au/For-Business,-Super-funds---Charities/Updating-or-cancelling-your-ABN/Update-your-ABN-details/)
 click the 'update your ABN' link at the bottom of the page you will open the java webpage

---

### Post by QIII on 2016-04-30
Hello!

How did you install Java?

---

### Post by jen8 on 2016-05-01
I tried many methods. try to download things from Ubuntu software centre , Java official site or plug-in from the website of firefox browser. but none of them works

---

### Post by jen8 on 2016-05-01
what is the best software for use java in firefox/ubuntu now? There used to be a program called something like iced tea, but i can only find 'iced tea web control panel' in software center. and after I installed. it can't be launched

---

### Post by jen8 on 2016-05-02
anyone knows anything about this?

---

### Post by izznogooood on 2016-05-02
Hi.

There are no official repositories for adding Oracle Java in Ubuntu. You could however add a 3rd party PPA which will run the installer for you.
This will add the plug-in to Firefox.
Chrome does not support Java.


```
[COLOR=#303336]sudo apt[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]add[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]repository ppa[/COLOR][COLOR=#303336]:[/COLOR][COLOR=#303336]webupd8team[/COLOR][COLOR=#303336]/[/COLOR][COLOR=#303336]java
sudo apt[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]get update
sudo apt[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]get install oracle[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]java9[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]installer[/COLOR]
```

---

### Post by jen8 on 2016-05-05
> **izznogooood said:**
> Hi.

There are no official repositories for adding Oracle Java in Ubuntu. You could however add a 3rd party PPA which will run the installer for you.
This will add the plug-in to Firefox.
Chrome does not support Java.


```
[COLOR=#303336]sudo apt[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]add[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]repository ppa[/COLOR][COLOR=#303336]:[/COLOR][COLOR=#303336]webupd8team[/COLOR][COLOR=#303336]/[/COLOR][COLOR=#303336]java
sudo apt[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]get update
sudo apt[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]get install oracle[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]java9[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]installer[/COLOR]
```

I tried ur code but the last line get this error.

'
...
download failed
Oracle JDK 9 is NOT installed.
dpkg: error processing package oracle-java9-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up gsfonts-x11 (0.24) ...
Errors were encountered while processing:
 oracle-java9-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

'

---

### Post by izznogooood on 2016-05-06
Try "[COLOR=#303336][FONT=Ubuntu Mono]sudo apt[/FONT][/COLOR][COLOR=#303336][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=#303336][FONT=Ubuntu Mono]get install oracle[/FONT][/COLOR][COLOR=#303336][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=#303336][FONT=Ubuntu Mono]java8[/FONT][/COLOR][COLOR=#303336][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=#303336][FONT=Ubuntu Mono]installer"

And make sure you have enabled canonical partners and installed the restricted package.[/FONT][/COLOR]

---

### Post by $yl9pAR%t on 2016-05-06
Output of the below terminal command could be helpful:

```
cat /etc/apt/sources.list
```

---

