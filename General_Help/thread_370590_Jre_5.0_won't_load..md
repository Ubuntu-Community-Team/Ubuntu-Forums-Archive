---
title: "Jre 5.0 won't load."
date: 2007-02-25
forum: General Help
---

### Post by helmeteye on 2007-02-25
Does anybody know how to get Jre to install on firefox 2.0 Ubuntu 6.10.  I tried to do some stuff on nascar today and I kept getting a firefox plugins needed.  It was for jre 5.0.  I did sudo aptitude install sun-java5-jre but nothing has happened.  Although it did download and install.  I read the instructions on the java web site but don't really understand them.  I can't even figure out which plugin to use.  Why doesn't it just load?

---

### Post by dcstar on 2007-02-25
> **helmeteye said:**
> Does anybody know how to get Jre to install on firefox 2.0 Ubuntu 6.10.  I tried to do some stuff on nascar today and I kept getting a firefox plugins needed.  I was for jre 5.0.  I did sudo aptitude install sun-java5-jre but nothing has happened.  I read the instructions but don't really understand them.

Use Synaptic and try and install the package.

The only "instruction" should be to accept the licence conditions.

---

### Post by Meson on 2007-02-25
You need to add the right package source.

System > Admin > Software Sources > check multiverse

Then search for JRE in synaptic,  you'll see the jre5 as well as the plugin

---

### Post by dcstar on 2007-02-25
> **Meson said:**
> I'm having the same problem.  I went to look at a page that uses Java and I realized I don't have the plugin.  I can't find the plug in synaptic, nor can I find JRE5 at all.
.......

You may have to enable some more repositories (apart from the default ones) - do a search on the one you need for Java.

---

### Post by helmeteye on 2007-02-26
I have all the repositories enabled.  I have some web sites that won't even recognize my browser as firefox 2.0.  What causes that?

---

### Post by phossal on 2007-02-26
You could always install Java 6 using the .bin file directly available from SUN, which is used to create the packages you see in the backports repositories. Installing directly might teach you something new about how your system works and allow you to look for and fix broken (or improperly executed) package installs.

The guide on installing Java in my sig includes *one* instruction on the java plugin for Firefox. Even if you choose a package, though, you can still move the links around manually.

---

### Post by helmeteye on 2007-02-26
Phossal, I had read that jre6 isn't really stable yet.  I guess it has been fixed.  The first install that wouldn't work came directly form java.  I then sudo aptituded(lol) it.  That didn't seem to work because the pages still told me I needed a plugin.  I actually found a thing in synaptic called jre plugin.  I have put it in but haven't tried doing that stuff again since.  

     My next or another question is, Why doesn't Hrblock.com recognize my browser?  I will go to jre6 but until then I am just curious.  That wasn't the first time that browser unsupported  has popped up, could someone go to hrblock.com and see if this is only happening to me?  Could be a coincidence because browser seems to be working just fine.

---

### Post by phossal on 2007-02-26
Are you just trying to view their front page, or were you trying to do some task? It appears their front page is *flash*, and not an applet.

As for Java6, I haven't heard any reports of it being unstable. Perhaps the *package* is unstable, but the JDK/JRE from SUN work fine. Quite frankly, the packages for Java are a mess, they're poorly packaged, and they're notorious for being behind SUN's updates. Months of using (a manually installed) Java 6 suggests it works well though.  The plugin is simply a link from /usr/bin/Firefox/plugin/plugin_name.so to /path_to_JDK/plugins/plugin_name.so. No matter how you install Java, that's essentially what is (or needs to be) done.

---

