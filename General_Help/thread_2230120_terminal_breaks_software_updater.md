---
title: "terminal breaks software updater"
date: 2014-06-17
forum: General Help
---

### Post by jjclonker on 2014-06-17
First I open a terminal and type the command "sudo apt-get update".
Internet may have cut out during update.

Second after waiting for the terminal to finish.
I open software updater. It opens, but only a blank(white with standard ext, minimize and maximize symbols) bocks.
There is no way to update using my software updater now.

Third I shut down and restart. The problem persist.

A similar problem has occurred on ubuntu version 12.04 and now with 14.04.

Thanks for any future help. :)

---

### Post by Bucky Ball on 2014-06-17
What is the problem, exactly? You update via a terminal then open Software Updater and it finds nothing to update. Probably because you just updated. 

Open a terminal and input these three commands:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

You're done. This will NOT upgrade your release to the next available, it will upgrade any software in your current install that needs it. Software Updater is basically a frontend GUI for apt-get update in the terminal. That's happening behind the scenes. I prefer the terminal so I can see what's happening. 

Next time the symbol comes up notifying you of updates, if you update in a terminal instead of using the GUI, the symbol will go away if you input those three commands. The GUI sometimes pops up during the process. 

Launch Software Updater from a terminal with 'gksudo software-updater' or whatever the terminal command for it is, and see the output of the terminal.

---

### Post by jjclonker on 2014-06-17
Ok. Sorry about my vague description.

The software updater (GUI) is broken. It only shows a white bocks no buttons except for the ext, etc...
The problem is I want to use the GUI software updater, because for me it is more user friendly, not the terminal, and  it is nonfunctional as stated above.

gksudo software-updater did not work for opening it in the terminal. :/

What now?

---

### Post by Bucky Ball on 2014-06-17
So you can update fine in a terminal? Please run those three commands I gave in my last post and report back any errors. If there are none, try the Software Updater again.

---

### Post by jjclonker on 2014-06-17
So far those commands seem to be working. I will let you know if there are any problems there.
However the software updater using the GUI has more options such as you can select the downloads that you want. (For slow Internet this is really useful.)
And it continues your progress if it fails... I think the terminal saves progress as well right?

---

### Post by kansasnoob on 2014-06-17
> **Bucky Ball said:**
> What is the problem, exactly? You update via a terminal then open Software Updater and it finds nothing to update. Probably because you just updated. 

Open a terminal and input these three commands:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

You're done. This will NOT upgrade your release to the next available, it will upgrade any software in your current install that needs it. Software Updater is basically a frontend GUI for apt-get update in the terminal. That's happening behind the scenes. I prefer the terminal so I can see what's happening. 

Next time the symbol comes up notifying you of updates, if you update in a terminal instead of using the GUI, the symbol will go away if you input those three commands. The GUI sometimes pops up during the process. 

Launch Software Updater from a terminal with '**[COLOR="#FF0000"]gksudo software-updater[/COLOR]**' or whatever the terminal command for it is, and see the output of the terminal.

Hi Bucky Ball, the package name is still 'update-manager'. The GNOME devs just like playing tricks on our minds :)

---

### Post by kansasnoob on 2014-06-17
> **jjclonker said:**
> So far those commands seem to be working. I will let you know if there are any problems there.
However the software updater using the GUI has more options such as you can select the downloads that you want. (For slow Internet this is really useful.)
And it continues your progress if it fails... I think the terminal saves progress as well right?

Should look like this when fully updated:

[ATTACH=CONFIG]254020[/ATTACH]

If not you may want to run:

```
sudo apt-get update
```

```
sudo apt-get -f install
```

That may show missing dependencies or broken packages.

---

### Post by jjclonker on 2014-06-17
Ok. I tried opening software-manager in the terminal, and it gave no input whatsoever, and it is still a white box. :( I am trying 'sudo apt-get update now'.

---

### Post by Bucky Ball on 2014-06-17
Try:

```
gksudo update-manager
```

... as suggested by kansasnoob. That is the correct terminal command. (Thanks for the 'rectification' kansasnoob. ;))

---

### Post by jjclonker on 2014-06-17
More bad news... I ran 'sudo apt-get update', and it gave me this.  zerg@zerg-Latitude-D610:~$ sudo apt-get update [sudo] password for zerg:  Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                        Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]            Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                      Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                   Could not resolve 'extras.ubuntu.com' Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) trusty InRelease                  Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) trusty-updates InRelease          Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) trusty-backports InRelease        Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) trusty Release.gpg               Could not resolve 'br.archive.ubuntu.com' Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) trusty-updates Release.gpg   Could not resolve 'br.archive.ubuntu.com' Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) trusty-backports Release.gpg   Could not resolve 'br.archive.ubuntu.com' Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [58,5 kB]              Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [17,9 kB]         Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]      Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [4.727 B]     Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [688 B]     Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [53,4 kB]   Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B] Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [19,3 kB] Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1.392 B] Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en              Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US Fetched 157 kB in 3min 44s (697 B/s) Reading package lists... Done W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/trusty/InRelease](http://br.archive.ubuntu.com/ubuntu/dists/trusty/InRelease)    W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://br.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)    W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease](http://br.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease)    W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease](http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease)    W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'extras.ubuntu.com'  W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://br.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'br.archive.ubuntu.com'  W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg](http://br.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg)  Could not resolve 'br.archive.ubuntu.com'  W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg](http://br.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg)  Could not resolve 'br.archive.ubuntu.com'  W: Some index files failed to download. They have been ignored, or old ones used instead. zerg@zerg-Latitude-D610:~$    PS: Sorry about the formatting. Something broke on the ubuntu forums and I can't put it in code format.

---

### Post by Bucky Ball on 2014-06-17
Please use [code] tags for terminal output. Keeps it clear and easy to read. That is virtually unreadable as there is no formatting. The black and red blob! :-k

Have you installed any PPAs manually? 

* Oh, just saw the last bit of your post. Please add [code] tags manually.

---

### Post by jjclonker on 2014-06-17
I restarted my computer again and now software updater is working again.  Well that was wierd... :/  Thanks for the help. I guess this is solved?

---

