---
title: "Installing Java and Flash"
date: 2014-03-10
forum: General Help
---

### Post by bill31 on 2014-03-10
I bought a Chromebook and was very disatified with the Chrome OS (mainely because it does not support java). I installed ubuntu and gave it 9 gigabytes of space to use. I am stumped however as to how to install just about anything because it keeps asking me what aplication I want to use. I dont think I have any since I just installed ubuntu. I have searched online but I cant seem to figure out how to get java. I mainly want it to play minecraft.

Installing flash seems to be failing as well

Got chrome browser to work but still cant install flash

---

### Post by claracc on 2014-03-10
What ubuntu have you installed?, the easiest way to install software is through software center, you choose the software you want to install and click on it.

Other way is through command line, opening a xterm (console) with ctrl+alt+T and running:

```
sudo apt-get install name_of _program
```

Please, see: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

In order to install oracle java and its plugin in the browser you can do through webup8 ppa, please see: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html) with full instructions.

---

### Post by bill31 on 2014-03-10
I am running 13.10 and was installed via ChrUbuntu

---

### Post by bill31 on 2014-03-10
I *think* following the instructions from askubuntu.com worked. I am going to test it out.

---

### Post by bill31 on 2014-03-10
Its still asking me to download flash player on anything that requires it through firefox (did not test chrome). Installing "yum" failed. Still stumped. I am going to see if minecraft will work however.

---

### Post by bill31 on 2014-03-10
I am able to install and play minecraft. Still not sure how to get flash to work in any of my browsers though :(

---

### Post by bill31 on 2014-03-10
Got flash working, but my java secrity level is so high it isnt allowing me to even use it. uhg so many issues. I am attempting to locate the control panel and found java's website and its instructions for doing so. Now the issue is that the command they give is a tad wrong. I think what it is, is the version they have as an example for the command is outdated. I put my current version (1.7.1) but I think what is getting me is what goes after the _ (underscore)

---

### Post by Yellow Pasque on 2014-03-10
Chrome has its own version of Flash built in. 
For other browsers:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by bill31 on 2014-03-10
I got flash to work on firefox but I need to access my secrity panel for java as its not allowing me to realy use it.

---

### Post by claracc on 2014-03-10
If you have oracle java, you will have to look for: Oracle java 7 plugin control panel, if I have understood correctly your problem.

---

### Post by bill31 on 2014-03-12
What I think I need is to locate my java control panel but I do not know how to do so. The Oracle website gives instructions for doing so with windows and mac OS but not for any Linux OS let alone ubuntu. So far I always get "Application Blocked by security Settings".

---

### Post by QIII on 2014-03-12
Assuming Ubuntu on your chromebook works the same, you should be able to open the Dash (the Ubuntu symbol in the upper left) and start typing  

```
oracle java
```

You should be presented with several choices, one of which is "Oracle Java 7 Console" or something like that.

Otherwise, try this from the terminal

```
javaws -viewer
```

---

### Post by bill31 on 2014-03-12
Thank you to everyone who has helped me in these issues. I also have a problem installing Wine, however there may already be a sollution lurking around somewhere which I will try to find. Even so that is for another topic I do believe.

---

### Post by 3rdalbum on 2014-03-12
Stick with it, Bill. Ubuntu actually isn't hard to set up and use, but it's so different to Windows that it can take some time to adjust your thinking and really get to grips.

I struggle to set up a Windows machine but to you it is probably second nature.

---

