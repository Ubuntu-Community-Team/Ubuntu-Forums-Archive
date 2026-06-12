---
title: "Permissions"
date: 2007-04-23
forum: General Help
---

### Post by Sabrage on 2007-04-23
I just installed Feisty Fawn and I love it! Howewer, I managed to mess up the permissions when trying to copy some files from my user to the guest user. Now when I log in as 'guest' I get this message:>  Users $HOME/.drmc file is being ignored. File should be owned by user and have 644 permissions.....blah blah..... Users $HOME directory must be owned by user and not writeable by other users.

I have tried changing the permissions for the guest folder (and clicked to apply the same to enclosed files): > Owner: Guest
Folder access:Create and delete
File access:---
Group: Guest
Folder Access Files
Others: (same as guest group)

But I still get this weird message when I log in as guest.....
What should the permissions for 'guest' be? I would like to just fix all the permissions for the guest folder and all the files....

---

### Post by spin2cool on 2007-04-23
Make sure guest owns the file:
```
sudo chown guest:guest ~/.drmc
```

and then make sure they have the appropriate permissions
```
chmod 644 ~/.drmc
```

---

### Post by Sabrage on 2007-04-23
Thanks spin2cool,

It worked! I added 'sudo' to the chmod command when it said that it couldn't find the directory, I was just guessing....:)

---

