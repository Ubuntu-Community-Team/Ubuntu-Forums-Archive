---
title: "Sharing Folder on Same PC"
date: 2017-05-14
forum: General Help
---

### Post by Quarkrad on 2017-05-14
Running 16.04.  I'm getting confused re all the reading and nothing working - wife and myself use the same physical machine - so we are two users on the same 16.04 Mate pc.  I would like to have access to her Desktop folder so when I do things for her (e.g. scanning) I can easily copy files from my Desktop to hers without logging off/switching user.  So ... using my Caja file manager is it possible for me to 'see' her Desktop and transfer file across to 'her side'?  Thanks.

---

### Post by Dennis N on 2017-05-14
I have done it this way:

With users A and B, Add A to B's group. B's group will normally have only read and execute permission on folders in B's home, so enable group write permission on the one folder in B's home that A is going to save files in. 

Also add B to A's group and enable group write permission on the one folder in A's home that B will save files in.

---

### Post by Quarkrad on 2017-05-15
I think I have already added A and B to each others group - see dad.png and liz.png.  Also, looking at the permissions (dadperm.png) the group has full access - (the permissions for liz also shows liz as the group owner).  I might be wrong here - I'm thinking that as A and B are part of each others group dadperm is correct in terms of the group owner.   If this is correct perhaps I'm not looking in the place, re caja, for Liz's Desktop folder.   Where would it be?

---

### Post by Dennis N on 2017-05-15
If you are using the Desktop folder for each user as the shared one, did you change both user's Desktop to have write premissions for the user's group? You show just one - I assume you did both? 

Then, If I understand it, your question is where to find B's Desktop from A's user account in file manager (and vice versa).

You can browse to B's Desktop from A's home folder by browsing to:
**/home/userB/Desktop**
then set a bookmark on this folder in Caja so you can get there directly (bookmark appears in sidepane).
Then, from B's home folder browse to:
**/home/userA/Desktop**
and set a bookmark there as well.

File System structure under /home:

```
/home
&#9500;&#9472;&#9472; userA
&#9474;   &#9500;&#9472;&#9472; Desktop			<-- userB bookmarks this folder
&#9474;   &#9500;&#9472;&#9472; Documents
&#9474;   &#9500;&#9472;&#9472; Downloads
&#9474;   &#9500;&#9472;&#9472; Music
&#9474;   &#9500;&#9472;&#9472; Pictures
&#9474;   &#9500;&#9472;&#9472; Public
&#9474;   &#9500;&#9472;&#9472; Templates
&#9474;   &#9500;&#9472;&#9472; Videos
&#9492;&#9472;&#9472; userB
    &#9500;&#9472;&#9472; Desktop			<-- userA bookmarks this folder
    &#9500;&#9472;&#9472; Documents
    &#9500;&#9472;&#9472; Downloads
    &#9500;&#9472;&#9472; Music
    &#9500;&#9472;&#9472; Pictures
    &#9500;&#9472;&#9472; Public
    &#9500;&#9472;&#9472; Templates
    &#9492;&#9472;&#9472; Videos


```permissions on both Desktops is 775 or rwxrwxr-x as shown in terminal.

---

### Post by Quarkrad on 2017-05-15
I haven't got this yet - attached lizperm shows liz as the Group owner for her Desktop, as mine shows dad as the Group owner for my Desktop (#3).  My reasoning is that as we are both members of each others Group, surely it does not matter who the owner of the Desktop is.  Also, my home.png shows my folder structure.

---

### Post by Quarkrad on 2017-05-15
Dennis - sorted.  I needed a restart and as you said above, I now have a choice of user folders under /home.  Many thanks.

---

