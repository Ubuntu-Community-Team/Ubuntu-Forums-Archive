---
title: "Java vm"
date: 2008-05-31
forum: General Help
---

### Post by LaXBubbaMan on 2008-05-31
I am having trouble installing java vm. I cant seem to be able to get it to install into usr/java and run properly. I need it so that I can install 

sh ./thinkorswim_installer.sh

When I try to install this it tells me that I do not have java loaded.

---

### Post by SyL on 2008-05-31
To see if java is already installed just run *java *on a terminal.

If you have installed different version but you need a specific version for run your apps, then you can choose which version you will use with:
```
update-java-alternatives
```


If this is not installed, choose the one you want to install

```
sudo apt-cache search java
```
check which version is needed for your thinkorswim app (what is it BTW?) and install the correct jre


You might also like to install the ubuntu-restricted-extras package which contains java and many other stuff.
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by LaXBubbaMan on 2008-06-03
I have tried that and it doesn't work. I continue to get the same message. It does not seem to be seeing the the newest version of java on my computer. I was able to install sun java 5 console in add and remove programs but the shell file still doesn't load.

I will attached a screen shot of the error im getting.

As for the shell file it is for one of the best applications for trading stocks and options. It works amazing in windows but the linux version is being a pain in the butt.

---

### Post by kpkeerthi on 2008-06-03
You need to define INSTALL4J_JAVA_HOME environment variable and point it to where your JVM is installed.

If you have sun-java-5 already installed, it should be **/usr/lib/jvm/java-1.5.0-sun**. Make sure this folder exists or look in /usr/lib/jvm to confirm the folder name. 

Set the environment variable from command line with this command
```
export INSTALL4J_JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun
```
Now run your script file. 

If it works, add the above line to ~/.bashrc so the shell reads the variable everytime it is launched.

To set it system-wide, add it to /etc/environment.

---

### Post by LaXBubbaMan on 2008-06-03
Thanks

I was able to get it installed and running but I didn't follow what you wanted me to do to with the other stuff. Where do I need to add those things so I do have to worry about it later.

---

### Post by kpkeerthi on 2008-06-09
> **LaXBubbaMan said:**
> Thanks

I was able to get it installed and running but I didn't follow what you wanted me to do to with the other stuff. Where do I need to add those things so I do have to worry about it later.

You need to add the line in .bashrc or /etc/environment like I mentioned in the last post.

---

### Post by LaXBubbaMan on 2008-06-10
Where do I need to add that in?

---

### Post by SyL on 2008-06-10
> **LaXBubbaMan said:**
> Where do I need to add that in?


As kpkeerthi said, you could either add it in: 
1. your home directory in the file .bashrc, if there is only your user using this application
2. in  /etc/environment if there is different users using this application

---

### Post by LaXBubbaMan on 2008-06-11
Do I just type that in after I export than file or do I need to add it to the export command in some way?

---

### Post by SyL on 2008-06-12
Hi,

```
sudo gedit ~/.bashrc
```add at the end of the file: 

```
export INSTALL4J_JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun
```





that's it

---

### Post by Pjotr123 on 2008-06-12
This is the easy way:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

---

