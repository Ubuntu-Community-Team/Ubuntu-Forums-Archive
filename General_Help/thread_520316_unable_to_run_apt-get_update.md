---
title: "unable to run apt-get update"
date: 2007-08-08
forum: General Help
---

### Post by varun_shrivastava on 2007-08-08
hi

sudo apt-get update displays this info

```
Err http://in.archive.ubuntu.com feisty Release.gpg                                                                   
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err http://in.archive.ubuntu.com feisty/main Translation-en_IN                                                        
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err http://in.archive.ubuntu.com feisty/restricted Translation-en_IN            
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err http://in.archive.ubuntu.com feisty/universe Translation-en_IN              
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err http://in.archive.ubuntu.com feisty/multiverse Translation-en_IN            
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err http://in.archive.ubuntu.com feisty-updates Release.gpg                     
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err http://in.archive.ubuntu.com feisty-updates/main Translation-en_IN          
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err http://in.archive.ubuntu.com feisty-updates/restricted Translation-en_IN    
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err http://security.ubuntu.com feisty-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/main Translation-en_IN           
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/restricted Translation-en_IN
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/universe Translation-en_IN
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/multiverse Translation-en_IN
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err http://archive.ubuntustudio.org feisty Release.gpg
  Could not connect to archive.ubuntustudio.org:80 (208.97.169.99). - connect (111 Connection refused)
Err http://archive.ubuntustudio.org feisty/main Translation-en_IN
  Could not connect to archive.ubuntustudio.org:80 (208.97.169.99). - connect (111 Connection refused)
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_IN.bz2  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_IN.bz2  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_IN.bz2  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_IN.bz2  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_IN.bz2  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_IN.bz2  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_IN.bz2  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_IN.bz2  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_IN.bz2  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_IN.bz2  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg  Could not connect to archive.ubuntustudio.org:80 (208.97.169.99). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_IN.bz2  Could not connect to archive.ubuntustudio.org:80 (208.97.169.99). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

but when i do ping in.archive.ubuntu.com it displays

```
 ping in.archive.ubuntu.com
PING in.archive.ubuntu.com (91.189.89.8) 56(84) bytes of data.
64 bytes from prat.canonical.com (91.189.89.8): icmp_seq=1 ttl=46 time=331 ms
64 bytes from prat.canonical.com (91.189.89.8): icmp_seq=2 ttl=46 time=334 ms
64 bytes from prat.canonical.com (91.189.89.8): icmp_seq=3 ttl=46 time=399 ms
64 bytes from prat.canonical.com (91.189.89.8): icmp_seq=4 ttl=46 time=332 ms
64 bytes from prat.canonical.com (91.189.89.8): icmp_seq=5 ttl=46 time=335 ms
64 bytes from prat.canonical.com (91.189.89.8): icmp_seq=6 ttl=46 time=365 ms
64 bytes from prat.canonical.com (91.189.89.8): icmp_seq=7 ttl=46 time=339 ms

--- in.archive.ubuntu.com ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6253ms
rtt min/avg/max/mdev = 331.508/348.404/399.781/23.548 ms

```


Actually a proxy server has been installed and all internet activity is done through that server
but in that case  "ping"  should also not work.

 my sources.list looks like

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```


kindly help
varun

---

### Post by AlexenderReez on 2007-08-08
this sure weird problem....what's about your browser.?can you access to internet?and....can you update using synaptic.....how about change to other mirror instead using that sources ?

---

### Post by anubhavrocks on 2007-08-08
How about using synaptic with your proxy settings.

---

### Post by varun_shrivastava on 2007-08-08
i m able to do with synaptic manager but not from command prompt

---

### Post by anubhavrocks on 2007-08-08
okay,then please set the env variable for proxy address,that should solve your problem

---

### Post by upthelum on 2007-08-08
I'm not 100% sure about this but you could try uncommenting these two lines:

# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

---

