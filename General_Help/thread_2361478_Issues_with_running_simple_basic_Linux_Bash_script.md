---
title: "Issues with running simple basic Linux Bash scripts in Ubuntu Budgie. GNOME related?"
date: 2017-05-17
forum: General Help
---

### Post by jessedavid4 on 2017-05-17
The reason I ask if it's Gnome related, is that, for some odd reason, you cannot create a document without creating one in your templates.
Thus, making the  document not open in bash... maybe? I've used KDE a few times and even Mint, and while both had very user-friendly 
interfaces for the File Management (Dolphin and Nautalis), I cannot seem to get the same "User-friendly" result from what I was getting
with the other OS's. 

I'm using the newest Ubuntu budgie 17.04. 

Perhaps something with my Gedit is not saving correctly? (Oh yes, it's also defaulting Gedit, obviously)

Anyone have any suggestions or a solution to my problem?

Thanks in advanced!
-Jesse

---

### Post by vasa1 on 2017-05-17
I don't understand the title and > Thus, making the document not open in bash... maybe? 
How are you trying to open the document in bash?

---

### Post by jessedavid4 on 2017-05-17
ie: "Hello World". 

1. Create an unamed document (have to do this in the Templates folder because I cannot find an option elsewhere)
2. Edit the document to run in a command in terminal (echo in this case)
3. Run the bash script in the terminal. -- this is where my issue is. The Terminal execute (run)  cannot find my file that I have saved and edited.

Sorry for the bad grammar. I've been up later than my normal bed time hours due to experimenting with my Budgie!

---

### Post by igdfpm on 2017-05-17
The templates folder is not there for that purpose... it is there for templates....You will need to provide more specific information before anyone can offer further assistance. What are you trying to achieve?

---

### Post by jessedavid4 on 2017-05-17
If it's making sense to me and not anyone else, then I probably need some sleep! 
But hopefully I can put it as rational as I can so I can come back to see a possible solution.

In my Ubuntu Budgie 17.04, I cannot add a new "untitled document". Thus my only solution is going into the template to create a text file.
I was hoping I could create a basic text bash script that would run inside the terminal. But it seems that the text bash script would not run. 
The issue I had came back as a "could not find the file or directory". When I was creating my Text bash script from the text document, 
I was using Gedit. I questioned Gnome, because I thought it could be something related to it, hoping someone would have a solution!

So perhaps with my train of thought, wherever it leads,  I was wondering if I could either create an Untitled Document or find a solution to
making a template text file run as a bash script.

---

### Post by again? on 2017-05-17
Run this to give right click menu to create a document.
```

mkdir ~/Templates
touch ~/Templates/Untitled.txt
```

Shell scripts won't autocomplete in terminal unless they are executable.

If you want a template for shell scripts.
```
gedit ~/Templates/shell-script.sh
```
Paste in the shebang.
```
#!/bin/sh
```
Save and close.

If you want all  scripts created from the template to be executable, make the template executable.
```
chmod +x ~/Templates/shell-script.sh
```

---

### Post by LastDino on 2017-05-17
I'm wondering, but are you probably having "permission issues"?

There shouldn't be any problem to create files on Ubuntu, irrespective of the version.

What is the error that you get when you try to create a new file? 

(simple way is to right mouse click>create new document)

/forgive me if I'm off but that is what seems to be your basic problem from the first line of your last post

---

### Post by apmcd47 on 2017-05-17
Could you open a terminal window in the folder containing the Templates folder and type the following:
```
echo $USER
whoami
ls -la

```
and post the results here (using code tags of course).

Andrew

---

### Post by HermanAB on 2017-05-17
To run a script in the current directory:
$ ./scriptname

---

### Post by jessedavid4 on 2017-05-17
> **apmcd47 said:**
> Could you open a terminal window in the folder containing the Templates folder and type the following:
```
echo $USER
whoami
ls -la

```
and post the results here (using code tags of course).

Andrew


```
total 176
drwxr-xr-x 32 jesse jesse 4096 May 17 14:21 .
drwxr-xr-x  3 root  root  4096 May 13 06:50 ..
-rw-rw-r--  1 jesse jesse    0 May 17 01:06 1
drwx------  3 jesse jesse 4096 May 16 16:22 .adobe
-rw-------  1 jesse jesse 4589 May 17 02:47 .bash_history
-rw-r--r--  1 jesse jesse  220 May 13 06:50 .bash_logout
-rw-r--r--  1 jesse jesse 3853 May 13 06:50 .bashrc
drwxrwxr-x 23 jesse jesse 4096 May 17 02:27 .cache
drwxr-xr-x 25 jesse jesse 4096 May 17 01:40 .config
drwx------  3 root  root  4096 May 17 02:27 .dbus
drwxr-xr-x  2 jesse jesse 4096 May 17 01:19 Desktop
drwxr-xr-x  6 jesse jesse 4096 May 17 01:04 Documents
drwxr-xr-x  6 jesse jesse 4096 May 16 16:51 Downloads
drwx------  2 jesse jesse 4096 May 17 11:35 .gconf
drwxrwxr-x  3 jesse jesse 4096 May 16 17:31 git
drwx------  2 root  root  4096 May 17 02:27 .gvfs
-rw-------  1 jesse jesse 1884 May 17 11:34 .ICEauthority
drwxrwxr-x  3 jesse jesse 4096 May 13 07:09 .local
drwx------  3 jesse jesse 4096 May 16 16:22 .macromedia
drwxrwxr-x  5 jesse jesse 4096 May 16 17:29 mlbhls
drwxrwxr-x  5 jesse jesse 4096 May 16 17:31 mlbhlsgit
drwxrwxr-x  5 jesse jesse 4096 May 16 17:29 mlbhs
drwxrwxr-x  3 jesse jesse 4096 May 16 17:57 mlbtv-hls-nexdef
drwxrwxr-x  5 jesse jesse 4096 May 16 17:26 mlbtv-hls-nexdef.git
drwx------  4 jesse jesse 4096 May 13 08:22 .mozilla
drwxr-xr-x  2 jesse jesse 4096 May 13 07:09 Music
drwxrwxr-x  2 jesse jesse 4096 May 17 01:43 .nano
-rw-------  1 jesse jesse   73 May 17 01:44 nano.save
drwxr-xr-x  2 jesse jesse 4096 May 17 14:21 Pictures
drwx------  3 jesse jesse 4096 May 13 07:11 .pki
drwxrwxr-x 12 jesse jesse 4096 May 13 20:48 .PlayOnLinux
lrwxrwxrwx  1 jesse jesse   37 May 13 17:33 PlayOnLinux's virtual drives -> /home/jesse/.PlayOnLinux//wineprefix/
-rw-r--r--  1 jesse jesse  675 May 13 06:50 .profile
drwxr-xr-x  2 jesse jesse 4096 May 13 07:09 Public
-rw-------  1 jesse jesse  256 May 13 09:25 .pulse-cookie
-rw-r--r--  1 root  root    61 May 17 02:28 Puppits
drwxrwxr-x  2 jesse jesse 4096 May 17 01:00 Sh intro
drwxrwxr-x 20 jesse jesse 4096 May 16 12:53 .steam
drwxrwxr-x  3 jesse jesse 4096 May 13 09:25 Steam
lrwxrwxrwx  1 jesse jesse   30 May 16 12:53 .steampath -> /home/jesse/.steam/bin32/steam
lrwxrwxrwx  1 jesse jesse   28 May 16 12:53 .steampid -> /home/jesse/.steam/steam.pid
drwxrwxr-x  3 jesse jesse 4096 May 16 16:43 .subversion
-rw-r--r--  1 jesse jesse    0 May 13 07:21 .sudo_as_admin_successful
drwxr-xr-x  2 jesse jesse 4096 May 17 01:49 Templates
drwxr-xr-x  2 jesse jesse 4096 May 13 07:09 Videos
-rw-------  1 jesse jesse   50 May 17 11:34 .Xauthority
-rw-------  1 jesse jesse 3418 May 17 11:34 .xsession-errors
-rw-------  1 jesse jesse 3418 May 16 12:53 .xsession-errors.old
```

---

### Post by jessedavid4 on 2017-05-17
> **LastDino said:**
> I'm wondering, but are you probably having "permission issues"?

There shouldn't be any problem to create files on Ubuntu, irrespective of the version.

I don't seem to notice any permission issues. But in truth, when I try to configure some installations,
I will have "permission denied".


>  (simple way is to right mouse click>create new document)

It seems in this version of Ubuntu Budgie (17.04), with whatever Gnome File system
it uses, I do not have that option. That is why I was trying to go through the templates.

---

### Post by apmcd47 on 2017-05-25
Sorry, I forgot to keep an eye on this thread. You didn't show the results of **whoami** or **echo $USER**. Rereading the thread it sounds like you are starting gedit from the file manager. What happens when you use the command prompt (terminal emulator, bash shell)? Can you still only create files in the Templates folder? It looks no different to your home directory.

Andrew

---

