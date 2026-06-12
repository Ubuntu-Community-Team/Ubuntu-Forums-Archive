---
title: "How do I fix this?"
date: 2007-11-25
forum: General Help
---

### Post by enchance on 2007-11-25
Why do I sometimes get his error?
```
Err http://hendrik.kaju.pri.ee gutsy/screenlets Packages
  503 Service Unavailable
Fetched 58.4kB in 1m5s (888B/s)
Reading package lists... Done
W: GPG error: http://security.ubuntu.com gutsy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```
I've tried "sudo apt-get update" and "sudo aptitude update" but they still come out.

---

### Post by jasmuz on 2007-11-25
Greetings,

That 503 error indicates that repository is down, so you better put a # in front of it in /etc/apt/sources.list

And about the GPG error, Go to the website of the Ubuntu repositories, they have listed how to add the signature you are missing.

---

### Post by enchance on 2007-11-25
> **jasmuz said:**
> Greetings,

That 503 error indicates that repository is down, so you better put a # in front of it in /etc/apt/sources.list

Since I've already installed Screenlets (which is causing the problem) is it ok to comment it instead? The only downside to this is that it won't check for screenlets updates, right?

---

### Post by #Reistlehr- on 2007-11-25
correct. you can always manually check, and download the deb pkg from their site.

---

