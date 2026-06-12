---
title: "restricted characters in username (workaround)"
date: 2007-10-21
forum: General Help
---

### Post by franzix on 2007-10-21
I'm trying to use my ubuntu box with windows active directory authentication.  The problem:  my domain uses first.last as username.  I can add users with "useradd" that allow periods in the name, but cannot use the gui tools for group membership, etc.  Can anyone help me to workaround this character restriction?

---

### Post by fragos on 2007-10-21
Try putting the name in quotes as in "first.last"

---

### Post by franzix on 2007-10-25
no go.  same error message.  thanks for the response.

Please set a valid user name consisting of a lower case letter followed by lower case letters and numbers.

---

### Post by fragos on 2007-10-25
The only other suggestion I have is substitute "%2E" for "."

---

### Post by mahousaru on 2007-10-25
Are you using your Ubuntu box to store the accounts to be accessed via samba?

If so I would recommend using a nifty samba global setting in /etc/samba/smb.conf like:

```

username map = /etc/samba/usermap

```

in the file /etc/samba/userman

```

dohjohn = "doh.john"

```

This allows you to use sensible user names in the Linux environment, but map over to the Windows ones.

---

