---
title: "Problems with certificates"
date: 2014-02-14
forum: General Help
---

### Post by jyulliano on 2014-02-14
Hi guys!

For years I solved every problem that I've had with ubuntu with google, forums and IRC, but I found one that I can't pass through. I'm with problems with ca-certificates, every site that I try to access ask me for a confirmation of the certification and my update is not working 100% too. I really apreciate any help.


```
jyulliano@Salamander:~$ sudo rm -rf /etc/ssl/certs/*
[sudo] password for jyulliano: 
jyulliano@Salamander:~$ sudo update-ca-certificates Updating certificates in /etc/ssl/certs... 152 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....done.
jyulliano@Salamander:~$ sudo apt-get update
[...]                                 
Err https://private-ppa.launchpad.net precise/main amd64 Packages              
  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
Err https://private-ppa.launchpad.net precise/main i386 Packages
  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en
Fetched 1,118 kB in 44s (24.9 kB/s)

E: Some index files failed to download. They have been ignored, or old ones used instead.
jyulliano@Salamander:~$ 

```

---

### Post by Bashing-om on 2014-02-14
jyulliano; ungood !

Maybe a 3rd party PPA that you do not have the signing key for ?
Let's look and see what might be:
Post the output - between code tags - of terminal commands:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And will see what tale
[INDENT][INDENT]the sources tell
[/INDENT][/INDENT]

---

