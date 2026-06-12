---
title: "Install Citadel mail-server"
date: 2008-02-26
forum: General Help
---

### Post by ukripper on 2008-02-26
I hope this will help to setup Citadel more easily:

Open terminal 
```
gksudo gedit  /etc/apt/sources.list
```

Add following to you /etc/apt/sources.list :
```
deb http://debian.citadel.org/ubuntu/ gutsy  main
```

save.

And in terminal do :
```
sudo apt-get update
```

And finally :
```
sudo apt-get install citadel-suite
```

when installation is complete  read through getting started guide:

[http://www.citadel.org/doku.php/installation:getting_started](http://www.citadel.org/doku.php/installation:getting_started)


I have recently installed Citadel on my Eeepc on Gutsy kernel.

I am testing this mailserver and will keep this post updated.

---

### Post by farahbod on 2008-03-30
how does it work now?

---

### Post by ukripper on 2008-03-30
> **farahbod said:**
> how does it work now?

this is the easiest mail server to maintain I have ever installed. It is on my production system now and working great.

---

### Post by smilinmonki666 on 2008-03-31
I have a problem with mine.

I'm remote installing & it gave:

"dpkg was interrupted, you must manually run 'dpgk --configure -a' to correct the problem"

Anyone got any ideas?

please help, I can't install anything or update....

---

### Post by ukripper on 2008-03-31
> **smilinmonki666 said:**
> I have a problem with mine.

I'm remote installing & it gave:

"dpkg was interrupted, you must manually run 'dpgk --configure -a' to correct the problem"

Anyone got any ideas?

please help, I can't install anything or update....

As suggested you need to run ```
sudo dpkg --configure -a 
```in terminal to sort the broken package.

---

### Post by jethro10 on 2008-04-20
I also looked at this and found it full of features and easy, a great combination.
However I found an issue with pop collection, it could not do gmail collection because it needed SSL and it seemed citadel pop collector could not do this.

Has anyone tried it and got it working ?

Thanks
Jeff

---

### Post by jethro10 on 2008-04-21
Incase it helps anyone else to get round Citadel not doing ssl pop3,
I installed fetchmail with  apt-get fetchmail

created a .fetchmailrc file with this in it:-

```
poll pop.gmail.com with proto POP3 and options no dns
user 'username@gmail.com' there with password 'password' is citadeluser@localhost here  options ssl
smtphost /var/run/citadel/lmtp.socket
```

then I ran it from a command prompt to test it with :-

fetchmail -vk

then put it in a cron job with this:-
/usr/bin/fetchmail -vk --syslog -f /home/username/.fetchmailrc >>/home/usernname/fetchmailerror.log 2>&1

writes transactions to syslog, errors to my home directory.

Sorted.
Jeff

---

### Post by jamesrfla on 2008-07-07
I did everything up to sudo apt-get update. When I did it I get  Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]. Then I did sudo apt-get install citadel-suite and I get Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  citadel-suite: Depends: citadel-server but it is not going to be installed
                 Depends: citadel-mta but it is not going to be installed
                 Depends: citadel-webcit but it is not going to be installed
E: Broken packages.
I also tried sudo dpkg --configure -a and that didn't help. Any ideas??

---

