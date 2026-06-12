---
title: "Help Citrix Client SUCKS on Ubuntu!"
date: 2005-07-29
forum: General Help
---

### Post by psypher on 2005-07-29
I am having very serious trouble with Ubuntu and the Citrix Client.

I am a citrix network admin and for me and my network team to migrate to Ubuntu this HAS to work. Shadowing users from the citrix ICA client works only 50% of the time, the other 50% my entire citrix session bombs out as soon as I log in. The session disconnects but keeps running on the server and I can reconnect to it but forget shadowing. Sometimes it doesn't bomb out but flashes in a cycle on both my screen and the person I am shadowing and it just keep cycling and flashing

This is quite serious as this is an integral part of a citrix network

We are running citrix MP3 and will soon be upgrading to MP4 (next 2 weeks in fact) and I hope that it will be fixed then but I doubt it, this seems like a client/gnome/ubuntu problem as I have been using the ICA client AND shadowing on Mandrake Community 10 for almost a year now and not once have a problem like this. I suspect it being a Gnome problem as Mandrake is using KDE. I have tried both version 8 and 9 clients and the exact same thing happens. This has also happened on new installs, old installs, different PC's and they all the same.

I have not had much luck googling this problem as nobody seems to have had this happen.

The only error I get when trying to shadow is (output on the command line):
segmentation fault


I am using a full desktop 1024x768 fixed connection and using the Management Console to shadow.

It seems that shadowing works ok when I shadow users that have smaller size dekstops, 800x600 and bombs out when trying to shadow 1024x768 desktops. When my screen tries to resize itself to their desktop size it disconnects me

PLEASE ANY HELP!!  ](*,)

---

### Post by dukeinlondon on 2005-07-29
[QUOTE=psypher]I am having very serious trouble with Ubuntu and the Citrix Client.

I am a citrix network admin and for me and my network team to migrate to Ubuntu this HAS to work. Shadowing users from the citrix ICA client works only 50% of the time, the other 50% my entire citrix session bombs out as soon as I log in. The session disconnects but keeps running on the server and I can reconnect to it but forget shadowing. Sometimes it doesn't bomb out but flashes in a cycle on both my screen and the person I am shadowing and it just keep cycling and flashing

This is quite serious as this is an integral part of a citrix network

We are running citrix MP3 and will soon be upgrading to MP4 (next 2 weeks in fact) and I hope that it will be fixed then but I doubt it, this seems like a client/gnome/ubuntu problem as I have been using the ICA client AND shadowing on Mandrake Community 10 for almost a year now and not once have a problem like this. I suspect it being a Gnome problem as Mandrake is using KDE. I have tried both version 8 and 9 clients and the exact same thing happens. This has also happened on new installs, old installs, different PC's and they all the same.

I have not had much luck googling this problem as nobody seems to have had this happen.

The only error I get when trying to shadow is (output on the command line):
segmentation fault


I am using a full desktop 1024x768 fixed connection and using the Management Console to shadow.

It seems that shadowing works ok when I shadow users that have smaller size dekstops, 800x600 and bombs out when trying to shadow 1024x768 desktops. When my screen tries to resize itself to their desktop size it disconnects me

PLEASE ANY HELP!!  ](*,)[/QUOTE]
 What does Citrix support say about it ? Also, have you tried using kde in ubuntu if you suspect kde has something to do with it ?

---

### Post by psypher on 2005-08-01
well like I said I googled it and searched citrix forums high and low. unless you can suggest a better list of words to search for other than a combination of "shadow linux client gnome segmentation fault" I can't find a thing

Just installed kubuntu and on my 1st shadow attempt it bombed out, so this must be a debain/ubuntu problem and is hopefully easy to fix. Just tried again and same problem

Just had a thought, could this be a xorg problem since my mandrake is still on xfree86?

I will see if there is anything on that on the net but I would appreciate it if anybody else who has any insight could post.

Thanks for the help in advance

---

