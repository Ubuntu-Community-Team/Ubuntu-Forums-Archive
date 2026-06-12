---
title: "Using multiple Java Versions with firefox"
date: 2007-06-19
forum: General Help
---

### Post by mjsoccer1 on 2007-06-19
So here's the run down:

I want to be able to access my University's Student Information System, which is a java applet, on my laptop (running Ubuntu Edgy Eft 6.10... planning on updating to Fiesty when I return to school in a couple of weeks).  I have no problem accessing the SIS on my Windows (bah) machine using Sun Java 1.5.blah.

However, it says on the site [[COLOR="Blue"]here[/COLOR]]("https://oasisweb.uga.edu/html/unixlinux.html") that to use Linux or Unix, you need JRE 1.4.2_06 - 1.4.2_10 to run the applet.  So I installed j2re1.4.2_10 and added it to the alternatives list, then ran update-alternatives -config java and chose the 1.4.2_10 engine.  This works on the local machine when running java apps. however it appears that Firefox is still using 1.5.0_08 (I checked by going to [[COLOR="Blue"]this site[/COLOR]]("http://www.javatester.org/version.html")).  What can I do to correct this? How can I point firefox to use the correct java so I can access the SIS...

Any help is GREATLY appreciated!  
Thanks!

---

### Post by kuja on 2007-06-19
I'm fairly sure Firefox is independent of the "alternatives" system. That can be changed.

What you'll need to do is look up the plugin locations, here is an example path:
/usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

Before anything else, create this directory: /usr/lib/browser-plugins

Now, what you'll need to do first is create the alternatives for the plugin:

Here's a sample.

sudo update-alternatives --install /usr/lib/browser-plugins/libjavaplugin_oji.so javaplugin /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so 1000 

After you're done adding the alternatives run "sudo update-alternatives --config javaplugin"

Next, either add /usr/lib/browser-plugins to your plugin path in your browser(s) or create symlinks to /usr/lib/browser-plugins/libjavaplugin_oji.so in one of your browsers preferred plugin directories. 

Now you should be able to manage the plugin with ease, just run the update-alternatives for javaplugin and voila.

---

### Post by mjsoccer1 on 2007-06-20
Sweet, thanks!

Works like a charm, now I can access my grades/class schedule/etc from my laptop using the java 1.4.2_10 plugin and still run java apps on my machine using java 1.5.0_08.  

I'll be switching to fiesty here in a few days, so I'll see if 1.6 works with the applet.  If not, at least now I'll know how to set firefox to use old java.

:D

---

