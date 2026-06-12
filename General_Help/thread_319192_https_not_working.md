---
title: "https not working"
date: 2006-12-15
forum: General Help
---

### Post by nabilmalik on 2006-12-15
I have been using Drapper (Ubuntu 6.06) for the last 2 months. All this time, I was not able to access web sites that require the secure https connection including gmail and others.. However, http works perfectly fine.

I installed another web browser named Opera, and it also cannot access https sites. Also, Gaim (messanger software) doesn't let me connect to the msn messanger service. Perhaps that also requires the use of https.

However, when I installed kubuntu package for KDE, the KDE web brower 'Konqueror' can access https websites. But Firefox and Opera still cannot access https, even when I am using KDE as my windowmanager. Additionally, KDE specific messanger (forgot the name) also works very well..

I have been searching the Internet for a solution but failed to come across any. Only yesterday i went for a fresh reinstall of ubuntu 6.06, and was hoping that the problem would dissapper, but i was wrong..

Any help will be very appreciated, as I don't want to move back to MS Windows.

Thanks,

-Nabil.
Edit/Delete Message

---

### Post by dcstar on 2006-12-15
> **nabilmalik said:**
> I have been using Drapper (Ubuntu 6.06) for the last 2 months. All this time, I was not able to access web sites that require the secure https connection including gmail and others.. However, http works perfectly fine.

I installed another web browser named Opera, and it also cannot access https sites. Also, Gaim (messanger software) doesn't let me connect to the msn messanger service. Perhaps that also requires the use of https.

However, when I installed kubuntu package for KDE, the KDE web brower 'Konqueror' can access https websites. But Firefox and Opera still cannot access https, even when I am using KDE as my windowmanager. Additionally, KDE specific messanger (forgot the name) also works very well..

I have been searching the Internet for a solution but failed to come across any. Only yesterday i went for a fresh reinstall of ubuntu 6.06, and was hoping that the problem would dissapper, but i was wrong..

Any help will be very appreciated, as I don't want to move back to MS Windows.

Thanks,

-Nabil.
Edit/Delete Message

Do a forum search for "disable ipv6" and you may want to try some of those options.

---

### Post by nabilmalik on 2006-12-16
ok, dcstar asked me to check if disabling ipv6 helps... I searched how to do it and every thing now works.. Please refer to the following post for disabling ipv6.

[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

Not that if you are using Drapper, please go ahead couple of pages for specific instructions for draper.. On second thought, i will past it here::

>>>>>>>>>>>>>>
In Dapper I got to disable ipv6 in this way: Make a file called 'blacklist-ipv6' in  /etc/modprobe.d/ and inside the file put this text: blacklist ipv6

So the next time you boot, the ipv6 module won't be loaded (lsmod | grep ipv6 ; it's a better way to check ipv6 presence than 'ip a | grep inet6', I think, since the module manages the thing).
<<<<<<<<<<<<<<

Thanks to all..!

-Nabil.

---

