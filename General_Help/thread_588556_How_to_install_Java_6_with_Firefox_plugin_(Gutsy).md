---
title: "How to install Java 6 with Firefox plugin (Gutsy)"
date: 2007-10-23
forum: General Help
---

### Post by Zoufiax on 2007-10-23
Somebody please give me the exact steps I have to take to install Java 6 JRE including a Firefox plugin. I have been trying for hours and hours now (indeed I must be the biggest Linux noob on this planet) but I can't get it working. I have searched this forum and Google but everything seems to fail.

Actually the only thing I need is the Firefox Java plugin.

I have enabled the multiverse software source as this seems to be necessary.

I seem to have installed Java here: /usr/java/jre1.6.0_03 by taking the steps at Sun's website, but the Java plugin doesn't seem to be working. When I do a test here: [http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com), it says the I'm running Java version 1.4.2. If I go to about: plugins in Firefox, it lists GCJ Web Browser Plugin 0.92, which says it should be able to run Java applets. No idea how I got it, but I just want the above mentioned version.

It is a shame the Java plugin is so hard to install (only the fact one has to enable multiverse in software sources is too hard for beginners). If Ubuntu is to compete with Windows in user friendliness, things like these should be made much easier. I am an experienced Windows user and I still think Ubuntu is behind Windows in some areas.

Thanks for your help in advance. If my English is not 100%, that's because I'm Dutch.

---

### Post by songshu on 2007-10-23
don't use the thing from the sun web site,

al you need to do is to enable the repository's and install "ubuntu-restricted extras"
(replace ubuntu with kubuntu or xubuntu if you have that one.)

if its too dificult to click a few buttons, dikke pech zo moeilijk is het niet ;)

---

### Post by Zoufiax on 2007-10-23
I had already installed ubuntu-restricted-extras, and now I have reinstalled it. But the Java test still says I'm running 1.4.2, and Firefox is still saying nothing about Java 6.

---

### Post by songshu on 2007-10-23
can you remove the 1.4.2 version first and then re-install the restricted extras

---

### Post by Zoufiax on 2007-10-24
Please explain how I can remove 1.4.2.

---

### Post by Nunu on 2007-10-24
Not to sure but see if you can remove it with synaptic package manager.

---

### Post by forestpixie on 2007-10-24
search in synaptic for java or sun to look for it - I ended up removing every instance of both and hidden files, before a reinstall worked properly.

---

### Post by the yawner on 2007-10-24
Enabling the multiverse repo is just a matter of selecting it on the drag/drop option on Add/Remove. Or clicking the checkbox on the software sources under System>Adminstration. Can't get any easier than that.

But anyway, I've checked the instructions and it says there that it offers either an rpm package or a binary install. I guess you probably ran the binary install and thus I dont think it would appear on Synaptic. I tried searching for uninstall instructions on the site but oddly enough, it appears to be non-existent.

---

### Post by Indigo7 on 2007-10-24
I have the same situation. I've installed Java6 from the repositories and *java -version* reports that I have Java 1.6.0.03. I've also confirmed that Sun's java is the default java engine. I've created the link in the plugins folder, but still no go. Could it be Firefox?

---

### Post by cytg on 2007-10-24
[http://plugindoc.mozdev.org/faqs/firefox-linux.html#install-where](http://plugindoc.mozdev.org/faqs/firefox-linux.html#install-where)


---
How do I install Java?

    If your distribution doesn't include it, Download and install JRE 1.4.2 or later. After your JRE is installed, open a terminal, change to your Mozilla Firefox plugins directory, and issue the following command:

    ln -s /usr/java/jre1.5.0_09/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so

    If you are not using Sun JRE 1.5.0_09, and/or you installed your JRE at a different location, you will need to modify the command accordingly. Do not copy the plugin, otherwise Firefox will crash if you try viewing a page containing a Java applet.

    Further information, including known issues, is available from the Java FAQ.

    [Download Sun JRE 6.0]


on my system

/usr/lib/firefox/plugins/libjavaplugin_oji.so

wich links to

/usr/lib/java6u2/jre/plugin/i386/ns7/libjavaplugin_oji.so

---

### Post by mahiyar on 2007-10-24
In the previous feisty and edgy I always ended up with more than one version of java, this time I decided t be careful. I went to Add/Remove searched for java and installed the Sun java 6.0 web start. See the attached pic. If you have more than on version of java installed then use this command to select >>sudo update-alternatives --config java

---

### Post by Zoufiax on 2007-10-25
It works. I reinstalled Gutsy, because I thougth I has messed things up by installing Java and some plugins "the wrong way" (for example by downloading it from the Sun website and installing it). This time (after reinstalling Gutsy) I installed "Ubuntu restricted extras" using Add/Remove Applications (among others), which also installed Java 6 and the Firefox plugin. It was not necessary to use the terminal window a single time. Thanks for all your help anyway.

---

### Post by Grellin on 2007-10-25
> **mahiyar said:**
> In the previous feisty and edgy I always ended up with more than one version of java, this time I decided t be careful. I went to Add/Remove searched for java and installed the Sun java 6.0 web start. See the attached pic. If you have more than on version of java installed then use this command to select >>sudo update-alternatives --config java

I tried the Add/Remove option and did a search for java, sun java but nothing comes up. I am guessing I don't have the proper repository set up but I don't know how to do that. Any help out there for a noob :)

---

### Post by Grellin on 2007-10-25
I installed the java 1.6 from Synaptic manager and java -version registers but I am having the same issue as a poster above. The java web site still says I have 1.4.

---

### Post by Indigo7 on 2007-10-25
I used synaptic to remove the "gcjwebplugin" and all is good!

Hope it helps!:)

---

### Post by wormie_dk on 2007-11-07
I have the same problem... Tried reinstalling java using aptitude but that did not help. If I look in /usr/lib/firefox/plugins AND /usr/lib/mozilla/plugins I have a libjavaplugin.so which points to etc/alternatives/firefox-javaplugin.so which again points to /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

However about:plugins does not list java in firefox. 

Any ideas? I installed gutsy from scratch but uninstalled/reinstalled firefox as I had problems with it.

---

### Post by bardu on 2007-11-10
Same thing here. Everything seems to be linked correctly, but Firefox doesn't recognized the Java plugin, although, if trying to install the plugin Firefox installation wizard says the Java 6 plugin is already installed. But about:plugins doesn't list it.

Because Java Applets are somehow important to my current development efforts I hope this problem can be fixed asa possible.

---

### Post by mahiyar on 2007-11-11
Go to this site [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp) and check whether java is installed or not.

---

### Post by bardu on 2007-11-12
Java is installed, I can compile and run Java apps. Even the link to the page you have provided requires the Java plugin.

---

### Post by krambo on 2007-11-18
> **wormie_dk said:**
> I have the same problem... Tried reinstalling java using aptitude but that did not help. If I look in /usr/lib/firefox/plugins AND /usr/lib/mozilla/plugins I have a libjavaplugin.so which points to etc/alternatives/firefox-javaplugin.so which again points to /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

However about:plugins does not list java in firefox. 

Any ideas? I installed gutsy from scratch but uninstalled/reinstalled firefox as I had problems with it.

I followed the advice of Indigo7  in the post above and after 3 hours of struggling to get java working and recognized correctly - it finally worked.  The Java,com page now reports the correct verion installed - thank you Indigo7  :)

---

