---
title: "[SOLVED] recompile to Autologin as root?"
date: 2008-01-16
forum: General Help
---

### Post by quandary on 2008-01-16
Hi!

I'm trying to enable autologin for the user "root". ;-)

I'm already logged in as root, and it worked for over a year now.

Finally, out of convenience, I want to enable autologin. 
It works for a normal user, but when I start gdmsetup, go to the tab security, then click "enable Automatic login" and in the field username type "root", a Message appears saying:
```

USER NOT ALLOWED
Autologin or timed login to the root account is forbidden.

```

I searched Ubuntuforms and google, but so far didn't found a solution.

Then i searched for the source for gdmsetup and found the package "gdm".

So far I managed to get the dependencies for the gdm package, and to compile.

Now i found in /gui/gdmsetup.c the following lines:
```

	if (user_uid == 0 || user_uid < GdmMinimalUID) {
		/* we can't accept users that have uid lower
		than minimal uid, or uid = 0 (root) */
		gchar *str;
		GtkWidget *dialog;
		GtkWidget *setup_dialog;
		
		if (gdm_user_uid (new_val) == 0)
			str = g_strdup (_("Autologin or timed login to the root account is forbidden."));
...

```

Now I concluded, that if i change:
```

if (user_uid == 0 || user_uid < GdmMinimalUID)

```
to
```

if (user_uid < GdmMinimalUID)

```

and do a ./configure, make, make install, then i would be able to AUTOlogin as root.

However I am not sure if that is gonna work, because:
1.  it maybe autologin as root is forbidden there because it crashes the system
2. i don't know what GdmMinimalUID UID is, and whether 0<GdmMinimalUID evaluates to true...

Any hints on that?

---

### Post by quandary on 2008-01-16
Oh, i found via google (GREP didn't found anything...)
#define GDM_KEY_MINIMAL_UID "greeter/MinimalUID=100"

looks like i've to replace that with 
```

if (false)

```

edit: Correction: it's C so no false exists:
```

if (0)

```

---

### Post by jken146 on 2008-01-16
Why don't you just boot in single user mode?

By the way, it's not at all advisable to be root for anything other than strictly administrative tasks.  I find sudo most adequate.

---

### Post by bodhi.zazen on 2008-01-16
Thread closed (please don't flame quandary).

FYI (if you are reading this) **Logging in as root is NOT necessary in Ubuntu, please use sudo or gksu**

---

