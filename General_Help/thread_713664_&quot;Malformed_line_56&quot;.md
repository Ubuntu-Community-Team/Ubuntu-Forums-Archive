---
title: "&quot;Malformed line 56&quot;"
date: 2008-03-03
forum: General Help
---

### Post by neonmagnolia on 2008-03-03
I'm very new to Ubuntu and wanted to install a program called Komodo Drop ([http://komodo.rabien.com/](http://komodo.rabien.com/)). I'm really not sure how to go about doing this, but I attempted anyways and failed. I tried to add a new repository with 'deb [http://rabien.com/software/KomodoDrop.tar.gz](http://rabien.com/software/KomodoDrop.tar.gz) komodo' knowing that it was probably wrong but hoping i could figure it out and fix it. No. Now I can't get Synaptic to work at all. I got a message saying to use 'sudo apt-get update' and 'sudo apt-get install -f', and when i typed those in this is what i got:
```
danielle@neon:~$ sudo apt-get update
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
danielle@neon:~$ sudo apt-get install -f
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
```
So my first question is how do I undo what I did, since I can't open Synaptic at all. Once I get that straightened out, how do I add this program?

---

### Post by amingv on 2008-03-03
First lesson: _Always_ make a backup of any file you modify manually:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

You cam try this; type this in a terminal:

```
gksudo gedit /etc/apt/sources.list
```

Comment out the line you added (that is, put a # character before it), seems to be the line 56 (you can see the line numbers by pressing F11).

Save the file and run this:

```
sudo apt-get update
```

If you want to add that repository, I dearly suggest using synaptic to do so; open synaptic and Settings>Repositories>New. Put the information on each corresponding line.

Run apt-get update and everything should be OK.

---

### Post by aysiu on 2008-03-03
That's not a repository. It's a compressed file (that's what the .tar.gz extension means).

Once you've fixed your repositories with the advice amingv gave, then you should paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://rabien.com/software/KomodoDrop.tar.gz
``` This downloads the compressed file. ```
tar -xvzf KomodoDrop.tar.gz
``` This decompresses the compressed file. ```
chmod +x KomodoDrop
``` This makes the decompressed file executable. ```
sudo mv KomodoDrop /usr/local/bin/
``` This moves the executable to a directory for locally installed programs. ```
rm KomodoDrop.tar.gz
``` This removes the originally downloaded file (which you no longer need).

The command ```
KomodoDrop
``` should now launch the application.

---

### Post by amingv on 2008-03-03
Good eye aysiu! I only saw as far as deb http:// and immediately labelled it as a repository.

On a side note for OP; it is also not recommendable to add random repositories unless you know and trust the source. The official Ubuntu repositories are (of course) optimized for Ubuntu and you can be quite confident they do not contain malicious programs.

---

### Post by neonmagnolia on 2008-03-03
Thanks so much, to you both!!

---

