---
title: "Removing stubborn fiels from trash (permisions issue)"
date: 2022-06-02
forum: General Help
---

### Post by steve234 on 2022-06-02
Hi there,

I'm trying to free up some space on a 1TB spinner mounted to /media/user/storage on my PC.

I have sent backups (from a system upgrade) of my old /etc/ /srv/ /usr/ and /var/ directories to trash.

Obviously I haven't got permission to either delete them or restore them in my file manager. 

I've tried a few options and nothing works:


[LIST]
[*]trash-cli and sudo trash-empty does nothing 
[*]if I look in .local/share/Trash - there are no files there to remove manually 
[*]If I open the file manager using sudo, there is no trash directory to manipulate. 
[/LIST]

Can anyone help me out - I'm obviously missing something fundamental here.

---

### Post by ActionParsnip on 2022-06-02
Try trash-cli

---

### Post by steve234 on 2022-06-02
> **ActionParsnip said:**
> Try trash-cli

eeerm I did - in my OP I said trash-cli and sudo trash-empty do nothing

---

### Post by dragonfly41 on 2022-06-02
In Ubuntu 20.04 I tried running .. trash-cli
and like you I got ..

[FONT=monospace][COLOR=#000000]trash-cli[/COLOR]
trash-cli: command not found

Now since I have Synaptic Package Manager installed
I searched for "trash" and saw that it was in repo 
but simply not installed. Easy to install.

I also see that there is a python script ..
python3-send2trash[/FONT]

---

### Post by TheFu on 2022-06-02
At the top of the mount directory, there will be a .Trash/ directory. Delete that recursively.
BTW, using sudo with most GUI programs often has undesirable side-effects. Beware.

So, just to be very clear, I record TV shows to /TV/Recordings/.  /TV is the mount location, so there is a subdirectory named /TV/.Trash/.  With that, daily I run 
```
rm -r  /TV/.Trash/* 
```
This is part of root's crontab, so it runs as root. By fully spelling out the entire, absolute, directory location, I've ensured that only stuff under that trash directory is removed.  Never trust the PWD in a crontab. Never.

---

### Post by steve234 on 2022-06-02
> **TheFu said:**
> At the top of the mount directory, there will be a .Trash/ directory. Delete that recursively.
BTW, using sudo with most GUI programs often has undesirable side-effects. Beware.

So, just to be very clear, I record TV shows to /TV/Recordings/.  /TV is the mount location, so there is a subdirectory named /TV/.Trash/.  With that, daily I run 
```
rm -r  /TV/.Trash/* 
```
This is part of root's crontab, so it runs as root. By fully spelling out the entire, absolute, directory location, I've ensured that only stuff under that trash directory is removed.  Never trust the PWD in a crontab. Never.

My Trash folders were slightly differently named, but this did the trick perfectly - it as the location of the sub directory in the mount location that the various guides I found online didn't mention.

dragonfly41 thanks for your help, but I think we're misunderstanding each other!

---

### Post by deadflowr on 2022-06-02
1GB seems quite small, is that correct?

---

### Post by steve234 on 2022-06-03
> **deadflowr said:**
> 1GB seems quite small, is that correct?

yes sorry - 1TB (3x 4TB currently on order!) amended in the OP

---

