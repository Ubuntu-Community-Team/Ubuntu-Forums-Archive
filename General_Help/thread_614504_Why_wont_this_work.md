---
title: "Why wont this work?"
date: 2007-11-16
forum: General Help
---

### Post by benniebrown07 on 2007-11-16
i'am trying to get java for limewire and it wont install for me can anyone help me?Edit: I just tried a different file and I think it worked but now when i try to ijnstall limewire the package installer says Error: Dependency is not satisfiable: sun-java5 but i just installed java 6 the newest one what am i doing wrong?

---

### Post by yabbadabbadont on 2007-11-16
No one will be able to help you unless you provide some relevant information...

What, exactly, are the commands you are running?
What, exactly, is the output/error messages if any?

:)

---

### Post by MrFSL on 2007-11-16
Frostwire
[http://www.frostwire.com/](http://www.frostwire.com/)

Free and Open Source.

---

### Post by benniebrown07 on 2007-11-16
it said, package installer says Error: Dependency is not satisfiable: sun-java5  <thats very similiar to what it said because its from memory, when i try to install limewire thats what i get but the installer said that java installed

---

### Post by ubuntu27 on 2007-11-16
Don't download Java from the web. Java is in the repositories. So just open-up "Synaptic" which is in System/Administration/Synaptic

Click on Search and type "Java" you will get a hundreds of results. Then install the java that you need. It ends in java-something-bin 

Also, I recommend you to use FrostWire. FrostWire is the same as LimeWire PRO, but without the advertisement, and without the limitation. 

[http://www.frostwire.com/](http://www.frostwire.com/)

FrostWire being based on LimeWire, also needs Java. So, install Java first.


Also, [check out this site ]("https://help.ubuntu.com/community/RestrictedFormats")where it explains topics such as codecs and other restricted formats such as java

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ubuntu27 on 2007-11-16
ok. Here is one command that will solve them all.
Make sure you are connected to the Intenet.

Open the Terminal

and type

**If you are using [Ubuntu]("http://www.ubuntu.com/")**
```
sudo apt-get install ubuntu-restricted-extras
```

**If you are using [Kubuntu]("http://www.kubuntu.org/")**

```
sudo apt-get install kubuntu-restricted-extras
```
[B]
If you are using [Xubuntu]("http://www.xubuntu.org")[/B]

```
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by benniebrown07 on 2007-11-16
what will sudo apt-get install ubuntu-restricted-extras do?

---

### Post by ubuntu27 on 2007-11-16
> **benniebrown07 said:**
> what will sudo apt-get install ubuntu-restricted-extras do?

It will download Sun Java, gstreamer plugins (that allows you to play mp3, flac, and other multimedia codecs) and install it automatically for you.

For more information see "[How to install Application Software in ubuntu]("http://monkeyblog.org/ubuntu/installing/")"

You might be interested in visiting website links that's in my Signature.

---

