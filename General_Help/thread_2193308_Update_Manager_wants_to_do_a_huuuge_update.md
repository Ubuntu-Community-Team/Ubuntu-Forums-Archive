---
title: "Update Manager wants to do a huuuge update"
date: 2013-12-12
forum: General Help
---

### Post by t0p on 2013-12-12
I'm running Ubuntu 12.04.  Last time I did a full update was about a week ago.  Today Update Manager wants to update 53 packages, totalling 262.9 MB.  I don't think I've ever seen anything like this, excepting new installs.

Is this right?  It seems so bizarre to need such a big update.  And this update list includes important security updates for Firefox, which I updated last week.  And multi-protocol file transfer libraries including OpenSSH.  And a new kernel (3.2.0 on 64-bit X86 SMP).  And lots of libraries.

Is this weird?  Or am I getting worried about nothing?

---

### Post by monkeybrain20122 on 2013-12-12
Do you have synaptic? Check it in synaptic for their origins and what they are. I disable the update manager and check for update manually with synaptic.

---

### Post by buzzingrobot on 2013-12-12
Not necessarily weird.  A new version of Firefox was released this week.  That, as well as a kernel update, is likely to bring in a good number of dependencies. Perhaps more so on 12.04 than on newer releases.

As monkeybrain suggested, have a look and see what it wants to do.  I wouldn't be inclined to worry, though.

---

### Post by claracc on 2013-12-12
I think, the update is correct, I have system configured to receive security updates everyday, and this morning with system fully updated from day before, I have received about 100 MB in security updates, between them firefox, samba and thunderbird (which I don't use).

---

### Post by t0p on 2013-12-12
I decided to install the updates, and Update Manager said the update "Requires installation of untrusted packages", and listed them for me:

> fonts-opensymbol landscape-client-ui-install libreoffice-base libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-java-common libreoffice-math libreoffice-style-human libreoffice-style-tango libreoffice-writer linux-firmware python-uno rar rsyslog software-center uno-libs3 ure

I'm baffled by the inclusion in this list of the libreoffice packages.  Does Ubuntu really consider libreoffice "untrusted"?  Libreoffice comes with Ubuntu as standard doesn't it?  And if so, why are its updates considered "untrusted packages"?

I know this might be a n00b bananas question, but I'm truly confused.  I've put the update on hold for now, at least until I understand why libreoffice packages are "untrusted".  Can anyone confirm this trust question?

Cheers.

---

### Post by t0p on 2013-12-12
> **claracc said:**
> I think, the update is correct, I have system configured to receive security updates everyday, and this morning with system fully updated from day before, I have received about 100 MB in security updates, between them firefox, samba and thunderbird (which I don't use).

Thanks claracc, at least I know I won't be sinking alone when I do this...

---

### Post by t0p on 2013-12-12
Ok, so now I appear to be in a mad cycle - Update Manager tells me it want to download a bunch of stuff, I click on Install; a warning appears about unauthenticated sources, I close that dialogue box; and it takes me back to the package list... repeat, repeat, repeat... Agh!

**EDIT:** I decided to try it on command line,

```
sudo apt-get update
```

and after it finished reading package lists, I got this warning:

```
W: GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

I don't know how to fix this - I also don't know what caused this, updates have worked fine before.  Help!!!

Cheers.

**ANOTHER EDIT:** Today my internet connection is slow as heck, I'm having timeouts all over the place - could that be the problem?

---

### Post by buzzingrobot on 2013-12-12
You are very likely getting those unauthenticated sources warnings because the GPG key for extras.ubuntu.com wasn't updated correctly, and *that* could well happen when your net connection is flakey.

---

### Post by claracc on 2013-12-12
I remember I also have received this past week security updates for libreoffice package, so I think it is O.K.

About the GPG key, perhaps you have a problem with server from which you obtain the security updates, you can try to change it from software sources. Also, I have found this link: [http://askubuntu.com/questions/131601/how-to-overcome-signature-verification-error](http://askubuntu.com/questions/131601/how-to-overcome-signature-verification-error) , which perhaps can help to fix your problem.

---

### Post by t0p on 2013-12-12
> **claracc said:**
> Also, I have found this link: [http://askubuntu.com/questions/131601/how-to-overcome-signature-verification-error](http://askubuntu.com/questions/131601/how-to-overcome-signature-verification-error) , which perhaps can help to fix your problem.

Thanks for the link, it suggested I change the mirror repo server, which I did, and now all seems well.

---

### Post by claracc on 2013-12-13
You are very welcome.

Glad you have fixed your problem.

---

