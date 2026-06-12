---
title: "Mail Notification 4.0 - unable to make"
date: 2007-05-14
forum: General Help
---

### Post by moehle on 2007-05-14
Hi,

I'm running fiesty (installed today) and haven't seen this error in previous versions. I tried changing the /bin/sh link to use bash but haven't had any luck. ./configure worked successfully and ssl is enabled. When I try to make I get this error:

/bin/sh: line 1: -o: command not found
make[2]: *** [bg.gmo] Error 127
make[2]: Leaving directory `/home/david/Desktop/mail-notification-4.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/Desktop/mail-notification-4.0'
make: *** [all] Error 2

Can anyone help with this? 

Thanks

---

### Post by reclusivemonkey on 2007-05-16
Is there a reason you aren't using the Mail Notifications in the repos?

---

### Post by mrbungle on 2007-05-16
i am having lots of problems with the one in the repos.  still in beta it seems.

---

### Post by mlind on 2007-05-16
Here's a newer mail-notification with SSL enabled for feisty i386 (taken from gutsy's archive).

---

### Post by mrbungle on 2007-05-16
thank you very much :)

its working great now!

---

### Post by Kent84 on 2007-05-16
I had problems using "mail-notification" from synaptics (fiesty i386) with an IMAP server. It worked initially but after about a week it wouldn't show new emails (no error messages). The version attached by mlind seems to be working for me... hopefully it won't stop working in a week like last time.

---

### Post by moehle on 2007-05-28
I tried the one in the repos but it doesn't seem to work using SSL and IMAP. I'll try the one posted above. Cheers for the help!

---

### Post by robbie75 on 2007-06-03
> **mlind said:**
> Here's a newer mail-notification with SSL enabled for feisty i386 (taken from gutsy's archive).

Thank you very much!!!
I was fighting with mail-notification since the upgrade to feisty
and now I've got imap-ssl working!
THANK YOU!
Rob

---

### Post by nwb1214 on 2007-12-15
I was having the same problem compiling Mail Notification 5.0 RC1 on Ubuntu 7.10. This thread was basically the only thing I found when I googled the error.  Here was my output from make:

Making all in po
make[2]: Entering directory `/tmp/mail-notification-5.0-rc1/po'
file=`echo bg | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file bg.po
/bin/sh: -o: not found
make[2]: *** [bg.gmo] Error 127
 make[2]: Leaving directory `/tmp/mail-notification-5.0-rc1/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/mail-notification-5.0-rc1'
make: *** [all] Error 2

Since no one actually answered the first post (which is really frustrating when trying to find answers for your problem), here's how I solved it.  I looked in the Makefile in the po directory and found that the GMSGFMT variable wasn't set to anything.  I googled that and found this link that gave me a hint:

[http://mail.gnome.org/archives/orca-list/2007-March/msg00345.html](http://mail.gnome.org/archives/orca-list/2007-March/msg00345.html)

I had gettext-base installed, but not the gettext package.  Once I installed that, I re-ran ./configure and then make and everything worked.

The reason I'm not using the package in the repos is because it's stripped of it's functionality.  My pop3 and imap mail server only allows ssl/tls logins, so the repo package won't even work for me.

---

### Post by auraithx on 2008-05-06
> **nwb1214 said:**
> I was having the same problem compiling Mail Notification 5.0 RC1 on Ubuntu 7.10. This thread was basically the only thing I found when I googled the error.  Here was my output from make:

Making all in po
make[2]: Entering directory `/tmp/mail-notification-5.0-rc1/po'
file=`echo bg | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file bg.po
/bin/sh: -o: not found
make[2]: *** [bg.gmo] Error 127
 make[2]: Leaving directory `/tmp/mail-notification-5.0-rc1/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/mail-notification-5.0-rc1'
make: *** [all] Error 2

Since no one actually answered the first post (which is really frustrating when trying to find answers for your problem), here's how I solved it.  I looked in the Makefile in the po directory and found that the GMSGFMT variable wasn't set to anything.  I googled that and found this link that gave me a hint:

[http://mail.gnome.org/archives/orca-list/2007-March/msg00345.html](http://mail.gnome.org/archives/orca-list/2007-March/msg00345.html)

I had gettext-base installed, but not the gettext package.  Once I installed that, I re-ran ./configure and then make and everything worked.

The reason I'm not using the package in the repos is because it's stripped of it's functionality.  My pop3 and imap mail server only allows ssl/tls logins, so the repo package won't even work for me.

Thanks this fixed my problem when trying to install the pidgin OTR plug-in.

```
sudo apt-get install gettext
```

---

### Post by newb1e on 2008-05-07
> **Kent84 said:**
> I had problems using "mail-notification" from synaptics (fiesty i386) with an IMAP server. It worked initially but after about a week it wouldn't show new emails (no error messages). The version attached by mlind seems to be working for me... hopefully it won't stop working in a week like last time.

I have a similar problem, it can get Gmail and IMAP, but not Yahoo mail (I have fetchyahoo package). It seems to connect to the yahoo mail server ok(no error messages), just the new mails don't show up. I built it from source because the one in repos couldn't get yahoo mail (the last time I checked)
> **mlind said:**
> Here's a newer mail-notification with SSL enabled for feisty i386 (taken from gutsy's archive).

can this one get yahoo?

---

