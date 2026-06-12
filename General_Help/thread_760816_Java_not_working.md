---
title: "Java not working"
date: 2008-04-20
forum: General Help
---

### Post by DougWeir on 2008-04-20
Hi all,
I am really frustrated.  I really want to learn Ubuntu.  I really need java for an ssl vpn and nothing seems to be working.  I tried installing the GCJ implementation, that didnt work, tried installing the latest JRE that did not work.....Help!!  It's like it doesnt know its there even though I installed it.  Also, I am a Linux noob so please be gentle :)

Thanks
Doug

---

### Post by Tomosaur on 2008-04-20
Java can be a real pain in the backside :P

What you want to do is forget completely about gcj for the time being, an stick with Sun's JRE:

Try this in the command line:
```

sudo apt-get install sun-java6-jre

```
(When it asks for your password, just type it in as normal - you will not see it being typed, so be sure to spell it right!)

This should download the latest JRE available in the Ubuntu repositories. After this is done, everything SHOULD work fine, but if it doesn't, try the following:
```

sudo ldconfig

```

Then try running some Java stuff again.

If that still doesn't work, post back here with any error messages you receive :) (While you're still figuring out the problem, it'll be easier for us if you try to run everything from the command line, as that's where the most information will get dumped to).

When you run some java app, use the following format at the command line:

```

myApplication > javaStuff.txt

```

This will dump the output of whatever application into a file which you can just copy and paste here if you run into problems.

Also, give us the output of this command if you run into trouble:
```

java -version

```

---

### Post by glennzo on 2008-04-20
Doug, here's what I would do if Java wasn't working for me in Ubuntu. Keep in mind that I'm a Fedora guy and pretty green with Ubuntu. Uddate the slocate database first with the command
```
sudo updatedb
```
Locate libjavaplugin_oji.so, like this
```
glenn@toshiba:~$ locate libjavaplugin_oji.so
[COLOR="Red"]/usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so[/COLOR]
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
```
Decide what version of Firefox you are using. In my case it's firefox-3.0b5 so the plugin folder will be /usr/lib/firefox-3.0b5/plugins. Using the info in the line that I colored red, make a link to the firefox plugins folder like this
```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox-3.0b5/plugins

```
Close and restart Firefox and check to see if Java works.

Of course, this all assumes that Java is actually present on your system somewhere. If libjavaplugin_oji.so isn't found, here's a link to my wiki page about how I download and install Java. [http://www.johnson.homelinux.net/mywiki/JavaSetup?action=show](http://www.johnson.homelinux.net/mywiki/JavaSetup?action=show)

---

### Post by DougWeir on 2008-04-20
Hi,
Thanks for the quick response.  While I was waiting, I tried installing the IcedTea version.  But still no luck.  What happens is that it doesnt see that there is Java installed.  Here is the output of java -version:

java -version
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea Client VM (build 1.7.0-b21, mixed mode, sharing)


Thanks in advance for the help.

Doug

---

### Post by DougWeir on 2008-04-20
Hi all,
I do not have the javaplugin file and the directions that were posted were for Fedora.  Any suggestions?  

Thanks
Doug

---

### Post by DougWeir on 2008-04-21
Hi all,
Just wanted to check in and see if anyone had any ideas?

Thanks,
Doug

---

### Post by glennzo on 2008-04-22
Hi Doug. I running the Ubuntu 8.04 Release Candidate right now and here's what I get when I type locate libjava:
```
glenn@toshiba:~$ locate libjava
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjava.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjava_crw_demo.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjavaplugin_jni.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjavaplugin_nscp.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjavaplugin_nscp_gcc29.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/usr/lib/openoffice/program/libjava_uno.so
/usr/lib/xulrunner-addons/plugins/libjavaplugin.so

```
In this case I would link **/usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so** to **/usr/lib/firefox-3.0b5/plugins** since I'm also running FireFox-3.0b5.

**ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so  /usr/lib/firefox-3.0b5/plugins**.

The attached screen shot is of my FireFox **about:plugins** with regard to Java.

Edit: Forgot to attach screen shot :rolleyes:

---

### Post by DougWeir on 2008-04-23
thanks, all, think I got it working.

---

