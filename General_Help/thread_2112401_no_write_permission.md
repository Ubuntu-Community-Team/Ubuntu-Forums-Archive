---
title: "no write permission"
date: 2013-02-04
forum: General Help
---

### Post by beengone on 2013-02-04
Ubuntu Server 10.04I have a folder at /home/shared that has write privilidges to the 'users' group. I created a new user and put her in the users group. But, she doesn't have write access. 

I'm accessing the machine through SSH and can write to the folder if I close and open a new session with a different user.

I must be missing something simple here. Thanks.

EDIT: BTW, I did search around and this is really common, but nothing seems to fix it. 

Example entry when I do "ls -l"
drwxr-xr-x  2 shared users     4096 2011-08-11 12:54 EW Filename

and "id"
uid=1009(username) gid=100(users) groups=100(users)

---

### Post by beengone on 2013-02-04
and 

```
$ ls -ld
drwxr-xr-x 154 shared users 12288 2013-02-04 15:56 .

```

---

### Post by kanikilu on 2013-02-04
> **beengone said:**
> drwxr**[COLOR="Red"]-[/COLOR]**xr-x That's not group-writable. Chmod 775 (or chmod g+w) should do it - unless I'm missing something about the question... :confused:

---

### Post by Morbius1 on 2013-02-04
You may have created a samba share and given the user and his group write access but nobody told Linux about it:
> drwxr-xr-x  2 shared users     4096 2011-08-11 12:54 EW Filename"shared" has read/write access - rwx
"users" has only read access - r-x

Change permissions on the folder:
```
sudo chmod 775 /path/to/folder
```
[COLOR=Blue]EDIT: What are the chances of simultaneous posts with the same content. Sorry about that.[/COLOR]

---

### Post by cjhabs on 2013-02-04
> **beengone said:**
> Ubuntu Server 10.04I have a folder at /home/shared that has write privilidges to the 'users' group. I created a new user and put her in the users group. But, she doesn't have write access. 

I'm accessing the machine through SSH and can write to the folder if I close and open a new session with a different user.

I must be missing something simple here. Thanks.

EDIT: BTW, I did search around and this is really common, but nothing seems to fix it. 

Example entry when I do "ls -l"
drwxr-xr-x  2 shared users     4096 2011-08-11 12:54 EW Filename

and "id"
uid=1009(username) gid=100(users) groups=100(users)

the group "users" does not have write access, only the user "shared" does.
You need to add write access to the group with:
chmod g+w 'EW Filename'
You will need to sudo that if you are not the owner "shared"

---

### Post by beengone on 2013-02-04
OOF. Well, that throws a bigger wrench in. This is shared out via Samba and all other Windows users have access. None are redirected as Shared. So, what am I missing here? I'm using Webmin and added this new user through that just like all the others - or so I thought. Whatever I need to change should have to do with this user then, right?

I thought I was able to write to that directory directly via any user, but that was incorrect. So, there's a Samba problem somewhere. How can I compare a working Samba user account to this one so I can see if there are differences? 

Suddenly this is a differnt problem.

---

### Post by Morbius1 on 2013-02-04
> and all other Windows users have accessThe only way I can think of at the moment that would do that and still prevent one user access is if you are using a "username map" in smb.conf and are mapping each user to the local server user "shared" but forgot to add this one particular user to the file.

---

### Post by beengone on 2013-02-04
username map = /etc/samba/user.map

That file is totally empty.

---

### Post by Morbius1 on 2013-02-04
Then clearly I'm not the right person to answer this question. There is usually no ambiguity to this:
> drwxr-xr-x  2 shared users Only one user will get write access and that's "shared". "shared" may be the user name you created and are making your windows clients use to authenticate to the share but there's no way that some jamoke sitting at a Win7 machine is going to gain access passing the user name morbius. Unless of course you used a "force user = shared" but then everyone on the network would be converted to shared and there would not be a problem.

Sorry, I'm at a loss.

---

### Post by beengone on 2013-02-05
> **Morbius1 said:**
> Then clearly I'm not the right person to answer this question. There is usually no ambiguity to this:
Only one user will get write access and that's "shared". "shared" may be the user name you created and are making your windows clients use to authenticate to the share but there's no way that some jamoke sitting at a Win7 machine is going to gain access passing the user name morbius. Unless of course you used a "force user = shared" but then everyone on the network would be converted to shared and there would not be a problem.

Sorry, I'm at a loss.

I'm lost too and no one else has chimed in after you. This doesn't make any sense to me.

Maybe I should remove the Linux and Samba user and start from scratch. Could someone walk me through that? Maybe I screwed something up along the way. Although, that still doesn't answer why the others can get in. So, so confused.

Any suggestions at all?

---

### Post by beengone on 2013-02-05
> **cjhabs said:**
> the group "users" does not have write access, only the user "shared" does.
You need to add write access to the group with:
chmod g+w 'EW Filename'
You will need to sudo that if you are not the owner "shared"

This might be the best way around. What is 'EW Filename'? 

If I'm not mistaken, I need to do 

```
chmod g+w -R /home/shared
```

Is that correct? That will give the group 'users' read/write access to the /home/shared directory and all its contents, right?

---

