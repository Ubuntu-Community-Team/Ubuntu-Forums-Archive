---
title: "For mikasjoman and possibly other 'new web developers'"
date: 2008-02-22
forum: General Help
---

### Post by ryanhaigh on 2008-02-22
In reply to [this thread]("http://ubuntuforums.org/showthread.php?t=704246") that was closed  and another that I don't have the address for. Hopefully third time lucky!

mikasjoman I was replying to you in another very similar thread of yours that must have been deleted/moved so I unfortunately lost what I was saying so here it is in brief.

[LIST]
[*]Users should not be able to change system directory permissions without proving that they have the right to do so, as someone mentioned policykit integration will make this easier but for the moment you could install [apt://nautilus-gksu]("apt://nautilus-gksu")  which will add a right click menu allowing you to open a folder/doc/etc with admin rights its a great tool but should be used sparingly and with caution, great power...responsibility and all that

[*]If you are using Apache there are docs explaining how you can setup /home/user/public_html folders to allow users to have their own sites accessible via [www.address.com/~user](www.address.com/~user) which is how my university does it. If users were given access to /var/www then they would overwrite each others stuff and no-one would be happy. Like you my universities are running Linux, it cannot and should not be assumed that only one user will be using the system, thus the permissions.

[*]You could look at other servers that allow you to run as users using higher port numbers im sure there are some in synaptic.

[*]The current system is not stupid, there is a reason a significant portion of the worlds servers run Linux and personally i think www is perfectly reasonable, although as with all things it can be configured, for Apache I believe the option is DocumentRoot although it has been a while so I can't be sure.

[*]I would be VERY surprised if 50% of ubuntu users wanted to run their own servers. 

[*]A quick rummage around the official ubuntu docs yeilds this: [https://help.ubuntu.com/7.10/server/C/httpd.html](https://help.ubuntu.com/7.10/server/C/httpd.html) don't have the time (or patience after three attempts) to read but I'm sure the info will be useful.

[/LIST].

---

