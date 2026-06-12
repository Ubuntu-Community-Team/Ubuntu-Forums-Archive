---
title: "sun-java6-plugin not working"
date: 2008-05-19
forum: General Help
---

### Post by schallstrom on 2008-05-19
In Hardy I installed the sun-java6-plugin package but my about:plugins page in Firefox does not show any java plugin. Could someone give me a hint on what to do?

(How stupid is that? The forum is making a dorky smiley out of the about: plugins string...)

---

### Post by zvacet on 2008-05-19
[Here]("http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html")

---

### Post by jamesstansell on 2008-05-19
> **schallstrom said:**
> In Hardy I installed the sun-java6-plugin package but my about:plugins page in Firefox does not show any java plugin. Could someone give me a hint on what to do?

Right now, if you're using Firefox 3 (the default in Hardy) try this:

sudo update-java-alternatives -s java-6-sun

You may need to restart Firefox.

If that doesn't work, try uninstalling openjdk-6-plugin.  You may need to try the steps above.

If you're using Firefox 2.5, there was a different configuration problem that has been fixed and is currently being tested.  It should be in hardy-updates soon, so if it's not urgent you might try waiting a few days.  If it is urgent there are a couple different work-arounds - I think one can be found by looking through here:

[http://ubuntuforums.org/tags.php?tag=java](http://ubuntuforums.org/tags.php?tag=java)

Note that even with the fix that will eventually show up in update-manager the steps above that are sometimes needed for Firefox 3 may still be needed.

HTH,

-james.

---

### Post by jamesstansell on 2008-05-19
> **zvacet said:**
> [Here]("http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html")

If you're reading this thread and visit the "Here" link above and can't make sense of those instructions, then look for other threads on these forums because there are some explanations that accomplish the same thing without requiring you to be as technically adept.

---

### Post by schallstrom on 2008-05-19
Thanks guys. I already used
```

update-alternatives --config java

```
to set it to Sun java. As this didn't work I already removed all openjdk packages I could find (openjdk-6-plugin does not exist as far as I can tell). Still got no plugin in firefox.

I just recognized that:
```

mo@molniya:~$ java
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * j2re1.4
 * kaffe
 * cacao
 * gij-4.1
 * jamvm
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found

```

although I'm pretty sure I have all the packages I need installed:
```

root@molniya:~# aptitude search java|grep ^i
i A java-common                     - Base of all Java packages                 
i A sun-java6-bin                   - Sun Java(TM) Runtime Environment (JRE) 6 (
i   sun-java6-jdk                   - Sun Java(TM) Development Kit (JDK) 6      
i A sun-java6-jre                   - Sun Java(TM) Runtime Environment (JRE) 6 (
i   sun-java6-plugin                - The Java(TM) Plug-in, Java SE 6           

```

I am able to start 'java' with the absolute path:
```

 /usr/lib/jvm/java-6-sun/jre/bin/java

```

Could it be that the alternatives-mechanism is not working properly?

---

### Post by FuturePilot on 2008-05-19
Are you using Firefox 2?

---

### Post by schallstrom on 2008-05-19
> **FuturePilot said:**
> Are you using Firefox 2?

Nah, 3.0b5, the default version in hardy. I was able to get the plugin to work by setting the symlink according to the howto zvacet posted (thanks!).

Still got the problem with the java cli program, although I just find this strange but I don't really need it.

---

### Post by jamesstansell on 2008-05-20
> **schallstrom said:**
> openjdk-6-plugin does not exist as far as I can tell

You're right - I was in la-la land when I typed that.  The actual plugin that works (for some people) with openjdk6 is icedtea-gcjwebplugin.

Sorry about that.

---

### Post by jamesstansell on 2008-05-20
> **schallstrom said:**
> Still got the problem with the java cli program, although I just find this strange but I don't really need it.

I've heard of some alternatives problems before, but never quite like what you are seeing.

Just curious - what does "ls -l /etc/alternatives/java" give you?

/etc/alternatives normally isn't in the PATH - rather /usr/bin/java should be linked to /etc/alternatives/java.  Assuming that you have /usr/bin in your path, then perhaps /usr/bin/java doesn't exist?

---

### Post by jamesstansell on 2008-05-20
> **schallstrom said:**
> I was able to get the plugin to work by setting the symlink according to the howto zvacet posted (thanks!).

I'm glad that worked for you.  You are obviously very capable on a Linux system.  So you'll probably be able to undo that symlink if it becomes appropriate for you in the future.

I'm currently looking looking at an ubuntu 7.04 system which has this chain of symlinks:

/usr/lib/firefox/plugins/libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

/etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

I'm not sure if 8.04 might have changed this a little, but even so it should be fairly close.

---

### Post by Shinoda on 2008-06-01
> **schallstrom said:**
> (How stupid is that? The forum is making a dorky smiley out of the about: plugins string...)
In the "Reply to Thread" page, check "Additional Options" &#8594; "Miscellaneous Options" &#8594; "Disable smilies in text".

---

### Post by schallstrom on 2008-06-06
> **jamesstansell said:**
> I'm currently looking looking at an ubuntu 7.04 system which has this chain of symlinks:

/usr/lib/firefox/plugins/libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

/etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

I'm not sure if 8.04 might have changed this a little, but even so it should be fairly close.

For some reason the /etc/alternatives/firefox-javaplugin.so link is absent on my system.

---

