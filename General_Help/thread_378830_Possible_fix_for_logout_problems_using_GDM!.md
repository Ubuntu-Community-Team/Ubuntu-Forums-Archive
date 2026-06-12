---
title: "Possible fix for logout problems using GDM!"
date: 2007-03-07
forum: General Help
---

### Post by payuco on 2007-03-07
After installing and setting up Ubuntu, things were going smooth.  However, at some point something happened to cause the logout option to not work properly.

I searched and searched these forums and have seen many posts from people with the same type of problem.

Exact problem I had:

Click logout
Blank Screen
Monitor kept trying to switch between analog and digital
ctr-alt-del and enter to reboot because I could do nothing else


I don't think this issue has one specific cause because many people have had this similar problem with various setups and different display managers.

I use gnome and it looks like it was a gnome fix/workaround that enabled my logins again.



This is what I did (this suggestion was buried in posts from August with only one reponse):



sudo gedit /etc/gdm/gdm.conf-custom

Add AlwaysRestartServer=true into the [daemon] section:

[daemon]
AlwaysRestartServer=true


Now I'm not sure this is really a proper fix, but it's working for me now and is sure alot better than having to do a soft boot every time.

I noticed a few bug reports about this issue, one of which is confirmed.  Hopefully there will be a fix in a future update.



If you have any other comments about using this method or other ideas, please comment.


If this fixes your problem or even if you tried and it doesn't, please post.


Thanks to Lonthong for this tip: [http://www.ubuntuforums.org/showthread.php?t=254167&page=4&highlight=logout+blank+screen](http://www.ubuntuforums.org/showthread.php?t=254167&page=4&highlight=logout+blank+screen)

:)

---

### Post by 45362457247 on 2007-03-10
Yes, thankyou.  This fixed my switch-user black screen issue.

edit: no it didn't.

---

