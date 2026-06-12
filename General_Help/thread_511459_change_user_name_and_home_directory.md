---
title: "change user name and home directory"
date: 2007-07-27
forum: General Help
---

### Post by aum11 on 2007-07-27
I am passing my laptop to a friend and I wish to change the user name and home directory name into his name.

How can I safely do this please?

---

### Post by aysiu on 2007-07-27
I think this can be done safely through system > Administration > Users and Groups

---

### Post by aum11 on 2007-07-27
I can see that I can change the users name, but what about changing the name of the directory.

Earlier I did this via mv /home/oldname /home/newname

and I could no longer login.

Suggestions?

Thanks

---

### Post by HermanAB on 2007-07-27
Don't try to rename a user account.  It won't work properly.

Make a new user account and copy any data that you want to give him over as well, then delete the old account.

---

### Post by aum11 on 2007-07-27
Is there any problem with privileges after the copy?

sudo cp /home/olduser /home/newuser    ?

Thanks

---

### Post by HermanAB on 2007-07-27
Don't copy the whole home directory, then you are back where you started - things won't work.  There are many important and hidden directories and files in the home directory.  Only copy the data over that you really need to copy over - if anything.

As you figured out already, you would need to use 'sudo cp' to copy the data.  Then afterwards, use 'sudo chown' to change the ownership of the data you copied.

'Hope that helps!

Herman

---

### Post by dando80 on 2007-07-28
If your friend wants to get your entire config including application preferences etc...

cp -r /home/user1 /home/user2

chown -R user2:user2 /home/user2

---

### Post by eeried on 2008-02-12
Adding a new user with administrative privileges doesn't seem to work properly in Gutsy. I got a lot of errors when I logged in after logging out from the old account.

NB: when I chose "Administrator" in the new user window, the new user wasn't created. So I created an ordinary user and then added "administration" to the list of privileges.

Well, perhaps I messed everything up because in the first place I changed the user  name, and kept the old user home name since it was impossible to log in after that. I deleted all the hidden files. Then I was able to log in. But I understand this isn't how it should be done. A bit tricky...

Can't you just edit /etc/passwd?  see [http://ubuntuforums.org/showthread.php?t=683566](http://ubuntuforums.org/showthread.php?t=683566)

---

