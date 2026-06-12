---
title: "Searches not working on Gimp (Snap)"
date: 2018-12-16
forum: General Help
---

### Post by braznyc on 2018-12-16
After installing Gimp through Snap the search functions don't work.
Gives no results to files I know are in the folders.


Any help is welcome.

---

### Post by Holger_Gehrke on 2018-12-16
I assume you mean the 'Search'-function in the file open dialog. Are the files you're looking for outside your home directory or it's sub-directories ? Programs installed from snap-packages are sandboxed and can't access files outside of the home directory of the user running the program or the '/media/$USER/' folder for accessing hotplugged devices for this user (actually, accessing /media/ depends on the configuration of the snap and might not be possible for a given snap ...).

Holger

---

### Post by braznyc on 2018-12-16
> **Holger_Gehrke said:**
> I assume you mean the 'Search'-function in the file open dialog. Are the files you're looking for outside your home directory or it's sub-directories ? Programs installed from snap-packages are sandboxed and can't access files outside of the home directory of the user running the program or the '/media/$USER/' folder for accessing hotplugged devices for this user (actually, accessing /media/ depends on the configuration of the snap and might not be possible for a given snap ...).

Holger


Yes, in the file open dialog.
The files are in the Home/Pictures folder.

---

### Post by Autodave on 2018-12-16
Kinda confused: my GIMP does not have a search function that I can find.  Is there a reason why you went with the Snal version instead of the one in the repositories?

---

### Post by braznyc on 2018-12-16
> **Autodave said:**
> Kinda confused: my GIMP does not have a search function that I can find.  Is there a reason why you went with the Snal version instead of the one in the repositories?


Not confusing: File > Open (a dialog will open)... There's a search function that will search for files in the folders. It never finds anything.

I can use that same dialog (file opener) to open any file when I know where they are. That's why I think it is not related to the fact that the Snap is sandboxed.

---

### Post by mc4man on 2018-12-16
> **braznyc said:**
> Not confusing: File > Open (a dialog will open)... There's a search function that will search for files in the folders. It never finds anything.

I can use that same dialog (file opener) to open any file when I know where they are. That's why I think it is not related to the fact that the Snap is sandboxed.
It would appear that the Search & Recent functions in the snap gimp are broken. Browsing works fine.
Don't think it has much to do with confinement in terms of where, your home directory should be fully accessible. Probably just how it's (the snap) created or  a current limitation of snapd. 

You could file an issue here (snapd
[https://forum.snapcraft.io/c/snapd](https://forum.snapcraft.io/c/snapd)

or  what **snap info gimp** says about issues
[https://github.com/snapcrafters/gimp/issues](https://github.com/snapcrafters/gimp/issues)

(- if you wanted a snap gimp with full access to / you'd - 
```
sudo snap remove gimp
```
```
sudo snap install gimp --classic
```

---

### Post by braznyc on 2018-12-16
> **mc4man said:**
> It would appear that the Search & Recent functions in the snap gimp are broken. Browsing works fine.
Don't think it has much to do with confinement in terms of where, your home directory should be fully accessible. Probably just how it's (the snap) created or  a current limitation of snapd. 

You could file an issue here (snapd
[https://forum.snapcraft.io/c/snapd](https://forum.snapcraft.io/c/snapd)

or  what **snap info gimp** says about issues
[https://github.com/snapcrafters/gimp/issues](https://github.com/snapcrafters/gimp/issues)

(- if you wanted a snap gimp with full access to / you'd - 
```
sudo snap remove gimp
```
```
sudo snap install gimp --classic
```



Thank you!

I trie to reinstall Gimp using those commands I had this error message:

"error: snap "gimp" is not compatible with --classic"


I thought snaps were supposed to solve issues when installing a program. :)

---

### Post by Autodave on 2018-12-16
File -> Open presents me with a menu of where to look for a file: no "search" there.  My pic files are generally on another drive.  From File -> Open, I can click on the second HD and then the folder with the pic files.

---

### Post by braznyc on 2018-12-16
> **Autodave said:**
> File -> Open presents me with a menu of where to look for a file: no "search" there.  My pic files are generally on another drive.  From File -> Open, I can click on the second HD and then the folder with the pic files.


Are you serious?

This: (in this image it shows that I had searched for the word "blue", and nothing was found. I know I have many image files that have the word "blue")

[IMG]http://i63.tinypic.com/2edwjmp.png[/IMG]

---

### Post by ajgreeny on 2018-12-16
Yes, Autodave probably is serious.

I'm using gimp 2.10.8 from the ppa, and using that in my Xubuntu 18.04 doesn't give me any search function in the dialogue box that opens from the File ->Open menu, just a navigation window as I expect.

---

### Post by braznyc on 2018-12-16
> **ajgreeny said:**
> Yes, Autodave probably is serious.

I'm using gimp 2.10.8 from the ppa, and using that in my Xubuntu 18.04 doesn't give me any search function in the dialogue box that opens from the File ->Open menu, just a navigation window as I expect.

I'm so sorry about that...  I'll never install Xubuntu then.


Let's go back to my question... :)

---

### Post by Autodave on 2018-12-16
Yep: the Snap is obviously quite different.  So, let me go back to what I asked before: is there a reason why you need the snap one instead of the one in the repositories?  I realize that sometimes they mat have a different feature(s) that you need / want.

---

### Post by Autodave on 2018-12-16
...that didn't work....  sorry.

---

### Post by ajgreeny on 2018-12-16
I now have to qualify my last comment, having looked a bit closer at the dialogue box of gimp-2.10.8, and it's nothing to do with Xubuntu but simply my lack of detailed memory of the dialogue box itself.

At the far left end of the titlebar of the dialogue box there is, I now see, a small "folder" icon which opens - guess what? - a search box which I was not aware of!

Perhaps we have both learned something from your original question; I certainly have.

---

### Post by braznyc on 2018-12-16
> **Autodave said:**
> Yep: the Snap is obviously quite different.  So, let me go back to what I asked before: is there a reason why you need the snap one instead of the one in the repositories?  I realize that sometimes they mat have a different feature(s) that you need / want.



I'm trying to solve something here. Your question why I'm using snap is not helping me.
That's not the reason why I started this thread.

I know I can install Gimp using a command line... But again: that's not the reason why I'm looking for help.

---

### Post by braznyc on 2018-12-16
> **ajgreeny said:**
> I now have to qualify my last comment, having looked a bit closer at the dialogue box of gimp-2.10.8, and it's nothing to do with Xubuntu but simply my lack of detailed memory of the dialogue box itself.

At the far left end of the titlebar of the dialogue box there is, I now see, a small "folder" icon which opens - guess what? - a search box which I was not aware of!

Perhaps we have both learned something from your original question; I certainly have.

Good to know that the search function is there. :)

---

### Post by Autodave on 2018-12-16
But, there are sometimes difference between the snap version and the repository version.  If the search doesn't work in the repository version, then someone may be able to help you. But, with the snap version, they may not be able to help.

---

### Post by mc4man on 2018-12-17
> **braznyc said:**
> Thank you!

I trie to reinstall Gimp using those commands I had this error message:

"error: snap "gimp" is not compatible with --classic"


I thought snaps were supposed to solve issues when installing a program. :)
Works here but not really the point, it would not solve your issue.
The Search function is broken, look for or if not already  file an issue with one of the links I gave, best bet is the github one.

---

### Post by braznyc on 2018-12-18
> **mc4man said:**
> Works here but not really the point, it would not solve your issue.
The Search function is broken, look for or if not already  file an issue with one of the links I gave, best bet is the github one.


Thank you, Mc4Man!

---

### Post by ununtrium on 2018-12-18
The current snap gimp doesn't work very well. The only problem snap I have faced in using snaps and I have 10+ other snaps that would great.
Best to use the one from the ubuntu repositories
so remove the snap with
```
snap remove gimp
```
and them simply input
```
sudo apt install gimp
```
no additional repo is required

---

