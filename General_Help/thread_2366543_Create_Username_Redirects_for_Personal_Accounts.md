---
title: "Create Username Redirects for Personal Accounts"
date: 2017-07-19
forum: General Help
---

### Post by cclloyd9785 on 2017-07-19
Is there a way I could make usernames redirect to a certain user on Ubuntu?  

For example, when I ssh into my ubuntu server from mac, it uses my name capitalized.  But on the server my name is lowercase, causing a username mismatch.  

Is there a way that when it tries to log in as *Username* it instead tries to log in as *username*?

---

### Post by steeldriver on 2017-07-19
For SSH specifically, yes there is: create an entry in your ~/.ssh/config file

Since that would be on the mac side, see for example [OSXDaily: Setup an SSH Config File](http://osxdaily.com/2011/04/05/setup-ssh-config-fie/)

Hope this helps

---

### Post by TheFu on 2017-07-19
Userids are case sensitive to Unix-based OSes, but historically, across all Unix-based OSes, userids have been lowercase.  My recommendation is to fix the name on OSX.

This isn't a 'checkbox' solution.

The pam_regex module should be able to handle it. Be certain to create a new user account to perform any testing AND a backup all-lowercase account that you can use to get in when the transform rule isn't working correctly.  If you aren't comfortable hacking into the machine after screwing this up (and I would expect it to take me 3 attempts), then perhaps attempting this isn't a good idea.

---

### Post by Tadaen_Sylvermane on 2017-07-19
could just ssh "$USER"@"$SERVER". user being the proper user. Instead of just ssh "$SERVER"

---

### Post by TheFu on 2017-07-19
> **Tadaen_Sylvermane said:**
> could just ssh "$USER"@"$SERVER". user being the proper user. Instead of just ssh "$SERVER"

Or setup the translation in your ~/.ssh/config file on the client-side.  I'd be careful using $USER, since that specific env variable is already used.

---

### Post by Tadaen_Sylvermane on 2017-07-19
didnt mean it literally. meant whatever user he is wanting to use. without knowing his username i can't suggest what to put there.

would ssh youruser@yourserver be more correct?

---

### Post by TheFu on 2017-07-19
```
$ env |grep USER
```
will show my point.  We don't always know what an poster here will read into our posts.

---

