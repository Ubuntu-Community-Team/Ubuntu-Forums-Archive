---
title: "User being demoted to standard user"
date: 2016-06-21
forum: General Help
---

### Post by daryl9 on 2016-06-21
I did a fresh install of Edubuntu 14.04.3.  I created a user during install, and after the installation was completed, I logged in with that user. Initially, the user was an Administrator.  But, after some point in time, the user became a standard user.  How did this happen, how do I keep this from happening again, and how do I promote this user back to Administrator?

Thank you.

Daryl

---

### Post by X-RED_Tech on 2016-06-21
> **daryl9 said:**
> Initially, the user was an Administrator.  But, after some point in time, the user became a standard user.  How did this happen, how do I keep this from happening again, and how do I promote this user back to Administrator?

No, it can't be. Someone with the sudo password did it.
Are there other users already configured?

---

### Post by daryl9 on 2016-06-21
I'm the only user on the system and I didn't do it, at least not intentionally.  Please explain how I could have accidentally demoted my user, and if I do it again, how to re-promote the user.

Thank you.

Daryl

---

### Post by QIII on 2016-06-21
Are you the only person with physical access to the machine?  Is your machine exposed to a network?  Is your machine firewalled?  Do you use SSH with a password?

---

### Post by daryl9 on 2016-06-21
I am the only one with access to the machine.  So....how would this happen?  How does the user get demoted, and how to re-promote the user to administrator?

Thank you.

Daryl

---

### Post by QIII on 2016-06-21
Other than the user being removed from sudoers by another user with such privileges, it's hard to think of a way under normal circumstances where this could happen.

How about your network access? LAN, WLAN, type of security, shared access?

---

### Post by &amp;KyT$0P# on 2016-06-21
Also how are you determining whether the user is an Administrator or not?

---

### Post by QDR06VV9 on 2016-06-21
> **daryl9 said:**
> I'm the only user on the system and I didn't do it, at least not intentionally.  Please explain how I could have accidentally demoted my user, and if I do it again, how to re-promote the user.

Thank you.

Daryl
Could not say for sure in this case but I have seen where using a GUI application using sudo to open the said app will do something similar. 
Just a possibility.

---

### Post by daryl9 on 2016-06-21
> **QIII said:**
> Other than the user being removed from sudoers by another user with such privileges, it's hard to think of a way under normal circumstances where this could happen.

How about your network access? LAN, WLAN, type of security, shared access?

Again, I am the only one with access to this machine.  This happened all by itself.  

> **halogen2 said:**
> Also how are you determining whether the user is an Administrator or not?

When I first installed the OS, in Users Accounts, the Account Type is "Administrator".  After a while of using the system, I go to install updates, and I am prompted for a password.  I enter in the password for the user, and I get an accesses denied.  After reading the wording closer, I realize that its asking for the "root" password, not the user password.  I review the user account, and the Account Type was changed to "Standard".  This has happened more that once today.  I've re-installed about three times, and this has happened on at least the first two installs

Again.  I ask.  How do I re-promote the user to administrator?  I just looked in the sudoers file, and this user is not in the sudoers file, so that is not what gives the user administrator privileges.  Where is this set?  

Thank you.

Daryl

---

### Post by &amp;KyT$0P# on 2016-06-21
It's controlled by which groups the users are part of.
In your user manager, compare the groups the administrator account is part of to the groups the "demoted" account is part of.  Then try the method you know of to re-promote the demoted account, and compare groups again.  Then log out the demoted account and log it back in.  Compare again.

Does this shed any useful light?

(BTW, are you using i386 or amd64 ISO?  If this isn't solved soon, I might make a test install in VirtualBox if I get the chance, and see if I can reproduce the problem...)

---

### Post by QIII on 2016-06-21
Perhaps we are not being clear.  This did not happen all by itself.  It was made to happen either by you or by someone else, and that either purposefully or by mistake.  Your machine only reacts to commands/inputs as it is designed and programmed to.  It does not make arbitrary decisions such as this.

If you would care to let us help you, it would be in your best interest to provide diagnostic information as requested.

Be that as it may, if you want to regain your privileges without looking at why you lost them, [this]("http://www.psychocats.net/ubuntu/fixsudo") should be helpful, even if only to give us an indication of what else may be necessary.

---

### Post by daryl9 on 2016-06-21
> **halogen2 said:**
> It's controlled by which groups the users are part of.
In your user manager, compare the groups the administrator account is part of to the groups the "demoted" account is part of.  Then try the method you know of to re-promote the demoted account, and compare groups again.  Then log out the demoted account and log it back in.  Compare again.

Does this shed any useful light?



I just figured that out.  I was adding my user to the "users" group via the usermod command.  I don't know where  in the GUI groups are modified.  I only see a single user in the users account, no groups or anything else.  Can my user not belong to any group other than what it was created with?

Thank you

Daryl

---

### Post by daryl9 on 2016-06-21
It appears that I have to be in the "sudo" group in order to be an Administrator.

Daryl

---

### Post by steeldriver on 2016-06-21
What was the exact usermod command that you used?

A user can only have one primary group (usermod -g), but may belong to as many supplementary groups as you like (usermod -G)

A common mistake weh using `usermod` to add supplementary groups is to forget the `-a` (or `--append`) flag - as explained in the manual page:

```

       -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
           A list of supplementary groups which the user is also a member of.
           Each group is separated from the next by a comma, with no
           intervening whitespace. The groups are subject to the same
           restrictions as the group given with the -g option.

           [B]If the user is currently a member of a group which is not listed,
           the user will be removed from the group. This behaviour can be
           changed via the -a option, which appends the user to the current
           supplementary group list.[/B]

```

In other words, you need to do

```

sudo usermod -[COLOR=#0000ff]**a**[/COLOR]G newgroup user

```
rather than 
```

sudo usermod -G newgroup user

```
to add to (rather than replace) the user's supplementary groups

I tend to prefer the `gpasswd` command, which doesn't have the same gotcha

```

sudo gpasswd --add someuser somegroup

```

---

### Post by &amp;KyT$0P# on 2016-06-21
Glad you figured that one out! :)

EDIT Like steeldriver said as I was writing this post ;) usermod command is tricky and as you found out it can delete all secondary groups if not used exactly right.  In any Ubuntu flavor that doesn't have a good graphic user manager, I would recommend using [FONT=Courier New]adduser[/FONT] to manage groups.

---

### Post by daryl9 on 2016-06-21
> **steeldriver said:**
> What was the exact usermod command that you used?

A user can only have one primary group (usermod -g), but may belong to as many supplementary groups as you like (usermod -G)

A common mistake weh using `usermod` to add supplementary groups is to forget the `-a` (or `--append`) flag - as explained in the manual page:

```

       -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
           A list of supplementary groups which the user is also a member of.
           Each group is separated from the next by a comma, with no
           intervening whitespace. The groups are subject to the same
           restrictions as the group given with the -g option.

           [B]If the user is currently a member of a group which is not listed,
           the user will be removed from the group. This behaviour can be
           changed via the -a option, which appends the user to the current
           supplementary group list.[/B]

```

In other words, you need to do

```

sudo usermod -[COLOR=#0000ff]**a**[/COLOR]G newgroup user

```
rather than 
```

sudo usermod -G newgroup user

```
to add to (rather than replace) the user's supplementary groups

I tend to prefer the `gpasswd` command, which doesn't have the same gotcha

```

sudo gpasswd --add someuser somegroup

```


I was not aware of the -a to "append" the user to a group.  In other distributions, and Unix, using -G is all a person has to do.  I will keep this in mind moving forward.

Thank you.

Daryl

---

