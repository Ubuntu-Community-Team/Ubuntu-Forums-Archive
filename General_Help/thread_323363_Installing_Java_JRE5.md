---
title: "Installing Java JRE5"
date: 2006-12-22
forum: General Help
---

### Post by Scottty on 2006-12-22
Hi Guys

I downloaded the self extracting file jre-1_5_0_10-linux-i586.bin
and I want to install it, How do I do that?
I used Add/Remove and installed the java plugin
and installed the Sun Java plugin 1.4 and I've also 
installe the Sun Java Runtime 5.0 but still I'm unable to view my java 
in my website. So I thought I would try and install from the self extracting file.
Am I doing the right thing??

Thanks
Scott

---

### Post by bruenig on 2006-12-22
> **Scottty said:**
> Hi Guys

I downloaded the self extracting file jre-1_5_0_10-linux-i586.bin
and I want to install it, How do I do that?
I used Add/Remove and installed the java plugin
and installed the Sun Java plugin 1.4 and I've also 
installe the Sun Java Runtime 5.0 but still I'm unable to view my java 
in my website. So I thought I would try and install from the self extracting file.
Am I doing the right thing??

Thanks
Scott

Remove all of that stuff you installed. And open the terminal and do the following:
```
sudo apt-get install sun-java5-bin sun-java5-plugin
```

---

### Post by Scottty on 2006-12-22
Hello

I did exactly what you told me to do and it seemed to install fine from the terminal
however when I open an instance of firefox I still can't see java. Do I need to reboot?
or is there something else?

Thanks
scott

---

### Post by taurus on 2006-12-22
In the address field of firefox, do you see java plugin with this command?

```
about:plugins
```

p.s.  Remember, you need to restart firefox after you installed java...

---

### Post by matchstich on 2006-12-22
how do i answer yes to the questions when installing the java plug in, thanks

---

### Post by Scottty on 2006-12-22
This is what I have when I type in the addres bar about:plugins
> 
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;jpi-version=1.5.0_08 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;jpi-version=1.5.0_08 	Java 		Yes



But I still can't see my java-applets working in firefox. I restarted Firefox but I didn't restart my system. What do you think?

thanks
Scott

---

### Post by taurus on 2006-12-22
How about 

```
java -version
```
Now, what websites that you don't see the java stuff?

---

### Post by bruenig on 2006-12-22
> **matchstich said:**
> how do i answer yes to the questions when installing the java plug in, thanks

Press the tab button to select the "yes" or "ok" or whatever it is. Then use enter.

---

### Post by Scottty on 2006-12-22
I typed in java -version and got the following

```

user@user-desktop:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)
scott@scott-desktop:~$ 


```

I would post the website but it's of a personel medical nature.

I can tell you I put two applets on the website as a counter and one displays the time and they
both don't come up.

At the same time I went to the java.sun.com page and they had dynamic content on their webpage. I'm assuming they would use java applets.

---

### Post by taurus on 2006-12-22
Are you sure it's java and not flash???

---

### Post by bollix47 on 2006-12-22
Try running

```
sudo update-alternatives --config java
```

and selecting Sun.

Also, you can check your site at [http://validator.w3.org/](http://validator.w3.org/)

---

### Post by bruenig on 2006-12-22
> **Scottty said:**
> I typed in java -version and got the following

```

user@user-desktop:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)
scott@scott-desktop:~$ 


```

I would post the website but it's of a personel medical nature.

I can tell you I put two applets on the website as a counter and one displays the time and they
both don't come up.

At the same time I went to the java.sun.com page and they had dynamic content on their webpage. I'm assuming they would use java applets.

You did not install correctly or remove the other stuff first. If you had installed sun-java5-bin and sun-java5-plugin, you should have gotten
```
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
```
Not saying that this is the reason that your java doesn't work, seems like 1.4 would probably still work.

---

### Post by RJ Hythloday on 2008-01-13
> **bruenig said:**
> Press the tab button to select the "yes" or "ok" or whatever it is. Then use enter.

Thanks, I was stuck and that was what I was looking for. :KS

---

