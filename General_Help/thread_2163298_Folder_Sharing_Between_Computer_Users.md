---
title: "Folder Sharing Between Computer Users"
date: 2013-07-17
forum: General Help
---

### Post by rbscairns on 2013-07-17
Ubuntu 12.04 with Gnome Classic

How do I set up a folder so that all uses ONLY of the computer can access the folder read only and I have full access to the folder?

---

### Post by gleedadswell on 2013-07-17
Hi rbscairns,

Do you know chmod?  There are various guides/manuals to chmod online since it is a very old unix command.  If by "full access" for yourself you mean read/write (i.e. not execute - this will depend on what kind of files they are)?  If so then assuming you are the owner of the folder you should be able to use

```
chmod 644 *
```

in that folder to get what you want.  But I'd read a chmod tutorial first if I were you.

I'm somewhat surprised the other users don't have read only access to the folder by default.  What is the nature of this folder?

---

### Post by HiImTye on 2013-07-17
create a shared group
```
sudo groupadd sharedfolder
```
then add the list of users to the group
```
echo 'user1|user2|etc|...' | while IFS=\| read -r u; do sudo usermod -a -G sharedfolder "$u"; done
```
then change the group and permissions of the folder
```
sudo chown -R user:sharedfolder /path/to/folder
find /path/to/folder | while read -r f; do if [ -f "$f" ]; then sudo chmod 0640 "$f"; else sudo chmod 0750 "$f"; fi; done
```[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

