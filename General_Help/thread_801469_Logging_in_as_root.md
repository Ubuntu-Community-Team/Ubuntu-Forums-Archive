---
title: "Logging in as root?"
date: 2008-05-20
forum: General Help
---

### Post by kooldino on 2008-05-20
There are certain situations where I'd like to actually log in as root where sudo won't cut it (for instance, if I run a sudo command from someone who's not in the sudoers file).

How can I accomplish this without adding them to the sudoers file?

---

### Post by sdennie on 2008-05-20
I think that if you are logged into a non-admin account, you can still use su to get to an admin account:

```

su -l some_admin_account

```

Once there, you should be able to use the admin account as normal or create a root shell with:

```

sudo -i

```

---

### Post by knutschr on 2008-05-20
You can also start in recovery mode and give the command startx

---

### Post by kooldino on 2008-05-20
> **vor said:**
> I think that if you are logged into a non-admin account, you can still use su to get to an admin account:

```

su -l some_admin_account

```

Once there, you should be able to use the admin account as normal or create a root shell with:

```

sudo -i

```

I will give this a whirl.

---

### Post by kooldino on 2008-05-20
> **knutschr said:**
> You can also start in recovery mode and give the command startx

Yup, but it requires a reboot.  :(

---

### Post by p_quarles on 2008-05-20
Thread closed, as root logins are not supported in Ubuntu. See the following thread for the reasoning:
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

To get a root shell:
```
sudo -i
```
As already mentioned, the su command can be used to switch to a sudoer on the fly in the shell/terminal emulator.

---

