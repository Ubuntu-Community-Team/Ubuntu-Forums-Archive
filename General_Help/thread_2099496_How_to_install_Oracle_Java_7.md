---
title: "How to install Oracle Java 7"
date: 2012-12-29
forum: General Help
---

### Post by grandsatrap on 2012-12-29
This post provides instructions on how to install Oracle Java 7 JDK.

Platform specifics: 
[LIST]
[*]This posting assumes that you are competent to enter commands at the CLI.
[*]I am running Ubuntu 10.04 LTS.
[*]I'm using the 64bit version of Ubuntu, but the instructions work for the 32 bit version too.
[*]I am installing the JDK (not just the JRE)
*What this means is that I am want to write and compile java programs instead of only running them. If you only want to install the JRE you can follow these instructions too.*
[/LIST]

**Steps:**
[LIST=1]
[*]Delete any old versions of Java. How you do this depends on how you installed them.
[*]Go to [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
[*]Click on the JDK download button (under Java Platform Standard Edition)
[*]Click OK to accept the license agreement
[*]Download the appropriate version (32bit=x86, 64bit=x64):  ** NOT THE RPM version
       Linux x86	92.97 MB  	[COLOR="Blue"]jdk-7u10-linux-i586.tar.gz[/COLOR]
       Linux x64	91.71 MB  	[COLOR="Blue"]jdk-7u10-linux-x64.tar.gz[/COLOR]
[*]Uncompress the file from wherever you saved it (e.g. $HOME/Downloads): ```
tar -xvf jdk-7u10-linux-x64.tar.gz
```
[*]Move the folder that has just been created (here it is "jdk1.7.0_10") to somewhere global. This is what I do: ```
sudo mv jdk1.7.0_10 /usr/local/
```
[*]If you are using the JDK and plan on running "javac ..." and "java ..." on the command line, you need to do this step. 

You probably also need to do this so that browsers (eg. Chrome) can find where Java is located.
Update $HOME/.profile with new path to Java. Add the following lines to your $HOME/.profile file
```
	# add path for Java JDK
	if [ -d "/usr/local/jdk1.7.0_10/bin" ] ; then
	    PATH="$PATH:/usr/local/jdk1.7.0_10/bin"
	fi
```Once this is done, you'll have to reboot, or possibly just log off in order for the changes in .profile to be read.
[*]Update Firefox plugins so that Java works
[LIST]
[*]This must be done in two places. There are three steps to each:
(i) change to the correct directory
(ii) remove the old java plugin
(iii) add a symbolic link to the new plugin
```
cd /usr/lib/firefox/plugins
sudo rm -i libnpjp2.so
sudo ln -s /usr/local/jdk1.7.0_10/jre/lib/amd64/libnpjp2.so
```
```
cd /usr/lib/firefox-addons/plugins
sudo rm -i libnpjp2.so
sudo ln -s /usr/local/jdk1.7.0_10/jre/lib/amd64/libnpjp2.so
```
[*]For 32 bit use [COLOR="Blue"]i386[/COLOR] instead of [COLOR="Blue"]amd64[/COLOR]
[/LIST]
[*]Now try Java in Firefox.  If it still doesn't work, first check "about: plugins". It probably won't say "Java 1.7..." there so you have to 
(i) close Firefox
(ii) go to your firefox profile in $HOME/.mozilla/firefox/___/ 
(iii) delete the file pluginreg.dat  (it will be recreated once firefox starts).


[/LIST]

---

### Post by grandsatrap on 2013-01-25
**NOTE:** The whole reason for doing this is **if you don't want to use _OpenJDK_,** but want Oracle's JDK.

---

