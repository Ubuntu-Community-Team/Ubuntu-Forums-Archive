---
title: "Openssl problem ?!"
date: 2018-11-29
forum: General Help
---

### Post by fairbird on 2018-11-29
I'm using ubuntu 18.10 64bit
and I have problem with openssl ,,
I have try to re install by following this command
```
sudo apt-get purge --auto-remove openssl
```
And remove it a lot of packages software such as chrome and software update ...etc
then I have try with this command
```
sudo apt-get install openssl
```
but doesn't work correctly every time after restart ubuntu I have got this error
```
raed@fairbird:~$ openssl version
openssl: /usr/local/lib/libssl.so.1.1: version `OPENSSL_1_1_1' not found (required by openssl)
openssl: /usr/local/lib/libcrypto.so.1.1: version `OPENSSL_1_1_1' not found (required by openssl)
```
and after give this command I can get version of openssl
```
raed@fairbird:~$ export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu
raed@fairbird:~$ openssl version
OpenSSL 1.1.1  11 Sep 2018

```
But same story after restart ubuntu same error
```
raed@fairbird:~$ openssl version
openssl: /usr/local/lib/libssl.so.1.1: version `OPENSSL_1_1_1' not found (required by openssl)
openssl: /usr/local/lib/libcrypto.so.1.1: version `OPENSSL_1_1_1' not found (required by openssl)
```

How to fix it ?!
And how to know which packages remove it by that command ?! to reinstall again ?!
```
sudo apt-get purge --auto-remove openssl
```

And sudo apt upgrade did not solve it
```
raed@fairbird:~$ sudo apt update && sudo apt upgrade
Get:1 http://security.ubuntu.com/ubuntu cosmic-security InRelease [83.2 kB]
Hit:2 http://ppa.launchpad.net/linuxuprising/shutter/ubuntu cosmic InRelease
Hit:3 http://bh.archive.ubuntu.com/ubuntu cosmic InRelease                 
Get:4 http://bh.archive.ubuntu.com/ubuntu cosmic-updates InRelease [83.2 kB]        
Hit:5 http://bh.archive.ubuntu.com/ubuntu cosmic-backports InRelease                           
Fetched 166 kB in 5s (30.4 kB/s)                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Thank you

---

### Post by HermanAB on 2018-11-29
Well, you are trying to unscramble and rescramble an egg...

At this point you will likely need to do a full install to get a complete working system again.

---

### Post by fairbird on 2018-11-29
So no way to fix it by terminal ?
```
raed@fairbird:~$ openssl version
openssl: /usr/local/lib/libssl.so.1.1: version `OPENSSL_1_1_1' not found (required by openssl)
openssl: /usr/local/lib/libcrypto.so.1.1: version `OPENSSL_1_1_1' not found (required by openssl)
raed@fairbird:~$ which openssl
/usr/bin/openssl
```

---

### Post by fairbird on 2018-11-29
Ok ..
I have solve it by this commands
```

sudo cp -f /usr/lib/x86_64-linux-gnu/libcrypto.so.1.1 /usr/local/lib/
sudo cp -f /usr/lib/x86_64-linux-gnu/libssl.so.1.1 /usr/local/lib/
sudo ln -sfn /usr/lib/x86_64-linux-gnu/libcrypto.a /usr/local/lib/
sudo ln -sfn /usr/lib/x86_64-linux-gnu/libssl.a /usr/local/lib/
sudo ln -sfn /usr/lib/x86_64-linux-gnu/libssl.so.1.1 /usr/local/lib/

```

---

### Post by slesh93 on 2019-09-29
[**[COLOR=#000000]@fairbird[/COLOR]**]("https://ubuntuforums.org/member.php?u=1027141"), I don't knwo what exactly your scripts did but it worked for me too. Thanks a lot. Could you please share more details about this solution? I'd be appriated. Thanks in advance!

---

