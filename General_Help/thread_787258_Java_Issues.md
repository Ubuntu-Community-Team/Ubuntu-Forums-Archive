---
title: "Java Issues"
date: 2008-05-08
forum: General Help
---

### Post by ahmedh on 2008-05-08
I performed a terminal installation according to the instructions on the Java website, and that didn't work, even after performing the follow up on getting applets to work in Firefox. Then I did an apt-get installation after reading a post on these forums, but that didn't work either. I've restarted Firefox after each installation and restarted my computer, but no luck. There's an item in the FF tools menu called "Java Console," but it is grayed out. Applets still don't load.

I checked about:plugins and it says Java is installed and gave no indication as to why it's not working. Any ideas guys? Thanks.

---

### Post by mardawi on 2008-05-08
I'm not sure i understand what you did, but this should work for you. Open a terminal and write
```
sudo apt-get insall sun-java6-plugin
```

---

### Post by Metaljaz on 2008-05-08
I had the same issue and after checking about:plugins java is installed. Firefox is having trouble finding the java. This is the link that I used to get java working in Firefox 3 beta 5. 

[http://ubuntuforums.org/showthread.php?p=4716149](http://ubuntuforums.org/showthread.php?p=4716149)

It says Firefox 2 but it worked for me with Hardy and Firefox 3 Beta 5. I just cut and pasted the commands in the terminal window. Worked like a charm.

---

### Post by ahmedh on 2008-05-08
I get this:
"E: Invalid operation install"

The problem is, I already installed Java. It didn't work either method. I used this: [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

And when that didn't work I tried the apt-get method.

---

### Post by ahmedh on 2008-05-08
Thanks for the link! Trying it now.

Edit: It didn't work. Now the "java console" item is not even present in the tools menu...

---

### Post by Metaljaz on 2008-05-08
In firefox if you type about : plugins in the address bar does it show java installed? If it does you should be okay with the thread that was provided. If it is not you may want to remove java and reinstall it then try the thread. 
When I used the commands provided in the thread I had not made any changes or reinstalls of java because it was already installed. Firefox was just having problems with it.

"there are no spaces between the words and the colon. I kept getting a smiley face instead of the colon and the p"

---

### Post by ahmedh on 2008-05-08
Yes, it is there.

No applets will load, though. In addons>plugins, it is not disabled, so I have no idea what the problem is.

---

### Post by ahmedh on 2008-05-08
If it helps, when I go to a page with an applet, it says in the status bar "Applet Loaded" and then it changes to "Start: applet not initialized."

---

### Post by Metaljaz on 2008-05-09
Try typing

sudo update-alternatives --config java

in a terminal and make sure that there is a * by the java-6-sun version.


Type this command in the terminal window and see what java you are using:

 java -version

---

