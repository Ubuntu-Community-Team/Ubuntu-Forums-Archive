---
title: "Help Wanted: to install Java 1.5.8 plugin as default"
date: 2007-05-11
forum: General Help
---

### Post by Iowa Dave on 2007-05-11
A widely used educational content management system requires the Java 1.5.8 plugin. I have found this much about the Java in my installation of Dapper 6.06:

[INDENT]$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-gcj/jre/bin/java    <= the currently active default, apparently
      3        /usr/lib/jvm/java-6-sun/jre/bin/java

$:/usr/lib/jvm/java-gcj/jre/bin$ java --version
java version "1.4.2"[/INDENT]

Also take a look at this output from entering 'about: plugins' in Firefox:

[INDENT]Java(TM) Plug-in 1.6.0-b105

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0[/INDENT]

It seems that I managed to skip over any and all versions of 1.5.

I need to get the 1.5.8 plugin installed and select it for the default in Firefox. Have searched the forums and search engines in vain. Any help would be appreciated.

Thanks in advance,

Iowa Dave

---

### Post by sdil on 2007-05-12
I think you should intall java by Application - > Add/Remove .... :popcorn:

---

### Post by Iowa Dave on 2007-05-12
Thanks for the suggestion, but it doesn't help.

Java doesn't appear in the list of applications under Applications > Add/Remove. None of the Java installations I have detected in my computer show up, nor do any others.

I think it may be because Java isn't an "application" as that particular utility defines the term.

Synaptic mentions Java in a number of places, but I haven't found anything that seems directly related to the 1.4 and 1.6 versions of Java that I know are installed on this machine.

Once again, I appreciate the willingness of people to help. This one's quite a stumper. I've been spending time in the #ubuntu room on freenode, where Java seems to attract more questions than answers.:(

---

### Post by Iowa Dave on 2007-05-12
I found the answer.  It took several steps.

1. Remove the java plugin that I did not want. This was accomplished through Synaptic, where I uninstalled the previously installed parts of sun-java6. To confirm that this removed the plugin, I typed  about:plugins into the Firefox url field. (Note, the confounded smiley in there is made of two characters that must be typed consecutively in the Firefox url field: the colon ":" followed by a "p". Not all occurences of colon-p are meant to smile. Sigh...) The java plugins were no longer listed. Step 1 accomplished.

2. Older versions of Java are well-hidden, but still available. I found java 1.5.8 by entering the following into a search engine: jre-1_5_0_08

The first thing that popped up was what I wanted: [Download Center - Download]("http://javashoplm.sun.com/ECom/docs/Welcome.jsp?StoreId=22&PartDetailId=jre-1.5.0_08-oth-JPR&SiteId=JSC&TransactionId=noreg")

And there was the official download page. After accepting the license terms, I downloaded the linux self-extracting file (not the rpm version.)

3. To install it, I followed instructions found here: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_JRE_v5.0_Update_10]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_JRE_v5.0_Update_10")

except I used "08" in place of "10" to indicate the version number I was installing.

I saw some warning messages while fakeroot was running. But at the end both fakeroot and dpkg reported success. And when I checked about:plugins (darn that smiley) in Firefox, it confirmed that java 1.5.8 was now active.

4. To test it, I went to a site that I have to use for work that requires Java 1.5.8. The browser sniffer on that site verified the installation.

It took some searching to find all this. The first clue was discovering that java isn't called "java" in Synaptic. It is called sun-java. I couldn't find it listed among packages starting with "j" because it starts with "s". 

Hope this helps someone.

Iowa Dave

---

