---
title: "import thuderbird settings from thunderbird root account?"
date: 2007-09-06
forum: General Help
---

### Post by sdowney717 on 2007-09-06
I setup my thunderbird when I was logged in as root.
Now I would like to simply take all my settings, email from this root account and have them showing when I log in as myself, a regular user.

I tried copying the .thunderbird folder, but that killed thunderbird completely and I had to undue the copy in order to even start it again.

So, do you export from one thunderbird and then import to another?

---

### Post by EndPerform on 2007-09-06
The problem here is permissions.  The root .thunderbird is owned by root itself, so when you copied it to your home directory, Thunderbird died because it could not access the folder.  What you need to do is change the permissions once you perform the copy.  Copy the folder, then do:

```
sudo chown -R username:username /home/username/.thunderbird 
```

Replace username with your username, of course.  That should fix it.

---

