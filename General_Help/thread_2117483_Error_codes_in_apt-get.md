---
title: "Error codes in apt-get"
date: 2013-02-18
forum: General Help
---

### Post by VGriffith on 2013-02-18
Hello, I'm experiencing some problems with apt-get. Running apt-get update in command line results in the following error code > Reading package lists... Error!
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG FAEB83059BD4ED25 Launchpad Trimage
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: GPG error: [http://download.opensuse.org](http://download.opensuse.org)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DF077CFAE6FCF974
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/download.opensuse.org_repositories_home:heimdall78_xUbuntu%5f12.04_en
E: The package lists or status file could not be parsed or opened.

Attempting to run either the update manager, software center, or other commands with apt-get results in similar error codes. Any help would be greatly appreciated.

Edit: forgot to mention that I'm running 12.04

---

### Post by Yellow Pasque on 2013-02-18
You tried to add a source for a different distro (opensuse). You need to remove that and then:
```
sudo rm /var/lib/apt/lists/download.opensuse*
sudo apt-get update
```

---

### Post by VGriffith on 2013-02-18
I tried running that, still got these error codes
```
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG FAEB83059BD4ED25 Launchpad Trimage
W: GPG error: http://dl.google.com stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: GPG error: http://download.opensuse.org  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DF077CFAE6FCF974

```

So, being the meddling idiot that I am, I decided to go into /var/lib/apt/lists/ and (after creating a backup) delete all the files with opensuse in their names. After praying to avoid a crash, I ran apt-get... and got the exact same error code. 

Any other ideas?

---

### Post by meteorrock on 2013-02-18
Try this code along with this wildcard switch here and see if it will clear up that error in your apt-get. Purge that opensudo repo or library and its PPA key with the tool "Y ppa manager" first if you still get an error. 

```
sudo rm /var/lib/apt/lists/* -vf
```

```
sudo apt-get update
```

---

### Post by Yellow Pasque on 2013-02-18
> W: GPG error: [http://download.opensuse.org](http://download.opensuse.org)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DF077CFAE6FCF974

If you're still getting this warning, then you didn't remove the opensuse line from your sources as I instructed.
If you need help removing it, then you should tell us how you added it...

---

### Post by VGriffith on 2013-02-18
Temüjin, I ran the commands that you suggested, and they didn't return any error messages so I assume they worked. 

I also ran the commands the meteorrock suggested, and they cleared up the first two error codes, but I still got the third. I wasn't able to figure out how to use "Y ppa manager," however.

The only opensuse source I've added was for the program geogebra, per the instructions [here](http://software.opensuse.org/download.html?project=home:heimdall78&package=geogebra). I deleted the source, and it cleared up the last error code, so I'll mark this solved. Thanks for the help, both of you.

---

