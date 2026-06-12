---
title: "Gutsy and Java"
date: 2007-10-26
forum: General Help
---

### Post by notamonopoly on 2007-10-26
I required Java for an application so I installed it using the commands I found in this forum: 
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts

I came accross a webpage that has an applet that I've accessed before without issue in Feisty, but now it absolutely devistaes my browser (Firefox). It freezes everything, I can't even force quit by hitting x, I have to kill it. Other applets work without issue so I'm very confused. The page in question is:
[http://jupload.sourceforge.net/applet-basic.html](http://jupload.sourceforge.net/applet-basic.html)

I've also tried this page under Windows with IE and while very slow to load, it did load and works.

Again, following advice found in the forums I tried:
sudo update-alternatives --config java

resulting in:
/usr/bin/gij-4.2
/usr/lib/jvm/java-6-sun/jre/bin/java

The latter is the default for me but I tried both and it made no difference.

What is the best way to install Java in Gutsy that will allow everything to work the way it used to? I never had a problem in Feisty.

Thanks

---

### Post by lyrids on 2007-10-26
I ran into problems with jconsole after 'apt-get install sun-java6-bin ...' stuff. It reported ugly exceptions at the AWT-GTK level, but JDK demos ran well.

Though not proved, I highly doubt the GIJ stuff may interfere with the SUN Java runtime, maybe at the native library level. ( Just a wild guess )

My solution is to download the JDK tarball from [http://java.sun.com](http://java.sun.com), and REMOVE the sun-java6- stuff by 'apt-get remove ...'.

Just unpack the downloaded .tar.gz under any directory you choose, then set the JAVA_HOME and PATH accordingly. Be sure to place $JAVA_HOME/bin ahead of /usr/bin .

Hope it helps.

---

### Post by notamonopoly on 2007-10-26
Thanks for replying.

I removed the Java6 stuff and downloaded directly from Sun. Everything still works the same and Firefox prompts me to choose a plugin.

GCJ Web Browser Plugin
The Java(TM) Plug-in, Java SE 6
The Java(TM) Plug-in, Java SE 5.0
The GCJ Web Browser Plugin (Using IcedTea)

I've tried adding/removing each of them and restarting the browser but none of them work on that page I mentioned. The first throws some warnings about security and then does nothing. The last one seems to work the best as there are no errors and no security warnings but the applet fails to start. The middle two cause Firefox (at least for me) to explode when I access the page. Well it doesn't explode, but I have to kill it when everything freezes up.

Have you tried the page I was referring to? Does the applet start for you?

I love Ubuntu and I love Gutsy for many reasons, but each upgrade causes me a new set of headaches. I thought Java of all things would be very smooth. I guess it is, except for this one thing. Stupid applets.

---

### Post by tikey on 2007-10-27
I have problems with java under Gutsy, too. I could solve the plugin problem with firefox, though. I downloaded the jre from the java-sun website and installed it. ([http://www.java.com/de/download/manual.jsp](http://www.java.com/de/download/manual.jsp) This is the German website but changing the de to s/th else probably works. I used the self extracting file and followed their instructions.)
Then I looked for the directory in which the mozilla plugins are installed (which is /usr/lib/mozilla/plugins) in my case. I switched to that directory and issued the command
sudo ln -s /usr/lib/jvm/jre1.6.0_03/plugin/i386/ns7/libjavaplugin_oji.so
Now my plugins are working again.

I still have problems with the jvm b/c matlab is still not working which I'm pretty sure is a java problem and azureus is also always crashing which could also be related to java.

---

### Post by tikey on 2007-10-27
ok, I fixed the matlab problem. I just had to install compiz and run it.

---

