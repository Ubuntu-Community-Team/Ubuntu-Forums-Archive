---
title: "Issue with Keepassx : couldn't save changes"
date: 2017-03-06
forum: General Help
---

### Post by cogset on 2017-03-06
I'm asking here because the Keepassx forum looks kinda useless, as the question I'm going to ask here has apparently been asked before and even submitted as a bug report, to no avail.

  The issue is that all of a sudden Keepassx will sometimes refuse to save changes to the database and display this message ```
File could not be saved. The file could not be removed
``` 

  If I'm not mistaken, I  may have already  seen this message (or a very similar one) sometimes before, but all it took was to close the dialog and save again the changes - on the contrary, what happens now is that *I really can't save any changes*, unless I reboot the system.

  I would logically suspect some kind of database corruption, but then why would only happen occasionally and also why would a reboot "fix" this?

  The really weird thing is that I've tried (after quitting Keepassx) to remove the lock file and the .tmp database and it wouldn't solve the issue, furthermore when trying to overwrite  the .kdb database with a good backup I couldn't do this: a message in the terminal showed that the file was actually in use and therefore couldn't be removed/renamed/overwritten.   

But I've checked with ```
sudo fuser -u -v ~/.keepass.kdb
``` and ```
sudo lsof ~/.keepass.kdb
``` at the very time this was happening, and according to this commands *no one was accessing the file*  : so why was the file reported in use, and by whom ? 

If there are no instances of Keepassx running (I've used pgrep to make sure) and neither fuser or lsof show the .kdb database to be in use, how come that I still can't operate on this file in any way when this issue is happening?

---

### Post by howefield on 2017-03-08
Which versions of Ubuntu and Keepassx are you using ?

```
cat /etc/*-release
```
```
keepassx -v
```

---

### Post by cogset on 2017-03-09
Keepassx 0.4.3 in Trusty - not that the OS may matter here, as I've seen this reported for MacOS as well.

   As I've said, it is an issue with Keepassx, but its forum is hardly useful as questions the likes of this one sit there unanswered forever. 

   I'm more interested in what knowledgeable folks here may say, starting with why a file should be "in use" when lsof and fuser show no evidence of that.

---

### Post by howefield on 2017-03-09
Reason I asked is that 0.4.3 is such an ancient version, there are likely to be very few who care about bugs/problems in 0.4.3 unless they are reproducible against the current version which is 2.0.3.

---

### Post by oldfred on 2017-03-09
I found when I installed 16.04LTS as my new main working install from my 14.04LTS install that I had to import the old .kdb into my new KeepassX program as it now uses .kdbx file and then save in new format.
It gave me various errors until I corrected that.

I gather that is more compatible with other password programs.

---

### Post by howefield on 2017-03-09
> **oldfred said:**
> I found when I installed 16.04LTS as my new main working install from my 14.04LTS install that I had to import the old .kdb into my new KeepassX program as it now uses .kdbx file and then save in new format.

The newer Keepassx 2.0.2 is the version packaged with 16.04 and 2.0.3 is what 17.04 will (does) have. 

Seems to have been a bit of a falling out over a lack of development in the keepassx team, leading to a fork keepassxc.

> Why KeePassXC instead of KeePassX?
KeePassX is an amazing password manager, but hasn't seen much active development for quite a while. Many good pull requests were never merged and the original project is missing some features which users can expect from a modern password manager. Hence, we decided to fork KeePassX to continue its development and provide you with everything you love about KeePassX plus many new features and bugfixes.

Don't think the newer keepassx will work on Ubuntu 14.04, at least not without having to resort to a PPA. I have tested the AppImage and snap package of Keepassxc on 14.04 and both seem to work well. This may not be suitable for the OP but mentioned for casual readers who may also be on Keepassx 0.4.3.

---

### Post by cogset on 2017-03-16
Thanks for the interesting replies: so not only version 0.4.3 is kinda outdated (although it's still the one you're stuck with if you are using older LTS versions such as Trusty), but actually the entire project seems to be not actively developed, or at least not closely followed - which doesn't sound good. 

 That - in retrospect - may also explain why over there >  the question I'm going to ask here has apparently been (already) asked before and even submitted as a bug report, to no avail. 

  However, short of finding a PPA for a newer version (which I'd rather not, because I tend to avoid PPAs as a general rule), there's really not much I can do about it. 

 It's  also good to know that there is a fork (Keepassxc) , but that also doesn't look as a straightforward fix [for Trusty at all]("http://www.omgubuntu.co.uk/2017/02/install-snap-apps-ubuntu-14-04") : > To install Snapd also require a number of additional packages to be installed and/or upgraded, including a new Linux Kernel, systemd (this won’t replace Upstart/init), snapd itself, ubuntu-core launcher, an updated apparmor, and others interesting, but that's really too much just for the sake of a password manager.  I'd rather keep this installation of Trusty as clean as possible (that's why I went for Lubuntu, BTW) . 

 
Having said  that, I'm still very curious about this part of my original post: > when trying to overwrite the .kdb database with a good backup I couldn't do this: a message in the terminal showed that the file was actually in use and therefore couldn't be removed/renamed/overwritten.  But I've checked with ```
sudo fuser -u -v ~/.keepass.kdb  sudo lsof ~/.keepass.kdb 
```  at the very time this was happening, and according to this commands no one was accessing the file : so why was the file reported in use, and by whom ?   Does anybody here have a clue ?

---

