---
title: "Mounting w/o Password Prompt"
date: 2008-02-19
forum: General Help
---

### Post by dlcho on 2008-02-19
I am new to Xubuntu and I am trying to mount a Windows shared directory.  The following command works:

```

sudo mount -t cifs //windowsserver/share /mnt/mountdir -o username=windowsuser

```

I get promted for the password of the Windows user and everything seems to work from there.  The problem is I want to have this mount available to all users so I don't want to be prompted for the password every time.  When I try something like this:

```

sudo mount -t cifs //windowsserver/share /mnt/mountdir -o username=windowsuser,password=windowspassword

```

I get a permission denied error.  I get the same error using a credentials file as well.

How can I make it so this mount is created for all users without being prompted for a password?  Thanks for any help.

---

### Post by dlcho on 2008-02-19
OK, even though it doesn't work at the command line as I described, when I add an entry in fstab, it works.  Thanks to anyone who look at my post and thought about it.

---

