---
title: "PolicyKit want permission to run /usr/bin/dropbox as the super user.  Should I allow?"
date: 2013-03-10
forum: General Help
---

### Post by tc101 on 2013-03-10
PolicyKit wants permission to run /usr/bin/dropbox as the super user.  Should I allow this?  I don't know anything about freedesktop.policykit.exec and have been running dropbox for months without getting this request.  I got it when I was looking at the official US timesite from firefox, although that could just be a coincidence.

---

### Post by tc101 on 2013-03-10
64 people have looked a this, but no answer so far.  Usually if nobody answers in 8 hours nobody is going to answer.  Is there someplace else I might post this question and get an answer?

---

### Post by guigs on 2013-05-06
I got the same message today and I don't have any idea what it means.

---

### Post by M0les on 2013-07-10
Just got this today too.

I suppose the simplistic answer is that PolicyKit (The thing that asks you for super-user permissions) is asking you to allow it to run the dropbox commandline tool as the super-user.

My response is that Dropbox should not need root access for the way I have it configured (Syncing a home-dir folder, all owned by my user ID) - So I denied the request.
This has the unfortunate side-effect that Dropbox nolonger syncs, but that's the price I'm prepared to pay.

Sorry if this sounds condescendingly simplistic, but I thought it may be of use to some of the readers.

---

### Post by noteviljoe on 2013-07-12
Had the same thing - I did a bit of googling and it seems to be a genuine dropbox thing so I just let it have the privileges as need my dropbox to keep working at the mo.

---

### Post by immanuel-normann on 2013-09-25
those who don't hesitate to put some effort to improve her/his system security might find interesting information here:

[https://grepular.com/Protecting_Your_GNU_Linux_System_from_Dropbox](https://grepular.com/Protecting_Your_GNU_Linux_System_from_Dropbox)

---

### Post by thilina on 2013-12-26
This can be fixed by correcting the **PARENT_DIR** variable in the dropbox executable. It points an invalid location. If you need to find a guide on how to fix this, please refer to [http://blog.ishans.info/2013/12/26/fixing-authentication-is-needed-to-run-usrbindropbox-as-the-super-user-error-in-linux/]("http://blog.ishans.info/2013/12/26/fixing-authentication-is-needed-to-run-usrbindropbox-as-the-super-user-error-in-linux/")

---

