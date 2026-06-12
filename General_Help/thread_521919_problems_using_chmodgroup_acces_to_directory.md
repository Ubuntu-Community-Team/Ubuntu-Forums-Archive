---
title: "problems using chmod/group acces to directory"
date: 2007-08-09
forum: General Help
---

### Post by lungdart on 2007-08-09
Heres my setup. I have a directory called public mounted off the root (/public) its an ext3 file system on a separate drive from my file system.

I have two users, "shawn" (me) and "nadine" (my girlfriend). Both users belong to the group "public".  I've done the following commands

```

sudo chown -R shawn:public /public
chmod -R 664 /public

```

this will in tern give me access denied for each directory inside which is my first problem. If I am the owner of everything in this directory and sub directories (ls -l confirms this) should I not be able to change file permissions?

so I do this for shits

```

sudo chmod -R 664 /public

```

This seems to work, but then when I go to cd into the directory /public I get an access denied as both users, but not as root. in nautilus the permisions for the folders are listed as "list, create/delete, no access" and --- for file access.

The only way I can get permissions to the folder is to give full permissions to owner and group and "apply to permissions to enclosed files". Then I have access until I go near it again with the chmod command.

If im going about this wrong, I would like to know. I just want to make a public folder that both users have read/write access to the entire folder.

Let me know if any outputs would help further. Thanks.

---

### Post by PaulFr on 2007-08-10
A reasonable permission for a directory where you want to give permission to multiple users in a group to read/write files in /public would be **775** and not **664**. The **x** permission is needed for navigation through the directory structure - see the manual page for **chmod**. So I would suggest ```
sudo chown -R shawn:public /public/*
sudo chmod -R 775 /public/*
```Hope this helps.

---

### Post by lungdart on 2007-08-10
Thank you for the information, I was aware directoires needed to be executable to navigate!

But would this not also give all my files executable permissions? It will do for now, but I dont want to have executable files all over the place. Thats disaster waiting to happen.

---

### Post by PaulFr on 2007-08-10
True, what was I thinking ? So maybe ```
sudo chown -R shawn:public /public/*
sudo find /public -type d -exec chmod 775 {} \;
sudo find /public -type f -exec chmod 664 {} \;
```However, if you do have executable scripts in **/public**, then the last line should read ```
sudo find /public -type f -exec chmod u+rw,g+rw,o-w {} \;
```i.e. use chmod in incremental mode.

Actually, once the chown is complete, the find commands can be run without the sudo since all files and directories are owned by you.

---

