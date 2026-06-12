---
title: "need some help with LetsEncrypt certificate"
date: 2016-08-30
forum: General Help
---

### Post by redking3 on 2016-08-30
I am trying to figure out how to get a real certificate working for my owncloud server as it seems I cannot use the mobile apps with the self-signed certificates. This is not my first try getting a real certificate working for my domain, but there is something I cant seem to understand.


Below I have tried to explain exactly what I did in my last try I hopes that someone will read it and see what I am doing wrong. If there is things in the text that is not relevant, it is simply because I dont know whats relevant here.

Any help I get I will be very great-full for!


This is what I have done on this try:


The VM running owncloud is "ubuntu server 16.04 LTS" and the owncloud install is installed via repos


The domain I own will in this text be "example.com". since I am behind NAT, I have setup a no-ip iddress that I use as the ip for example.com. and I made a www-Forwarder from cloud.example.com to [https://example.com/owncloud](https://example.com/owncloud) 


I also forwarded ports 80, 443 and 8080 to the ip of the Owncloud VM. cant really remember why I opened the 8080 port tbh.


I can access my owncloud outside my network on both [http://example.com/owncloud](http://example.com/owncloud) and [https://example.com/owncloud](https://example.com/owncloud) ( I followed a guide for selfsigned cert when setting upp owncloud)


In the VM running owncloud I set the hostname to "cloud.example.com" (I am very unsure what effekt the local hostname has on the setup of certificates, so I tried to keep the same domain just incase it wouldnt work if I chose something else).


after this I did the steps bellow to try and follow this guide: [https://manandkeyboard.tk/2015/12/20/lets-encrypt-certificate-steps-for-owncloud/](https://manandkeyboard.tk/2015/12/20/lets-encrypt-certificate-steps-for-owncloud/)


Make a directory of your server
    1. cd /var/www/html
    2. mkdir .well-known 
    3. cd .well-known
    4. mkdir acme-challenge


Update your .htaccess file
    5. cd /var/www/owncloud
    6. cd /var/www/owncloud
    7. sudo nano .htaccess
In the <IfModule mod_rewrite.c> section, add:   (I added the text bellow at the bottom of the <IfModule mod_rewrite.c> section)
```
    RewriteRule ^\.well-known/acme-challenge letsEncrypt.php
    RewriteCond %{HTTPS} off
    RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}
```
Copy the Let’s Encrypt code onto your computer using the instructions from “Installing Let’s Encrypt”
    9. cd /tmp
    10. git clone [https://github.com/letsencrypt/letsencrypt](https://github.com/letsencrypt/letsencrypt)
    11. cd letsencrypt
Run Let’s encrypt from this directory    
    12. ./letsencrypt-auto certonly -a manual --email "the mail I registered my domain on here" -d example.com -d [http://cloud.example.com](http://cloud.example.com)
    
This is where it fails. Giving me this "error code 1":
```
rupert@cloud:/tmp/letsencrypt$ ./letsencrypt-auto certonly -a manual --email rupert@example.com -d example.com.no -d http://cloud.example.com
Bootstrapping dependencies for Debian-based OSes...
Hit:1 http://no.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://no.archive.ubuntu.com/ubuntu xenial-updates InRelease                   
Hit:3 http://no.archive.ubuntu.com/ubuntu xenial-backports InRelease    
Ign:4 http://download.owncloud.org/download/repositories/stable/Ubuntu_16.04  InRelease
Hit:5 http://download.owncloud.org/download/repositories/stable/Ubuntu_16.04  Release
Get:7 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Fetched 94.5 kB in 5s (17.8 kB/s)                              
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
augeas-lenses is already the newest version (1.4.0-0ubuntu1).
ca-certificates is already the newest version (20160104ubuntu1).
gcc is already the newest version (4:5.3.1-1ubuntu1).
libaugeas0 is already the newest version (1.4.0-0ubuntu1).
libffi-dev is already the newest version (3.2.1-4).
python is already the newest version (2.7.11-1).
python-dev is already the newest version (2.7.11-1).
dialog is already the newest version (1.3-20160209-1).
python-virtualenv is already the newest version (15.0.1+ds-3).
virtualenv is already the newest version (15.0.1+ds-3).
libssl-dev is already the newest version (1.0.2g-1ubuntu4.2).
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-image-4.4.0-31-generic linux-image-extra-4.4.0-31-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Creating virtual environment...
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/virtualenv.py", line 2363, in <module>
    main()
  File "/usr/lib/python3/dist-packages/virtualenv.py", line 719, in main
    symlink=options.symlink)
  File "/usr/lib/python3/dist-packages/virtualenv.py", line 988, in create_environment
    download=download,
  File "/usr/lib/python3/dist-packages/virtualenv.py", line 918, in install_wheel
    call_subprocess(cmd, show_stdout=False, extra_env=env, stdin=SCRIPT)
  File "/usr/lib/python3/dist-packages/virtualenv.py", line 812, in call_subprocess
    % (cmd_desc, proc.returncode))
OSError: Command /home/rupert/.local/...ncrypt/bin/python2.7 - setuptools pkg_resources pip wheel failed with error code 1
```

---

### Post by darkeale on 2016-09-01
Hi,

Have you tried running the command (./letsencrypt-auto certonly -a manual --email [email]rupert@example.com[/email] -d example.com.no -d [http://cloud.example.com](http://cloud.example.com)) using sudo?

---

