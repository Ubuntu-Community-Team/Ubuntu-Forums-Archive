---
title: "Root privileges"
date: 2007-02-18
forum: General Help
---

### Post by damiros on 2007-02-18
Hello people.

I was wondering if its possible to create a user account for daily usage, that has all root priviliges and NEVER gets prompted for a password?

If there is a way to make this possible, i would be happy if someone explained how :) 

):P

---

### Post by llamakc on 2007-02-18
You should use the Search function of the forums. The answer is "yes".

---

### Post by Maestro23 on 2007-02-18
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by damiros on 2007-02-18
> **llamakc said:**
> You should use the Search function of the forums. The answer is "yes".

I had no luck searching :(

---

### Post by llamakc on 2007-02-18
> **damiros said:**
> I had no luck searching :(

Sorry for being gruff. I'm glad you tried.

The above link will help you.

---

### Post by gradedcheese on 2007-02-18
You sure can, but you really shouldn't.  Instead, I would disable the password prompt for 'sudo'.  This way, you will never be asked for a password, but you will still have to use 'sudo' to do dangerous things as before.  It's a good safety measure.

If you want to do this, open /etc/sudoers like this:

sudo gedit /etc/sudoers

and find the line:

```

%admin ALL=(ALL) ALL

```

and now replace it with:

```

%admin ALL= (ALL) NOPASSWD: ALL

```

Make sure you've done this correctly and carefully, and then save the file and close gedit.

---

