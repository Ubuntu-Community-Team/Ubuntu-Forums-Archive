---
title: "Lost stored passphrase from &quot;Passwords and Keys&quot; (seahorse)"
date: 2017-09-12
forum: General Help
---

### Post by Z-Blocker on 2017-09-12
Hi,

Today I came to the horrible conclusion there is no "undo" function in seahorse.
By accident I removed (instead of copying) the string that represents a password in seahorse.
As the string was a passphrase to unlock the secret key of some Bitcoins I am seriously worried.
Seems that should not have trusted seahorse to reliable.

---

### Post by Z-Blocker on 2017-09-12
To reproduce this problem:

First assume you have a very important passphrase or password.
Do not do this with something that is important to you or you might end up like me, loosing data or money.

Start seahorse and click the + button.
Select "Stored Password".
Add a description and the passphrase.
Close the window and stop seahorse.

Now you do an action where you need the password.

Start seahorse
Search the right stored password by the description.
Double click the entry.
Make the password viewable.
Select the whole passphrase and hit C (instead of CTRL+C)
Now the password is gone.

---

### Post by untrustytahr on 2017-09-12
Sorry to hear about your issue.  If you happen to have a backup of your system, you could restore the file:

```
/home/$USER/.local/share/keyrings/login.keyring
```

That is where passwords for the default keyring is.

I always looked at Seahorse/gnome keyrings as something that is used by programs directly, not interactively (except in emergency).  The way you are using it, you might be better off with a  product such as keepassX.

---

### Post by dragonfly41 on 2017-09-12
Being curious I looked to see if I have seahorse installed.
I do, but I never use it.
I see that it holds a number of sessions and importantly my OpenSSH keys.

I tried an experiment.
Created a test account and added a password.
Sure enough using the key sequence you describe deleted the password.
It seems a poor design since there should be a verify field before wiping a password.

I immediately backed up my keyrings.

Next I looked around to see how passwords might be retrieved.

From this thread ...

[https://ubuntuforums.org/showthread.php?t=2125918](https://ubuntuforums.org/showthread.php?t=2125918)

I found this python script ...

[https://blog.schmichael.com/2008/10/30/listing-all-passwords-stored-in-gnome-keyring/](https://blog.schmichael.com/2008/10/30/listing-all-passwords-stored-in-gnome-keyring/)

but this requires the package python-gnomekeyring to be installed before running the script.  I used Synaptic to install.

It works when I run it.

...


There is LastPass as a password manager (browser extension).

But the rule must be to backup such important data, in different geographic locations.

...
[COLOR=#ff0000]
[Later edit][/COLOR]

I read this in mail list archives.   Supports your point.   Use seahorse with care.
[URL="http://https://mail.gnome.org/archives/seahorse-list/2016-June/msg00000.html"]
https://mail.gnome.org/archives/seahorse-list/2016-June/msg00000.html[/URL]

---

