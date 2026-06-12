---
title: "Thunderbird suddenly refused connection to Googlemail"
date: 2015-01-30
forum: General Help
---

### Post by stepheny on 2015-01-30
I have been using Thunderbird and Googlemail together on my Ubuntu laptop for years now but suddenly, this morning Thunderbird started giving the warning "Could not connect to [email]xxx.yyy@googlemail.com[/email]. The connection was refused" I can connect to Googlemail via a browser and on my Android phone.

I am using Thunderbird 31.3.0 and Ubuntu 14.04. Thunderbird is set up to use imap.googlemail.com port 993 (SSL/TLS) with normal password. Perhaps my password has got corrupted but I cannot remember how to clear it to re-write it.

I don't think I have done anything that could cause this to happen. All I have done is recently is set up a network drive using this howto [http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/)

Other threads with similar problems have not helped so any help would be greatly appreciated.

---

### Post by howefield on 2015-01-30
Solved, as in you've fixed the issue ?

I'd think you'd be prompted for the password if it was wrong/corrupted. But you can delete or view the password by going to Edit > Preferences > Security > Passwords > Saved Passwords.

---

### Post by stepheny on 2015-01-30
In order to get the network drive working I had edited the line in the file /etc/nsswitch.conf from 

```
hosts:          files myhostname mdns4_minimal [NOTFOUND=return] dns mdns4
``` to

```
hosts:          files myhostname mdns4_minimal [NOTFOUND=return] wins dns mdns4
```

After changing it back Thunderbird started being able to log on to Googlemail again.

But I will need another way of setting up the cifs network drive :cry:

---

