---
title: "Facebook Image Upload Applet Doesn't Work"
date: 2007-10-28
forum: General Help
---

### Post by Sillee String on 2007-10-28
A simple problem...the java applet on facebook to upload photos won't load at all, instead I see a grey box in its place.  I've installed the java plugin required to make it work, but no dice.  Any ideas?

---

### Post by Dwarf007 on 2007-11-07
Remove completely GCJ:
```
sudo apt-get remove gcj libgcj-common libgcj7-0
```

Go onto the facebook page where the java applet is and when the missing plugin box appears follow the instructions to install sun-java6.

If it says that it is already installed or if it does not solve the problem, then create a symbolic link to the java plugin from your firefox plugin directory.

For instance:
```
sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin.so
```

Once this is done, you should restart firefox and it should work.

Enjoy!

---

### Post by sophaking on 2007-11-10
Awesome! Thanks a lot.

---

### Post by ukblacknight on 2007-11-13
Cheers!! This has been bugging me for a while!

---

### Post by aproan on 2008-01-08
I use amd64 so sun-java6-plugin is not available for my arch.

I have to use IcedTea but this doesn't enable me to upload pictures via the Facebook applet which makes me sooo sad.

---

### Post by Matokias on 2008-02-24
Hi all!...

As always, this forum has turned out to be priceless...

I followed the necessary steps, and everything is now working beautifully!

Thank you yet again, forum guys...

I LOVE UBUNTU!!!!!
:popcorn::popcorn:

---

### Post by DoriftuEvo on 2008-04-28
I have attempted the fix listed above, but I still get a "click here to download plugin" every time I try to upload pictures.  

Clicking brings up the plugin finder service with four options; GCJ, Java 6, Java 5, and GCJ (using IcedTea).  Clicking Java 6 just brings up a message saying "Package 'sun-java-6' plugin is already installed."  The symbolic link step doesn't change my results.

I've restarted firefox and my computer with no luck.

---

### Post by insert_name_here on 2008-05-01
I'm using the new firefox 3.0b5 that comes with Hardy, and after I follow the instructions here, I never get a little dropdown "install a plugin!" thing, so I'm left totally java-less.  Help?

---

### Post by EtherBunny on 2008-05-02
I'm using a fresh install of 8.04 and having this problem. I tried installing sun-java6-plugin and all the other java stuff. It doesn't work. Firefox doesn't prompt me to install the plugin ('cause it's already installed). There's a grey box and it says "applet not initialized".

---

### Post by georingo on 2008-05-08
I have the same problem. A java applet won't initialize... any ideas??

---

### Post by mofrikaantje on 2008-05-12
Worked like a charm. =D>

---

### Post by jopari on 2008-05-19
> **georingo said:**
> I have the same problem. A java applet won't initialize... any ideas?? Same here :(

---

### Post by georingo on 2008-05-20
OK removed icedtea (look in synaptic), and now everything works fine. Looks like Sun Java 6 isn't used as long as icedtea is available?!

---

### Post by pangloss on 2008-05-20
I believe not being able to switch plugins is this bug: [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/226911]("https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/226911")

openjdk-6, sun-java5, and sun-java6 install .jinfo files in /usr/lib/jvm that reference "xulrunner-addons-javaplugin.so". Replacing that reference with "xulrunner-1.9-javaplugin.so" should allow you to run update-java-alternatives to use the Java version (and plugin) of your choosing.

For example, if you're using sun-java5, edit /usr/lib/jvm/.java-1.5.0-sun.jinfo, replacing "xulrunner-addons-javaplugin.so" with "xulrunner-1.9-javaplugin.so". Then execute "sudo update-java-alternatives -s java-1.5.0-sun", restart Firefox, and enter "about:plugins" in the location bar to verify the correct Java plugin is available.

---

### Post by arasbm on 2008-05-23
> **georingo said:**
> OK removed icedtea (look in synaptic), and now everything works fine. Looks like Sun Java 6 isn't used as long as icedtea is available?!

I was getting the blank box. Removing icedtea worked for me too.
Thanks!

---

### Post by Strawp on 2008-05-30
This was bothering me for ages too and the instructions in this thread didn't work either.

I just got it working and in the end I uninstalled everything java-related in Add/Remove that I could, then removed sun-java in Synaptic as well.

Then after there was no more installed instances of Java or java plugins at all anywhere I installed sun-java RE and browser plugin using add/remove and it finally popped up in about:plugins and the uploader worked!

Thanks to the thread for giving me something to work with despite it not working for me though!

---

### Post by gladstone on 2008-06-08
I did this (which worked):

```
sudo apt-get remove gcj libgcj-common libgcj7-0 icedtea-gcjwebplugin openjdk-6-jdk openjdk-6-jre opendjdk-6-jre-headless libaccess-bridge-java tzdata-java

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

This will remove [OpenJDK]("http://en.wikipedia.org/wiki/OpenJDK") and install standard Java. You could also have a look at a great guide [here]("http://ubuntuforums.org/showthread.php?t=202537&highlight=openjdk") or [here]("http://ubuntuforums.org/showthread.php?t=743354&page=2") for an older thread during dev.

---

### Post by bzzzzz on 2008-06-10
> **georingo said:**
> OK removed icedtea (look in synaptic), and now everything works fine. Looks like Sun Java 6 isn't used as long as icedtea is available?!

Yep this fixed it for me too.

---

### Post by halitech on 2008-06-28
> **Dwarf007 said:**
> Remove completely GCJ:
```
sudo apt-get remove gcj libgcj-common libgcj7-0
```

Go onto the facebook page where the java applet is and when the missing plugin box appears follow the instructions to install sun-java6.

If it says that it is already installed or if it does not solve the problem, then create a symbolic link to the java plugin from your firefox plugin directory.

For instance:
```
sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin.so
```

Once this is done, you should restart firefox and it should work.

Enjoy!

Thank you for this, should have looked at this at lot sooner :) worked like a charm for me.

---

### Post by Kedster on 2008-06-28
Removing all the Icedtea stuff worked awsome for me

---

### Post by bzzzzz on 2008-06-29
Java installs pretty much automatically if you use mozilla.  Just click on the bit that says add plugins and install Java 6.

The problem is that your computer won't recognize it if icedtea is already installed.  Simply go to the add/remove programs synaptic and find icedtea and remove.

---

### Post by Larsj82 on 2008-07-06
For people using AMD64 with firefox 3 the plugin menu only shows the 2 GCJ plugins which only gives a gray box. It's been bugging me for ages having to use the simple uploader. However, if you use 32bit firefox you can use the java6 plugin and it works like a charm.

For anybody using 64bit having the gray box problem, follow this: [http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

Although it says it will install FF3, you actually get FF2. It will install it as a separate browser though, so you will still keep FF3. I can totally live with launching FF32bit on the rare occasions I want to expose myself on facebook

---

