---
title: "Admin problems - Admin account gone"
date: 2008-01-08
forum: General Help
---

### Post by TSBonLinux on 2008-01-08
Sorry if this was posted already, but I am in school right now listening to my teacher blabbing about what is going on 2nd semester and I don't know what to use to search for this.

I am setting up an old HP computer for my grandparents and I installed Xubuntu 7.10 on it. Now my grandfather is a nosey person and I am afraid he will go/do something he shouldn't and screw things up. I decided to keep him from doing something udderly destructive that will have me called every week, I was going to have him as a user and set up an admin account. This is where problems started...

I set up an admin account (with the 'admin' group set for it), then changed administration properties off on his account then saved everything. I restarted to install the updates that were downloading while I did this, but when I got back on, Admin was missing! (I had one of the login setups that has a user browser to show all the accounts for the sake of simplicity...) I thought maybe it was because Admin doesn't show up on user browsers so I tried logging on as Admin, but it said the password was wrong. I tried EVERY password that I knew and it wouldn't worked. I can't fix it on his account because he doesn't have admin privliges... Can someone please help? I rather not reinstall it all again with updates, so if there is a way I can reset the accounts, that would be awesome.

---

### Post by Bliepo32 on 2008-01-08
You could try recovery mode. In recovery mode, you will become root automatically.

---

### Post by bodhi.zazen on 2008-01-08
Once you boot to recovery mode :

1. Add user to admin :

```
addgroup <username> admin
```

2. Set the user password (if needed)

```
passwd <username>
```

In both <username> = the name of the user to add to admin and set password

---

### Post by TSBonLinux on 2008-01-08
Sweet! Thanks again guys and I am sorry for posting without searching. I was posting while the teacher was turned the other way ^_^" You think I could look for help in a class about computer repair, but apparently what he had on the overhead was much more important....

---

