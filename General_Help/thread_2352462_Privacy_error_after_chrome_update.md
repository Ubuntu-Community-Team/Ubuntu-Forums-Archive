---
title: "Privacy error after chrome update"
date: 2017-02-12
forum: General Help
---

### Post by b_e_e_k on 2017-02-12
Since I have updated chrome to the latest stable version, I get a 'Privacy Error' when I try to access Google websites (and a few others). When I lauch a google search, or try to access my email, I see this error message:



```
Your connection is not private

Attackers might be trying to steal your information from mail.google.com (for example, passwords, messages, or credit cards).
 NET::ERR_CERT_WEAK_SIGNATURE_ALGORITHM

```

The message does not allow me to proceed to the site anyway.

I can access google Finance, and I see the general site for a non-signed-in user. But when I try to sign in, I get the privacy error instead of the sign-in page. 

Google Drive behaves slightly different: My directories and files are displayed, but the file names are grayed-out, and I cannot open them.

Apparently, Google Finance does not consider me as logged-in, while Drive does.

I have disabled all my extensions to no effect. I have also tried to access the web sites in incognito mode (suggested by Google forums), but I get the same result.

I followed these instructions to upgrade Chrome: 
tecadmin.net/install-chrome-in-ubuntu/

Chrome version after update: Version 56.0.2924.87 unknown (64-bit)  
(Output of Help -> About Google Chrome)

Ubuntu version: 14.04 LTS

How can I resolve this?

---

### Post by Habitual on 2017-02-13
Try 
```
sudo apt-get install libnss3-1d
``` and see.

---

### Post by b_e_e_k on 2017-02-13
Hi Habitual -

I get this error when I try to install libnss-1d:

```

$ sudo apt-get install libnss3-1d
...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libnss3-1d : Depends: libnss3 (= 2:3.15.4-1ubuntu7) but 2:3.17.1-0ubuntu0.14.04.2 is to be installed
E: Unable to correct problems, you have held broken packages.

```

I already have the newer version 2:3.17.1 of libnss3. However, it seems as if libnss3-1d only works with an older version of libnns3:

```

$ apt-cache policy libnss3
libnss3:
  Installed: 2:3.17.1-0ubuntu0.14.04.2
  Candidate: 2:3.17.1-0ubuntu0.14.04.2
  Version table:
 *** 2:3.17.1-0ubuntu0.14.04.2 0
        100 /var/lib/dpkg/status
     2:3.15.4-1ubuntu7 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

$ apt-cache policy libnss3-1d
libnss3-1d:
  Installed: (none)
  Candidate: 2:3.15.4-1ubuntu7
  Version table:
     2:3.15.4-1ubuntu7 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```


How should I go about installing libnss3-1d?

Regards,
Bernd

---

### Post by b_e_e_k on 2017-02-14
I have managed to install libnss3-1d by reverting to older versions for libnss3 and libnss3-nssdb:

```

sudo apt-get install libnss3=2:3.15.4-1ubuntu7 libnss3-nssdb=2:3.15.4-1ubuntu7
sudo apt-get install libnss3-1d

```

However, I still get the same Privacy Error in Chrome.

What to do?

---

### Post by Habitual on 2017-02-14
Don't know, sorry.

---

