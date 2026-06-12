---
title: "Java dependencies"
date: 2013-04-22
forum: General Help
---

### Post by triplemaya on 2013-04-22
Hi. Having read about the security problems with java I am quite interested in uninstalling it. But I am worried that will break something I am used to depending on. Is there a list of apps that use java in the standard distribution, or a simple way to find out what depends on java? (The only one I know about is open office and that is ok to use without java.)

---

### Post by schragge on 2013-04-22
You can do it with a custom package filter in [Synaptic Package Manager]("http://manpages.ubuntu.com/manpages/quantal/en/man8/synaptic.8.html")
```

Filter "Java" {
  status::flags 0x1;
  pattern::patterns {
    Depends; "^java"; false;
    Depends; "javascript.*"; true;
  };
};

```
Save it as *java.filter* to your home folder, then start Synaptic with
```
synaptic -f ~/java.filter -iJava
```
 But I prefer doing the same on command line.

Install aptitude
```
sudo apt-get install aptitude
```
then run
```
aptitude search '~i~Djava!~Djavascript'
```
This will show all installed packages that depend on something containing *java* in its name, but not *javascript*.

Another useful command-line tool is [apt-rdepends]("http://manpages.ubuntu.com/manpages/quantal/en/man1/apt-rdepends.1.html"). It recursively searches for package dependencies and reverse dependencies like *apt-cache --recursive depends/rdepends* does, but has more options. Below are the output of some *apt-rdepends* commands on my system (Debian wheezy):
```

[COLOR=#008000]$[/COLOR] apt-rdepends -r java-runtime 2>/dev/null|grep '^[^ ]'|grep -v ^java
[COLOR=#008000]bootchart-view
charactermanaj
igv
jcadencii
mobile-atlas-creator
picard-tools
piespy
statcvs
statsvn[/COLOR]

```
```

[COLOR=#008000]$[/COLOR] apt-rdepends -r java7-runtime 2>/dev/null|grep '^[^ ]'|grep -v ^java|sort
[COLOR=#008000]biomaj-watcher
geogebra
geogebra-gnome
geogebra-kde
guacamole-tomcat
jajuk
king
pegasus-wms
solr-tomcat
tomcat6
tomcat6-admin
tomcat6-common
tomcat6-docs
tomcat6-examples
tomcat6-extras
tomcat6-user
[/COLOR]

```
There are much more packages that depend on *java2-runtime*, *java6-runtime*, or *java5-runtime*:
```

[COLOR=#008000]$[/COLOR] apt-rdepends -r java{,2,5,6,7}-runtime 2>/dev/null|grep '^[^ ]'|sort -u|wc -l
[COLOR=#008000]288[/COLOR]

```

---

### Post by Cheesemill on 2013-04-22
Another way is to simulate removing java to see what other packages apt would want to remove with it....
```
[COLOR=#008000]$[/COLOR] sudo apt-get -s remove java-common
[COLOR=#008000]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  java-common oracle-java7-installer
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Remv oracle-java7-installer [7u21-0~webupd8~0]
Remv java-common [0.43ubuntu3][/COLOR]
```

The -s switch just simulates the removal so no changes are made to your system. Run the same command without it to remove Java.
As you can see I don't have anything that depends on Java at all on my system at the moment (it's a new install).

---

### Post by triplemaya on 2013-04-23
Many thanks for all this. I get a fairly large list, over half have java in the name. The only things I recognise are eclipse, which I don't use, and open office, which I know will work ok, for my puposes, without it. All the same, with that many things on the list there could so easily be something I'm using without knowing! I think I might wait until I am about to do a new install for a new version release. Then if I get a system I am not happy with I can just move on.

One puzzling thing. With

root@debian:/home/pc# apt-get -s remove java-common

I get
 
The following extra packages will be installed:
  gsfonts-x11 sun-java6-bin sun-java6-jre unixodbc

So that does not take me quite where I was interested in going.

---

### Post by schragge on 2013-04-23
> **triplemaya said:**
> I get a fairly large list, over half have java in the name.To exclude packages with java in the name, run
```
aptitude search '~i!java~Djava!~Djavascript'
```

> **triplemaya said:**
> So that does not take me quite where I was interested in going.I guess it depends on how you've installed Java in the first place. **Cheesemill**'s is from [WebUpd8 PPA]("https://launchpad.net/%7Ewebupd8team/+archive/java"). [Default JRE]("http://packages.ubuntu.com/quantal/default-jre-headless") on Ubuntu (which is OpenJDK) also depends on *java-common*, so removing the latter would trigger uninstalling the official JRE package as well. But as you can see at [uhelp]community/Java[/uhelp], there are quite a few alternatives. It's up to packagers of each JRE, how they will handle dependencies.

You may also use ```
aptitude why java-common
``` to similar effect as *apt-get -s remove java-common*.

---

### Post by triplemaya on 2013-04-27
I did the deed on a test system - I've built an i3 box to use debian with MATE. Removed everything with java in the name, except for libjavascriptcoregtk verisions 1 and 3. Synaptic produced a fearsome list of packages that would have to go if these went, including gnome and others rather central to my experience of linux. Everything seems to work fine.

---

