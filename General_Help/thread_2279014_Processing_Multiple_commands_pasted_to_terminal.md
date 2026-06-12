---
title: "Processing Multiple commands pasted to terminal"
date: 2015-05-20
forum: General Help
---

### Post by mistrblank2 on 2015-05-20
So I had a system that was running Ubuntu 10.04.  I went through the process of upgrading it to 14.04 recently.  I use this particular host (it's actually a vm on a virtual box instance) as a jump server to all of the 300 or so hosts that I manage.  Often if I needed to execute a command on multiple hosts I would quickly build a set of commands in notepad++ and copy from that window into my terminal and let it serially execute the commands.  Now when I try to do that, it executes exactly one line of code and stops processing the paste which is entirely frustrating. 

No, I don't want to copy and paste into a script that I will execute all at once.  I want to be able to copy blocks of code and execute to my choosing because saving to a file is adding extra steps, particularly when I have to go back and figure out if a command didn't execute.  

It happens when I'm native on the host using gnome-terminal, if I'm using gnome-terminal, or if I'm using putty or the older version of the SSH Tectia Client.  So it might be shell related.   Any help would be appreciated.

---

### Post by mistrblank2 on 2015-05-20
also of note, it only seems to happen when I execute multiple ssh commands.  Local commands seem to execute as expected.

---

### Post by steeldriver on 2015-05-20
Some specific examples might be helpful - are you trying to run sequential *interactive* SSH sessions?

---

### Post by dragonfly41 on 2015-05-20
I'm not sure if clusterssh might be useful for 300 hosts to manage .. it is in Ubuntu Software Centre.

[http://sourceforge.net/projects/clusterssh/](http://sourceforge.net/projects/clusterssh/)

---

### Post by HermanAB on 2015-05-20
Cluster SSH, Parallel SSH, Puppet...

Otherwise separate the commands by semi colons, not CR/LF.

---

### Post by mistrblank2 on 2015-05-20
I'm not interested in other frameworks or solutions.  It won't help achieve this one goal.
I do use dsh already in many circumstances.   My issue is more with successive repetitive command calls and being able to build them quick within a code editor (in my case I use notepad++).

I'm pretty much afraid at this point I'm just going to have to roll back to the old version of the jump system and live on 10.04 unsupported (which I'm going to have a fight on my hands to keep with my CISO).

implementing semicolons and single line presents the same problem as putting them into a script and executing the script.  It also eliminates the advantage of column editing that I actively use in Notepad++ to quickly build command lists.

---

### Post by Keith_Helms on 2015-05-20
> **mistrblank2 said:**
> 
implementing semicolons and single line presents the same problem as putting them into a script and executing the script.  It also eliminates the advantage of column editing that I actively use in Notepad++ to quickly build command lists.

Possibly dumb idea here, but try leaving the commands on multiple lines as you have them now, but stick a semicolon on the end of each line.  It could be that somehow the lines are all being combined and treated as one command instead of several.

---

### Post by HermanAB on 2015-05-20
Hmm, it sounds to me that you have a CR/LF issue with notepad++.

Are you sure the lines are terminated with LF only and not CR and LF?

You may have to paste into hexedit to see.

---

### Post by SeijiSensei on 2015-05-20
> **HermanAB said:**
> Hmm, it sounds to me that you have a CR/LF issue with notepad++.

Are you sure the lines are terminated with LF only and not CR and LF?

You may have to paste into hexedit to see.

Have you tried doing this on a Linux box with a native editor like gedit or emacs rather than notepad++?

---

### Post by mistrblank2 on 2015-05-22
> **SeijiSensei said:**
> Have you tried doing this on a Linux box with a native editor like gedit or emacs rather than notepad++?

Yes, natively in a gui session with the host.  Has the same issue when I paste into the local gnome-terminal or xterm.   It's got to be something in the way bash is processing.

---

