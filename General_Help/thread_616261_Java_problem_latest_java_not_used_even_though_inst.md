---
title: "Java problem: latest java not used even though installed (firefox)"
date: 2007-11-18
forum: General Help
---

### Post by BatPenguin on 2007-11-18
Hello,

I've tried to get this working by surfing the forums but still no luck. Basically, my problem is that the the Java test page at sun still says that:

> Oops! You don't have the recommended Java installed.
Your Java version is 1.4.2. Please click the button below to get the recommended Java for your computer.  

..even though I've installed latest Java through Synaptic. I've also done:

```
sudo update-java-alternatives --set java-6-sun
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so 

```

(the latter command while in the /usr/lib/firefox/plugins directory). The ouput of the plugins directory is this:

```
lrwxrwxrwx 1 root root   37 2007-10-21 23:57 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root   34 2007-11-07 10:40 libgcjwebplugin.so -> ../../classpath/libgcjwebplugin.so
lrwxrwxrwx 1 root root   73 2007-11-18 09:22 libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root root   39 2007-11-18 09:03 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
-rw-r--r-- 1 root root 9104 2007-10-22 17:12 libunixprintplugin.so
lrwxrwxrwx 1 root root   31 2007-11-10 23:03 xineplugin.so -> ../../xine-plugin/xineplugin.so

```

And Java is enabled in Firefox Preferences menu, too. But still no luck. Java test page claims I don't have the latest installed, and I can't get to some pages. This is the page I tried to get into when I detected this problem:

[http://www.450laajakaista.fi/karttapalvelu/](http://www.450laajakaista.fi/karttapalvelu/)

I'm using Gutsy 32-bit. Any ideas what I've done wrong here? My guess is that the firefox plugin still is using the old one for some reason even though the link is correct...is this the case? How should I try fixing this? Thanks.

---

### Post by bartkl on 2007-11-18
I have the exact same problem, so I hope people can solve this. It's annoying.
I've uninstalled the unused 1.4 version and still Java.com claims I'm using it.

---

### Post by BatPenguin on 2007-11-18
OK, so I'm not the only one.  After my message I also tried downloading Java and installing it manually. That didn't work either, same problem still.

---

### Post by Ber P on 2007-12-03
Has anyone solved this??? It's driving me nuts!!!!

---

### Post by doundounba on 2007-12-03
Same here.  I see that I had sun-j2re1.5 installed.  I tried to install j2re1.4-mozilla-plugin, but the process failed and the package is now marked a broken...  FWIW, Java was working before my upgrade to Gutsy (yesterday).

---

### Post by johnbanni on 2007-12-03
Hmm it seems to be a common issue in 7.10

I have the same problem and my net banking doesn't work at all!  :(

I hope they fix it soon, because I would hate to go back to XP again!  [-o<

---

### Post by Ber P on 2007-12-04
I found the solution (for me at least) in another thread. Removed "gcjwebplugin" and finaly it uses java 6!

---

### Post by Greenskycity on 2007-12-04
I just got into Ubuntu last night and I also had the same problem.  The java site said I had the wrong version.  I just now did what Ber P did and it worked for me.  In Symnaptic Pakage manager do a search for GCJ and "GCJwebplugin" will show up and check it for removal and viola!  You have Java, I don't have audio with it, but you might.

---

### Post by pulicoti on 2008-01-23
Yesss Thank you very much ber p uninstalling the "gcjwebplugin" it worked fine!!!

:):):)

---

### Post by Cibola on 2008-01-24
Could you please tell me how you removed "gcjwebplugin". I am a novice. Where do you find the thread.

Thanks

---

### Post by Cibola on 2008-01-24
> **Greenskycity said:**
> I just got into Ubuntu last night and I also had the same problem.  The java site said I had the wrong version.  I just now did what Ber P did and it worked for me.  In Symnaptic Pakage manager do a search for GCJ and "GCJwebplugin" will show up and check it for removal and viola!  You have Java, I don't have audio with it, but you might.
Where do I get Symnaptic Package manager??

---

### Post by SyL on 2008-01-24
> **Cibola said:**
> Could you please tell me how you removed "gcjwebplugin". I am a novice. Where do you find the thread.

Thanks


Command line:
```
sudo apt-get remove gcjwebplugin
```

or with Symnaptic Package manager --> you will find it under the system menu.

---

### Post by pulicoti on 2008-01-24
Ok Cibola,
Sistem administrator synaptics

type into search  gcjwebplugin 

mark it and select remove

apply


:)

---

### Post by stchman on 2008-01-24
When you install Java you need to install the Java plugin.  I use Java 5 so I installed the

sun-java5-plugin

Firefox then can load sites that use Java applets.

---

### Post by Bablefish on 2008-01-24
When I had trouble with Java someone gave me this command

To set java use this command in terminal



sudo update-alternatives --config java

---

### Post by AdNZL on 2008-01-25
Superb! I had tried everything else and nothing had worked till I tried this. Although I think this one on its own might not be enough for some people. I think I was just lucky that I came across this first [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html")

That link didn't get firefox working with java but even though I had the latest version of java installed the old version was still being used. I'll cute and paste one of the posts in this link that was a huge help for me.

#  Les Says:
September 5th, 2007 at 3:58 am

For people have problems with their java coming up with an old version after you install the new 1.6, do the following from a root shell:

> update-java-alternatives -s java-6-sun

This will change the Java engine over to the new version.

You can check the installed version or change with:

> update-java-alternatives -l

..which will give you output similar to:

java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1041 /usr/lib/jvm/java-gcj

I didn't use a root shell I just put sudo at the beginning of the first line, which worked just fine.

After I did this then I needed to do as this thread sugested and delete GCJwebplugin. Anyone still wondering where to find this, you'll find it in System>Administration>Synaptic Package Manager

Just enter GCJ into the search field and it will come up with a bunch of other packages. I found I only needed to delete that one file, not any of the others with VERY similar names.

It would be great if someone could figure out a way to do this without deleting this file, but it works, and its easy to do. Took me weeks to find this thread. I hope more people find it useful as I'm sure a hell of a lot of people are suffering because of this bug.

---

