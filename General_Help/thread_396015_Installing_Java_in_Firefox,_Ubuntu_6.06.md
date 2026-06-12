---
title: "Installing Java in Firefox, Ubuntu 6.06"
date: 2007-03-28
forum: General Help
---

### Post by manqueller on 2007-03-28
I've gone to the Java site and downloaded the Self Extracting file for Linux and that didn't work, so I went to Applications, Add/Remove and found Java there and installed that way, still if I go to any sites the Java doesn't work.  I'm using Firefox 2.0 and Ubuntu 6.06.  

I did reboot the browser, and then the whole system after the install.  Am I doing someting wrong?

---

### Post by aysiu on 2007-03-28
This will help you:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by zvacet on 2007-03-29
Probably you ned to install plugin.
[http://java.com/en/download/help/5000010500.xml]("http://java.com/en/download/help/5000010500.xml")

---

### Post by manqueller on 2007-04-15
> **aysiu said:**
> This will help you:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

In there I read that I must first enable the multiverse repository, so I followed the link on how to do that.  I ended up here:  [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
and I went to System Administration Software Properties and there added Universe and Multiverse properties.  Then (if you scroll down at the same URL) I went to the Synaptic package manager and added this repository: [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

The problem I'm having now is that When I go to Synaptic it tells me that the list of sources could not be read and it refrences [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main in etc/apt/sources.list so I figured I'll just go to sources.list and remove that line.  However, when I go to Places Computer and navigate to etc/apt/sources.list and when I try to save the file after removing the URL It tells me that  I don't have permissions to save.

How do I open sources.list as root?

---

### Post by Maestro23 on 2007-04-15
Edit in terminal. You need "sudo" in front of your command.  What editor are you using?  gedit, nano....

Open up a terminal:

> gksudo gedit /etc/apt/sources.list

Make your changes and save.

More info on sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by manqueller on 2007-04-26
> **Maestro23 said:**
> Edit in terminal. You need "sudo" in front of your command.  What editor are you using?  gedit, nano....

Open up a terminal:



Make your changes and save.

More info on sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thanks!  That let me in so that I could save the changes and now I have access to the repositories again.

---

### Post by pdizzyd on 2007-04-27
Have you created a symbolic link in the mozilla-firefox/plugins directory. After the Java install you still need to place a sym link in the plugins dir

Make sure these are your install dirs, 

~$ cd /usr/lib/mozilla-firefox/plugins

~$ ln -s <path to java jre>/libjavaplugin_oji.so ./libjavaplugin_oji.so

Restart the browser if open.

---

