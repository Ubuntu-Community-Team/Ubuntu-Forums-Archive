---
title: "upgrade from old version, how??"
date: 2008-06-13
forum: General Help
---

### Post by madara_sama on 2008-06-13
How to upgrade ubuntu from previous version to latest version?
I mean not from the 1 previous version.
For example, from feisty(7.04) to hardy(8.04). Of course not clean install.
So, only upgrading old packages and add new packages.

---

### Post by Lord Xeb on 2008-06-13
Just got to update manager and you will see a thing that says upgrade. Just upgrade. Or burn the .ISO of Hardy and put it in. You should be able to upgrade that way...I think.

---

### Post by madara_sama on 2008-06-13
I have only live n install cd. I don't have alternate cd.
I have read from ubuntu documentation about how to update. But, only for from 1 previous version. And the other, clean n install.
That's it. I mean from live n install cd. Can I??

---

### Post by jrusso2 on 2008-06-14
> **madara_sama said:**
> I have only live n install cd. I don't have alternate cd.
I have read from ubuntu documentation about how to update. But, only for from 1 previous version. And the other, clean n install.
That's it. I mean from live n install cd. Can I??

I don't know if its still possible you would have to upgrade using the upgrade manager from feisty to gutsy first, then use it again to upgrade to hardy.

When I use the upgrade manager I first rem out any non stock repository I have used like if I had used automatix or wine repos.

Then I so the upgrade and keeping an eye on it cause it will stop and ask if you want to keep configurations which I usually say yes to.

Of course YMMV.  Always back up any data you can't afford to lose.

---

### Post by cdtech on 2008-06-14
I upgraded my server from 6 to 8 using the command line:

Changed the sources.list to Hardy:

```
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main universe multiverse restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy-security universe main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse
```

Then I updated the source list using the following command:
sudo apt-get update

Then performed the upgrade with the following command:
sudo apt-get dist-upgrade

And to make sure that everything was installed, I issued the command:
sudo dpkg –configure -a

I opted to keep my old menu.lst during the upgrade and just edited it to include the new kernel image.

Once I rebooted my system I tested my upgrade with the following command:
sudo lsb_release -a

The output looked like this:
Distributor ID: Ubuntu
Description: Ubuntu 8.04
Release: 8.04
Codename: hardy

This may not work for everyone but it did work for me and I kept all of my installed packages that were also upgraded as well.

---

### Post by madara_sama on 2008-06-14
So, that's mean I must do clean install if I only have ubuntu live n install cd....??

---

### Post by jrusso2 on 2008-06-14
> **madara_sama said:**
> So, that's mean I must do clean install if I only have ubuntu live n install cd....??

Not sure what you mean, you have been given two options and the third of download the alternate cd.

Of course a clean install is the best which you could do with the live cd.

---

### Post by madara_sama on 2008-06-14
Yeah, I know. Internet or alternate cd. But, both of 'em I never have. So, there above I said I have only ubuntu live n install.
In my place, only ubuntu live n install CDs are sold.
Well, I give up...
clean install is my choice after all...

---

