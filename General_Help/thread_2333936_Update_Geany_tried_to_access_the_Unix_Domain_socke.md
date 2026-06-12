---
title: "Update: Geany tried to access the Unix Domain socket of another instance running as a"
date: 2016-08-14
forum: General Help
---

### Post by Naja_Linux on 2016-08-14
Updating a post I saw from 2014...this problem still exists.

The error message is, "Geany tried to access the Unix Domain socket of another instance running as another user...."

The sign is that geany will not start and gives a dialog with this error message.

I saw a post here from 2014 that claimed the problem was solved and posted a 'solution'.  It did not really adequately describe the problem nor why suggested solution works.  It was a good stepping off place to find the problem though.  Note the dialog for geany has not been updated to be any more meaningful (the quote above does not describe the problem to mere users.)  It appears that geany was stopped without cleaning up all of its open 'sockets' and one must exist in a current configuration directory.  Removing the directory will clear the problem but any settings or history may also be lost.  A better solution is to find the socket and delete it (rm [socket name])  If you look in your ~/.configs/geany directory, you will see a listing with a similar name to:

geany_socket_I3770K__0 -> /tmp/geany_socket.b9fcdd9b

Delete this and  you should be back directly to your previous (normal) state of operation.  Someone did mention using gksu or gksudo instead of sudo, probably mysterious but good advice to users.  A terminal construct such as (exactly):
(gksu geany &) 
will start it up nicely.  Just enter password when prompted.

I believe my post has new information that updates or is more relevant than the post from 2 years ago.

/..

---

### Post by wildmanne39 on 2016-08-14
Hello, gksu and gksudo is deprecated it is no longer recommended to be used when running GUI application as root, in fact gksu nor gksudo is installed in Ubuntu by default anymore.

Yes you do not want to run GUI application from the terminal using sudo because in many cases and I have seen it happen the files become owned by root then you can not access them anymore without fixing the permissions issues and it can be a mess.

The preferred command is [COLOR="#FF0000"]sudo -H[/COLOR] I myself have been using this command a lot and it works great and it is safe.

Please update your post to include this information and remove the deprecated method please.

The man page explains about sudo's options.
> -H, --set-home
                 Request that the security policy set the HOME environment
                 variable to the home directory specified by the target user's
                 password database entry.  Depending on the policy, this may
                 be the default behavior.
[http://manpages.ubuntu.com/manpages/xenial/en/man8/sudo.8.html](http://manpages.ubuntu.com/manpages/xenial/en/man8/sudo.8.html)
Thanks

---

