---
title: "Root, Sudo, Admin?? (Solved)"
date: 2006-10-22
forum: General Help
---

### Post by Forgott3n on 2006-10-22
Ok,

I have installed ubuntu dapper drake (I think). I login under 'justin'

I cannot locate or change important things like the time (I entered in password but I get an error with sudo or something).

I need to find the Synaptics Package Manager so I can install the basic package so I can compile programs.


Its not located under System -> Administration nor a lot of things.

It appears I have very limited access to what I can do. Please help.

---

### Post by meng on 2006-10-22
Do you understand sudo?
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
I'm not sure why you don't have Synaptic in your menu - one assumes that justin is the first user account that was created - you didn't happen to have another user account that you deleted?

---

### Post by newlinux on 2006-10-22
can you do 
```

gksudo synaptic
```

or try Applications->Add/Remove Programs (kind of synaptic "lite"  - you can click on Advanced to get full synaptic from there).

---

### Post by bikeboy on 2006-10-22
The very first user you create (during the install) has the right to use sudo, if you created the "justin" login after that you will not be able to use sudo with that user, unless you add him to the list of users allowed to do sudo. If that seems to be your problem, just post back here to find out how to add justin to the sudo list.

Sorry if that's confusing.

---

### Post by Forgott3n on 2006-10-22
Well I didnt pull the brightest move on the install:

[http://ubuntuforums.org/showthread.php?t=281755](http://ubuntuforums.org/showthread.php?t=281755)

So I had to create a user named 'justin' in recovery mode.

```
sudo adduser justin
```

So 'justin' prolly doesn't have rights. Can someone tell me how?

---

### Post by aysiu on 2006-10-22
```
sudo adduser justin admin
```

---

### Post by Forgott3n on 2006-10-22
> **aysiu said:**
> ```
sudo adduser justin admin
```


This will modify my current user 'justin'?

And can I do this in terminal or must it be in recovery mode like before?

---

### Post by aysiu on 2006-10-22
If your current user is not already in the *admin* group, then you will have to boot into recovery mode to do it (and you won't need the *sudo* prefix).

---

### Post by Forgott3n on 2006-10-22
> **aysiu said:**
> If your current user is not already in the *admin* group, then you will have to boot into recovery mode to do it (and you won't need the *sudo* prefix).

Ok, thanks, justin is now added into the admin group.

It works now. Thank you everyone.

---

