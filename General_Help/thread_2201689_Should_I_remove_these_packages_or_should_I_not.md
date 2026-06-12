---
title: "Should I remove these packages or should I not?"
date: 2014-01-25
forum: General Help
---

### Post by deaton25 on 2014-01-25
Hello
I am pretty new to Ubuntu. Recently, I had some problems with Skype. So I uninstalled/re-installed it. And the problem was solved. I also decided to get rid of the little message/mail indicator on top because I did not want/need it.
I followed the command information I found on the forum. And the indicator went away. So far so good.
Then I pressed apt-get autoremove and got the following:
```
alan@alan-Latitude-D530:~$ sudo apt-get autoremove
[sudo] password for alan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libaudio2:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libcups2:i386 libdatrie1:i386 libdbusmenu-qt2:i386
  libfontconfig1:i386 libfreetype6:i386 libgcrypt11:i386 libgnutls26:i386
  libgpg-error0:i386 libgssapi-krb5-2:i386 libice6:i386 libjpeg-turbo8:i386
  libjpeg8:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms1:i386 libmng1:i386 libmysqlclient18:i386
  libp11-kit0:i386 libqt4-dbus:i386 libqt4-declarative:i386
  libqt4-network:i386 libqt4-script:i386 libqt4-sql:i386 libqt4-sql-mysql:i386
  libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtgui4:i386
  libqtwebkit4:i386 libsm6:i386 libsqlite3-0:i386 libtasn1-3:i386
  libthai0:i386 libtiff4:i386 libxi6:i386 libxrender1:i386 libxss1:i386
  libxt6:i386 libxv1:i386 mysql-common skype-bin:i386 sni-qt:i386
0 upgraded, 0 newly installed, 48 to remove and 0 not upgraded.
After this operation, 118 MB disk space will be freed.
Do you want to continue [Y/n]? 
```

This was also confirmed at Ubuntu Tweak Janitor, where it says I have 48 unneeded, unnecessary packages that can/should be removed. IT ALSO HAS A SMALL RED CIRCLE BEFORE THIS!! This sure looks like a beware/warning sign to me!!! 
My question is: should I get rid of this stuff or did I press a wrong button somewhere, In which case, if I get rid of this stuff will my computer crash and burn! This has happened before!!! Should I worry or is everything ok and I can remove this stuff. To do or not to do: that is the question! If it is really dangerous to eliminate this stuff, then how would I fix Ubuntu Teak Janitor and autoremove at the terminal so I don't get these messages?

---

### Post by sudodus on 2014-01-25
I have such a warning sign in Ubuntu Tweak too (in one of my systems). I cannot clean the packages 'belonging' to it. I think you can try, if they go away, good, otherwise they will probably only occupy some space on the HDD.

---

### Post by deaton25 on 2014-01-25
Thanks for your reply. Presumably, that warning sign is there for a good reason, no?!
My concern is that if I do manage to remove those packages through Autoremove, then my computer will die!
Are my fears justified?

---

### Post by sudodus on 2014-01-25
Mine didn't die. And if you would need those packages, they can be restored.

But it will give you peace of mind to have a ***good backup***, at least of all your personal files. The system can be restored rather easily.

Let those packages stay, if Ubuntu Tweak cannot remove them!

---

### Post by dnemcanin2 on 2014-01-25
With **autoremove** you are deleting libraries that are not in use any more. When deleting package, libraries that package depend on aren't delete because some other package might depends on them. But if no one package depends on these libraries autoremove offered it to delete them.
try sudo apt-cache rdepands <libraries> to see who is depending on this libraries

bottom line: do it without fear

---

### Post by Frogs Hair on 2014-01-25
I find synaptic a good tool to indicate what to autoremove after removing  a software program . The unneeded packages are listed under status as auto-removable. The Ubuntu Tweak Janitor has never removed anything vital from my system though I use it mainly for old kernel removal.

---

