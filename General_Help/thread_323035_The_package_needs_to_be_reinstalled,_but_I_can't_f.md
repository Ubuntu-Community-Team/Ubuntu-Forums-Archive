---
title: "The package needs to be reinstalled, but I can't find an archive for it."
date: 2006-12-21
forum: General Help
---

### Post by ions on 2006-12-21
I want to make sure everything is as up to date as possible to move from Breezy to 6.06LTS but I get the following:

```
$ sudo apt-get update
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Get:2 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Fetched 3B in 1s (3B/s)
Reading package lists... Done

```

K, good.

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
E: The package linux-image-2.6.12-10-686 needs to be reinstalled, but I can't find an archive for it.
```

Not so good.  No matter what I try and install that's what it says.

---

### Post by az on 2006-12-21
> **ions said:**
> I want to make sure everything is as up to date as possible to move from Breezy to 6.06LTS but I get the following:

```

E: The package linux-image-2.6.12-10-686 needs to be reinstalled, but I can't find an archive for it.
```

Not so good.  No matter what I try and install that's what it says.

That's because you removed all the breezy repos from your list.

If you are running a desktop, you should really just uise the update-notifier and use the new version upgrader thinggy there.

---

### Post by ions on 2006-12-21
Heh, oops. 

I had tried to run the upgrade from update notifier and it failed.  I guessed it failed because I wasn't properly up to date so I tried updating again.  Didn't even notice the change in sources.list.  Heh.  Thank you for pointing out my stupidity.  :)

---

### Post by az on 2006-12-21
To properly use the updtae-notifier in Breezy, you must run a completely up-to-date breezy.  You you would have have to dist-upgrade while all your sources are breezy to the latest version of the update-notifer for it to work properly.
Perhaps it's not too late for you to do that.

Otherwise you can plow through and dist-upgrade by hand.

Do a dist-upgrade and then keep trying to re-install ubuntu-desktop if it gets removed.  You may have to run a dist-upgrade a few times to accomplish that.

---

