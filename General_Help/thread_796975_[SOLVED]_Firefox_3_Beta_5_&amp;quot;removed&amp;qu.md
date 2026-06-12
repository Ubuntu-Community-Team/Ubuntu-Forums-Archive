---
title: "[SOLVED] Firefox 3 Beta 5 &amp;quot;removed&amp;quot;, can't install or open Firefox 2 or 3..."
date: 2008-05-16
forum: General Help
---

### Post by Jordinho on 2008-05-16
I removed Firefox 2 by accident when trying to remove Firefox 3 using the terminal (sudo apt-get remove firefox). Then I uninstalled Firefox 3 Beta 5 by [_deleteing the folder_]("http://support.mozilla.com/en-US/kb/Uninstalling+Firefox"). Now I go through this sequence of nonsense to install any kind of Firefox on my computer:

```

k@Ubuntu:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
k@Ubuntu:~$ sudo apt-get install firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
k@Ubuntu:~$ firefox-3.0
The program 'firefox-3.0' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox-3.0: command not found
k@Ubuntu:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
k@Ubuntu:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
k@Ubuntu:~$ 

```

Questions:

How do I install Firefox 2 using aptitude?
How do I install Firefox 3 again if that fails?

Thanks.

Edit: All of this in Hardy Heron of course.

---

### Post by mikewhatever on 2008-05-17
Try <locate firefox> to make sure it's been uninstalled.

---

### Post by Bubba64 on 2008-05-17
> **Jordinho said:**
> I removed Firefox 2 by accident when trying to remove Firefox 3 using the terminal (sudo apt-get remove firefox). Then I uninstalled Firefox 3 Beta 5 by [_deleteing the folder_]("http://support.mozilla.com/en-US/kb/Uninstalling+Firefox"). Now I go through this sequence of nonsense to install any kind of Firefox on my computer:

```

k@Ubuntu:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
k@Ubuntu:~$ sudo apt-get install firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
k@Ubuntu:~$ firefox-3.0
The program 'firefox-3.0' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox-3.0: command not found
k@Ubuntu:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
k@Ubuntu:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
k@Ubuntu:~$ 

```

Questions:

How do I install Firefox 2 using aptitude?
How do I install Firefox 3 again if that fails?

Thanks.

Edit: All of this in Hardy Heron of course.

Both FF 2-3 are in synaptic I would look there to see if anything is installed but not showing or just install what you need. Using the terminal at times by itself without checking synaptic can make things more difficult. If you want to install you need to run an update before install in the terminal.

---

### Post by Jordinho on 2008-05-21
> **Bubba64 said:**
> Both FF 2-3 are in synaptic I would look there to see if anything is installed but not showing or just install what you need. Using the terminal at times by itself without checking synaptic can make things more difficult. If you want to install you need to run an update before install in the terminal.

Yeah, I just used Synaptic to reinstall firefox 3 and uninstall 2. I should use it more often actually. Thanks for the help!

---

