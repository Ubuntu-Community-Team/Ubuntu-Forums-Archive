---
title: "Can't access www.wsistudents.com private areas. Asks for Java Virtual Machine!"
date: 2007-05-30
forum: General Help
---

### Post by darkmaster on 2007-05-30
Hello everyone, I already know nobody's going to help me on this.
I cannot acess to a site I use for work from Ubuntu using Firefox or Konqueror, nothing changes. I visit:
[http://www.wsistudents.com/](http://www.wsistudents.com/)
and Login. Then appears a page where I choose "English anytime" and then "My COurse".
At that point, another window opens with the following error:

> Client browser unable to communicate with server - missing JVM.\nYou will need either Sun (or) Microsoft Virtual Machine.\nPlease contact administrator.

What could I do? None of you are probably subscribed to this service, that's why I think it will be hard for anyone to help me but... is it legal to post the code of the page here? From the code there is described the function that stops me from viewing the java content of the page. It only works in IE7 and IE7 doesn't work on my PC with Wine or anything but I also closed with Windows, so, I don't want to use is in any case. 

please, anyone, any idea, help me, please.....

P.S.: I also tryed with IETAB for Firefox but it tells me that it needs a plugin and then that it is impossibile to find the plugin... guess it looks for plugins to install into a firefox running in windows, damnit.....

---

### Post by odiseo77 on 2007-05-30
I'm not sure because I haven't entered to this site, but it seems to me you don't have the Sun JVM and its browser plugin installed (and/or configured). Try the following:

```
sudo apt-get install sun-java5-jre sun-java5-plugin
```

After these packages are installed, execute:

```
sudo update-alternatives --config java
```

You'll get several JVM's, type the number for Sun's JVM and hit enter. Then open firefox and retry accessing the web site you mention above. If it's just a problem with the java plugin not installed, the previous seteps should solve it.

Regards.

---

### Post by darkmaster on 2007-06-02
> **odiseo77 said:**
> I'm not sure because I haven't entered to this site, but it seems to me you don't have the Sun JVM and its browser plugin installed (and/or configured). Try the following:

```
sudo apt-get install sun-java5-jre sun-java5-plugin
```

After these packages are installed, execute:

```
sudo update-alternatives --config java
```

You'll get several JVM's, type the number for Sun's JVM and hit enter. Then open firefox and retry accessing the web site you mention above. If it's just a problem with the java plugin not installed, the previous seteps should solve it.

Regards.

Java and the plugin where already installed. I tryed switching between one java solution and another but it didn't change anithing... that was not the problem. It doesn't work. Then again, is it legal to post here the page code? Could it be helpfull for someone to understand my problem?

---

### Post by dns on 2007-08-06
Let me confirm that your problems are not due to any installed JRE version, but simply the fact that wsistudents.com runs a whole bunch of carefull crafted IE-only code.

I'm not associated with the site maintainers in any way. My wife is currently taking courses with them, after we have repeatedly been assured that it's gonna be all web-based and her iBook should work just fine.

Just working out what the issues are. So far it is mostly a particularly poor HTML and JavaScript coding. I will report back once I know more.

---

### Post by cypress.cynthia on 2007-08-13
Hello, according to [this site]("http://packages.ubuntu.com/feisty/virtual/java-virtual-machine") the following packages provide Java Virtual Machine for Ubuntu Linux: jamvm, sablevm. All you have to do is to download and install them. I hope this helps you.

---

### Post by darkmaster on 2007-08-20
> **cypress.cynthia said:**
> Hello, according to [this site]("http://packages.ubuntu.com/feisty/virtual/java-virtual-machine") the following packages provide Java Virtual Machine for Ubuntu Linux: jamvm, sablevm. All you have to do is to download and install them. I hope this helps you.

Hi! Thank you for the answer, I'll try it soon!

---

### Post by cypress.cynthia on 2007-08-20
You're welcome. Let me know if it works. :-D

---

### Post by cypress.cynthia on 2007-09-29
Hello again, I've finally figured out how to install Java Virtual Machine in Ubuntu. Just follow the instructions posted below. I hope you'll find find them useful, in case you didn't install it. :grin: These instructions are based on those posted in Spanish [here]("http://jroliva.wordpress.com/2007/02/08/java-virtual-machine-para-firefox-en-ubuntu-dapper/").

cd /usr
sudo mkdir java
or just type
cd /usr/java
if that directory already exists 
now you have to dowload the latest Java (in this case, jre-6u2-linux-i586.bin) from [the Java site]("http://java.com/en/download/linux_manual.jsp") to this directory 
sudo chmod a+x jre-6u2-linux-i586.bin
sudo ./jre-6u2-linux-i586.bin

when the licence appears in the terminal, all you have to do is to press "q", and then type "yes" and press Enter in order to accept it. And you're done. Now, in order to use it in Firefox you have to follow these instructions:    

cd /usr/lib/firefox/plugins
sudo ln -s /usr/java/jre1.6.0_02/plugin/i386/ns7/libjavaplugin_oji.so
restart the browser

That's it! Now I hope you can access that site. :)

P.S. You can test the installation by visiting [this site]("http://java.com/en/download/help/testvm.xml").

---

