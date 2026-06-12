---
title: "About cURL packages"
date: 2017-08-14
forum: General Help
---

### Post by satimis on 2017-08-14
Hi folks,

On testing Tastyiginiter I need to install cURL

[https://tastyigniter.com/](https://tastyigniter.com/)

$ apt-cache search cURL | grep cURL```

curlftpfs - filesystem to access FTP hosts based on FUSE and cURL
gnupg-curl - GNU privacy guard - a free PGP replacement (cURL)
httpie - CLI, cURL-like tool for humans
lua-curl - libcURL bindings for the Lua language
lua-curl-dev - libcURL development files for the Lua language
uwsgi-plugin-alarm-curl - cURL alarm plugin for uWSGI
uwsgi-plugin-curl-cron - cron cURL plugin for uWSGI

```

Whether I need to install all of them?  Please advise.  Thanks

Regards
satimis

---

### Post by deadflowr on 2017-08-14
just curl is all you need.
as in
```
sudo apt install curl
```

---

### Post by satimis on 2017-08-15
> **deadflowr said:**
> just curl is all you need.
as in
```
sudo apt install curl
```
Hi,

Thanks for your advice.

I already have curl installed but a warning still popu;```

cURL: 	is cURL installed?

```
Later I found it needs php7.0-curl

$ apt-cache policy php7.0-curl```

php7.0-curl:
  Installed: (none)
  Candidate: 7.0.22-0ubuntu0.16.04.1
  Version table:
     7.0.22-0ubuntu0.16.04.1 500
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     7.0.18-0ubuntu0.16.04.1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     7.0.4-7ubuntu2 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

After haveing  php7.0-curl installed the warning disapppears

Regards
satimis

---

### Post by sotiris2 on 2017-08-15
> **satimis said:**
> Hi,

Thanks for your advice.

I already have curl installed but a warning still popu;```

cURL:     is cURL installed?

```

In Linux, cURL is not curl which is not Curl etc.
Case matters. 
Typically all commands are all lower case letters. So it's ```
curl
```


After a bit of searching to make sure we speak of the same software I now learned that curl's official name is cURL. Still even though it has a very deliberate fancy capitalization you use curl on the command line.

---

### Post by satimis on 2017-08-15
> **sotiris2 said:**
> In Linux, cURL is not curl which is not Curl etc.
Case matters. 
Typically all commands are all lower case letters. So it's ```
curl
```


After a bit of searching to make sure we speak of the same software I now learned that curl's official name is cURL. Still even though it has a very deliberate fancy capitalization you use curl on the command line.
Hi,

Thanks for your advice.

They name it in this way.  Please refers to attached photo (screenshot_server_requirements.jpg)

Regards
satimis

---

### Post by sotiris2 on 2017-08-15
I saw that you always referred to it as cURL so I checked if it was a different project. 
Check the wiki page for [cURL](https://en.wikipedia.org/wiki/CURL). See the name, then check the example screenshot and see how it is used in the command line.

---

