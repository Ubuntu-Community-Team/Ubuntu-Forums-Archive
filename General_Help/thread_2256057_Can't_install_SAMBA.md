---
title: "Can't install SAMBA"
date: 2014-12-09
forum: General Help
---

### Post by Dev_Benson on 2014-12-09
OK, just spent a couple of hours trying to access files on a WD MyBook live NAS without success.  Hoping someone can help with this as I'm finding it hard to do most things with Ubuntu that I have no problems doing with Windows, although this could be in part due to unfamiliarity with Ubuntu.  Running out of patience though!

So I'm running 11.04 and in searching for the solution I saw that the installation of SAMBA was the recommended way to go.

This is what I typed into terminal -

s**udo apt-get install samba samba-common**

This is the resulting error -

[B]Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main samba i386 2:3.5.4~dfsg-1ubuntu8.5
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main samba i386 2:3.5.4~dfsg-1ubuntu8.5
  404  Not Found [IP: 91.189.88.149 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.5.4~dfsg-1ubuntu8.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.5.4~dfsg-1ubuntu8.5_i386.deb)  404  Not Found [IP: 91.189.88.149 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[/B]
Can anybody translate what this means and what I need to do to progress with this please?

Any help appreciated!

---

### Post by deadflowr on 2014-12-09
It means maverick has reached it's end of life.
You would better suited to install a newer, still supported version of Ubuntu.

Also, 11.04 has also reached end of life.

I'd recommend 12.04, or 14.04 which have support until April 2017 and April 2019, respectively.
read our Staff recommendations here
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

Good luck, and if you need to help on how to do something like preserve your files, feel free to ask.

---

### Post by Dev_Benson on 2014-12-09
Thanks for the quick response.

I'm sure I tried to upgrade the Ubuntu version before & got an error message.  I'll try again & report any errors.

---

### Post by Dev_Benson on 2014-12-09
Ah, so I'm running 10.10 (Maverick) not 11.04.

The Update Manager only gives me the option to upgrade to 11.04 - should I look to do multiple upgrades this way or is there a safe way to upgrade straight to 12.04 which is recommended in your above link?

---

### Post by deadflowr on 2014-12-09
You might be better served downloading a newer version and installing fresh.
Upgrading to a supported version (which the closest is 12.04) would mean first having a successful upgrade to another dead release (11.10) and then upgrading to 12.04.
Even on a stable upgrade a double upgrade is fraught with the possibly of something going bad.

Like I stated though, if you need help figuring out how to save any files or things you think you need, feel free to post about that.

Edit: see new reply, but the above still applies, regardless if the install is 10.10, or 11.04.

---

### Post by Dev_Benson on 2014-12-09
OK so I did a bit more research on the recommended path to upgrade Ubuntu and decided to use the upgrade manager.

This shows that 11.04 is available, but clicking Upgrade opens up an error window -

[B]Failed to fetch

Fetching the upgrade failed.  There may be a network problem.[/B]

Does this mean the upgrade to 11.04 no longer exists?  Obviously there is no network issue on my side as I'm connected ok (I'm typing on the netbook that I'm trying to upgrade).

---

### Post by verymadpip on 2014-12-09
Hi there.
I think deadflowr means download a new image & install afresh.
Actually, that's exactly what he said............

Try from here:
[http://releases.ubuntu.com/trusty/](http://releases.ubuntu.com/trusty/)

Or from here:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by deadflowr on 2014-12-09
> **verymadpip said:**
> Hi there.
I think deadflowr means download a new image & install afresh.
Actually, that's exactly what she's said............

Try from here:
[http://releases.ubuntu.com/trusty/](http://releases.ubuntu.com/trusty/)

Or from here:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

He.
Don't let the avatar fool you.(Been too lazy to change my Halloween theme-week avatar, so there is that)
Though some would like to say I act like a little girl...
(my brother for one);)

---

### Post by verymadpip on 2014-12-09
Oops, sorry my bad.  I've always just assumed....& look at where that's got me.
Edited  :)

---

