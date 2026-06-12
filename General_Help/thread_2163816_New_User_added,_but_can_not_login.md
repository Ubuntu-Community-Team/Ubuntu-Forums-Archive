---
title: "New User added, but can not login"
date: 2013-07-19
forum: General Help
---

### Post by satyamM on 2013-07-19
I know it is a very common problem and I might be re-creating a thread which might be existing but I wasn't able to find one. 

So I am adding a user by following procedure:

**useradd satm**
**passwd satm**
**usermod -d -m satm**   (this is for creating the home directory of new user, although I do not see it in **/home/** after issuing this command) :confused:


But it is not able to login at the login screen....I know there might be some problems with groups...I might have not added this user to a group needed...or there might be something else.

I want help..

---

### Post by steeldriver on 2013-07-19
AFAIK, the usermod -m option is for moving an existing home directory's contents to a specified new home e.g. 

```
sudo usermod -d /home/newuser -m olduser
```

You could manually create /home/satm and then run usermod -d (without the -m) 

```

sudo mkdir /home/satm

sudo addgroup satm

sudo chown satm:satm /home/satm

sudo usermod -d /home/satm satm

```

but to be honest, it would probably be easiest if you deleted the new user and then create it again using **adduser **instead of the (low level) useradd - by default that *does *create the home dir iirc, as well as a suitable user private group, and also populates the account with sensible defaults from /etc/skel (such as a working .profile and a .bashrc)

---

### Post by TheFu on 2013-07-19
Why not make the user HOME directory manually?  If that directory doesn't exist, I think you cannot login.

```
sudo mkdir /home/satm
sudo chown satm.satm /home/satm
sudo chmod 755 /home/satm
```

I'm fairly certain that addusr only updates the /etc/passwd and /etc/group files.  I've always manually created HOMEs for new users except the 1st user created during an install.  Perhaps I've been doing it wrong all these years?

---

### Post by satyamM on 2013-07-19
**adduser **did everything!!! :D  Cheers! :D

So I understand few things here:

1. There should be a home directory for the new user inside /home
2. There should be a group with same username as of user's owner of which will be the same user.
3. By **usermod -d** , you made the home directory of **user** satm to be /home/satm....right? 


I checked actually by following this longer method **instead of adduser**, and yeah...it worked. I was able to login.! :)

Thank you steeldriver.

---

### Post by satyamM on 2013-07-19
> **TheFu said:**
> Why not make the user HOME directory manually?  If that directory doesn't exist, I think you cannot login.

I'm fairly certain that addusr only updates the /etc/passwd and /etc/group files.  I've always manually created HOMEs for new users except the 1st user created during an install.  Perhaps I've been doing it wrong all these years?

Guess what? Yes, you were following a long way.! :D

**adduser** does everything.....Creates a home directory....a group.....sets your password.....prompts for receiving all your information....like Name, Work and Home phone no.s and other stuff.!..And you are done!.. :D

Cheers.. :)

---

### Post by TheFu on 2013-07-20
> **satyamM said:**
> Guess what? Yes, you were following a long way.! :D

**adduser** does everything.....Creates a home directory....a group.....sets your password.....prompts for receiving all your information....like Name, Work and Home phone no.s and other stuff.!..And you are done!.. :D

Cheers.. :)

Perhaps.  However, last week I used adduser and it didn't. Over the last 15 yrs, I've added users with it and had to manually create HOME directories lots of times.  I must be specifying too many options as inputs to the command, so it assumes I want manual control over everything.  I need to **check the man page** for adduser, which certainly explains everything.

The location of the HOME for each user is set inside the /etc/passwd file. It can be anywhere.  Often, it is under /home/, but that is NOT a requirement.

Debian or Ubuntu started the *create a group to match the userid* thing. This is also unusual to me.  For a long time, there was a default group "users" that everyone was placed into. On single group systems, this was fine, but as more and more different groups were added to the same server, the group became larger than people understood and files meant to be shared with 5 people were being shared with 500 users.  Overall, this change was a good thing, but having 500+ groups on a server seems outrageous to me.

Were I work, we add groups for every different project hosted on a server and use the g+sticky bit to ensure the group remains correct down the path.

Alas, that is way off-topic.

---

