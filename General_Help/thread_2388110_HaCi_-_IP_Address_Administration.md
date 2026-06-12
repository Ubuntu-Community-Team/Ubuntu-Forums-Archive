---
title: "HaCi - IP Address Administration"
date: 2018-03-28
forum: General Help
---

### Post by edunnington on 2018-03-28
Hello,

I am attempting to install HaCi onto my ubuntu server and appear to be having issues. I followed the install guide from [http://haci.larsux.de/wiki/HaCiInstall](http://haci.larsux.de/wiki/HaCiInstall) but it does not help. I am wondering if anyone here knows of or can guide me through setting this up. I have created the MYSQL database and installed apache2. Downloaded the HaCi package moved it to the proper directory and when i enter the command ```
sudo a2ensite haci.conf
``` it tells me bascially to reload apache, when i do it i get an error which after looking at the logs says that there is an error in my .conf file on line 9. i checked line 9 ```
SetHandler    perl-script
``` i verified that perl is installed but do not know where to go from here.

Any help would be appreciated.

---

### Post by SeijiSensei on 2018-03-28
Try adding the Perl module to Apache and see if that helps.

```
sudo apt install libapache2-mod-perl2
```

Restart Apache.  

I don't know if this will help or not since I haven't ever looked at this software before.  More details here: [https://perl.apache.org/docs/2.0/user/config/config.html](https://perl.apache.org/docs/2.0/user/config/config.html)

---

### Post by edunnington on 2018-03-28
Hello,

Yes i just did that. But now i am having an issue with startup.pl

It is saying that it needs that file, i check the directory and its not there. I have no clue where to get this file from either. Any ideas?

EDIT:

i have found it from another install i downloaded, copied the file contents over to the server but still getting a failed message in the apache error log:

```

[Wed Mar 28 12:45:50.884847 2018] [perl:error] [pid 22692:tid 140511166998400] Can't locate Apache/DBI.pm in @INC (you may need to install the Apache::DBI module) (@INC contains: /var/www/haci.pscu.local/modules /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.22.1 /usr/local/share/perl/5.22.1 /usr/lib/x86_64-linux-gnu/perl5/5.22 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.22 /usr/share/perl/5.22 /usr/local/lib/site_perl . /etc/apache2) at /var/www/haci.pscu.local/etc/startup.pl line 8.\nBEGIN failed--compilation aborted at /var/www/haci.pscu.local/etc/startup.pl line 8.\nCompilation failed in require at (eval 2) line 1.\n
[Wed Mar 28 12:45:50.884991 2018] [perl:error] [pid 22692:tid 140511166998400] Can't load Perl file: /var/www/haci.pscu.local/etc/startup.pl for server haci.pscu.local:0, exiting...

```

---

### Post by SeijiSensei on 2018-03-30
If you have things in /usr/local then you must have installed software by a method other than from the repositories.  

Perhaps that script you dug up references an older installation where perl was installed manually to /usr/local?  If so, try changing the paths in the script to use the version from the repositories.  On my system running Kubuntu 18.04 perl lives in /usr/share/perl.

---

