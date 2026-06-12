---
title: "Evolution with Exchange Connector on Hardy 8.04"
date: 2008-05-08
forum: General Help
---

### Post by holodad on 2008-05-08
Hello Everyone
Hope you are all fine. 

I need some help with my evolution mail client.
Since i upgraded to Hardy 8.04, my evolution keeps on giving problems... 
Actually, i cannot use it at all...:(

The need is to use the latest Evolution to connect to my Exchange server and get my mails.
So i'm using Evo with the Exchange plugin to connect to a Exchange server. Since the upgrade to 8.04, the Evo application just crashes with a nice :"application aborted coredump". This is annoying... 
It works with Imap or any other type of connexions but only Exchange plugin is giving trouble.
If I start Evo without any plugins with something like: evolution --disable-plugins, the AP opens but without any plugins, no connection possible. So it's just not working

Have you got similar issues just after the upgrade? How can i solve this? I already tried many things like reinstalling it after purging all conf files but nothing to do.
One more thing, if anyone knows any other mail clients that uses Exchange proto on Linux, please let me know.

Thanks a lot
Holo

---

### Post by pete on 2008-05-08
Evolution was working fine for me on 8.04 at first, but following this past Tuesday's updates, I've had nothing but problems with the Exchange connector.

It starts up okay (downloads new messages from the Exchange server), but then I get a message that Evolution "Tasks" has died, and then I'm unable to view my calendar on the Exchange server.  

After that, Evolution loses its connection to the back-end process, and I'm unable to view messages in my Exchange account folder.

Force-shutdown of Evolution just leads to a repeat of the problems above, and removal/purge and reinstall of Evolution doesn't help either.  At this point, Evolution is pretty much useless to me, and I've had to resort to Outlook 2k3 in Virtualbox.

Very frustrating.

---

### Post by commonlyUNIQU3 on 2008-06-04
This may help:  [http://ubuntuforums.org/showthread.php?t=812893&highlight=evolution+calendar+exchange](http://ubuntuforums.org/showthread.php?t=812893&highlight=evolution+calendar+exchange)

Here's a quote of the solution: 

> **tytus said:**
> OK. The problem was fixed by installing pre-released version of evolution update. Here are the packages that were upgraded on my system when I enabled pre-release updates and checked in evolution check box:
```
Upgraded the following packages:
evolution (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
evolution-common (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
evolution-data-server (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
evolution-data-server-common (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
evolution-exchange (2.22.1-0ubuntu1) to 2.22.2-0ubuntu1
evolution-plugins (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libcamel1.2-11 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libebook1.2-9 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libecal1.2-7 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libedata-book1.2-2 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libedata-cal1.2-6 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libedataserver1.2-9 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libegroupwise1.2-13 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libgdata-google1.2-1 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libgdata1.2-1 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1

```There is also a discussion about it on evolution mailing list under subject: "Evo started asking for Keyring password every time I start Evo"

---

