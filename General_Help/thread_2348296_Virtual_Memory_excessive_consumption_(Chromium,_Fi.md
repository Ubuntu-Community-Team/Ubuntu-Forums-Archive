---
title: "Virtual Memory excessive consumption (Chromium, Firefox, etc.)"
date: 2017-01-02
forum: General Help
---

### Post by cest2 on 2017-01-02
Hello,

I'm not an expert but I have the feeling my PC is using too much Virtual Memory. Please check the attached screenshot of the Task Manager. I also don't understand why are there 5 instances of Chromium while I'm using only 1 with 2 tabs open (in the same instance).

I'm using Lubuntu 16.04.1 LTS with 2GB RAM.

Any help would be highly appreciated, thank you!

---

### Post by dragonfly41 on 2017-01-02
If you click on top right View and select
All Processes
and tick Dependencies

you will see a tree structure of processes.

In Chromium there is one entry per tab open, plus parent processes.

I try to reduce tab count by using OneTab and SessionBuddy add-ons for Chromium.

It gobbles up memory.   Why do you have both Firefox and Chromium open?
I see only 2 GB of RAM which may be a problem if you have too many processes running.
View the Resources tab to see memory usage.

[Later edit]
Sorry. I see that you have Task Manager open.  I am describing System Monitor found under System Tools.

---

### Post by cest2 on 2017-01-03
Hi, I'm using Firefox for other purposes. In Chromium I had only 2 tabs opened, why is the Task Manager showing 7 processes? Even soffice.bin is using too much Virtual Memory: 1GB for a simple text document opened. Is that normal? Is there anything I can do about it?
Thank you :)

---

### Post by dragonfly41 on 2017-01-03
> [COLOR=#000000]Is there anything I can do about it?[/COLOR][COLOR=#000000]

[/COLOR](a) Buy more RAM .. say double your 2 GB to 4 GB?

(b) Don't run two processes together if you don't need them (e.g. two browsers running concurrently).
      Put one to sleep.

(c) As explained, there are other parent processes running.  
I've looked at my Chromium in System Monitor and it seems to be 5+n where n=number of open tabs.

(d) Use tab managers as suggested (OneTab, SessionBuddy, search around in Chromium repo).

(e) Don't use memory hogging LibreOffice for simple text files when you can use say gedit, geany or simpler editors.
I use cherrytree a lot for notes.

(f) Only launch Thunderbird when you need it.

[Later edit]

This might help to explain columns in Task Manager.

[https://www.quora.com/What-does-rss-in-the-task-manager-program-of-xubuntu-stand-for](https://www.quora.com/What-does-rss-in-the-task-manager-program-of-xubuntu-stand-for)

In System Monitor there is no VM column.

---

### Post by cest2 on 2017-01-07
> **dragonfly41 said:**
> 
(a) Buy more RAM .. say double your 2 GB to 4 GB?[COLOR=#000000]
[/COLOR]

[COLOR=#000000]Thank you, I think I will have to make a complete upgrade of my PC :)
[/COLOR]
> **dragonfly41 said:**
> 
(d) Use tab managers as suggested (OneTab, SessionBuddy, search around in Chromium repo).[COLOR=#000000]
[/COLOR]

I started using OneTab and the PC seems to be moving faster.

> **dragonfly41 said:**
> 
(e) Don't use memory hogging LibreOffice for simple text files when you can use say gedit, geany or simpler editors.
I use cherrytree a lot for notes.[COLOR=#000000]
[/COLOR]

For some reason I cannot install cherrytree or Abiword. I'll probably open another topic for this issue.

Thank you very much for your help and your hints, they are all helpful!

---

### Post by dragonfly41 on 2017-01-07
Abiword is a good choice and a useful feature is its command line API for document conversion.

Here are installation instructions .. [https://www.howtoinoadedstall.co/en/ubuntu/xenial/abiword](https://www.howtoinoadedstall.co/en/ubuntu/xenial/abiword)

But you should have Geany and Gedit already installed as alternative editors.  Another is Atom.

CherryTree .. [http://www.giuspen.com/cherrytree/](http://www.giuspen.com/cherrytree/) .. can be downloaded and placed in say /opt/ directory. There are instructions on its website for running.
It offers a tree structure for notes and rdf snippets.

You might find this link helpful for configuring older generation computers.
[URL="https://ubuntuforums.org/showthread.php?t=2130640"]
https://ubuntuforums.org/showthread.php?t=2130640[/URL]

---

### Post by cest2 on 2017-01-08
I managed to install Abiword and it's working fine. It consumes 800 MB of VM but out of all the options is the one that resembles Word the best.
Thank you very much, you've been very helpful! And also thank you for the link about configuring older generation computers! \\:D/

---

### Post by Kevin McCready on 2017-10-16
I prefer Sublime Text as editor.

I am also having memory problems. I suspect firefox. System Monitor reports usage of up to 144% CPU.  How can that be?? Please help. My system=
 k-Lenovo-H50-55 Kernel: 4.4.0-21-generic i686 (32 bit) Desktop: MATE 1.14.1           Distro: Linux Mint 18 Sarah

I'm sorry, I don't know the terminal command to list the memory information that I see when I click on the system tab of the System Monitor.

Grateful for any help.

---

