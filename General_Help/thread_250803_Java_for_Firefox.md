---
title: "Java for Firefox"
date: 2006-09-04
forum: General Help
---

### Post by eschreib on 2006-09-04
I installed JRE 1.5x, but can not get firefox to 'recognize' it.
Any ideas?

---

### Post by mgpower0 on 2006-09-05
try this   sudo update-alternatives --config java

and choose the sun option
(/usr/lib/jvm/java-1.5.0-sun/jre/bin/java)

---

### Post by eschreib on 2006-09-06
I tried that, but no avail.
Interesting, Azurus runs, but no ability to get the jre to run in firefox


root@eschreibman-laptop:/home/eschreibman# sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.

---

### Post by David Corrales on 2006-09-06
I'm having the same problem on my laptop. It's a problem with the flash-nonfree plugin... bleh.

---

### Post by mgpower0 on 2006-09-07
> **eschreib said:**
> I tried that, but no avail.
Interesting, Azurus runs, but no ability to get the jre to run in firefox


root@eschreibman-laptop:/home/eschreibman# sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.

Yeah found that out last night too. Going to try and link to the java plugin will post what to do if it works

---

### Post by mgpower0 on 2006-09-07
Ok if you installed java from the repositories(synaptic) try the following
In terminal change directory to firefox plugin folder so

cd /usr/lib/firfox/plugins

now do the following to create link to java plugin

sudo ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so



hopefully this will work for you

---

### Post by dsmithnc on 2006-09-07
I am having the same problem.  I followed the instructions. No change, at least so far without a reboot.  I did close FF and restart it.

I didn't get any kind of an indication that anything happened after typing in the sudo..., so don't know if I should have seen anything or not.

Cheers,
Dick SMith

---

### Post by mgpower0 on 2006-09-07
> **dsmithnc said:**
> I am having the same problem.  I followed the instructions. No change, at least so far without a reboot.  I did close FF and restart it.

I didn't get any kind of an indication that anything happened after typing in the sudo..., so don't know if I should have seen anything or not.

Cheers,
Dick SMith

you can check if the firefox plugins folder has the link in it.
using nautilus just navigate to the firefox plugins folder located at usr/lib/firefox/plugins  and look for the libjavaplugin_oji.so  link. If it has a red square on it it means it is a broken link and you will have to find the correct path to the java plugin

---

### Post by dsmithnc on 2006-09-07
> **mgpower0 said:**
> you can check if the firefox plugins folder has the link in it.
using nautilus just navigate to the firefox plugins folder located at usr/lib/firefox/plugins  and look for the libjavaplugin_oji.so  link. If it has a red square on it it means it is a broken link and you will have to find the correct path to the java plugin

mgpower,

Thanks for the heads up.  both the libjavaplugin and jave have not squares but ovals on them with the internation no symbol.  On looking at the properties it does say link broken.  Any hints on how to fix the link would be much appreciated.

Dick

---

### Post by mgpower0 on 2006-09-07
> **mgpower0 said:**
> Ok if you installed java from the repositories(synaptic) try the following
In terminal change directory to firefox plugin folder so

cd /usr/lib/firfox/plugins

now do the following to create link to java plugin

sudo ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so



hopefully this will work for you

you need to find where your libjavaplugin_oji.so file is and link to it.
as you can see in my sudo line above my java-1.5.0-sun-1.5.0.06 folder is located in my jvm folder. you may have a seperate java folder that has sun java in it or a newer/older version in which case you have to adjust the link accordingly mine uses 1.5.0.06
if you can find the libjavaplugin_oji.so file with nautilus it is quite easy to work out the link needed as at the top of nautilus window it lists each folder you have opened to get to the final file.This is your link so then just do the sudo ln -s command listing each folder opened until you get to the plugin starting with /first folder/second/next and so on

---

### Post by mgpower0 on 2006-09-07
Sorry, you may need to remove the broken link before putting in your new one so do this   sudo rm /usr/lib/firefox/plugins/libjavaplugin_oji.so   

then check firefox plugin folder and make sure its gone

---

### Post by dsmithnc on 2006-09-08
Thanks for the last tip.  While it didn't work, I was able to find where I went wrong.  Finally got Synaptic set up tofind the JRE files, dowloaded and went through the installation and all is well.

I really need to do some more reading about Ubunut, I guess.

Thanks again,
Dick

---

