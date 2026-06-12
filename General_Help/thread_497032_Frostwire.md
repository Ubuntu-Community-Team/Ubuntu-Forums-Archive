---
title: "Frostwire"
date: 2007-07-09
forum: General Help
---

### Post by Bofur on 2007-07-09
I installed the frostwire deb along with java from synaptic, but it won't startup at all. Is there something else I need to install for it to work? Thanks.

---

### Post by Kodfish on 2007-07-09
Try executing it from the console. 

```
frostwire&
```

and then post your results

---

### Post by Bofur on 2007-07-10
```
justin@linuxbox:~$ frostwire&
[1] 6308
justin@linuxbox:~$ Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com


```
Well it looks like I need to upgrade my java. Anyone know how I go by doing that? Sorry I'm a newbie :confused:

---

### Post by mikewhatever on 2007-07-10
Remove the java you've installed and install the new version 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox)

---

### Post by labtek on 2007-07-10
My Frostwire would not boot up until I installed Sun Java 6 Runtime and Sun Java 6 Webstart from the Kubuntu repositories. I use Kubuntu Feisty Fawn.

I went to K menu, then to "Add/remove programs" which brought up Adept Installer- I did a search for Sun Java. I toggled them on and then applied the changes.

Frostwire booted perfectly after that.

Hope this helps.

---

