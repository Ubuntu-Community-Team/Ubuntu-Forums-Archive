---
title: "Cannot sign dsc files for DEB/PPA"
date: 2013-09-07
forum: General Help
---

### Post by dentaku65 on 2013-09-07
Hi,

Im trying to create a package for PPA, but I run in this error executing the command:
```
debuild -S -sa 
```
> Now signing changes and any dsc files...
 signfile thunar-shares-plugin_0.2.0-1.dsc 24FD16F7
gpg: skipped "24FD16F7": secret key not available
gpg: /tmp/debsign.stAiWni4/thunar-shares-plugin_0.2.0-1.dsc: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1278:
running debsign failed
Trying to force with the -k
```
debuild -S -sa -k24FD16F7
```
I got the same error 

GPG seems correct to me:
```
gpg --list-keys
```
> -----------------------------
pub    768D/24FD16F7 2010-01-06
uid                  dentaku65 (dentaku for ubuntu) <dentaku65@snip.com>
sub    768g/6F9CD1C5 2010-01-06

DEBFULLNAME e DEBMAIL env are correct
Code of Conduct on PPA is signed

Can someone give me an hint?
TIA

---

### Post by mc4man on 2013-09-07
Does your changelog have the same exact name (nick) &  email as your gpg uid? (as seen in gpg -K

Here don't use a nick so a little easier & also decided to 'automate' the process thru some .bashrc entries, ie.
export GPGKEY=<insert key here>                                                         
export DEBFULLNAME=[COLOR="#FF0000"]'[/COLOR]<insert name here>[COLOR="#FF0000"]' [/COLOR]                                    
export DEBEMAIL=<insert mailhere>

Note that DEBFULLNAME= needs a ' at start & finish

( here just use debuild -S
& dch -i to create the changelog which gets the name & email from the .bashrc exports

---

### Post by dentaku65 on 2013-09-07
Hi,

thx for your answer
I did all the exports but I still have the same issue 

This is my debian/changelog:
> thunar-shares-plugin (0.2.0-1) unstable; urgency=low

  * Initial release (Closes: #nnnn)  <nnnn is the bug number of your ITP>

 -- dentaku65 <dentaku65@snip.com>  Sat, 07 Sep 2013 11:55:59 +0200
Seems correct...

Tried debuild -S only, same error.... I really getting mad :-)

---

### Post by mc4man on 2013-09-07
"uid dentaku65 (dentaku for ubuntu)<dentaku65@snip.com>"
So try using the nick - (dentaku for ubuntu) in your debian changelog, ie. 

```
thunar-shares-plugin (0.2.0-1) unstable; urgency=low

* Initial release (Closes: #nnnn) <nnnn is the bug number of your ITP>

-- dentaku65 (dentaku for ubuntu) <dentaku65@snip.com> Sat, 07 Sep 2013 11:55:59 +0200 
```

---

### Post by dentaku65 on 2013-09-07
No way....
changing the uuid still the same issue
> Now signing changes and any dsc files...
 signfile thunar-shares-plugin_0.2.0-1.dsc dentaku65 (dentaku for ubuntu) <dentaku65@snip.com>
gpg: skipped "dentaku65 (dentaku for ubuntu) <dentaku65@snip.com>": secret key not available
gpg: /tmp/debsign.lPaiyJxs/thunar-shares-plugin_0.2.0-1.dsc: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1278:
running debsign failed


---

### Post by mc4man on 2013-09-07
(you didn't snip your email in last reply if that matters to you

Assuming your name (nick) & email in your changelog match  exactly the gpg one, do you have more than one OpenPGP key set up in launchpad?
(edit: the above comment shouldn't matter, would likely only affect dput

Did you start over in a new terminal, no exports? (or correct one for name (nick)

---

### Post by dentaku65 on 2013-09-07
Hi,

I put the exports in .bashrc and rebooted the machine
I have no other gpg in Launchpad; the only thing is that I don't use it since 2010

Perhaps I'll created a new one and delete this one...

> **mc4man said:**
> (you didn't snip your email in last reply if that matters to you

Assuming your name (nick) & email in your changelog match  exactly the gpg one, do you have more than one OpenPGP key set up in launchpad?
(edit: the above comment shouldn't matter, would likely only affect dput

Did you start over in a new terminal, no exports? (or correct one for name (nick)

---

### Post by mc4man on 2013-09-07
I took a look at your lp page, seems fine & your uid does contain the nick  (dentaku for ubuntu)  so it would have to be in the debian/changelog

Here once I got it setup I've copied my ~/.gnupg folder elsewhere so every new install I just copy back. Then with the .bashrc entries I just need to setup the keyring once per install with proper password & the whole deal is auto (set the keyring to unlock at bootup/login

The only other thing I noticed is you show a different first group for "pub" & "sub/ssb". Don't know what "sub/ssb" means but here they're the same - 

$ gpg --list-keys
/home/doug/.gnupg/pubring.gpg
-----------------------------
pub   2048R/8C1EA520 2012-02-04
uid                  Doug McMahon <snip@gmail.com>
sub   2048R/BF81E6C0 2012-02-04


$ gpg -K
/home/doug/.gnupg/secring.gpg
-----------------------------
sec   2048R/8C1EA520 2012-02-04
uid                  Doug McMahon <snip@gmail.com>
ssb   2048R/BF81E6C0 2012-02-04

---

### Post by dentaku65 on 2013-09-07
Interesting...
if I fire:
gpg -K

I got no result

---

### Post by dentaku65 on 2013-09-09
bump!
Any idea why my gpg signature do not have secret key?
TIA

---

