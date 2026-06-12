---
title: "New user home folder permissions"
date: 2008-04-22
forum: General Help
---

### Post by vishnumrao on 2008-04-22
I created a new user login on my Hardy install. However I do not wish to share my home folder with the new user. But that is not the case at present. The new user is able to view the contents of the home of the administrator.

How do I set permissions such that the home folders of each user is only accessible to the individual users(and ofcourse, the administrator).

---

### Post by sdennie on 2008-04-22
You should be able to something like:

```

sudo chmod 0700 /home/some_user

```

That will make it so only the owner of that directory can see anything in it.

---

### Post by chrisccoulson on 2008-04-22
Also, if you want to change the default permissions for home folders that are created in the future, I think you can set the permissions in /etc/adduser.conf

---

### Post by vishnumrao on 2008-05-01
Thanks for your replies. And sorry for my delayed response. I have been away from my system for a while now.

Vor, 
Your suggestion worked. 

But I am interested in a more general method of setting permissions. The second reply by chrisccoulson, did not work. 

But thanks for your replies.

---

### Post by sdennie on 2008-05-01
I believe that chrisccoulson is correct in that changing DIR_MODE from 0755 to 0700 in /etc/adduser.conf will cause any *new* user that is created to have their home directory only readable by themselves.

---

### Post by vishnumrao on 2008-05-03
I get it. So changing 0755 to 0700 in /etc/adduser.conf would work only for new users created after changing the file! Hmm...

I thought changing the conf file would automatically alter the permission of all existing users home folders also. Maybe the OS designers should make it that way. Just a thought.

Thanks for the clarification.

---

### Post by Francewhoa on 2009-10-08
Tutorial can be found at [http://swiss.ubuntuforums.org/showthread.php?t=976610](http://swiss.ubuntuforums.org/showthread.php?t=976610)

---

