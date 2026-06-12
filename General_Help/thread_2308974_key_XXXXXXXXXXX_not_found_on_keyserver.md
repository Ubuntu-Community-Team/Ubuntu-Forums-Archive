---
title: "key XXXXXXXXXXX not found on keyserver"
date: 2016-01-07
forum: General Help
---

### Post by Hodevah on 2016-01-07
After ```
sudo apt-get update
``` I get the following:

```
Reading package lists... Done
W: GPG error: http://download.opensuse.org  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A7D1D38BEB6D886
```
I have tried the following:
Using different servers such as the following:
```
pool.sks-keyservers.net
subkeys.pgp.net
pgp.mit.edu
keys.nayr.net
keys.gnupg.net
wwwkeys.XX.pgp.net  --where XX represents my country code
```

Have also tried the following:

```
gpg --armor --export 5A7D1D38BEB6D886 |sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
root@DellXPS-15-9530:~# gpg --armor --export BEB6D886 | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found
```
Also, no good results. 

with mixed results. Either the server timed out or key could not be found. Examples are listed below:

```
gpg --keyserver pool.sks-keyservers.net --recv-keys 5A7D1D38BEB6D886
gpg: requesting key BEB6D886 from hkp server pool.sks-keyservers.net
gpgkeys: key 5A7D1D38BEB6D886 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
root@DellXPS-15-9530:~# gpg --keyserver pgp.mig.edu --recv-keys 5A7D1D38BEB6D886
gpg: requesting key BEB6D886 from hkp server pgp.mig.edu
?: pgp.mig.edu: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
root@DellXPS-15-9530:~# gpg --keyserver pgp.mit.edu --recv-keys 5A7D1D38BEB6D886
gpg: requesting key BEB6D886 from hkp server pgp.mit.edu
gpgkeys: key 5A7D1D38BEB6D886 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
root@DellXPS-15-9530:~# gpg --keyserver keys.nayr.net --recv-keys 5A7D1D38BEB6D886
gpg: requesting key BEB6D886 from hkp server keys.nayr.net
?: keys.nayr.net: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
root@DellXPS-15-9530:~# gpg --keyserver wwwkeys.ca.pgp.net --recv-keys 5A7D1D38BEB6D886
gpg: requesting key BEB6D886 from hkp server wwwkeys.ca.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```


this includes the Ubuntu server, 
```
**http://keyserver.ubuntu.com**
```
Have also manually gone to keyserver at [http://keyserver.ubuntu.com/](http://keyserver.ubuntu.com/) and input the key in the appropriate field with key not found. 
This include input with 0x5A7D1D38BEB6D886 and just 5A7D1D38BEB6D886 with "No results found: No keys found"

Have also tried to use port 80 such as the following:
```
sudo gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 5A7D1D38BEB6D886
gpg: requesting key BEB6D886 from hkp server keyserver.ubuntu.com
gpgkeys: key 5A7D1D38BEB6D886 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

Have tried to see if key exists with command:

```
apt-key list
```
but it is not listed there. 
Have tried to also del key with following command:
```
sudo apt-key del 5A7D1D38BEB6D886
OK

```
It says "OK" but after ```
sudo apt-get update 
```

I still get the same error as reported/ posted.
Have also tried the following:

```
gpg --armor --export 5A7D1D38BEB6D886 |sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
root@DellXPS-15-9530:~# gpg --armor --export BEB6D886 | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found
```

As you can see, many avenues explored with no good results. Have also looked inside the gpg.conf file in the /home directory but there is nothing remarkable there. 
Can post if like but believe me, there is nothing substantial there.


Looking for some help, please

---

### Post by Bucky Ball on 2016-01-07
Why not remove the opensuse PPA from your sources list? Unsure why it's there, but guess you have your reasons. Disable it and see if you get the same error message.

(You can also go 'Software and Updates' and untick that PPA.) 

Which release of Ubuntu are you using?

---

### Post by Hodevah on 2016-01-07
Thank you for your** res**ponse Bucky Ball. [B]

Kubuntu 15.10 _Wily Werewolf_ - Alpha amd64[/B]

```
cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 15.10 _Wily Werewolf_ - Alpha amd64 (20150924)]/ wily main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ wily main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ wily main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ wily universe
deb-src http://us.archive.ubuntu.com/ubuntu/ wily universe
deb http://us.archive.ubuntu.com/ubuntu/ wily-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ wily multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ wily multiverse
deb http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu wily-security main restricted
deb-src http://security.ubuntu.com/ubuntu wily-security main restricted
deb http://security.ubuntu.com/ubuntu wily-security universe
deb-src http://security.ubuntu.com/ubuntu wily-security universe
deb http://security.ubuntu.com/ubuntu wily-security multiverse
deb-src http://security.ubuntu.com/ubuntu wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu wily partner
# deb-src http://archive.canonical.com/ubuntu wily partner
deb http://downloads.sourceforge.net/project/xenlism-wildfire/repo deb/
```

forgot to mention that I had already tried that route. As you can see, no OpenSuse is listed.

EDIT: I have a hidpi screen and some (not all ) apps don't appear correctly. Hence when I had gone to Software Sources at a point earlier I did not clearly see it. Having gone there again, I managed to see it this time (bad eyes. I guess I am getting old :D ). 
Regardless, removed the offending PPA and all is good now. 

**Resolved. **And thank you for the reminder for myself to re-check the sources list.

---

### Post by matt_symes on 2016-01-07
Hi

The problem is that key does not exist on the key servers you have checked.

```

matthew-xu-16-04:/home/matthew:3 % gpg --keyserver hkp://keyserver.ubuntu.com --search-keys 5A7D1D38BEB6D886
gpg: searching for "5A7D1D38BEB6D886" from hkp server keyserver.ubuntu.com
**gpg: key "5A7D1D38BEB6D886" not found on keyserver**
matthew-xu-16-04:/home/matthew:3 %  gpg --keyserver hkp://pool.sks-keyservers.net --search-keys 5A7D1D38BEB6D886
gpg: searching for "5A7D1D38BEB6D886" from hkp server pool.sks-keyservers.net
**gpg: key "5A7D1D38BEB6D886" not found on keyserver**
matthew-xu-16-04:/home/matthew:3 % 
```

You need to find the key server or a web page where that public key exists.

I'll look for you and see if i can find it as two eyes are better than one.

**EDIT:**

Seems i was cross posting :)

**EDIT 2:**

> Why not remove the opensuse PPA from your sources list?

Good catch BuckyBall. I missed that one.

@OP what are you trying to install from the OpenSuse repos that you cannot find in a Ubuntu repo ?

@OP to find the repo

```
grep -i suse /etc/apt/sources.list{,.d/*}
```

Anyway, for the keys, i came across this....

BTW: [http://linux01.gwdg.de/apt4rpm/](http://linux01.gwdg.de/apt4rpm/)

...but apt is not very well supported in the openSuse repositories.

Kind regards

---

### Post by Bucky Ball on 2016-01-07
All good. Sometimes easier to look in 'Software and Updates' in the 'Other Software' tab. Enjoy! (and thanks for marking solved) :)

---

### Post by Hodevah on 2016-01-07
@matt_symes
it was for some theme that I was wanting to play with and install. 
It just didnt' work out as expected. 
Decided to delete it and hence I came up with this error.

---

### Post by matt_symes on 2016-01-07
Hi

> **Hodevah said:**
> @matt_symes
it was for some theme that I was wanting to play with and install. 
It just didnt' work out as expected. 
Decided to delete it and hence I came up with this error.

I'm glad you got it fixed with BuckyBall's help

It's best to use the Ubuntu repositories when you can. You'll get far less problems.

I'll spend the rest of the day trying not to cross post with everybody :D

As BuckyBall said, if you could mark this thread as SOLVED using the thread tools menu under post #1 then that would help others looking for a solution. 

Kind regards

---

### Post by Bucky Ball on 2016-01-07
> **matt_symes said:**
> It's best to use the Ubuntu repositories when you can. You'll get far less problems.

+1. Roam in the wild at your own risk and only when necessary. :)

---

### Post by brianfinley on 2016-01-28
Thanks!

I was having the same issue, and found the key in a file on the URL you listed.

Then...  I imported it and sent it to the MIT keyservers so that others should be able to actually find it there now.

In case it might be helpful to anyone, here's what I did:

```
[$] wget [http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10/Release.key](http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10/Release.key)
[$] gpg --import Release.key
gpg: key BEB6D886: public key "home:Horst3180 OBS Project <home:Horst3180@build.opensuse.org>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
gpg: WARNING: digest algorithm MD5 is deprecated
gpg: please see [https://gnupg.org/faq/weak-digest-algos.html](https://gnupg.org/faq/weak-digest-algos.html) for more information
[snip]
[$] gpg --send-keys BEB6D886
gpg: sending key BEB6D886 to hkp server pgp.mit.edu
```


Which means that we can all now do this to get the key into your personal keyring:

```
[$] gpg --recv-keys BEB6D886
gpg: requesting key BEB6D886 from hkp server pgp.mit.edu
gpg: key BEB6D886: "home:Horst3180 OBS Project <home:Horst3180@build.opensuse.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```


Then this to tell apt about it:

```
[$] gpg -a --export BEB6D886 | sudo apt-key add -
OK
```


Cheers!

---

### Post by matt_symes on 2016-01-28
Hi

@brianfinley

That's a great explanation of the steps you took.

Thanks for posting it and many thanks for posting the key to the key server. That never even crossed my mind :)

Kind regards

---

