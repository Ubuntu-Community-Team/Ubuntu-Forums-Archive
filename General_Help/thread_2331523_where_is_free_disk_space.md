---
title: "where is free disk space?"
date: 2016-07-22
forum: General Help
---

### Post by andrew2016 on 2016-07-22
Hi All 

Couple weeks ago I had a half of my disc free, but I found today that there is no space(see the system info below).  I did not save/create any big files, so it is not clear where the space disappeared.   

My disc is 450G, Home directory is 190G, Root in 252G. However, I do not understand why root is so big. There are no any big folders in it. Except Home, all other folders together are not more than 10G. So, where these 240G are? See two attached images (baobab's result and folders sizes).

  Could you please advise what happened and how to free space.  I am not very advanced linux user (just use it to run my software), please send me simple instructions.  

Thakyou!!! 
Cheers.  

plasmashell 5.6.90 

Qt: 5.5.1 

KDE Frameworks: 5.21.0 

Konsole: 15.12.3  



luda@luda-Vostro-V131:~$ sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort
12K     /home/luda/.local/share/Trash
4.0K    /home/luda/.local/share/Trash/files
4.0K    /home/luda/.local/share/Trash/info

luda@luda-Vostro-V131:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            2.9G     0  2.9G   0% /dev
tmpfs           588M  8.6M  579M   2% /run
**/dev/sda1       453G  423G  7.4G  99% /**
tmpfs           2.9G   92K  2.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.9G     0  2.9G   0% /sys/fs/cgroup
tmpfs           588M   16K  588M   1% /run/user/1000
luda@luda-Vostro-V131:~$  sysinfo:/

---

### Post by Bashing-om on 2016-07-22
andrew2016; Ouch ;

The outputs are not at all what I had expected to see,

How about we get a more detailed look at the 'disk usage' ?
```

cd /

```
and post back - Between code tags - the output of terminal command:
```

sudo du -sx * | sort -n

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We see then what
[INDENT][INDENT]tale gets told
[/INDENT][/INDENT]

---

### Post by andrew2016 on 2016-07-22
Thank you [**[COLOR=#DD4814][B]Bashing-om **[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1111508")
Please find the output below
```

uda@luda-Vostro-V131:~$ cd /
luda@luda-Vostro-V131:/$ sudo du -sx * | sort -n
[sudo] password for luda: 
du: cannot access 'proc/3396/task/3396/fd/4': No such file or directory
du: cannot access 'proc/3396/task/3396/fdinfo/4': No such file or directory
du: cannot access 'proc/3396/fd/4': No such file or directory
du: cannot access 'proc/3396/fdinfo/4': No such file or directory
0       dev
0       initrd.img
0       initrd.img.old
0       proc
0       sys
0       vmlinuz
0       vmlinuz.old
4       cdrom
4       lib64
4       mnt
4       srv
8       media
16      lost+found
56      tmp
8792    run
9872    etc
11036   sbin
12980   bin
29656   opt
102448  boot
615236  lib
731720  var
5810148 usr
185162376       home
249744968       root

```
[**[COLOR=#DD4814][B]**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1111508")[**[COLOR=#DD4814][B]**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1111508")

---

### Post by &amp;KyT$0P# on 2016-07-22
Likewise, can you please post the output of this command?
```
sudo /bin/bash -c 'cd /root; du -sx `ls -A`' | sort -n
```

---

### Post by andrew2016 on 2016-07-22
Hi Halogen2
Here you are
```

luda@luda-Vostro-V131:~$ sudo /bin/bash -c 'cd /root; du -sx `ls -A`' | sort -n
[sudo] password for luda: 
4       .aptitude
4       .bashrc
4       .nano
4       .profile
8       .local
12      .dbus
28      .config
60      .synaptic
10308   .cache
975992  tmpceX5ixLU2NcpB50NJrmadKXvRxIK2MOssACUZsmAM1EFNRG4YG0NkJghG3qykEdZBtVKCrEX386s9Oaz7EUxTaCz9ewHmToYSsgqUu8YtrrGmw5paKeIDFuWCxn0Tqgm.hPBofYdufIuisFW31ZNLu1dNT2iA.mr_iNBplZaEaDiRdah18xwFJJQcNgmMbgZQabAt6MUWvZRWvsSCevHY7xapNU2OBkCR18BKdsY9497oUHIKyehvYAzoLV
1017464 tmpX0W_y7G.SXg3gV_nW-AV0ck9Ssfk1MbXX2I1nV-6Ffd7fh0wbuEFexbV1KaDiEVc-OEsCT3sb3wrkTRnxTotCix9sYRkhlGlxnlga2XpQZXf35-5Pp-VR5Jy3QySsr0P_xGMGQc0P2GnUVnq-Qy_UtkXBW38yE-lM8q2DokZdjW-DcWUaqki0X9ui.IN0CuWA0lAS6FUYxKtrt7gqbRwx2YDioy7Lcw-jEIhrrUCim5HOxhfHRMvHyl3QCn
1030776 tmpViiIhnlqC4hii0BYGzMs_qb..sqK.J8Tesyv4hlSeMsd0VGw-TlN2Krz1wJen0DSYfeIUeQn4HEDmpeIg2Oa2Y4-_pdNAZi8Yn.3mhvw8O-Zni61BpSusbz7SQ.0j8MBRYwtYk_cbvDkiHOaXYROrjEkKO9Kro8fhYzxW5GH9ePmgCjBHaaVn7dXE0QswvDjaj_rgOoMW.Ep.iWWjzApDEE61ddQOjzHIigMZ6ds8em.ZamG4TYbQXDezMG
246710300       tmpo3PFYBLK4DyRW1o0tNIfhN69swFBTRVgHFsSgjmV8K_I0yBVVW-VMsu0-WbIijGXk9-ulKSp8acGglBcexnh_FeTo5UJbrSnskgOfqek7PB0bhAbth5ag5D1geafalNLwySOrevQSE3pZvP6eeQGaIZ9YZy2hATQTygzyYq.2veq8R2dujVJsu9Y9HpVYxsYSSHgfxoC.NA8OmH6ogdSiTbjDbMl3qMGRLQsYoyCKCIVh-ELYBwKcyU6Ih_
luda@luda-Vostro-V131:~$

```

---

### Post by &amp;KyT$0P# on 2016-07-23
:shock:
I have never seen something like it.  Do you know what all you've done as root (authenticated to do) since before you noticed the problem?

Now can you please post the output of
```
sudo ls -la /root/tmp*
```

---

### Post by Bashing-om on 2016-07-23
andrew2016; halogen2; Uh Huh ----

> **halogen2 said:**
> :shock:
I have never seen something like it.  Do you know what all you've done as root (authenticated to do) since before you noticed the problem?

Now can you please post the output of
```
sudo ls -la /root/tmp*
```

ditto !

Also might be good to look at /var and /usr directories, as they too are abnormally large.

My go-to for a looksee:
```

sudo du -ah /var | sort -n -r | head -n 20
sudo du -ah /usr | sort -n -r | head -n 20

```

Find out the why;

[INDENT][INDENT]then delete unwanted files off of the system.

[INDENT][INDENT][INDENT]we can do that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2016-07-23
> **Bashing-om said:**
> Also might be good to look at /var and /usr directories, as they too are abnormally large.
(Hmm.  I don't currently have a free disk space issue, so here's mine for comparison:
```

6220420 /usr
1158840 /var

```
:-k )

---

### Post by Bashing-om on 2016-07-23
guys;

I run a very tight system .. And I have to watch my disk space usage .
For comparison my " sudo du -sx * | sort -nsudo du -sx * | sort -n ":
```

74860   boot
185768  opt
318436  home
458708  var
537856  lib
1000456 usr
sysop@1404mini:/

```
However we do know that andrew2016's major issue is in the /root directory .

cause and effect !

---

### Post by andrew2016 on 2016-07-23
I can't remember doing something special as root. Usually I use linux to run my specific software or browsing internet.
```


luda@luda-Vostro-V131:/$ sudo ls -la /root/tmp*
ls: cannot access '/root/tmp*': No such file or directory


```

---

### Post by andrew2016 on 2016-07-23
The results are

```

luda@luda-Vostro-V131:/$ sudo du -ah /var | sort -n -r | head -n 20
1000K   /var/log/kern.log
980K    /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_i18n_Translation-en
972K    /var/cache/apt/archives/udev_229-4ubuntu7_amd64.deb
964K    /var/cache/apt/archives/console-setup-linux_1.108ubuntu15.2_all.deb
936K    /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_source_Sources
892K    /var/log/syslog
884K    /var/tmp/kdecache-luda/ksycoca4
864K    /var/cache/apt/archives/grub-pc-bin_2.02~beta2-36ubuntu3.1_amd64.deb
848K    /var/cache/apt-xapian-index/index.1/spelling.DB
816K    /var/cache/apt/archives/linux-libc-dev_4.4.0-31.50_amd64.deb
800K    /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_i18n_Translation-en
792K    /var/cache/apt/archives/libmysqlclient20_5.7.13-0ubuntu0.16.04.2_amd64.deb
784K    /var/cache/apt/archives/libgstreamer1.0-0_1.8.2-1~ubuntu1_i386.deb
776K    /var/cache/apt/archives/libmysqlclient20_5.7.13-0ubuntu0.16.04.2_i386.deb
764K    /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_main_binary-amd64_Packages
764K    /var/cache/apt/archives/linux-headers-4.4.0-31-generic_4.4.0-31.50_amd64.deb
752K    /var/log/syslog.1
752K    /var/cache/apt/archives/libgstreamer1.0-0_1.8.2-1~ubuntu1_amd64.deb
740K    /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_main_binary-i386_Packages
728K    /var/cache/app-info/xapian/default/spelling.DB
luda@luda-Vostro-V131:/$ sudo du -ah /usr | sort -n -r | head -n 20
1020K   /usr/share/man/man7
1020K   /usr/share/icons/ubuntu-mono-light/status/16
1020K   /usr/share/icons/ubuntu-mono-dark/status/16
1016K   /usr/share/doc/texlive-doc/latex/ocgx
1016K   /usr/lib/x86_64-linux-gnu/libQtCLucene.so.4.8.7
1016K   /usr/lib/x86_64-linux-gnu/libKF5Libkdepim.so.5.1.3
1016K   /usr/lib/telepathy/telepathy-gabble
1016K   /usr/lib/libreoffice/presets/database/biblio
1012K   /usr/share/yelp/mathjax/jax
1012K   /usr/share/libreoffice/help/en-US/sbasic.jar
1012K   /usr/lib/x86_64-linux-gnu/libliveMedia.so.50.1.8
1008K   /usr/src/linux-headers-4.4.0-31/fs
1008K   /usr/src/linux-headers-4.4.0-28/fs
1008K   /usr/share/libreoffice/share/config/images_breeze.zip
1008K   /usr/share/icons/Humanity/apps/24
1008K   /usr/lib/firefox/libnss3.so
1004K   /usr/share/ksmserver/themes/contour/screenshot.png
1004K   /usr/share/doc/texlive-doc/latex/texshade/texshade.pdf
1004K   /usr/share/doc/texlive-doc/latex/flipbook
1004K   /usr/lib/libreoffice/program/types




```

---

### Post by &amp;KyT$0P# on 2016-07-23
> **andrew2016 said:**
> ```
ls: cannot access '/root/tmp*': No such file or directory

```
Oops, sorry, forgot about that minor detail :oops: See if this works better
```
sudo /bin/bash -c 'ls -la /root/tmp*'
```

---

### Post by andrew2016 on 2016-07-23
Thank you
```

luda@luda-Vostro-V131:/$ sudo /bin/bash -c 'ls -la /root/tmp*'                                                                                                                                
[sudo] password for luda:                                                                                                                                                                     
-rw------- 1 root root    999408750 Jul  8 14:12 /root/tmpceX5ixLU2NcpB50NJrmadKXvRxIK2MOssACUZsmAM1EFNRG4YG0NkJghG3qykEdZBtVKCrEX386s9Oaz7EUxTaCz9ewHmToYSsgqUu8YtrrGmw5paKeIDFuWCxn0Tqgm.hPBofYdufIuisFW31ZNLu1dNT2iA.mr_iNBplZaEaDiRdah18xwFJJQcNgmMbgZQabAt6MUWvZRWvsSCevHY7xapNU2OBkCR18BKdsY9497oUHIKyehvYAzoLV                                                                         
-rw------- 1 root root 252631318528 Apr 25 17:28 /root/tmpo3PFYBLK4DyRW1o0tNIfhN69swFBTRVgHFsSgjmV8K_I0yBVVW-VMsu0-WbIijGXk9-ulKSp8acGglBcexnh_FeTo5UJbrSnskgOfqek7PB0bhAbth5ag5D1geafalNLwySOrevQSE3pZvP6eeQGaIZ9YZy2hATQTygzyYq.2veq8R2dujVJsu9Y9HpVYxsYSSHgfxoC.NA8OmH6ogdSiTbjDbMl3qMGRLQsYoyCKCIVh-ELYBwKcyU6Ih_                                                                         
-rw------- 1 root root   1055506710 Apr 25 16:35 /root/tmpViiIhnlqC4hii0BYGzMs_qb..sqK.J8Tesyv4hlSeMsd0VGw-TlN2Krz1wJen0DSYfeIUeQn4HEDmpeIg2Oa2Y4-_pdNAZi8Yn.3mhvw8O-Zni61BpSusbz7SQ.0j8MBRYwtYk_cbvDkiHOaXYROrjEkKO9Kro8fhYzxW5GH9ePmgCjBHaaVn7dXE0QswvDjaj_rgOoMW.Ep.iWWjzApDEE61ddQOjzHIigMZ6ds8em.ZamG4TYbQXDezMG                                                                         
-rw------- 1 root root   1041875430 Apr 23 12:05 /root/tmpX0W_y7G.SXg3gV_nW-AV0ck9Ssfk1MbXX2I1nV-6Ffd7fh0wbuEFexbV1KaDiEVc-OEsCT3sb3wrkTRnxTotCix9sYRkhlGlxnlga2XpQZXf35-5Pp-VR5Jy3QySsr0P_xGMGQc0P2GnUVnq-Qy_UtkXBW38yE-lM8q2DokZdjW-DcWUaqki0X9ui.IN0CuWA0lAS6FUYxKtrt7gqbRwx2YDioy7Lcw-jEIhrrUCim5HOxhfHRMvHyl3QCn 

```

---

### Post by &amp;KyT$0P# on 2016-07-23
:confused: Looks that each /root/tmp... is a massive single file!
What type(s) of files are they?
```
sudo /bin/bash -c 'file /root/tmp*;file -i /root/tmp*'
```

---

### Post by andrew2016 on 2016-07-23
The output is
```

luda@luda-Vostro-V131:/$ sudo /bin/bash -c 'file /root/tmp*;file -i /root/tmp*'
[sudo] password for luda: 
/root/tmpceX5ixLU2NcpB50NJrmadKXvRxIK2MOssACUZsmAM1EFNRG4YG0NkJghG3qykEdZBtVKCrEX386s9Oaz7EUxTaCz9ewHmToYSsgqUu8YtrrGmw5paKeIDFuWCxn0Tqgm.hPBofYdufIuisFW31ZNLu1dNT2iA.mr_iNBplZaEaDiRdah18xwFJJQcNgmMbgZQabAt6MUWvZRWvsSCevHY7xapNU2OBkCR18BKdsY9497oUHIKyehvYAzoLV: data
/root/tmpo3PFYBLK4DyRW1o0tNIfhN69swFBTRVgHFsSgjmV8K_I0yBVVW-VMsu0-WbIijGXk9-ulKSp8acGglBcexnh_FeTo5UJbrSnskgOfqek7PB0bhAbth5ag5D1geafalNLwySOrevQSE3pZvP6eeQGaIZ9YZy2hATQTygzyYq.2veq8R2dujVJsu9Y9HpVYxsYSSHgfxoC.NA8OmH6ogdSiTbjDbMl3qMGRLQsYoyCKCIVh-ELYBwKcyU6Ih_: data
/root/tmpViiIhnlqC4hii0BYGzMs_qb..sqK.J8Tesyv4hlSeMsd0VGw-TlN2Krz1wJen0DSYfeIUeQn4HEDmpeIg2Oa2Y4-_pdNAZi8Yn.3mhvw8O-Zni61BpSusbz7SQ.0j8MBRYwtYk_cbvDkiHOaXYROrjEkKO9Kro8fhYzxW5GH9ePmgCjBHaaVn7dXE0QswvDjaj_rgOoMW.Ep.iWWjzApDEE61ddQOjzHIigMZ6ds8em.ZamG4TYbQXDezMG: data
/root/tmpX0W_y7G.SXg3gV_nW-AV0ck9Ssfk1MbXX2I1nV-6Ffd7fh0wbuEFexbV1KaDiEVc-OEsCT3sb3wrkTRnxTotCix9sYRkhlGlxnlga2XpQZXf35-5Pp-VR5Jy3QySsr0P_xGMGQc0P2GnUVnq-Qy_UtkXBW38yE-lM8q2DokZdjW-DcWUaqki0X9ui.IN0CuWA0lAS6FUYxKtrt7gqbRwx2YDioy7Lcw-jEIhrrUCim5HOxhfHRMvHyl3QCn: data
/root/tmpceX5ixLU2NcpB50NJrmadKXvRxIK2MOssACUZsmAM1EFNRG4YG0NkJghG3qykEdZBtVKCrEX386s9Oaz7EUxTaCz9ewHmToYSsgqUu8YtrrGmw5paKeIDFuWCxn0Tqgm.hPBofYdufIuisFW31ZNLu1dNT2iA.mr_iNBplZaEaDiRdah18xwFJJQcNgmMbgZQabAt6MUWvZRWvsSCevHY7xapNU2OBkCR18BKdsY9497oUHIKyehvYAzoLV: application/octet-stream; charset=binary
/root/tmpo3PFYBLK4DyRW1o0tNIfhN69swFBTRVgHFsSgjmV8K_I0yBVVW-VMsu0-WbIijGXk9-ulKSp8acGglBcexnh_FeTo5UJbrSnskgOfqek7PB0bhAbth5ag5D1geafalNLwySOrevQSE3pZvP6eeQGaIZ9YZy2hATQTygzyYq.2veq8R2dujVJsu9Y9HpVYxsYSSHgfxoC.NA8OmH6ogdSiTbjDbMl3qMGRLQsYoyCKCIVh-ELYBwKcyU6Ih_: application/octet-stream; charset=binary
/root/tmpViiIhnlqC4hii0BYGzMs_qb..sqK.J8Tesyv4hlSeMsd0VGw-TlN2Krz1wJen0DSYfeIUeQn4HEDmpeIg2Oa2Y4-_pdNAZi8Yn.3mhvw8O-Zni61BpSusbz7SQ.0j8MBRYwtYk_cbvDkiHOaXYROrjEkKO9Kro8fhYzxW5GH9ePmgCjBHaaVn7dXE0QswvDjaj_rgOoMW.Ep.iWWjzApDEE61ddQOjzHIigMZ6ds8em.ZamG4TYbQXDezMG: application/octet-stream; charset=binary
/root/tmpX0W_y7G.SXg3gV_nW-AV0ck9Ssfk1MbXX2I1nV-6Ffd7fh0wbuEFexbV1KaDiEVc-OEsCT3sb3wrkTRnxTotCix9sYRkhlGlxnlga2XpQZXf35-5Pp-VR5Jy3QySsr0P_xGMGQc0P2GnUVnq-Qy_UtkXBW38yE-lM8q2DokZdjW-DcWUaqki0X9ui.IN0CuWA0lAS6FUYxKtrt7gqbRwx2YDioy7Lcw-jEIhrrUCim5HOxhfHRMvHyl3QCn: application/octet-stream; charset=binary
luda@luda-Vostro-V131:/$ 


```

---

### Post by &amp;KyT$0P# on 2016-07-23
That basically means it doesn't know what kind of files they are. :(

Well, 3 of the 4 were last modified more than 2 months ago, but I'd be very hesitant to suggest deleting any of them if we don't know why they're there...

In that ls output, those dates/times (for example, the [FONT=Courier New]Jul  8 14:12[/FONT]) are when each file was last modified.  The fact it's displaying a time, instead of a year, means the files were last modified this year.
Do you remember doing anything as root around the time of any of those files' last modified times?
Are those times consistent with any job you're running as root on your machine (as far as you know)?
What software, if any, did you install most recently before those last modified dates/times? (the history* log files in /var/log/apt/ might be of help answering this)

---

### Post by andrew2016 on 2016-07-23
Thank you. I do not believe that I did something specific as root that time.

The history is
```

l
Start-Date: 2016-07-04  18:14:25
Commandline: apt-get --yes autoremove
Requested-By: luda (1000)
Remove: linux-image-4.4.0-22-generic:amd64 (4.4.0-22.40), linux-image-extra-4.4.0-22-generic:amd64 (4.4.0-22.40), linux-headers-4.4.0-22:amd64 (4.4.0-22.40), linux-headers-4.4.0-22-generic:amd64 (4.4.0-22.40)
End-Date: 2016-07-04  18:14:54

Start-Date: 2016-07-04  18:34:25
Commandline: /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 14680071 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpdxzjhbsp
Requested-By: luda (1000)
Upgrade: libappstream-glib8:amd64 (0.5.13-1, 0.5.13-1ubuntu2)
End-Date: 2016-07-04  18:34:34

Start-Date: 2016-07-04  18:35:53
Install: baobab:amd64 (3.18.1-1ubuntu1)
End-Date: 2016-07-04  18:36:00

Start-Date: 2016-07-04  18:55:17
Commandline: apt-get purge texlive*
Requested-By: luda (1000)
Purge: texlive-font-utils:amd64 (2015.20160320-1), texlive-latex-base:amd64 (2015.20160320-1), texlive-base:amd64 (2015.20160320-1), texlive-generic-recommended:amd64 (2015.20160320-1), texlive-pictures:amd64 (2015.20160320-1), prosper:amd64 (1.00.4+cvs.2007.05.01-4), texlive-pstricks-doc:amd64 (2015.20160320-1), texlive-pstricks:amd64 (2015.20160320-1), texlive-binaries:amd64 (2015.20160222.37495-1), texlive-latex-recommended-doc:amd64 (2015.20160320-1), texlive-pictures-doc:amd64 (2015.20160320-1), texlive-latex-recommended:amd64 (2015.20160320-1), texlive-extra-utils:amd64 (2015.20160320-1), texlive-latex-base-doc:amd64 (2015.20160320-1)
End-Date: 2016-07-04  18:55:45

Start-Date: 2016-07-04  19:08:19
Upgrade: lsb-release:amd64 (9.20160110, 9.20160110ubuntu0.1), lsb-base:amd64 (9.20160110, 9.20160110ubuntu0.1)
End-Date: 2016-07-04  19:08:32

Start-Date: 2016-07-04  19:09:53
Remove: texstudio-l10n:amd64 (2.10.8+debian-1), texstudio:amd64 (2.10.8+debian-1)
End-Date: 2016-07-04  19:09:57

Start-Date: 2016-07-04  19:16:29
Install: texstudio-l10n:amd64 (2.10.8+debian-1, automatic), texlive-font-utils:amd64 (2015.20160320-1, automatic), texlive-latex-base:amd64 (2015.20160320-1, automatic), texlive-base:amd64 (2015.20160320-1, automatic), texlive-generic-recommended:amd64 (2015.20160320-1, automatic), texlive-pictures:amd64 (2015.20160320-1, automatic), prosper:amd64 (1.00.4+cvs.2007.05.01-4, automatic), texstudio:amd64 (2.10.8+debian-1), texlive-pstricks-doc:amd64 (2015.20160320-1, automatic), texlive-pstricks:amd64 (2015.20160320-1, automatic), texlive-binaries:amd64 (2015.20160222.37495-1, automatic), texlive-latex-recommended-doc:amd64 (2015.20160320-1, automatic), texlive-pictures-doc:amd64 (2015.20160320-1, automatic), texlive-latex-recommended:amd64 (2015.20160320-1, automatic), texlive-extra-utils:amd64 (2015.20160320-1, automatic), texlive-latex-base-doc:amd64 (2015.20160320-1, automatic)
End-Date: 2016-07-04  19:17:44

Start-Date: 2016-07-04  19:26:03
Install: texlive-fonts-recommended-doc:amd64 (2015.20160320-1, automatic), texlive-latex-extra-doc:amd64 (2015.20160320-1, automatic), texlive-fonts-recommended:amd64 (2015.20160320-1), texlive-latex-extra:amd64 (2015.20160320-1), preview-latex-style:amd64 (11.88-1.1ubuntu1, automatic), tipa:amd64 (2:1.3-20, automatic), tex-gyre:amd64 (20150923-1, automatic), fonts-texgyre:amd64 (20150923-1, automatic)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2016-07-04  19:27:42

Start-Date: 2016-07-04  19:47:51
Commandline: apt-get dist-upgrade
Requested-By: luda (1000)
End-Date: 2016-07-04  19:47:57

Start-Date: 2016-07-08  12:30:11
Commandline: /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 90177543 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpn_w74g7r
Requested-By: luda (1000)
Upgrade: libservlet3.1-java:amd64 (8.0.32-1ubuntu1, 8.0.32-1ubuntu1.1), python3-software-properties:amd64 (0.96.20.1, 0.96.20.2), libservlet3.0-java:amd64 (7.0.68-1, 7.0.68-1ubuntu0.1), command-not-found-data:amd64 (0.3ubuntu16.04.1, 0.3ubuntu16.04.2), libusbmuxd4:amd64 (1.0.10-2, 1.0.10-2ubuntu0.1), software-properties-kde:amd64 (0.96.20.1, 0.96.20.2), python3-commandnotfound:amd64 (0.3ubuntu16.04.1, 0.3ubuntu16.04.2), libimobiledevice6:amd64 (1.2.0+dfsg-3~ubuntu0.1, 1.2.0+dfsg-3~ubuntu0.2), bash:amd64 (4.3-14ubuntu1, 4.3-14ubuntu1.1), command-not-found:amd64 (0.3ubuntu16.04.1, 0.3ubuntu16.04.2), linux-firmware:amd64 (1.157.1, 1.157.2), ubuntu-mono:amd64 (14.04+16.04.20160415-0ubuntu2, 14.04+16.04.20160621-0ubuntu1), tzdata:amd64 (2016d-0ubuntu0.16.04, 2016f-0ubuntu0.16.04), software-properties-common:amd64 (0.96.20.1, 0.96.20.2)
End-Date: 2016-07-08  12:31:04

Start-Date: 2016-07-08  14:00:17
Commandline: apt-get dist-upgrade
Requested-By: luda (1000)
Upgrade: lsb-release:amd64 (9.20160110ubuntu0.1, 9.20160110ubuntu0.2), lsb-base:amd64 (9.20160110ubuntu0.1, 9.20160110ubuntu0.2)
End-Date: 2016-07-08  14:00:29

Start-Date: 2016-07-20  21:03:11
Commandline: /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 81788935 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmptei15po4
Requested-By: luda (1000)
Install: linux-headers-4.4.0-31-generic:amd64 (4.4.0-31.50, automatic), linux-headers-4.4.0-31:amd64 (4.4.0-31.50, automatic), linux-image-4.4.0-31-generic:amd64 (4.4.0-31.50, automatic), linux-image-extra-4.4.0-31-generic:amd64 (4.4.0-31.50, automatic)
Upgrade: libgstreamer-plugins-base1.0-dev:amd64 (1.8.1-1ubuntu0.1, 1.8.2-1ubuntu0.1), libnm-glib4:amd64 (1.2.0-0ubuntu0.16.04.2, 1.2.0-0ubuntu0.16.04.3), libmpx0:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), libgcc-5-dev:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), linux-headers-generic:amd64 (4.4.0.28.30, 4.4.0.31.33), gir1.2-gtk-3.0:amd64 (3.18.9-1ubuntu3, 3.18.9-1ubuntu3.1), linux-libc-dev:amd64 (4.4.0-28.47, 4.4.0-31.50), libnss3-nssdb:amd64 (2:3.21-1ubuntu4, 2:3.23-0ubuntu0.16.04.1), libgstreamer1.0-dev:amd64 (1.8.1-1~ubuntu1, 1.8.2-1~ubuntu1), update-notifier-common:amd64 (3.168, 3.168.1), libgtk-3-common:amd64 (3.18.9-1ubuntu3, 3.18.9-1ubuntu3.1), grub-common:amd64 (2.02~beta2-36ubuntu3, 2.02~beta2-36ubuntu3.1), linux-image-generic:amd64 (4.4.0.28.30, 4.4.0.31.33), qapt-deb-installer:amd64 (3.0.2-0ubuntu1, 3.0.2-0ubuntu1.1), libgtk-3-0:amd64 (3.18.9-1ubuntu3, 3.18.9-1ubuntu3.1), libgd3:amd64 (2.1.1-4ubuntu0.16.04.1, 2.1.1-4ubuntu0.16.04.2), cpp-5:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), python2.7-minimal:amd64 (2.7.11-7ubuntu1, 2.7.12-1~16.04), binutils:amd64 (2.26-8ubuntu2.1, 2.26.1-1ubuntu1~16.04.1), libarchive13:amd64 (3.1.2-11ubuntu0.16.04.1, 3.1.2-11ubuntu0.16.04.2), libitm1:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), libpython2.7:amd64 (2.7.11-7ubuntu1, 2.7.12-1~16.04), python2.7:amd64 (2.7.11-7ubuntu1, 2.7.12-1~16.04), console-setup-linux:amd64 (1.108ubuntu15, 1.108ubuntu15.2), libpython3.5:amd64 (3.5.1-10, 3.5.2-2~16.01), python3.5:amd64 (3.5.1-10, 3.5.2-2~16.01), libnm-glib-vpn1:amd64 (1.2.0-0ubuntu0.16.04.2, 1.2.0-0ubuntu0.16.04.3), python3.5-minimal:amd64 (3.5.1-10, 3.5.2-2~16.01), grub2-common:amd64 (2.02~beta2-36ubuntu3, 2.02~beta2-36ubuntu3.1), libcilkrts5:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), console-setup:amd64 (1.108ubuntu15, 1.108ubuntu15.2), libgfortran-5-dev:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), flashplugin-installer:amd64 (11.2.202.626ubuntu0.16.04.1, 11.2.202.632ubuntu0.16.04.1), gstreamer1.0-plugins-base:amd64 (1.8.1-1ubuntu0.1, 1.8.2-1ubuntu0.1), gstreamer1.0-plugins-base:i386 (1.8.1-1ubuntu0.1, 1.8.2-1ubuntu0.1), libnm0:amd64 (1.2.0-0ubuntu0.16.04.2, 1.2.0-0ubuntu0.16.04.3), libasan2:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), language-pack-en:amd64 (1:16.04+20160415, 1:16.04+20160627), libquadmath0:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), libklibc:amd64 (2.0.4-8ubuntu1, 2.0.4-8ubuntu1.16.04.1), upower:amd64 (0.99.4-2ubuntu0.2, 0.99.4-2ubuntu0.3), network-manager:amd64 (1.2.0-0ubuntu0.16.04.2, 1.2.0-0ubuntu0.16.04.3), grub-pc:amd64 (2.02~beta2-36ubuntu3, 2.02~beta2-36ubuntu3.1), libqapt3-runtime:amd64 (3.0.2-0ubuntu1, 3.0.2-0ubuntu1.1), gtk2-engines-murrine:amd64 (0.98.2-0ubuntu2, 0.98.2-0ubuntu2.1), libnm-util2:amd64 (1.2.0-0ubuntu0.16.04.2, 1.2.0-0ubuntu0.16.04.3), grub-pc-bin:amd64 (2.02~beta2-36ubuntu3, 2.02~beta2-36ubuntu3.1), gcc-5-base:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), gcc-5-base:i386 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), gstreamer-qapt:amd64 (3.0.2-0ubuntu1, 3.0.2-0ubuntu1.1), libstdc++-5-dev:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), libtsan0:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), libgtk-3-bin:amd64 (3.18.9-1ubuntu3, 3.18.9-1ubuntu3.1), libubsan0:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), g++-5:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), libgfortran3:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), libqapt3:amd64 (3.0.2-0ubuntu1, 3.0.2-0ubuntu1.1), gcc-5:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), gfortran-5:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), libgstreamer-plugins-base1.0-0:amd64 (1.8.1-1ubuntu0.1, 1.8.2-1ubuntu0.1), libgstreamer-plugins-base1.0-0:i386 (1.8.1-1ubuntu0.1, 1.8.2-1ubuntu0.1), gstreamer1.0-x:amd64 (1.8.1-1ubuntu0.1, 1.8.2-1ubuntu0.1), liblsan0:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), libgomp1:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), gir1.2-gst-plugins-base-1.0:amd64 (1.8.1-1ubuntu0.1, 1.8.2-1ubuntu0.1), libpurple-bin:amd64 (1:2.10.12-0ubuntu5, 1:2.10.12-0ubuntu5.1), libupower-glib3:amd64 (0.99.4-
2ubuntu0.2, 0.99.4-2ubuntu0.3), keyboard-configuration:amd64 (1.108ubuntu15, 1.108ubuntu15.2), libpurple0:amd64 (1:2.10.12-0ubuntu5, 1:2.10.12-0ubuntu5.1), language-pack-en-base:amd64 (1:16.04+20160415, 1:16.04+20160627), qapt-batch:amd64 (3.0.2-0ubuntu1, 3.0.2-0ubuntu1.1), libpython2.7-minimal:amd64 (2.7.11-7ubuntu1, 2.7.12-1~16.04), pidgin-data:amd64 (1:2.10.12-0ubuntu5, 1:2.10.12-0ubuntu5.1), libnss3:amd64 (2:3.21-1ubuntu4, 2:3.23-0ubuntu0.16.04.1), gir1.2-gstreamer-1.0:amd64 (1.8.1-1~ubuntu1, 1.8.2-1~ubuntu1), libpython3.5-stdlib:amd64 (3.5.1-10, 3.5.2-2~16.01), libatomic1:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), libcc1-0:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), libpython2.7-stdlib:amd64 (2.7.11-7ubuntu1, 2.7.12-1~16.04), libpython3.5-minimal:amd64 (3.5.1-10, 3.5.2-2~16.01), libstdc++6:amd64 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), libstdc++6:i386 (5.3.1-14ubuntu2.1, 5.4.0-6ubuntu1~16.04.1), klibc-utils:amd64 (2.0.4-8ubuntu1, 2.0.4-8ubuntu1.16.04.1), update-notifier:amd64 (3.168, 3.168.1), libgstreamer1.0-0:amd64 (1.8.1-1~ubuntu1, 1.8.2-1~ubuntu1), libgstreamer1.0-0:i386 (1.8.1-1~ubuntu1, 1.8.2-1~ubuntu1), linux-generic:amd64 (4.4.0.28.30, 4.4.0.31.33), libnspr4:amd64 (2:4.11-1ubuntu1, 2:4.12-0ubuntu0.16.04.1), base-files:amd64 (9.4ubuntu4.1, 9.4ubuntu4.2)
End-Date: 2016-07-20  21:08:53

Start-Date: 2016-07-20  21:14:46
Remove: bleachbit:amd64 (1.10-1)
End-Date: 2016-07-20  21:14:49

Start-Date: 2016-07-23  08:24:22
Commandline: apt-get autoremove
Requested-By: luda (1000)
Remove: python-notify:amd64 (0.1.1-4), linux-image-4.4.0-24-generic:amd64 (4.4.0-24.43), linux-headers-4.4.0-24:amd64 (4.4.0-24.43), linux-image-extra-4.4.0-24-generic:amd64 (4.4.0-24.43), linux-headers-4.4.0-24-generic:amd64 (4.4.0-24.43)
End-Date: 2016-07-23  08:24:48

Start-Date: 2016-07-23  10:28:38
Commandline: /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 37748743 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmp7w1qpsh9
Requested-By: luda (1000)
Upgrade: libmysqlclient-dev:amd64 (5.7.12-0ubuntu1.1, 5.7.13-0ubuntu0.16.04.2), libsystemd0:amd64 (229-4ubuntu6, 229-4ubuntu7), libsystemd0:i386 (229-4ubuntu6, 229-4ubuntu7), gstreamer1.0-plugins-good:amd64 (1.8.1-1ubuntu0.1, 1.8.2-1ubuntu0.1), udev:amd64 (229-4ubuntu6, 229-4ubuntu7), isc-dhcp-common:amd64 (4.3.3-5ubuntu12, 4.3.3-5ubuntu12.1), libgstreamer-plugins-good1.0-0:amd64 (1.8.1-1ubuntu0.1, 1.8.2-1ubuntu0.1), libudev1:amd64 (229-4ubuntu6, 229-4ubuntu7), libudev1:i386 (229-4ubuntu6, 229-4ubuntu7), gstreamer1.0-pulseaudio:amd64 (1.8.1-1ubuntu0.1, 1.8.2-1ubuntu0.1), libudev-dev:amd64 (229-4ubuntu6, 229-4ubuntu7), systemd-sysv:amd64 (229-4ubuntu6, 229-4ubuntu7), libpam-systemd:amd64 (229-4ubuntu6, 229-4ubuntu7), systemd:amd64 (229-4ubuntu6, 229-4ubuntu7), mysql-common:amd64 (5.7.12-0ubuntu1.1, 5.7.13-0ubuntu0.16.04.2), libmysqlclient20:amd64 (5.7.12-0ubuntu1.1, 5.7.13-0ubuntu0.16.04.2), libmysqlclient20:i386 (5.7.12-0ubuntu1.1, 5.7.13-0ubuntu0.16.04.2), isc-dhcp-client:amd64 (4.3.3-5ubuntu12, 4.3.3-5ubuntu12.1)
End-Date: 2016-07-23  10:29:48
 


```

---

### Post by &amp;KyT$0P# on 2016-07-23
Thanks but that log is too recent, do you have a history.log*.gz file with information from on and before 23 April 2016?

Also, do you have an external disk that's formatted as ext4 (or other comparable file system) that has enough free space to hold those files?

---

### Post by andrew2016 on 2016-07-24
I have checked there are no files history.log*.gz 
Yes, I have an external disk with sufficient free space

---

### Post by &amp;KyT$0P# on 2016-07-24
OK then let's just see what happens if you move those files to the external disk?  Will need to be done as root, so:

1) Plug in the external disk, make sure it's mounted (if you don't know what that means, just make sure you can open it in your file manager)
2) Open the destination folder on the external disk in a Terminal
3) Run this command to actually move all these files
```
sudo /bin/bash -c "mv -v /root/tmp* $(pwd)"
```

Please note that even if this works, this is just a "band-aid", **not a solution.**  The solution requires figuring out what is/was creating those files, and making sure it doesn't do it again, or at least doesn't go out of control again.  You can run this command to check your /root folder for the presence of any tmp* files
```
sudo ls -la /root
```
Do this often enough and you will catch it fast enough that you'll have all the system logs from around the time the tmp* file was modified - and if you're really lucky, you might even get the chance to see all running processes while a tmp* file is being written to.

Sorry but I don't know how to use logs to check what *was* running as root at a previous time (this thing seems very unlikely to be related to anything initiated by you).

---

### Post by andrew2016 on 2016-07-24
Thank you. However, as I wrote I am not too advanced  in linux". My external drive is "Andriy Seagate Drive" the directory to move files is "linux"

 After multiple attempts the best result I got is

```

luda@luda-Vostro-V131:/media/luda/Andriy Seagate Drive/linux$ sudo /bin/bash -c "mv -v /root/tmp* $"Andriy Seagate Drive/linux""                                                                
mv: target '/root/tmpX0W_y7G.SXg3gV_nW-AV0ck9Ssfk1MbXX2I1nV-6Ffd7fh0wbuEFexbV1KaDiEVc-OEsCT3sb3wrkTRnxTotCix9sYRkhlGlxnlga2XpQZXf35-5Pp-VR5Jy3QySsr0P_xGMGQc0P2GnUVnq-Qy_UtkXBW38yE-lM8q2DokZdjW-DcWUaqki0X9ui.IN0CuWA0lAS6FUYxKtrt7gqbRwx2YDioy7Lcw-jEIhrrUCim5HOxhfHRMvHyl3QCn' is not a directory 

```

---

### Post by &amp;KyT$0P# on 2016-07-24
The command was meant to be pasted as-is into a Terminal opened in 'Andriy Seagate Drive/linux' (which is probably buried somewhere in /media).

EDIT
Oops, missed the full path directory in your post.  Because of the spaces, you'll need to add single-quotes around the $(pwd)
```
sudo /bin/bash -c "mv -v /root/tmp* '$(pwd)'"
```

or just run this, then you don't have to bother about which directory the Terminal is in
```
sudo /bin/bash -c "mv -v /root/tmp* '/media/luda/Andriy Seagate Drive/linux'"
```

---

### Post by Keith_Helms on 2016-07-24
What goes in a /root directory?

---

### Post by &amp;KyT$0P# on 2016-07-24
> **Keith_Helms said:**
> What goes in a /root directory?
Well, /root is the root user's home directory (equivalent of your user account's /home/user directory).

Going by my 16.04 system, typically the only things in /root are:
 - any preferences saved for applications run by the root user.  E.g. gtk/qt theming, Synaptic settings, and the like
 - a .bashrc and .profile (and .bash_history etc if we ever used a shell as root)
 - root's dconf/gconf settings
 - root dbus session
 - anything else we manually put there

Everything in andrew2016's /root directory, except for those tmp* files, is consistent with the typical stuff you'd find in /root.  You can check what's in yours:
```
sudo ls -la /root
```

---

### Post by andrew2016 on 2016-07-25
Dear [**[COLOR=#000000]halogen2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2034672")
Thank you very much!!! 
It worked! tmps removed to the external drive. 
Hope there are no hidden problems, but  I will keep them for a week.
Thank you for your time.
Andrew

---

### Post by &amp;KyT$0P# on 2016-07-25
> It worked! tmps removed to the external drive.
Hope there are no hidden problems
Great!  Now just need to watch for such files popping up again.

>  I will keep them for a week.
Given the time separation of those files' last modified dates, I'd recommend keeping them for slightly more than 2 months.

> Thank you for your time.
You're welcome!  :KS

---

### Post by Bashing-om on 2016-07-25
@halogen2; :)

Well done . I did keep an eye on this .

@halogen2; Hey;

As this matter is now concluded, pending another occurrence ;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

If it pops up again, open a new thread and we prosecute what is generating those files .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2016-07-25
> **Bashing-om said:**
> @halogen2; :)

Well done . I did keep an eye on this .
Thank you Bashing-om.  It's really nice to know when I'm trying to help people, that I'm contributing the quality of help they deserve. 8-)

---

### Post by andrew2016 on 2016-08-01
Hi [**[COLOR=#000000]halogen2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2034672") and Bashing-om
I believe I identified the program creating tmp files. It seems is Bleachbit ([https://www.bleachbit.org/](https://www.bleachbit.org/)). I checked for tmp files before and after running it. They appeared after cleaning the PC using Bleachbit (not each time, but today between two "sudo /bin/bash -c 'file /root/tmp*;file -i /root/tmp*'" was only Bleachbit execution and no other commands). 
Would be glad to know your opinion/recommendations.
Regards,
Andrew

---

### Post by Bashing-om on 2016-08-01
andrew2016; Sorry (not);

I have never used bleachbit, so have no direct opinion. I have progressed to hands on maintenance and have no use for any GUI utility for administering the system.

[INDENT][INDENT]it is all a process
[INDENT][INDENT][INDENT]in learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2016-08-01
@andrew2016: Nice work finding that! 8-)

My recommendation is to uninstall Bleachbit.  In my experience, a Linux system will generally take care of itself and such cleaning programs are potentially dangerous.

If something isn't cleaning up after itself, it will usually leave its mess in a user's home directory.  No big deal though, because you've already seen in this thread how to deal with it - quit the program in question, backup the "stray" files, double-check that things are still working, then (if so) delete the stray files.

---

### Post by QDR06VV9 on 2016-08-01
Bleachbit is an excellent tool...but one dose have a learning curve to using it...it can be your best friend or your worst enemy!
I use it as much as twice daily or as little as once monthly...
Here is a basic guide to using it: [http://www.howtogeek.com/116971/7-tips-to-get-the-most-out-of-bleachbit-a-ccleaner-for-linux/](http://www.howtogeek.com/116971/7-tips-to-get-the-most-out-of-bleachbit-a-ccleaner-for-linux/)

---

### Post by uRock on 2016-08-01
It is very odd to see that activity from Bleachbit. I use it at least twice a week. I get "4506264	usr" most of the sizable data is in the "lib" and "share" folders.

```
urock@5FDP:/usr$ sudo du -sx * | sort -n
20	locale
480	local
6728	lib32
13760	games
19016	sbin
23516	include
130704	src
183516	bin
1738812	share
2389708	lib

```
Did you run Bleachbit as root and user? I usually do both. Clears 300MB to 2GB every time. Mostly from Apt, Firefox, and Chrome.

---

