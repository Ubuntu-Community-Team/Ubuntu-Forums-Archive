---
title: "Edgy spoiled my Linux partition"
date: 2006-11-01
forum: General Help
---

### Post by krypto_wizard on 2006-11-01
I was happily using Dapper until Edgy came and destroyed my partition.

I did the following thing to move from dapper to edgy.

1. Changed all occurrences of dapper to edgy in the /etc/apt/source.list

2. sudo apt-get update
2. sudo apt-get dist-upgrade


Then I could never boot.

When the computer restarts it says " count not mount the partition /vmlimz.... sometthing like that.

I can't even login in the recovery mode....its halts after some tiem and says "file checking .."


Can you please help me and help me restore my Linux partition.

I don't want the hassle of going through the pain all over again.

Thanks

---

### Post by highneko on 2006-11-01
Is that how you're supposed to upgrade to edgy? Who told you to do this? Maybe undo the source.list thing by: sudo sed -i 's/edgy/dapper/g' /etc/apt/source.list

---

### Post by krypto_wizard on 2006-11-01
Thats how I upgraded from Breezy to Dapper.

What should I do now ?

---

### Post by regeya on 2006-11-01
> **highneko said:**
> Is that how you're supposed to upgrade to edgy? Who told you to do this? Maybe undo the source.list thing by: sudo sed -i 's/edgy/dapper/g' /etc/apt/source.list

Basically what I did too, and I ran into problems, too.  Mainly a few b0rked packages that I'd probably not notice if I did a fresh install.  Edgy is bringing back old nightmares of RH upgrades so far ;) Nah, not really, I even had this sort of thing happen when I used Debian, but I'm betting it's pretty disconcerting for the average user.

As for not even being able to boot, um, wow.  That's pretty wild.  No ideas here.

---

### Post by krypto_wizard on 2006-11-01
I cant even boot into my linux partition.


How can I mend it..........please help.

---

### Post by highneko on 2006-11-02
> **krypto_wizard said:**
> I cant even boot into my linux partition.


How can I mend it..........please help.
I'm sure there's a way. Right now, if I was in your position, I would be reading and asking for help. Don't give up!

---

### Post by vyruss on 2006-11-02
> **krypto_wizard said:**
> I cant even boot into my linux partition.
How can I mend it..........please help.

First of all **don't panic**, nothing is wrong with your ***partitions***. It's just that you didn't use the ***recommended*** upgrade method!

(see **[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)** and **[http://www.debianadmin.com/upgrade-ubuntu-606-dapper-drake-to-ubuntu-10-edgy-eft.html](http://www.debianadmin.com/upgrade-ubuntu-606-dapper-drake-to-ubuntu-10-edgy-eft.html)**)

**Find an Ubuntu Desktop (live) CD and boot your PC with it.**

Then **open a console window and do** this: ```
sudo su
```. Then make a **mountpoint** for your ubuntu partition e.g. if your ubuntu installation is on /dev/hda2 then: ```
mkdir /mnt/a
mount /dev/hda2 /mnt/a
```

Now you have to sort-of "login" to your installation to complete your upgrade by doing this:```
**chroot** /mnt/a
```

You are now at the root directory of your almost-upgraded ubuntu installation. **You can now start doing things to complete the upgrade & rescue your system**.

Try running these now:```
apt-get update
apt-get upgrade
apt-get dist-upgrade
```

If things go wrong, apt-get will tell you more or less what the problem is.

Usually **you will have to run these** commands a few times:```

apt-get -f install
dpkg --configure -a
```

And **these may also come in handy** for problems:```

apt-get -f remove
apt-get autoremove
```

**Remember**, you may have to run these commands **many times each**, and not always in the above order, depending on what is needed. Generally the basic rule is that a few packages have not upgraded properly, so it's best to remove them and reinstall them. The most basic packages you need installed are: **ubuntu-minimal, ubuntu-standard, ubuntu-desktop and xserver-xorg**. Good luck and get to work! :)


**P.S.:** You will also find **these links** helpful:
**[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)** (**very** helpful)
**[http://www.howtogeek.com/howto/ubuntu/upgrading-ubuntu-from-dapper-to-edgy-with-apt-get/](http://www.howtogeek.com/howto/ubuntu/upgrading-ubuntu-from-dapper-to-edgy-with-apt-get/)**
**[https://launchpad.net/distros/ubuntu/+bug/57121](https://launchpad.net/distros/ubuntu/+bug/57121)**

---

### Post by krypto_wizard on 2006-11-02
Thanks for your help.

I will try this method.

---

