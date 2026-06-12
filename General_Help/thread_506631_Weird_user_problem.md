---
title: "Weird user problem"
date: 2007-07-21
forum: General Help
---

### Post by sefs on 2007-07-21
I am trying to create a user on ubuntu feisty 7.04

It tells me that the username already exists to choose another.

However when I go into main menu -> adminstration -> users and groups  and the user dialog comes up ... there is no user listed under the user name i am trying to create.

So something is very wrong here.

How do I rectify this if possible.

Thanks.

---

### Post by ]Nbx*cmD[ on 2007-07-21
Open a console and try the following:

```

sudo userdel username

```

where "username" is the name of the user you want to create, this will erase it if it actually exists.

To create a new user account do:

```

sudo adduser username

```

That should work, somethime GUIs have weird behaviour...

---

### Post by sefs on 2007-07-22
I think this is the result of a bug in nxserver_3.0.0-63_i386.

I have confirmed that is must be a bug in nxserver_3.0.0-63_i386.
I have reproduced the behaviour in ubuntu 7.04 and a fresh install 
of ubuntu 7.10.  What happens is that somehow the nxserver does not
do a very good job of creating the nx user.  It seems to create a 
fragment (corrupted version) of this user.  After full installation
of nxserver when you open system -> administration -> users and groups
There is no nx user listed.  Suggesting that nxserver did not create 
this user. If I then go to manually create the user, then ubuntu reports
that the user already exists. If I remove nxserver_3.0.0-63_i386. Then
it also removes this partially installed nx user.  And I can again manually
create a user with username nx.  This problem is not present in
nxserver_2.x verions, as the nx user is created fine with this previous 
version.

Can anyone else confirm this behavior if possible?

---

### Post by sefs on 2007-07-22
I had to delete the half installed nx system account (created by nxserver) via the cli like you suggested, as it cant be done via the gui, since the nx account is not shown in the gui at all.

I then recreated the system account nx and nx Group. I temporarily had to set the home dir to /home/nx and the shell to /bin/bash.

After deleting the corrupt nx account earlier  the files under /usr/NX that had owner nx were changed to a user with uid 118.

i then use the command "find /usr/NX -uid 118" which gave me a list of all the the files that should be owned by the nx system user that are currently now owned by some user with uid 118.

I then "sudo chown nx:root /usr/NX/filetomodify"  all of these files.

Finally I went into the gui for nx user i had to create manually and change its homdir to /usr/NX/home/nx and its shell to /usr/NX/bin/nxserver.

After these changes, then I was successfully able to connect to the nxserver with an ssh server set only to aunthenticate with keys.  ie. userPAM = no and passwordauthentication = 0

---

### Post by ]Nbx*cmD[ on 2007-07-22
Glad it helped you a little :)

---

