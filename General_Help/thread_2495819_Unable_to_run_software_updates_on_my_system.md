---
title: "Unable to run software updates on my system"
date: 2024-03-02
forum: General Help
---

### Post by rdagher on 2024-03-02
I haven't been able to get the latest software updates on my system, has anyone seen these fails? If so, how did you get this issue resolved. Here are the messages I get when I run "sudo apt-get updates" command in a terminal window.

Following Ubuntu version is installed on my system:
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy


Most of the issues are due to missing or expired public keys.

>sudo apt-get update
Hit:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease                 
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]
Hit:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB]
Err:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
Err:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
Err:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
Fetched 229 kB in 1s (207 kB/s)
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: [http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease:](http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease:](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: [http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease:](http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jammy/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/jammy/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease](http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ian-weisser on 2024-03-02
Why does your system have wrong-version 16.04 (xenial) repos active?

That's a characteristic of a systems with broken release-upgrades or strange haywired release-upgrades.
In both cases, there are often other other serious problems.
And in both cases, those other serious problems often lead to a reinstall.

---

### Post by TheFu on 2024-03-02
As Ian says, looks like like your repos have been screwed up for some time.  Probably not repairable. Do a fresh install. Don't forget to be certain you have backups of anything you don't want to lose first.

I'd install 22.04 today.  Then next August when 24.04.1 is released, move to that.

---

### Post by coffeecat on 2024-03-03
Support, not chat. *Thread moved to **General Help**.*

---

### Post by rdagher on 2024-03-04
I already have Ubuntu 20.04 installed on my system. Here is the release information

Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy

Thank you all for your input. Some history of Ubuntu version installed on my system.

Several years ago, I installed Ubuntu LTS on my system. Afterwords, I received a notification every once in a while that a new version of Ubuntu is available. The notice included a button to select if I wanted to upgrade to the new version. That is how I upgraded from version 16 to 18 to 22.04.

Unfortunately, I didn't do a clean install every time I upgraded to a new version which is possibly why older repositories do still exist on my system.

Basically, to go around this problem, I hear that the recommendation is to do a clean install, correct?

---

### Post by TheFu on 2024-03-04
> **rdagher said:**
> I already have Ubuntu 20.04 installed on my system. Here is the release information

Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy
 

You keep writing that you have 20.04 installed, then show 22.04 in the output.  Details matter.  **This seems solved to me.** Please mark is **SOLVED **using the _thread tools button._

If you are still having issues, do a clean install ... please post that and then mark it SOLVED.  Remember, we can't read your mind.

Somewhere you didn't follow the upgrade procedures.  I've only seen this happen when someone went out of their way to modify the repos manually.  The do-release-upgrade process handles this automatically and there haven't been issues with that part of the upgrade process in 15+ yrs, if ever.

---

