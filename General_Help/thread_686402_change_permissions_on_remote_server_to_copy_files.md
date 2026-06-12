---
title: "change permissions on remote server to copy files"
date: 2008-02-03
forum: General Help
---

### Post by Jason Weiss on 2008-02-03
I am so tired and i have been working on this all day. 

I know this is so simple but it is nealy midnight and I need to work tomorrow :(

I am trying to set up zen cart for a fiend, I have set up a ssh server on tash@192.168.1.109
 and I am trying to copy the zencart files to /var/www/

but of course that is a secure folder. 

how can I change the permission on that folder so that I can just copy to and from that folder super easily?

---

### Post by .nedberg on 2008-02-03
Easies way, but not very secure:
```

sudo chmod 777 /var/www

```

Better, but not the best:
```

sudo chown username:username /var/www

```

Or:
Find out what group the owner of /var/www belongs to and add yourself to that group. Give that group write access to /var/www if it does not have it already

I _think_ the last way is the right way (tm)

---

### Post by Jason Weiss on 2008-02-04
> **.nedberg said:**
> Find out what group the owner of /var/www belongs to and add yourself to that group. Give that group write access to /var/www if it does not have it already

I _think_ the last way is the right way (tm)

Hmm is there an easy way to do this via command line?

---

### Post by .nedberg on 2008-02-05
Humm

As I am now close to my Ubuntu server I see that /var/www belongs to root. Not a good idea to add yourself to that group. What you could do is to make a new directory under /var/www

```

sudo mkdir /var/www/somedir

```

then chown that directory

```

sudo chown yourusername:yourgroup /var/www/somedir

```

then [http://localhost/somedir](http://localhost/somedir) will be the URL to use and you will be able to copy files freely to that place with your user.

Another way would be to make a new Apache config, but I dont't know how to do that...

---

### Post by nemilar on 2008-02-05
What I did, to be able to easily move files in/out of my /var/www folder, was:

```
chown :jdeprizi /var/www
chmod g+rxw /var/www

```

jdeprizi being my user's group.  The first command changes the folder's group designation to my group, and the second adds read/write/execute privileges for the members of that group (me).

If there's more than one user that needs to be able to quickly move things in/out of /var/www, then you should create a separate group for those users.

---

### Post by Jason Weiss on 2008-02-05
> **nemilar said:**
> What I did, to be able to easily move files in/out of my /var/www folder, was:

```
chown :jdeprizi /var/www
chmod g+rxw /var/www

```

jdeprizi being my user's group.  The first command changes the folder's group designation to my group, and the second adds read/write/execute privileges for the members of that group (me).

If there's more than one user that needs to be able to quickly move things in/out of /var/www, then you should create a separate group for those users.

OK I think this is the permenant solution i am after. 

So how do I know what group i am in?

---

### Post by .nedberg on 2008-02-06
```

groups

```
will give you your groups

---

