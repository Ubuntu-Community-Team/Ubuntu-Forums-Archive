---
title: "gnome removing password from keyring"
date: 2014-06-21
forum: General Help
---

### Post by Picek on 2014-06-21
Hi

I have a problem with evolution mail & gnome keyring which drives me nuts. Gnome keeps asking for password for my gmail account (but it remembers password for second account I use). It asks not only when I run Evolution but also every time I log in or reset gnome (eg using Alt+ F2 and typing 'r') or when I search for something in Monitor Activity mode (the thing you access with Super key).
Following [http://ubuntuforums.org/showthread.php?t=2211920 ]("http://ubuntuforums.org/showthread.php?t=2211920")was somehow helpful but every time I run Seahorse it shows that Gnome2 keyring is locked despite the fact that I have unlocked it. And the strangest thing: when I run evolution it asks for password, I type it and then it shows up in Seahorse. But after I reset gnome or press Super key & start typing anything a window pops up asking for password for Gmail account. Then (regardless of what I do: type it, press cancel, check or uncheck 'save in keyring') the password vanishes from Seahorse. 
I have not managed to find any additional information, nor anything interesting in system logs, especially no error messages in /var/log/auth.log

I use evolution 3.10.4, GNOME Shell 3.10.4 and gnome-keyring 3.10.4 and Ubuntu 14.04 LTS
I would appreciate any solutions or tips how to debug the problem

---

### Post by Picek on 2014-06-22
I hate self-bumping but someone must have at least idea where to seek for the error...

---

### Post by timotej2 on 2014-08-19
Hi!

I have the same problem - it's driving me crazy. I'm linux beginner so not able to solve problem, but I'm witing for someone to help. Seems to me like a bug...
Best regards, Tim

---

### Post by Briga on 2014-11-05
I don't have the exact same issues, similar in evolution but my seahorse is properly unlocked. 

What I do is delete every evolution entry in seahorse and for a while it works well (except that I have to re-enter the 9 different passwords for my 9 accounts!). 

Strangely it seems to get stucked with some specific accounts that apparently are no diffierent than others....

---

