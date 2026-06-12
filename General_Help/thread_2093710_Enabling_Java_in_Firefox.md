---
title: "Enabling Java in Firefox"
date: 2012-12-11
forum: General Help
---

### Post by Robert R on 2012-12-11
According to java.com to enable java for firefox do the following:

problem is that i have no clue where firefox is installed by default,

Can anyone help? 

> **Enable and Configure**

 **Firefox or Mozilla**

 To configure the Java Plugin follow these steps:  
[LIST=1]
[*]**Exit Firefox browser if it is already running.**
[*]**Uninstall any previous installations of Java Plugin.**
Only one Java Plugin can be used at a time. When you want to use a  different plugin, or version of a plugin, remove the symbolic links to  any other versions and create a fresh symbolic link to the new one.
[*]**Create a symbolic link to the libnpjp2.so file in the browser plugins directory**
[LIST]
[*]Go to the plugins sub-directory under the Firefox installation directory
	cd <*Firefox installation directory*>/plugins
[*]Create the symbolic link 
	ln -s <*Java installation directory*>/lib/i386/libnpjp2.so
[/LIST]
[/LIST]


---

### Post by Abhinav Kumar on 2012-12-11
> **Robert R said:**
> According to java.com to enable java for firefox do the following:

problem is that i have no clue where firefox is installed by default,

Can anyone help?
Hi Robert R,

Firefox directory is generally 
/usr/lib/mozilla/

Just cd to the directory and you can see there is a plugins folder in it.

You can also know the directory of mozilla by typing the following code in terminal
```
sudo find / -name 'firefox' -type d | more
```

Visit the following link 
[http://kb.mozillazine.org/Determining_plugin_directory_on_Linux](http://kb.mozillazine.org/Determining_plugin_directory_on_Linux)

Regards,
Abhinav

---

### Post by Pjotr123 on 2012-12-11
This is a complete and easy how-to:
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

Easy as can be.... :)

---

### Post by Buntu Bunny on 2012-12-11
> **Pjotr123 said:**
> This is a complete and easy how-to:
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

Easy as can be.... :)

I'd like to toss my thanks for this into the ring. Great website BTW.

---

### Post by Robert R on 2012-12-12
Thanks this works and the command is also very helpful, thanks all for your help. :)

---

### Post by Abhinav Kumar on 2012-12-12
> **Robert R said:**
> Thanks this works and the command is also very helpful, thanks all for your help. :)
Glad it worked for you.:)

Please mark the thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Abhinav

---

