---
title: "Trouble with Java in 32 bit Firefox on 64-bit system"
date: 2008-04-29
forum: General Help
---

### Post by btmiller on 2008-04-29
Hi All,

I am having trouble getting the Sun Java 6 plugin working with Kubuntu 8.04 (64 bits). I am running a 32 bit Firefox 2.0.0.14 (for plugin compatibility) downloaded directly from Mozilla. This system was running 7.10 no problem with a JRE downloaded from Sun. When I upgraded Gutsy -> Hardy, though, Java stopped working with lock errors. After some trial and error I removed my Java version and installed ia32-sun-java6-bin. I have followed the advice about using sed to rename the symbol in libmawt.so given in [this thread]("http://ubuntuforums.org/showthread.php?t=615734"). Now that I've done this, whenever I start an applet Firefox hangs with 100% of the CPU and I must forcibly terminate it.

I've tried this with various combinations of the ia32-sun-java5-bin and the latest Java 6 JRE downloaded directly from Sun, all to no avail. Does anyone know where I am going wrong, as others I've seen on the forums seem to be able to get this working?

---

### Post by FredB on 2008-04-29
There is a 64 bits java plugin for firefox available with openJDK.

And which plugins force you to use firefox 32 bits ?

---

### Post by btmiller on 2008-04-29
Currently Flash is the main one keeping me at 32 bit. I have been meaning to try this with NSPluginWrapper but haven't had the opportunity. From reading the [Java page]("https://help.ubuntu.com/community/Java") it seems like I need to get icedtea-gcjwebplugin. I try this and getthe following error:

[FONT="Courier New"]
Setting up icedtea-gcjwebplugin (1.0-0ubuntu5) ...
update-alternatives: unable to make /usr/lib/xulrunner-addons/plugins/libjavaplugin.so.dpkg-tmp a symlink to /etc/alternatives/xulrunner-1.9-javaplugin.so: No such file or directory
dpkg: error processing icedtea-gcjwebplugin (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 icedtea-gcjwebplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/FONT] 

Do you know what my problem might be?

Unfortunately, my experiences with the GCJ based plug-ins has been bad with Java apps I need to run (mostly Jmol, which is used for molecular visualization). I don't think I've tried Icedtea, though, so perhaps it will do better.

Thanks for your help.

---

### Post by FredB on 2008-04-29
I see you're running hardy ? So, try to find in adept (as you're using Kubuntu) OpenJdk package.

IcedTea is the code name of OpenJDK and not used anymore. Hope it helps.

---

### Post by mivo on 2008-04-30
I had the same trouble in Ubuntu. After spending an evening on the problem, I installed the 32-bit version of Hardy on my 64-bit box. Not happily, but I have to say that there is absolutely no speed difference between 7.10 64-bit and 8.04 32-bit on my system. If anything, the 32-bit version seems faster, though I attribute that to Hardy. :) I'll go back to 64-bit when Sun releases a 64-bit version of Java and javaws. (The free alternatives don't work for some Java applets I need to use.) So unless you depend on a 64-bit OS (4 or morer GB RAM, I only have 3) or compile a lot, do audio editing or lots of video encoding, then perhaps that's an alternative until the next release.

---

### Post by LeSid on 2008-06-17
I'm getting the same error message when installint lots of things (eg fluxbox). What can be done?

---

### Post by MatthewHudson on 2008-08-16
found other thread for jmol
[http://ubuntuforums.org/showthread.php?t=675794&highlight=jmol]("http://ubuntuforums.org/showthread.php?t=675794&highlight=jmol")

---

