---
title: "can't access /usr/local"
date: 2008-03-25
forum: General Help
---

### Post by ai3gtmc on 2008-03-25
it says you don't have the permissions necessary to view the contents of local

when i try to user@user-linuxbox:/usr/local$ ls i get "ls: .: Permission denied"

im using UBUNTU 7.10

pls help..

thanks in advance

---

### Post by dannyboy79 on 2008-03-25
well on my machine la -la /usr/

drwxr-xr-x  11 root root  4096 2007-09-27 08:26 local

which means that it's owned by root and isn't writable by anyone but root. you need to use sudo. if you want to switch to root privelages temporarily, use
sudo -i
then enter your users password, then you'll get a root prompt. BUT when you're done, enter 
exit
then you'll be back to your username. good luck

---

### Post by ai3gtmc on 2008-03-25
hmm few hours ago i can access it normally..

how can i set it to use my username as owner?

---

### Post by dannyboy79 on 2008-03-25
sudo chown username:usergroup /usr/local/

example:

sudo chown daniel:daniel /usr/local/

---

### Post by ai3gtmc on 2008-03-25
> **dannyboy79 said:**
> sudo chown username:usergroup /usr/local/

example:

sudo chown daniel:daniel /usr/local/

didnt work :( still permission denied.

---

### Post by dannyboy79 on 2008-03-25
please post the output of this command

ls -la /usr/ | grep local

---

### Post by ai3gtmc on 2008-03-25
```
d-wx--x--x  15 dave dave  4096 2008-03-25 20:57 local
```

dave is my user and dave is my groups

UPDATE I can now access local but not the files and folders inside it.

the folders has the lock in their icons.

EDIT oh nvm i did the same command to all the folders manually :P it works now! Thanks!

---

### Post by dannyboy79 on 2008-03-26
> **ai3gtmc said:**
> ```
d-wx--x--x  15 dave dave  4096 2008-03-25 20:57 local
```

dave is my user and dave is my groups

UPDATE I can now access local but not the files and folders inside it.

the folders has the lock in their icons.

EDIT oh nvm i did the same command to all the folders manually :P it works now! Thanks!

you didn't have to do it manually to each folder, if you read the man pages for the chown command, you could have seen that the -R means recursive. meaning it would apply the chown command to all the folders and files within it. just an FYI. Also, i see that /usr/local/ is still not readable by ANYONE. I don't know how this happened???? you should now use the chmod command, which changes the read, write, execute permissions for the owners and groups. If you want /usr/local/ readble by your username, then you would need to do this command

sudo chmod u+r /usr/local/

if you want to apply to all files and folders, again use the -R, so it would be

sudo chmod -R u+r /usr/local/

good luck but I am very curious as to why your folders permissions and owners are all messed up.

---

### Post by chrisccoulson on 2008-03-26
A word of warning - don't go messing with permissions of files / folders outside of your home folder. There should be no need to do it, and there have been so many people on these forums who have hosed their system doing this.

Obviously, you need to fix your current issue, but as long as you've only changed permissions on /usr/local, you should be ok (as there isn't much stuff under there). As an example, changing ownership of /usr will have all sorts of strange effects, such as removing the suid bit on the sudo binary, which will stop it from working completely.

---

