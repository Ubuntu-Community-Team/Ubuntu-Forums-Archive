---
title: "Java JRE and JDK automation"
date: 2007-06-18
forum: General Help
---

### Post by stchman on 2007-06-18
Hello all I am creating some scripts to automate the install of various applications.  Using the -y switch for apt-get works very well until I try to install Java.  Here is the command I use to install Java:

sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin

During the install Java prompts the user to agree to the terms.  Is there a way to agree to the terms from the command line for example sun-java5-jre --agree?  I believe it is the sun-java5-jre asking for this.

Thanks.

---

### Post by zvacet on 2007-06-18
No,you have to scroll down with space and then hit tab and eter I belive.I don´t understand why don´t you download Java with synaptic if you need exact that version or 

> Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.

This will install latest Java and other things you need.

---

### Post by stchman on 2007-06-18
> **zvacet said:**
> No,you have to scroll down with space and then hit tab and eter I belive.I don´t understand why don´t you download Java with synaptic if you need exact that version or 



This will install latest Java and other things you need.

I am writing a script that installs applications and Java is one of them.  I would like the script to run unattended once it is launched.

---

