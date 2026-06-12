---
title: "Just installed Ubuntu - need Java JRE help"
date: 2007-05-18
forum: General Help
---

### Post by Cloudedbrains on 2007-05-18
Help I just installed Ubuntu today (via Wubi) and am trying to get JRE (java runtime environment) working as it is needed for a chatroom and broadband speedtest website I use :(

I've downloaded it but how do I install it :confused:

This is one website I need to access and cant :mad:

[http://speedtester.bt.com/](http://speedtester.bt.com/)

Help I need really easy basic instructions to get JRE working :)

I've got the manual download file but what on earth do I do with it :(

---

### Post by taurus on 2007-05-18
Use this guide to install java.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by IgnorantGuru on 2007-05-18
You don't need that file.  For Sun java just go into a terminal and type:
```
sudo apt-get install sun-java6-jre
```
Use tab enter to press OK, and left-arrow enter to select Yes.

If you use Firefox, then create a link to it:
```
ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so
```

---

### Post by mikewhatever on 2007-05-18
If you have internet connection try > sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by Cloudedbrains on 2007-05-18
> **taurus said:**
> Use this guide to install java.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Looking at that I dont have "Software Properties" listed :confused:

---

### Post by Cloudedbrains on 2007-05-18
> **IgnorantGuru said:**
> You don't need that file.  For Sun java just go into a terminal and type:
```
sudo apt-get install sun-java6-jre
```
Use tab enter to press OK, and left-arrow enter to select Yes.

If you use Firefox, then create a link to it:
```
ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so
```

Tried the first thing and it seemed to work in the terminal thing but its still wanting me to download the manual java plugin (firefox 2) when I goto either the websites I need to use java on :o

---

### Post by IgnorantGuru on 2007-05-18
Did you create the link to the plugin and restart Firefox?

In firefox visit this URL:
```
about:plugins
```
 and see if Java is listed.

---

### Post by zvacet on 2007-05-18
Java is in synaptic.Type sun in search box and pick wich java you want.And yes,you have to make link as Cloudedbrains told you.

---

### Post by Cloudedbrains on 2007-05-18
How do I make the link ???

According to system/prefernces/ Java is listed there but NOWHERE else !!!

Everytime I goto either the website with the java chatromm or the site linked to earlier it wants me to install Java !!!

[IMG]http://i112.photobucket.com/albums/n200/Cloudedbrains/Screenshot.png[/IMG]

I need simple STEP-by-STEP instructions on how to get this stupid Java to work !!

---

### Post by IgnorantGuru on 2007-05-18
You make the link with
```
sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so
```

I forgot the sudo above so maybe that's why it didn't work if you tried it.

Then restart firefox.

---

### Post by Cloudedbrains on 2007-05-18
Have solved it - had to add the repositries a different way and I have now got it up and running :)

applications
add/remove
preferences
third party software
then added the two repositries on this screenshot below
then downloaded the java runtime I needed
bingo up and running


[IMG]http://i112.photobucket.com/albums/n200/Cloudedbrains/Screenshot-1.png[/IMG]

---

