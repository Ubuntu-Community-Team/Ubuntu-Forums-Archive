---
title: "In need of some help"
date: 2013-01-07
forum: General Help
---

### Post by Nik2013 on 2013-01-07
Hi, this is my first time using ubuutu as an OS and I'm going to try and put together a media server with it. Since people in my house still want to use the computer I'm going to be setting it up on I'll have to use Ubuutu desktop and not the server for it.

Anyway, I've found a number of guides for setting up a server and most use Samba to share folders/drives. Recently though I read another way to share drives in this article:

[COLOR=Blue][http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu](http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu)[/COLOR]

As far as I can tell with that method you mount the drive and then check the 'share this folder' tab in Nautilus. 

Assuming that that above method works my question is should I go with using Samba or that method in the article? would there be any advantages/disadvantages of either option? bear in mind that the other machines in the house are all running windows 7.

Thanks for any help and if anyone has any futher advice that would be great too.

---

### Post by Cheesemill on 2013-01-07
The lifehacker article that you linked to ***does*** use samba to share files, you are just configuring it using nautilus instead of manually editing text files.

If you set up a share using nautilus and then take a look at the /etc/samba/smb.conf file you will see the share declaration that nautilus has put there.

So at the end of the day both methods use exactly the same program, you are just doing the configuration in a different way.

---

### Post by Nik2013 on 2013-01-07
Thanks Cheesemill for your reply and your answer to my question.

---

