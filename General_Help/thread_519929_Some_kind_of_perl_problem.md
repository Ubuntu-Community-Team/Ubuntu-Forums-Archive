---
title: "Some kind of perl problem"
date: 2007-08-07
forum: General Help
---

### Post by TorchlightJay on 2007-08-07
So I am trying to do apt-get upgrade and this is the error message I get

eading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
17 not fully installed or removed.
Need to get 0B/9263kB of archives.
After unpacking 77.8kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
(Reading database ... 43703 files and directories currently installed.)
Preparing to replace firefox 2.0.0.4+1-0ubuntu1 (using .../firefox_2.0.0.6+1-0ubuntu1_i386.deb) ...
Unpacking replacement firefox ...
Can't locate File/Glob.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate File/Glob.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: error processing /var/cache/apt/archives/firefox_2.0.0.6+1-0ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
Can't locate File/Glob.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_2.0.0.6+1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Now I have tried to do -f install and -f remvoe, I've tried unistnalling firefox. It even gives me problems when I tried to install webmin from source so I think it's a perl problem. Any ideas how to fix this? Also, what generally causes this to happen so I can prevent it in the future. It literally seemed to appear out of nowhere. Thanks for your help

---

### Post by milosz.galazka on 2007-08-07
Command below

aptitude show perl

shows "State: installed"?


Maybe

aptitude reinstall perl

will help.

---

### Post by 67GTA on 2007-08-11
Some recent updates with Kubuntu Gutsy has caused the exact same error message. I can't install or remove anything. Every app is only halfway installed. It has me stumped.

---

