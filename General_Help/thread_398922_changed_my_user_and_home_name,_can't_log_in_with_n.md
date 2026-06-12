---
title: "changed my user and home name, can't log in with new name"
date: 2007-04-01
forum: General Help
---

### Post by grantm on 2007-04-01
yup the title says it all.

I changed my user name and home dir in the user account editor and now I can't get back into the gui to put things back the way they were.

I get an error message at the GDM login screen that says

**$HOME/.dmrc  the file name should be owned by user**

Now I know I should be able to get under the hood somehow (root) and put things back the way they were via the terminal but I cannot find the info in my ramblings

I probably have to edit a file.

thru the terminal I created another user so I could get graphical access to the gui for changing user info but I can't get root power thru that new user

aaarrrgh  please assist

Grant

---

### Post by dreadlord_chris on 2007-04-01
> **grantm said:**
> yup the title says it all.

I changed my user name and home dir in the user account editor and now I can't get back into the gui to put things back the way they were.

I get an error message at the GDM login screen that says

**$HOME/.dmrc  the file name should be owned by user**

Now I know I should be able to get under the hood somehow (root) and put things back the way they were via the terminal but I cannot find the info in my ramblings

I probably have to edit a file.

thru the terminal I created another user so I could get graphical access to the gui for changing user info but I can't get root power thru that new user

aaarrrgh  please assist

Grant

Sounds like the new user's $HOME folder permissions didn't get created properly.
In all the following substitute <USER NAME> for the user name in question (w/out the <>).

To start boot into Recovery Mode.
First we'll check that user's $HOME perms:
```

ls -la /home/<USER NAME>

```

This will list the contents of that folder. In the 3rd & 4th columns you'll see the user and group that owns them - you should see the user's name listed in both columns for everything except **..** which should say **root  root**.
If that's not the case then enter this:
```

chown -hR <USER NAME>:<USER NAME> /home/<USER NAME>

```
That will change the user & group ownership to <USER NAME> for all files & folders in there.

Now, to give the new user access to sudo:
```

useradd --groups admin <USER NAME>

```
This will add that user to the **admin** group, giving it access to sudo

You *should* be able to reboot & log in to the new user account now.

HTH

---

### Post by grantm on 2007-04-01
it is working!

thank you doesn't seem good enuf

I am stress free ... for now

THANK YOU!!!

---

