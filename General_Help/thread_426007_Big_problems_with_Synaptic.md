---
title: "Big problems with Synaptic"
date: 2007-04-28
forum: General Help
---

### Post by hackarre on 2007-04-28
Hi!

Every time I try to open my synaptic gestor this message showes up 

E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: S'ha produ\u00eft un error durant el processament de thunderbird-locale-nb-no (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
E: No s'han pogut analitzar o obrir les llistes de paquets o fitxer d'estat.
E: _cache->open() failed, please report.

"An error had been produced during the processesin of thunderbird-locale-nb-no"

"It wasn't possible to analitze or open the package lists or state documents"

This also happens to me when I try with terminal sudo apt-get and try to update some programs.


Plz I really need help :cry: 

The only thing that I've done that could affect something is that I changed my grub with a nice image instead of the regular one.

---

### Post by lw5 on 2007-04-28
First off; I don't know the answer :p  but:

Did you run this error through google? It seems to have a lot of hits on the subject.
Also it might be helpful to post your /etc/apt/sources.list

---

### Post by hackarre on 2007-04-28
I've been thinking for a while and I think that the problem is that I did that for installing ubuntu studio:

    :~$ sudo su


    :~$ cp /etc/apt/sources.list /etc/apt/sources.list_backup_`date +%Y%m%d%H%M`


    :~$ echo deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse > /etc/apt/sources.list


    :~$ echo deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse >> /etc/apt/sources.list


    :~$ echo deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse >> /etc/apt/sources.list


    :~$ echo deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse >> /etc/apt/sources.list


    :~$ echo deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse >> /etc/apt/sources.list


    :~$ echo deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse >> /etc/apt/sources.list


    :~$ apt-get update


    :~$ apt-get dist-upgrade


    :~$ exit

The true is that I didn't think when I was doing it :( 


And my sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty main universe restricted multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-security universe main multiverse restricted
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-updates universe main multiverse restricted
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

I had to active universe and multiuniverse sources.

Now the error is like that:

E: Dynamic MMap ran out of room
E: S'ha produ\u00eft un error durant el processament de basilisk2 (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/es.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages
E: No s'han pogut analitzar o obrir les llistes de paquets o fitxer d'estat.
E: _cache->open() failed, please report.

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages)

---

### Post by indytim on 2007-04-28
Start with your sources.lst.  The warning message you posted at the bottom says you've got duplicates in there.  Clean that up and post back the errors.   As usual, backup the file before you start editing it.

IndyTim

---

### Post by hackarre on 2007-04-28
I had an idea, I just ereased everything I had in my sources.list, then I actived universe and multiuniverse and everything worked.

---

### Post by trivix on 2007-05-06
> **hackarre said:**
> I had an idea, I just ereased everything I had in my sources.list, then I actived universe and multiuniverse and everything worked.

Can you post the actual code you used in the terminal?  Thanks.

---

