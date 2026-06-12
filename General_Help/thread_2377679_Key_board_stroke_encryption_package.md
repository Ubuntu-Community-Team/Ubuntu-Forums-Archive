---
title: "Key board stroke encryption package"
date: 2017-11-15
forum: General Help
---

### Post by pointy2 on 2017-11-15
Does one exist for Ubuntu Linux? I'm running AA 17.10 with plans to upgrade to 18.04 LTS when it's available from the repository. In doing a search, I haven't found a keyscrambler for Linux, however, many reuests for one. Perhaps that might be a project for a coder to tackle. 

Comments and suggestions are welcomed.

---

### Post by Kirboosy on 2017-11-16
It doesn't look like such a thing exists for Linux. I've looked around at many websites. Most people laugh at the idea or ask the greater question "Why would you need one in the first place?"

Hope that helps!
~Caboose

---

### Post by pointy2 on 2017-11-16
> **Caboose885 said:**
> It doesn't look like such a thing exists for Linux. I've looked around at many websites. Most people laugh at the idea or ask the greater question "Why would you need one in the first place?"

Hope that helps!
~Caboose

Doesn't that seem to be a fool hearted idea....that Linux is so secure that basic security isn't needed? Just a thought, and not intended to be sarcastic. There are alot of keyloggers in the wild, I know, because I've had a couple installed on my old Windows machine. It didn't take me long to find Keyscrambler for a cost of $40 or more per year... it was well worth it. 

Rootkits do exist for Linux, as I recall the first worm was written in UNIX code. While the great folks do wonders in the open source community, no one has told me why a Linux rootkit is makes reading keystrokes impossible.

---

### Post by Holger_Gehrke on 2017-11-17
Let me give you an analogy which might help you see why keystroke encryption is a waste of processing power:
Input handling is like a bucket chain, only with programs instead of people passing buckets and event data packets instead of buckets full of water. Current keyloggers are like watchers standing beside a specific point in the middle of the chain looking into the buckets. Keystroke encryption works by placing two additional people in the chain, one who puts a lid on the buckets passing through and another one just before the end of the chain who removes the lid again. Nothing stops the watcher from going to an earlier point in the chain or even to join the chain at an arbitrary point.
It's basically another arms race like the one with viruses and antivirus programs. It's an attempt to mitigate the consequences of a successful attack instead of stopping attackers.

Holger

---

### Post by Kirboosy on 2017-11-17
> **pointy2 said:**
> Doesn't that seem to be a fool hearted idea....that Linux is so secure that basic security isn't needed? Just a thought, and not intended to be sarcastic. There are alot of keyloggers in the wild, I know, because I've had a couple installed on my old Windows machine. It didn't take me long to find Keyscrambler for a cost of $40 or more per year... it was well worth it. 

Rootkits do exist for Linux, as I recall the first worm was written in UNIX code. While the great folks do wonders in the open source community, no one has told me why a Linux rootkit is makes reading keystrokes impossible.

I found this post. Very good information: [How can I detect a keylogger on my system?]("https://askubuntu.com/questions/169887/how-can-i-detect-a-keylogger-on-my-system")

The only keylogger that I have found for Linux is so far is [Logkeys]("https://github.com/kernc/logkeys"). It is available to install through the repositories on Ubuntu if you would like to play with it. I think playing with the software might help put your mind at ease. You will be able to come away with a better understanding of how keyloggers on Linux work.

---

### Post by pointy2 on 2017-11-17
> **Caboose885 said:**
> I found this post. Very good information: [How can I detect a keylogger on my system?]("https://askubuntu.com/questions/169887/how-can-i-detect-a-keylogger-on-my-system")

The only keylogger that I have found for Linux is so far is [Logkeys]("https://github.com/kernc/logkeys"). It is available to install through the repositories on Ubuntu if you would like to play with it. I think playing with the software might help put your mind at ease. You will be able to come away with a better understanding of how keyloggers on Linux work.

I'm reading the post now....thanks caboose for this link. As for Logkeys, I may just well dl and study the inards of the logger. While I haven't read abd dl'd as of yet, is it a fair uestion to ask that a black hat hacker could write his own code and sell it underground?The person (trusted, at the time) behind the previous attacks on Windows, could go anywhere for a keylogger and conceal it in emails and photos. The goal here is too make this computer highly resistant to such attacks.

---

