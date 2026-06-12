---
title: "Permissions changing on shared partition - multiple OS"
date: 2008-04-21
forum: General Help
---

### Post by Perpetual on 2008-04-21
I must be doing something wrong.  I have 4 Linux OS's on my laptop and a partition that is shared, /media/MyData.  I set the permission to the user 

```

sudo chown -R landon:landon /media/MyData
sudo chmod -R 755 /media/MyData

```

but when I boot into any of the other OS's I have to do the above again to regain permissions.  When I go back to the original OS, I have to do it again.  It's a vicious circle which leads back to me doing something wrong.  Is there a way to make set the permissions universally despite which OS I am using?

Thanks,

Landon

---

### Post by Rocket2DMn on 2008-04-22
It could be that the user IDs are different across the distributions.  Setting the username to have the same ID may solve the problem.  Ubuntu uses ID of 1000 for the first user, whereas some other distros might use 500 or something else.  You can try changing the ID using usermod.  I think the user needs to be logged out, so reboot into the recovery kernel for EACH install and run
```
usermod -u 1500 <username>
```
I chose 1500 since it is out there is probably not used by anybody else on any installation that you have.

Then reboot normally.

ALTERNATIVELY, it seems that you can make a group in each of the installs, using the same method for the group IDs, then add your user to that group in each install.  Just don't forget to use group permissions when you chmod - ie 775 instead of 755.  Using groups may be the preferred way to do this since you don't have to fiddle as much with your username (other than adding them to the group) - see [http://linux.die.net/man/8/groupmod](http://linux.die.net/man/8/groupmod)
```
sudo adduser <username> <groupname>
```

If you would like me to walk you through that, I can do so.

---

### Post by Perpetual on 2008-04-22
Rocket2DMn, I can't find the 'thanks' button so...thanks!  Looks like it's a little more than I was expecting (hoping) for but right now I am at work and on my Windows computer so I will have to look into it as I get a chance.  

I was hoping that because I am the only user on each install and use the same user name it would work ok.  Of course not :)

I will let you know if I need more help.

Thanks!

Landon

---

