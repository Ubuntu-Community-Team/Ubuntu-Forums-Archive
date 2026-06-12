---
title: "GRSYNC - Won't run to Remote Server, under Ubuntu 18.04LTS"
date: 2018-10-31
forum: General Help
---

### Post by rbscycle on 2018-10-31
GRSYNC won't run on Ubuntu 18.04.1 LTS, to a server.  No error message and it doesn't ask for the server password.  It worked fine in 16.04LTS. If I copy the 'rsync' command from 'grsync' GUI to a terminal window it executes flawlessly. I trashed the system.  reformat HDD. Re-installed Ubuntu 18.04.01.  No change, still won't run.  No error message.  Copy & Paste the grsync command line to terminal, it runs fine.  If I go to my terminal and type grsync, the GUI comes up.  I have to type my password in the terminal, then it runs flawlessly.

---

### Post by rbscycle on 2018-11-09
Can anyone verify this?  Install grsync and test it to a remote server!?

---

### Post by HermanAB on 2018-11-10
Well, you can debug it yourself:

Start by running tcpdump and staring at the packets for a while, both when running from the command line and with the GUI.  See what is different.

Something like this:
$ sudo tcpdump -nlX -i eth0

Also look at the system log files and google the error messages.  It isn’t rocket surgery...

---

### Post by rbscycle on 2018-11-13
The first thing that happens when using "rsync" from the command line to a remote server is: it asks for the password of the remote server. 
From the "Grsync" GUI, it used to ask for the password in Ubuntu 16.04LTS.  It does not ask for the password in Ubuntu 18.04LTS, it waits forever.

---

### Post by rbscycle on 2018-11-23
I tried: $ sudo tcpdump -nlX -i eth0, which printed out pages of code I didn't understand.

---

### Post by rbscycle on 2018-11-24
Tried grsync from Kubuntu 18.04lts, it worked properly.

---

### Post by linux4me on 2018-11-25
I can confirm that grsync doesn't prompt for the password if you're connecting to a remote machine in Ubuntu 18.04. 

It seems that although ssh-askpass is installed, for some reason I haven't been able to identify, grsync doesn't use it to prompt you for a password. 

As you discovered, the workaround is to start grsync from Terminal, then fill in the password in Terminal when you're prompted.

---

### Post by vector on 2019-01-06
I can also confirm grsync does not prompt or at least you cant see it. 
works via terminal but thats a pain.
Looking at Various log files was none the wiser.
Was hoping this would have been identified and fixed by now

---

