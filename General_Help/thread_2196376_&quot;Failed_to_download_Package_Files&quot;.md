---
title: "&quot;Failed to download Package Files&quot;"
date: 2013-12-29
forum: General Help
---

### Post by mogojohn on 2013-12-29
Ubuntu 12.04.3 LTS on Acer AOA150 Netbook dual-booted with XP

I have three important updates that fail:
Multi-protocol File Transfer Library (OpenSSL)
Multi-protocol File Transfer Library (GnuTLS)
Multi-protocol File Transfer Library (NSS)

The error is "Failed to download Package Files
Failed to fetch 
[http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3-gnutls_7.22.0-3ubuntu4.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3-gnutls_7.22.0-3ubuntu4.5_i386.deb) 
404  Not Found [IP: 91.189.92.200 80]
Failed to fetch 
[http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.22.0-3ubuntu4.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.22.0-3ubuntu4.5_i386.deb)
404  Not Found [IP: 91.189.92.200 80]
Failed to fetch 
[http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3-nss_7.22.0-3ubuntu4.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3-nss_7.22.0-3ubuntu4.5_i386.deb)
404  Not Found [IP: 91.189.92.200 80]

All other updates worked fine, browser works.  
What could be wrong?

Thank you

---

### Post by vanadium on 2013-12-29
It might be a temporary problem with the server. Wait a few days, or temporarily change your download server.

---

### Post by Old_Grey_Wolf on 2013-12-29
It appears you need to update the package list to get the current list of packages. Enter this command in a terminal ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mogojohn on 2013-12-29
Thanks Old_Grey_Wolf - that worked, and the Updater now says the software is up to date.  Why would the Updater not be aware of that issue?

---

### Post by Old_Grey_Wolf on 2013-12-29
I don't know. I either use the Update Manager and click Check for updates or I use the command line.

Edit: I assume you are referring to the icon at the top of the screen that shows updates are available. For some reason I don't trust it to not be stale so I use the Update Manager in the launcher or use the command line method.

---

### Post by mogojohn on 2013-12-29
Correction - I was using the Update Manager - it was the one reporting the errors

Thanks

---

### Post by Old_Grey_Wolf on 2013-12-29
If it happens again, and it says packages are being held back use a different command to get the kernel updates that are being held back. ```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by mogojohn on 2013-12-29
Thanks again!

---

### Post by gheiberg59 on 2014-06-29
> **Old_Grey_Wolf said:**
> It appears you need to update the package list to get the current list of packages. Enter this command in a terminal ```
sudo apt-get update && sudo apt-get upgrade
```

I have been experiencing the same issue with 14.04LTS. I used your above command to isolate the particular problem file -
 "[COLOR=#0000ff]W: Failed to fetch [http://mirror.it.ubc.ca/ubuntu/pool/main/e/evince/libevdocument3-4_3.10.3-0ubuntu10.1_amd64.deb](http://mirror.it.ubc.ca/ubuntu/pool/main/e/evince/libevdocument3-4_3.10.3-0ubuntu10.1_amd64.deb)
  gnutls_handshake() failed: The Diffie-Hellman prime sent by the server is not acceptable (not long enough). [/COLOR]"

I tried a couple of different repositories, but got the same error (other than the repository/mirror portion of the above line). I removed evince (Document Viewer) and replaced it with Okular.

---

### Post by Old_Grey_Wolf on 2014-06-29
> **gheiberg59 said:**
> I have been experiencing the same issue with 14.04LTS. I used your above command to isolate the particular problem file -
 "[COLOR=#0000ff]W: Failed to fetch [http://mirror.it.ubc.ca/ubuntu/pool/main/e/evince/libevdocument3-4_3.10.3-0ubuntu10.1_amd64.deb](http://mirror.it.ubc.ca/ubuntu/pool/main/e/evince/libevdocument3-4_3.10.3-0ubuntu10.1_amd64.deb)
  gnutls_handshake() failed: The Diffie-Hellman prime sent by the server is not acceptable (not long enough). [/COLOR]"

I tried a couple of different repositories, but got the same error (other than the repository/mirror portion of the above line). I removed evince (Document Viewer) and replaced it with Okular.

Confused, are you posting in a 6 month old thread asking for help or offering a solution? The problem you describe is not the same as the problem the OP had.

---

### Post by gheiberg59 on 2014-07-08
> **Old_Grey_Wolf said:**
> Confused, are you posting in a 6 month old thread asking for help or offering a solution? The problem you describe is not the same as the problem the OP had.

The symptom I was having was identical to that of the OP - the vague "Failed to download Package Files" message; in my case, when running Software Updater. While the particular cause was different than that of the OP, your suggestion to him also enabled me to identify the particular package that was causing my problem.

So, I guess my comment is that your solution has a more general application for *anyone* encountering the "Failed to download Package Files" message.

Thanks,
Gunnar

---

