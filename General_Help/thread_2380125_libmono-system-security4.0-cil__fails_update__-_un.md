---
title: "libmono-system-security4.0-cil  fails update  - unauthenticated packages"
date: 2017-12-13
forum: General Help
---

### Post by jason63 on 2017-12-13
apt-get update 
```
 libmono-system-security4.0-cil E:there were unauthenticated packages and -y was used without --allow-unauthenticated
```


any idea why this wont update ?

---

### Post by Kirk Schnable on 2017-12-14
Can you provide the full output of "apt-get update"?  It looks like you have a repository with a missing, expired, or corrupted GPG key.

---

### Post by jason63 on 2017-12-14
yes sir


```



user@ubuntu-server:~$ sudo apt-get update
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://ca.archive.ubuntu.com/ubuntu xenial InRelease
Get:3 http://ca.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Ign:4 http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04  InRelease
Get:5 http://ca.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:6 http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04  Release [1,009 B]
Get:7 http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04  Release.gpg [481 B]
Ign:8 http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04  Release.gpg
Hit:9 http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04  Packages
Fetched 308 kB in 0s (391 kB/s)
Reading package lists... Done
W: GPG error: http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0A506F712A7D8A28
W: The repository 'http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04  Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
user@ubuntu-server:~$




```

---

### Post by Kirk Schnable on 2017-12-14
> **jason63 said:**
> ```
W: GPG error: http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0A506F712A7D8A28
W: The repository 'http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04  Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
```

This is the repository that's missing the GPG key signature.

Try this command to download the repository's key, and install it.

```
wget -qO - http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04/Release.key | sudo apt-key add -
```

Then run apt-get update again.

---

### Post by jason63 on 2017-12-15
> **Kirk Schnable said:**
> This is the repository that's missing the GPG key signature.

Try this command to download the repository's key, and install it.

```
wget -qO - http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04/Release.key | sudo apt-key add -
```

Then run apt-get update again.


This worked! Can you elaborate on what went wrong, and how you figure out what key was missing etc. I'd like to learn what Im looking for!

Thank you very much!


PS: I don't use Emby Media Server anymore and its uninstalled - what would I do to remove this?

---

### Post by Kirk Schnable on 2017-12-15
> **jason63 said:**
> This worked! Can you elaborate on what went wrong, and how you figure out what key was missing etc. I'd like to learn what Im looking for!
Sure, every repository for Apt has a GPG key which is used to authenticate the repository.  It's sort of like how an SSL certificate confirms that you're connecting to the website you think you are connecting to.  The key confirms that the repository is the one you added originally.  It's possible for the repository to change the key, or for circumstances on your local machine to cause the key file to become deleted or corrupted.

I don't really have a way to know if the repository changed their key or what happened to cause it, but at some point your locally stored key signature stopped matching the repository's for some reason.

I found the key by visiting the repository in my browser: [http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04/](http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04/)

But it's usually called Release.key and it's usually in the root folder of the repository.


> **jason63 said:**
> PS: I don't use Emby Media Server anymore and its uninstalled - what would I do to remove this?
If you don't need the repository anymore, you can delete or comment out the lines that reference it.  Repositories are usually listed in /etc/apt/sources.list or it might have a separate file in /etc/apt/sources.list.d/.  Find the file that references the repository's URL, and either comment it out by adding a # in front of the line, or if it's the only repository in the file in sources.list.d, simply remove the entire file.  The next time you run apt-get update, you shouldn't see the repository anymore.

---

### Post by jason63 on 2017-12-17
Kirk, I need to say thank you. This was so clear, I understand everything you said. I'm by no means a beginner, but not a whole lot better than that. It is very refreshing to see people like you take this time. 

The take away for me, is now I know not to focus on the specific problem ie: "libmono-system-security4.0-cil fails update - unauthenticated packages" and look deeper into the error (the key failing).

Your help allows me to diagnose simple issues like this in the future.

THANK YOU!

---

### Post by Kirk Schnable on 2017-12-17
No problem, thanks for probably the nicest forum reply I've ever read!  Haha

I know I always appreciate helpful replies, especially when I was learning more about Linux myself.  I pop in here on the forums once in awhile, usually to ask a question myself, and always try to answer more threads than I create.  If everyone did the same, we would have everyone supported.  I also have a number of years of user facing support in a mostly Linux environment under my belt, so I've gotten quite good at explaining Linux stuff in an understandable way.  :)

Hopefully when your own knowledge has advanced to the point where you can help out, you will do the same.  Good luck and keep on learning!

---

