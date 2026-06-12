---
title: "Deleting in the terminal... Where do they go...?"
date: 2007-07-26
forum: General Help
---

### Post by Fallen_62 on 2007-07-26
So, I put some files in the "/" root.  I then made a "shared" directory in the "/home folder", then used the mv command to move the files from "/" to "/home/shared".  Then, I realized that the files werent complete, so i typed "rm /home/shared/*".  All of this is done after I did the "su -" command.

My question is...  where did those go...?  They arent in the /root/.Trash/ folder, and I think they are still on my hard drive, because the space that they took up is not freed up...  Anyone know...?

---

### Post by kevinlyfellow on 2007-07-26
try this
```
sudo updatedb
locate *filename*
```

---

### Post by HermanAB on 2007-07-26
They went to the great bit bucket in the sky... bless their little mortal souls...

The 'trashcan' usually only works from a graphical environment, not from a raw shell.

Sorry!

Herman

---

### Post by Fallen_62 on 2007-07-26
> **kevinlyfellow said:**
> try this
```
sudo updatedb
locate *filename*
```

Tried that, and it found it on my external HD, but not on my Linux partition.

Is there a way that, when I moved it, it made symbolic (or possibly even hard) links to the inode, and the things I deleted were the links, so the stuff is still out there on the inode...?  Is there any way I could tell that...?  Or any other possible explanation for why I don't have that space back...? 

HermanAB:  I kinda gathered that, but then why didnt I get my space back that they used when I removed them while in the terminal...?

---

### Post by kevinlyfellow on 2007-07-26
Could it be in /tmp ???

---

### Post by Fallen_62 on 2007-07-26
> **kevinlyfellow said:**
> Could it be in /tmp ???
I dont think so.  Loading up Nautilus, turing on hidden folders, and then I look at the size of the directory, and it is only 11.4 KB worth of files.

---

### Post by kevinlyfellow on 2007-07-26
hmmm.... how are you checking the remaining the space?  Are you using df?

You may be able to track it down using baobab

---

### Post by Wim Sturkenboom on 2007-07-26
Files might still be opened by an application. There is a command to find the program, but I can not remember it :(

[edit]
Ah, found it: *lsof*
[/edit]

---

### Post by Fallen_62 on 2007-07-26
> **kevinlyfellow said:**
> hmmm.... how are you checking the remaining the space?  Are you using df?

You may be able to track it down using baobab
I was just going off of what it told me I had for free space down at the bottom of a window (Like when I went to my home folder and had nothing highlighed).  DF says I have about 2 gigs more than what it tells me when I look in the window.

baobab doesnt show anything out of the ordinary...  *shrug*  Iunno...

---

### Post by Fallen_62 on 2007-07-26
> **Wim Sturkenboom said:**
> Files might still be locked by an application. There is a command to find the program, but I can not remember it :(
Not a whole lot of help right now then, is it...?  ;)  If you remember it/find it, please let me know.  Im ganna be heading to bed now...

---

### Post by kevinlyfellow on 2007-07-26
I think nautilus (or whatever you use) just needs to update.  It should do it on its own in at some point, but maybe you can force the issue by 
```
killall nautilus
```

---

### Post by Fallen_62 on 2007-07-26
> **kevinlyfellow said:**
> I think nautilus (or whatever you use) just needs to update.  It should do it on its own in at some point, but maybe you can force the issue by 
```
killall nautilus
```
I've rebooted the system and I have refreshed the windows and stuff.  I have also tried to copy the file back over, but it wont let me, saying that there isnt enough room to copy it over.  That is the reason that I think the files are still out there somewhere...  I made sure there was enough room before I started copying the files over the first time, and it got about 3.5 gigs done and another process killed the copying, at which point i moved them to the shared folder, then deleted them to try and copy them over again.  That is when I got the no space error message, and the space from the files was still being used (or so it seems).

I really am going to bed now :P  I will read up in the morning.  Thanks for the suggestions so far!

---

### Post by Wim Sturkenboom on 2007-07-26
> **Fallen_62 said:**
> Not a whole lot of help right now then, is it...?  ;)  If you remember it/find it, please let me know.  Im ganna be heading to bed now...I did edit my post :) but ok, the command is *lsof*

---

### Post by Fallen_62 on 2007-07-26
> **Wim Sturkenboom said:**
> I did edit my post :) but ok, the command is *lsof*
Nothing showed in there that related to the files.

---

