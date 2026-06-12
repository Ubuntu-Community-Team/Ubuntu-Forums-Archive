---
title: "CheckGmail says I have wrong username or password"
date: 2008-02-26
forum: General Help
---

### Post by Mattaus on 2008-02-26
...except I know there right. Just every time I run it, a little window pops up asking me for it again so I enter them and it just does something for 5 seconds and comes back again telling me one of them is wrong. I know for sure they are correct!

If anyone knows why it is doing this and possibly how to fix it that would be great!

Thanks

---

### Post by PhilippHD on 2008-02-26
Same with me, although I can't say that it worked before as I just installed it a few minutes ago.

---

### Post by misterfloyd on 2008-03-04
I'm getting this aswell.  Did you guys figure out what was wrong?

---

### Post by patrickfromspain on 2008-03-04
Try the package I attach, it worked for me

---

### Post by jeffus_il on 2008-03-04
Mine works fine out of the box, but does not work on a gmail hosted domain. (it is supposed to). I am checking it out and will post soon.

---

### Post by jeffus_il on 2008-03-04
Here is the latest debian package, install with GDebi...

---

### Post by jeffus_il on 2008-03-04
And this is needed for a hosted domain:
```
**Can I check Gmail on hosted domains?**

 			Yes!  As described in the [Features]("http://checkgmail.sourceforge.net/#features") section above, use the -hosted=[hosted domain] command-line switch the first time you run CheckGmail (if you've run it before, either use a new profile or manually delete the Atom feed line from the preferences file) 

```
from:
[http://checkgmail.sourceforge.net/#faq](http://checkgmail.sourceforge.net/#faq)

---

### Post by jeffus_il on 2008-03-04
I'm having problems connecting CheckGMail to an imap server on a google hosted domain. 
Xfce 4 Mailwatch Plugin works perfectly.

---

### Post by Mattaus on 2008-03-04
Whao...thought this thread had died lol.

Defintely gonna check this all out when I get home. Thanks!

---

### Post by bred on 2008-03-04
> **misterfloyd said:**
> I'm getting this aswell.  Did you guys figure out what was wrong?

works for me!

thx dude!!!

---

### Post by espurious on 2008-05-14
> **patrickfromspain said:**
> Try the package I attach, it worked for me

yup, that got it working for me too. Thanks for that.

---

### Post by EarloftheWest on 2008-05-22
I still can't get this to work with hosted domains.

Here is what is in my pref.xml file:

```
<opt archive_as_read="0"
     atomfeed_address="mail.google.com/a/hosteddomain.com/feed/atom"
     delay="120000"
     gmail_command="firefox %u"
     hosted="hosteddomain.com"
     language="English"
     nomail_command=""
     notify_command=""
     passwd="password"
     popup_delay="6000"
     save_passwd="1"
     show_popup_delay="250"
     time_24="0"
     user="username">
  <label_delay></label_delay>
</opt>
```

Can anyone suggest any tweaks to get this working? Thanks.

UPDATE
I logged out of my hosted Gmail account, closed and reopened my browser, went to my atom feed site: (example)
[http://mail.google.com/a/hosteddomain.com/feed/atom](http://mail.google.com/a/hosteddomain.com/feed/atom)
It then asked me for my username and password which I provided. It then returned:
Unauthorized
Error 401

I logged back into my hosted Gmail account and was then able to access the atom feed correctly (via firefox) without being prompted for a username or password.

This makes me think that there is something wrong with authorization with Gmails atom feeds.

UPDATE2
Problem Solved:
[http://sourceforge.net/forum/forum.php?thread_id=2042637&forum_id=463626](http://sourceforge.net/forum/forum.php?thread_id=2042637&forum_id=463626)

---

### Post by jeffus_il on 2008-05-29
Use ```
checkgmail -update
``` to download the latest version, it will fix your problem.

---

