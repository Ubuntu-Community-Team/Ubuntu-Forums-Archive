---
title: "apt-get update -- can I list the packages differently?"
date: 2008-04-21
forum: General Help
---

### Post by Asham on 2008-04-21
Hi folks,

I was wondering if there is some way to customize the output of the package list when apt-get update is invoked?

Instead of the current output, which I find a little difficult to read: 
```
adam@kubuntu-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  bluez-audio bluez-cups bluez-utils dictionaries-common gdebi-core gdebi-kde kdesudo python2.5 python2.5-dev python2.5-minimal
  system-config-printer-common ubuntu-minimal ubuntu-standard
13 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7061kB of archives.
After this operation, 69.6kB of additional disk space will be used.
Do you want to continue [Y/n]?

```

I'd like to have the package list formatted such as:
```
adam@kubuntu-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  bluez-audio
  bluez-cups
  bluez-utils
  dictionaries-common
  gdebi-core
  gdebi-kde
  kdesudo 
  python2.5 
  python2.5-dev
  python2.5-minimal
  system-config-printer-common
  ubuntu-minimal
  ubuntu-standard
13 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7061kB of archives.
After this operation, 69.6kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

Is it possible to change this in a not-so complicated manner? Keep in mind that I am still learning. ;-)  ):P

---

### Post by Vermind on 2008-04-21
Hello,
This is a little bit of awk that does something to that effect:
```
apt-get install -s xmms2 | awk '{ if ($0 ~ "  .*" ) { for (i=1; i<=NF; i++) print "  "$i; } else { print $0; }}'
``` The problem with this is that it doesn't show You the [Y/n] question, so You have to know that apt-get is asking it.

To make apt-get look like this always, You can make a file named apt-get-something-else.sh with the contents:
```
#!/bin/bash
apt-get $* | awk '{ if ($0 ~ "  .*" ) { for (i=1; i<=NF; i++) print "  "$i; } else { print $0; }}'
```

And then make it executable, and run with for example ```
./apt-get-something-else.sh install -s xmms2 
``` to show what it would do if You wanted to install xmms2.

---

### Post by Asham on 2008-04-21
Didn't think it'd be doable, so many thanks for proving me wrong! :D
[SIZE="1"](Haven't tried it yet though. ;))[/SIZE]

---

