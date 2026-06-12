---
title: "Update Manager could not download a repository index"
date: 2006-08-08
forum: General Help
---

### Post by jis on 2006-08-08
I tried to update my xubuntu, but I got this error message:

<clip>

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out

</clip>

What has happened to that repository? Anyway I checked updates after this and I did not get the error anymore.

---

### Post by Jagot on 2006-08-08
The server may be down for some reason.  It'll probably be up in a couple of hours.

---

### Post by jis on 2006-08-09
Later, when I chose to install updates, I get the following question: "Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?" After installing, I get the following warning: "W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.2.11-1ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.2.11-1ubuntu3.1_i386.deb)
  Could not connect to security.ubuntu.com:80 (195.248.90.23), connection timed out".

Later, when I tried to install updates again, I succeeded to update Gimp related packaes that were not up-to-date.

---

