---
title: "Error http://archive.ubuntu.com/ubuntu/dists/jammy/InRelease: Key is stored in legacy"
date: 2024-01-28
forum: General Help
---

### Post by tellapu on 2024-01-28
For some time I get following error when I try to update the system [Ubuntu 22.04, upgraded from 20.04 two years ago]:
```
W: http://archive.ubuntu.com/ubuntu/dists/jammy/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details
```

It may have started when I tried to clean up the PPA list including Authentication keys in Software & Updates.

I applied the tips from this AskUbuntu question ([https://askubuntu.com/a/1409732/30631](https://askubuntu.com/a/1409732/30631)) and the discussion [https://chat.stackexchange.com/rooms/149607/discussion-between-heynnema-and-filbuntu](https://chat.stackexchange.com/rooms/149607/discussion-between-heynnema-and-filbuntu). But it did not solve the problem.

---

### Post by btindie on 2024-01-30
Depending on what you've already done, it may be the case that you've got multiple keys in /etc/apt/trusted.gpg.d that are the same and would need cleaning up.

The below will give you a rough idea if you've got any duplicate keys. It'll only work if they're in the same format.
```
cd /etc/apt/trusted.gpg.d
md5sum * | grep -F -f <(md5sum * | awk '{print $1}' | sort | uniq -c | grep -v '\b1\b' | awk '{print $2}')
```

What is the output of
```
sudo apt-key --keyring /etc/apt/trusted.gpg list
```
I suspect you need to delete any keys that are still in there.

Disable any custom repositories you have in /etc/apt/sources.list.d/ by renaming the files.

Run ```
sudo apt update
``` and it should complete without a error.

Then re-enable a custom repository one at a time. Check the file for a line that includes the *signed-by=* block as that's specifying an explicit key to use. If it's using one of them then it should be fine.

Run ```
sudo apt update
``` again. It may complain about a missing key if it had originally been stored in the file /etc/apt/trusted.gpg

If that's the case, you'll need to get the key again following the guide for [man apt-key]("https://manpages.ubuntu.com/manpages/jammy/man8/apt-key.8.html#deprecation") in terms of where / how to store it.

Rinse and repeat for each custom repository you have.

---

### Post by tellapu on 2024-01-31
Hi btindie

**Thanks a lot for your answer and guidance!**

Following are the outputs of the different commands.

A minor correction: **cd** is probably needed for the first command ```
cd /etc/apt/trusted.gpg.d
```

```
$ cd /etc/apt/trusted.gpg.d
$ md5sum * | grep -F -f <(md5sum * | awk '{print $1}' | sort | uniq -c | grep -v '\b1\b' | awk '{print $2}')
d41d8cd98f00b204e9800998ecf8427e  flatpak-ubuntu-stable.gpg~
d41d8cd98f00b204e9800998ecf8427e  gerardpuig-ubuntu-ppa.gpg~
d41d8cd98f00b204e9800998ecf8427e  kdenlive-ubuntu-kdenlive-stable.gpg~
76cef3f1e93a78af2ad3a870b21665f5  mozillateam-ubuntu-ppa.gpg
76cef3f1e93a78af2ad3a870b21665f5  mozillateam-ubuntu-ppa.gpg~
5bf101fe585dbf6ef2d1ff53132a8ea8  openshot_developers-ubuntu-ppa.gpg
5bf101fe585dbf6ef2d1ff53132a8ea8  openshot_developers-ubuntu-ppa.gpg~
c8a95bb9ebecd5d6b174fff4315026fe  strukturag_ubuntu_libde265.gpg~
c8a95bb9ebecd5d6b174fff4315026fe  strukturag_ubuntu_libheif.gpg~
d41d8cd98f00b204e9800998ecf8427e  touchegg-ubuntu-stable.gpg~
78e1975c64db2f4e09efa2e3abbb5a78  vivaldi-33EAAB8E.gpg
78e1975c64db2f4e09efa2e3abbb5a78  vivaldi-33EAAB8E.gpg~
fece3f2fc18543a29c1513edbba4c92e  vivaldi-4218647E.gpg
fece3f2fc18543a29c1513edbba4c92e  vivaldi-4218647E.gpg~
feebefe6a45409be4db76b3832d165cb  webupd8team-ubuntu-y-ppa-manager.gpg
feebefe6a45409be4db76b3832d165cb  webupd8team-ubuntu-y-ppa-manager.gpg~
```


```
$sudo apt-key --keyring /etc/apt/trusted.gpg list

Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
/etc/apt/trusted.gpg
--------------------
pub   rsa4096 2017-04-05 [SC]
      ABBA 007D 6E14 E2DB 5B28  3C45 D599 C1AA 1267 62B1
uid           [ unknown] Wire Releases Signing Key <releases@wire.com>
sub   rsa4096 2017-04-05 [E]

pub   rsa2048 2010-02-11 [SC]
      1C61 A265 6FB5 7B7E 4DE0  F4C1 FC91 8B33 5044 912E
uid           [ unknown] Dropbox Automatic Signing Key <linux@dropbox.com>

pub   rsa4096 2018-09-17 [SC]
      F6EC B376 2474 EDA9 D21B  7022 8719 20D1 991B C93C
uid           [ unknown] Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com>

pub   rsa4096 2019-09-12 [SC] [expired: 2021-09-11]
      68E9 B2B0 3661 EE3C 44F7  0750 4B8E C3BA ABDC 4346
uid           [ expired] Opera Software Archive Automatic Signing Key 2019 <packager@opera.com>

pub   rsa4096 2017-04-11 [SC] [expired: 2019-09-28]
      D4CC 8597 4C31 396B 18B3  6837 D615 560B A5C7 FF72
uid           [ expired] Opera Software Archive Automatic Signing Key 2017 <packager@opera.com>
```


I have not yet deleted any keys that are still in there. How would you recommend to do it?


I disabled any custom repositories in /etc/apt/sources.list.d/ by renaming the files.

```
$ sudo apt update
Hit:1 https://download.virtualbox.org/virtualbox/debian jammy InRelease        
Hit:2 http://archive.ubuntu.com/ubuntu jammy InRelease                         
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
W: http://archive.ubuntu.com/ubuntu/dists/jammy/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
```


**Could you give any additional with the above information? Thanks in advance!**

---

### Post by btindie on 2024-01-31
> **tellapu said:**
> A minor correction: **cd** is probably needed for the first command ```
cd /etc/apt/trusted.gpg.d
```
Well spotted! I've fixed that in my original post.

All of the duplicate keys you have in /etc/apt/trusted.gpg.d/ appear to be backups &#8212; files ending in '~'. It should be fine to clean them up by running
```
sudo rm -v /etc/apt/trusted.gpg.d/*~
```

It looks like the keys you have stored in /etc/apt/trusted.gpg are either expired or really old, so you should simply be able to delete them.

You can delete each key stored in that file with:
```
#!/bin/bash
while read KEY; do
  echo "Deleting key: $KEY"
  apt-key --keyring /etc/apt/trusted.gpg del "$KEY" 2>/dev/null
done < <(apt-key --keyring /etc/apt/trusted.gpg list 2>/dev/null | sed -E -ne '/^\s+[[:alnum:] ]/s/.*([[:alnum:]]{4}) ([[:alnum:]]{4})$/\1\2/p' )

```
You'll want to run the above script as *root* 
[LIST=1]
[*]so save it to disk as [FONT=system]/tmp/clean.sh[/FONT] (the filename doesn't matter)
[*]make it executable with [FONT=system]chmod +x /tmp/clean.sh[/FONT]
[*]run [FONT=system]sudo /tmp/clean.sh[/FONT]
[/LIST]
When done, you can delete that file.

It may be possible to just delete that file, I'm not familiar with that specific version of Ubuntu. But with Debian 12 it doesn't have one.

You'll then be able to run [FONT=system]apt update[/FONT] and hopefully that should have fixed that error message.

You can then re-enable the disabled repositories one by one followed by [FONT=system]apt update[/FONT] adding any missing keys if required.
[FONT=system]

[/FONT]

---

### Post by tellapu on 2024-01-31
Thanks again for the quick response!

Just a small note for others following the thread in the future. Instead of
run sudo /tmp/clean.sh
It is probably: cd /tmp/-path and then ./clean.sh ([https://askubuntu.com/questions/38661/how-do-i-run-sh-scripts](https://askubuntu.com/questions/38661/how-do-i-run-sh-scripts))

```
$ sudo rm -v /etc/apt/trusted.gpg.d/*~ removed '/etc/apt/trusted.gpg.d/agornostal_ubuntu_ulauncher.gpg~'
removed '/etc/apt/trusted.gpg.d/alexlarsson_ubuntu_flatpak.gpg~'
removed '/etc/apt/trusted.gpg.d/bablu-boy_ubuntu_nutty.gpg~'
removed '/etc/apt/trusted.gpg.d/brave-browser-release.gpg~'
removed '/etc/apt/trusted.gpg.d/dschaerf-ubuntu-rogerrouter.gpg~'
removed '/etc/apt/trusted.gpg.d/dschaerf_ubuntu_rogerrouter.gpg~'
removed '/etc/apt/trusted.gpg.d/embrosyn_ubuntu_cinnamon.gpg~'
removed '/etc/apt/trusted.gpg.d/flatpak-ubuntu-stable.gpg~'
removed '/etc/apt/trusted.gpg.d/gerardpuig-ubuntu-ppa.gpg~'
removed '/etc/apt/trusted.gpg.d/gerardpuig_ubuntu_ppa.gpg~'
removed '/etc/apt/trusted.gpg.d/home_bgstack15_aftermozilla.gpg~'
removed '/etc/apt/trusted.gpg.d/home_stevenpusser.gpg~'
removed '/etc/apt/trusted.gpg.d/kdenlive-ubuntu-kdenlive-stable.gpg~'
removed '/etc/apt/trusted.gpg.d/microsoft.gpg~'
removed '/etc/apt/trusted.gpg.d/mozillateam-ubuntu-ppa.gpg~'
removed '/etc/apt/trusted.gpg.d/openshot_developers-ubuntu-ppa.gpg~'
removed '/etc/apt/trusted.gpg.d/qr-tools-developers_ubuntu_daily.gpg~'
removed '/etc/apt/trusted.gpg.d/strukturag_ubuntu_libde265.gpg~'
removed '/etc/apt/trusted.gpg.d/strukturag_ubuntu_libheif.gpg~'
removed '/etc/apt/trusted.gpg.d/touchegg-ubuntu-stable.gpg~'
removed '/etc/apt/trusted.gpg.d/ubuntu-keyring-2012-cdimage.gpg~'
removed '/etc/apt/trusted.gpg.d/ubuntu-keyring-2018-archive.gpg~'
removed '/etc/apt/trusted.gpg.d/vivaldi-33EAAB8E.gpg~'
removed '/etc/apt/trusted.gpg.d/vivaldi-4218647E.gpg~'
removed '/etc/apt/trusted.gpg.d/vivaldi-B69735B2.gpg~'
removed '/etc/apt/trusted.gpg.d/vivaldi-C27AA466.gpg~'
removed '/etc/apt/trusted.gpg.d/webupd8team-ubuntu-y-ppa-manager.gpg~'
```

```
$ ./clean.sh
Deleting key: 126762B1
Deleting key: 5044912E
Deleting key: 991BC93C
Deleting key: ABDC4346
Deleting key: A5C7FF72
```

Unfortunately it did not help:

```
$ sudo apt update
Hit:1 https://download.virtualbox.org/virtualbox/debian jammy InRelease        
Hit:2 http://archive.ubuntu.com/ubuntu jammy InRelease                        
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
W: http://archive.ubuntu.com/ubuntu/dists/jammy/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
```


It looks like to be a difficult case ... Hopefully you have some more tips! Thanks in advance!

---

### Post by Holger_Gehrke on 2024-01-31
First off, it's not an error, it's a warning (that's what the 'W:' at the beginning means). 'apt-key' as a program is deprecated, you're not supposed to use one central /etc/apt/trusted.gpg anymore but have separate key files in /etc/apt/trusted.gpg.d/ instead. Doing it that way makes adding and removing keys a simple matter of file management. You can also have your keys elsewhere and have a Signed-By option either pointing to  the key-file or including the key in your sources.list for each repository. My Xubuntu 22.04 - which was a clean install, not an update - doesn't have a /etc/apt/trusted.gpg at all.

Holger

---

### Post by btindie on 2024-02-01
> **tellapu said:**
> Just a small note for others following the thread in the future. Instead of
run sudo /tmp/clean.sh
It is probably: cd /tmp/-path and then ./clean.sh ([https://askubuntu.com/questions/38661/how-do-i-run-sh-scripts](https://askubuntu.com/questions/38661/how-do-i-run-sh-scripts))


It doesn't make any difference if you run
```
cd /tmp
./clean.sh
```
or simply
```
/tmp/clean.sh
```
they both do the same thing. The script is using absolute paths so it doesn't matter what directory you're in.

The issue with what you've done though is you haven't followed the instructions fully.

You forgot to prefix [FONT=system]/tmp/clean.sh[/FONT] with **sudo** meaning that you would of had insufficient privileges to modify the keyring. STDERR is redirected to [FONT=system]/dev/null[/FONT] to avoid all those stupid messages "Warning: apt-key is deprecated.". But the consequence of that is it wouldn't have displayed a message about being unable to update the keyring. If you remove [FONT=system]2>/dev/null[/FONT] from the [FONT=system]apt-key del[/FONT] command you'll see.

Once done correctly, list the keys in the keyring again — it should be empty this time.
```
sudo apt-key --keyring /etc/apt/trusted.gpg list
```

---

### Post by tellapu on 2024-02-06
Thank you, @Holger, for the response! It is indeed only a warning by now. In the beginning, the message would also show when I tried to update the system with the "Updater" or in "Updates" in "Software" and more like an error message. With the instructions by btindie, the warning only appears in the terminal now.

At the same time, I noticed that there is a new option in "Software & Updates": "Subscribed to". I have not seen this before and not sure if I have overlooked it.

I changed the "Subscribed to" From "Custom" to "All updates" and finally all the missing updates arrive to my system.

As my install is not a clean install but an update from 20.04, the key storage is not sorted out yet and I would be glad if it is changed to the new more secure way and the warning addressed.

---

### Post by tellapu on 2024-02-06
Sorry for the late reply, @btindie, I did not get a notification for your answer - probably because I was not logged in when I read the message from Holger. 

Thank you for your patience and your helpful instructions! You are right, I missed the sudo. Small changes can make a big difference. Here are the new outputs:

```
$ sudo ...../tmp/clean.sh
[sudo] password for cds: 
Deleting key: 126762B1
OK
Deleting key: 5044912E
OK
Deleting key: 991BC93C
OK
Deleting key: ABDC4346
OK
Deleting key: A5C7FF72
OK
```

```
$ sudo apt-key --keyring /etc/apt/trusted.gpg list
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
```

```
$ sudo apt update
Hit:3 https://download.virtualbox.org/virtualbox/debian jammy InRelease                                                                                        
Hit:4 http://archive.ubuntu.com/ubuntu jammy InRelease                                                                                                         
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease
Hit:6 http://archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:7 http://archive.ubuntu.com/ubuntu jammy-backports InRelease
Err:4 http://archive.ubuntu.com/ubuntu jammy InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
Err:5 http://security.ubuntu.com/ubuntu jammy-security InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
Err:6 http://archive.ubuntu.com/ubuntu jammy-updates InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
Err:7 http://archive.ubuntu.com/ubuntu jammy-backports InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
Fetched 1,559 B in 1s (1,355 B/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com/ubuntu jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com/ubuntu jammy-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com/ubuntu jammy-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com/ubuntu jammy-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jammy/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

I tried to follow the recommended instructions: [https://manpages.ubuntu.com/manpages/jammy/man8/apt-key.8.html#deprecation](https://manpages.ubuntu.com/manpages/jammy/man8/apt-key.8.html#deprecation)

```
$ wget -qO- http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease | sudo tee /etc/apt/trusted.gpg.d/jammy-security.asc
[sudo] password for cds: 
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA512

Origin: Ubuntu
Label: Ubuntu
Suite: jammy-security
Version: 22.04
Codename: jammy
Date: Tue, 06 Feb 2024  7:12:28 UTC
Architectures: amd64 arm64 armhf i386 ppc64el riscv64 s390x
Components: main restricted universe multiverse
Description: Ubuntu Jammy Security
MD5Sum:
 0a9bd87b61f547699775ca2618271847       1402644573 Contents-amd64
 f9455e9026eae22ece1323e3502c78dd         76199613 Contents-amd64.gz
 8957078a58fe17e6a355a510bce3a5f8       1557074371 Contents-arm64
 9f02f1025e63105e81c08789796bcda1         84240849 Contents-arm64.gz
.......
 577ca6001d9537a3806e75f8377c232075889375b4ca04b66a1da0bebe57b03d          1065432 universe/source/Sources
 293eb4b11712d5149b38972540fb237cc9590c4636071ba31d7f3f1de9aeb268           229715 universe/source/Sources.gz
 5a24b9c619d2ca5f4f144e41b4407e3cfa3c5b1afd390a6fdc853fb00c851182           176832 universe/source/Sources.xz
Acquire-By-Hash: yes
-----BEGIN PGP SIGNATURE-----

iQIzBAEBCgAdFiEE9uyzdiR07anSG3Aihxkg0ZkbyTwFAmXB3AkACgkQhxkg0Zkb
yTzeIBAAvzcFJIspAkWdtTuocwDId57sxmiyonDRzKZTBzAXNQriSf5MZ4nXobXr
iDWFbnTrGX8K10ie5QxkE2YXeKtCd/YQ65CNxissJKwWr3k3h5uUoOMixyXiSQ/C
1m7ughnIihbj+UcIMq4vj3HVrBbyRqNgt52KY0pR7bD0sIeU5qLKo8CS4T+GqWKt
40eyKoyhUqhcQLhaebZilumC96ZXZ24WbOOVFy8V9fOD1+FveBSEFbcRJIg45by1
pN29Z9yc/3YzLnaCiRmI/+KcSIMbHvS1O0frQpM7A30gdpdlNx4I8EnGxr4yRMQb
+fUYexCILu+WFHEDeMkaK//jsSSmgKlbl4iw+ziw6VoUx/tq8RHi3RqfvZ4lbdv2
lZvUj8x5lsiGHPIshaMkY/9cconMpAQQn6qP4t0CQ1wppQ7f+0JoRYhhBsLUt3ij
fjHCX9X+mUqAse9NUzzz0WG6rj1h1JyGp5vTJnaKoezft/IpEayEwDvnzvAQ7odJ
lVxK6ooavJiTyUt65t1P+d+rk/WYyPWylJl9nG1JBiba6FtPNSNcBv0QIqsgv1SV
hrgN2Z2z5z+ZG2TMvi9pWxnbsz+++g2dyWA5yUC4eCXpBMgE+PLwXPcDNfbXkJ4W
5jSTkO4yG+vby77adjSqCBhNtL4+fG2MvNDBkO5UQdiHzZDPG34=
=2yLI
-----END PGP SIGNATURE----
```


But it could be that I missed something as there is a new error now:

```
$ sudo apt update
Get:1 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Hit:2 http://archive.ubuntu.com/ubuntu jammy InRelease                                                                                            
Get:3 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB] 
Hit:6 http://archive.ubuntu.com/ubuntu jammy-backports InRelease                                       
Err:2 http://archive.ubuntu.com/ubuntu jammy InRelease
  At least one invalid signature was encountered.
Hit:7 https://download.virtualbox.org/virtualbox/debian jammy InRelease
Fetched 231 kB in 1s (196 kB/s)           
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com/ubuntu jammy InRelease: At least one invalid signature was encountered.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://download.opensuse.org/repositories/home:/ungoogled_chromium/Ubuntu_Jammy  InRelease: At least one invalid signature was encountered.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com/ubuntu jammy-security InRelease: At least one invalid signature was encountered.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com/ubuntu jammy-updates InRelease: At least one invalid signature was encountered.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com/ubuntu jammy-backports InRelease: At least one invalid signature was encountered.
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jammy/InRelease  At least one invalid signature was encountered.
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease  At least one invalid signature was encountered.
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  At least one invalid signature was encountered.
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  At least one invalid signature was encountered.
W: Failed to fetch http://download.opensuse.org/repositories/home:/ungoogled_chromium/Ubuntu_Jammy/InRelease  At least one invalid signature was encountered.
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

Any tip for further steps?

---

### Post by ActionParsnip on 2024-02-06
[https://www.omgubuntu.co.uk/2022/06/fix-apt-key-deprecation-error-on-ubuntu](https://www.omgubuntu.co.uk/2022/06/fix-apt-key-deprecation-error-on-ubuntu)

Explains it

---

### Post by btindie on 2024-02-06
> ```
$ wget -qO- http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease | sudo tee /etc/apt/trusted.gpg.d/jammy-security.asc
```
That file you've downloaded is not a GPG key, hence the errors you're seeing. So please delete it.
```
sudo rm /etc/apt/trusted.gpg.d/jammy-security.asc
```

I'm not sure how you updated your system but I suspect you may be missing the supplied gpg keys that are in the [FONT=system]ubuntu-keyring[/FONT] package.

What's in your /etc/apt/trusted.gpg.d directory?
```
ls -l /etc/apt/trusted.gpg.d
```

You can see the files in it at [https://packages.ubuntu.com/jammy/ubuntu-keyring](https://packages.ubuntu.com/jammy/ubuntu-keyring)

That packages postinst script does:
```
if [ "$1" = 'configure' -a -n "$2" ]; then    # remove keys from the trusted.gpg file as they are now shipped in fragment files in trusted.gpg.d
    if dpkg --compare-versions "$2" 'lt' "2016.09.19" && which gpg > /dev/null && which apt-key > /dev/null; then
        TRUSTEDFILE='/etc/apt/trusted.gpg'
        eval $(apt-config shell TRUSTEDFILE Apt::GPGV::TrustedKeyring)
        eval $(apt-config shell TRUSTEDFILE Dir::Etc::Trusted/f)
        if [ -e "$TRUSTEDFILE" ]; then
            for KEY in 40976EAF437D05B5 46181433FBB75451 3B4FE6ACC0B21F32 D94AA3F0EFE21092; do
                apt-key --keyring "$TRUSTEDFILE" del $KEY > /dev/null 2>&1 || :
            done
        fi
    fi
fi
```
which is essentially what you did earlier.

It also contains the GPG keys for that release.

If you manually download that package [https://packages.ubuntu.com/jammy/all/ubuntu-keyring/download](https://packages.ubuntu.com/jammy/all/ubuntu-keyring/download)

Then install the downloaded file, that should add the missing GPG keys. e.g.
```
sudo apt-get install --reinstall ./Downloads/ubuntu-keyring_2021.03.26_all.deb
```
You need to prefix the path/filename with [FONT=system]./[/FONT] so it knows to treat it as a local file.

The missing key with ID [FONT=system]871920D1991BC93C[/FONT] is in [FONT=system]/etc/apt/trusted.gpg.d/ubuntu-keyring-2018-archive.gpg[/FONT] in that package.

---

### Post by tellapu on 2024-02-09
Thank you, ActionParsnip, for your response!

---

### Post by tellapu on 2024-02-09
Thanks a lot, btindie, for all the instructions. It has been really busy here but I hope to be able to have some spare time next week as I really want to fix this.

A quick response at least to your question:
```
$ ls -l /etc/apt/keyring.d
ls: cannot access '/etc/apt/keyring.d': No such file or directory
$ ls -l /etc/apt/keyrings
total 4
-rw-r--r-- 1 root root 3147 Feb  2 12:00 teams-for-linux.asc
```

---

### Post by tellapu on 2024-02-10
No output or error with sudo ..../tmp/clean2.sh

I downloaded ubuntu-keyring_2021.03.26_all.deb.

```
$sudo apt-get install --reinstall ./.../ubuntu-keyring_2021.03.26_all.deb
E: Unsupported file ./media/Storage/tmp/ubuntu-keyring_2021.03.26_all.deb given on commandline
```

I tried then with GDebi but it gives the error "no longer provides ubuntu-keyring".

In the Synaptic app I found the package and marked it for "reinstall". This worked and afterwards, I got no error anymore:

```
$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://download.opensuse.org/repositories/home:/ungoogled_chromium/Ubuntu_Jammy  InRelease [1,559 B]
Get:3 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]                 
Hit:4 https://download.virtualbox.org/virtualbox/debian jammy InRelease     
Hit:5 https://repo.teamsforlinux.de/debian stable InRelease                    
Get:6 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]        
Get:7 http://archive.ubuntu.com/ubuntu jammy-backports InRelease [109 kB]
Get:8 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages [400 kB]
Get:9 http://archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [567 kB]
Get:10 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages [1,142 kB]
Get:11 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [1,366 kB]
Get:12 http://security.ubuntu.com/ubuntu jammy-security/main Translation-en [211 kB]        
Get:13 http://security.ubuntu.com/ubuntu jammy-security/universe i386 Packages [590 kB]          
Get:14 http://archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [272 kB]               
Get:15 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 Packages [839 kB]         
Get:16 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [1,044 kB]          
Get:17 http://security.ubuntu.com/ubuntu jammy-security/universe Translation-en [160 kB]                                                                                                                    
Get:18 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages [1,366 kB]                                                                                                                
Get:19 http://archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [687 kB]                                                                                                                       
Get:20 http://archive.ubuntu.com/ubuntu jammy-updates/universe Translation-en [235 kB]                                                                                                                      
Get:21 http://archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages [1,412 kB]                                                                                                                  
Get:22 http://security.ubuntu.com/ubuntu jammy-security/restricted Translation-en [224 kB]                                                                                                                  
Get:23 http://archive.ubuntu.com/ubuntu jammy-updates/restricted Translation-en [233 kB]                                                                                                                    
Get:24 http://archive.ubuntu.com/ubuntu jammy-backports/universe i386 Packages [13.4 kB]                                                                                                                    
Get:25 http://archive.ubuntu.com/ubuntu jammy-backports/universe amd64 Packages [24.3 kB]                                                                                                                   
Fetched 11.1 MB in 14s (822 kB/s)                                                                                                                                                                           
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

Hallelujah! I now have to work on all the PPAs and learn how to move them to /etc/apt/trusted.gpg.d/. But I guess ActionParsnip's link will help with this.
Thanks again so much for all your help!!!

---

### Post by btindie on 2024-02-10
> **tellapu said:**
> 
A quick response at least to your question:
```
$ ls -l /etc/apt/keyring.d
ls: cannot access '/etc/apt/keyring.d': No such file or directory
$ ls -l /etc/apt/keyrings
total 4
-rw-r--r-- 1 root root 3147 Feb  2 12:00 teams-for-linux.asc
```

Sorry, I had meant to say
```
ls -l /etc/apt/trusted.gpg.d
```

On a clean docker image of ubuntu:22.04 it contains just
```
root@6eed3a8b0a0f:~# ls -l /etc/apt/trusted.gpg.dtotal 8
-rw-r--r-- 1 root root 2794 Mar 26  2021 ubuntu-keyring-2012-cdimage.gpg
-rw-r--r-- 1 root root 1733 Mar 26  2021 ubuntu-keyring-2018-archive.gpg
```

which are the gpg keys contained in that deb package. That's where you need to place the keys from your PPA's.

---

### Post by tellapu on 2024-02-11
Thank you!

The list in /etc/apt/trusted.gpg.d is long, I guess the previously done work has already helped.

But I am suprised that I have two Vivaldi-keys:
-rw-r--r-- 1 root root 2285 Feb 11 09:48 vivaldi-33EAAB8E.gpg
-rw-r--r-- 1 root root 2285 Feb 11 09:48 vivaldi-4218647E.gpg

Probably I could delete one at some stage. How to find out which one?

---

### Post by tellapu on 2024-02-11
Interestingly /usr/share/keyrings/ includes Ubuntu-Pro-Keys. Why would Ubuntu add them there in Nov 2023 as it is depreciated?
```
$ ls -l /usr/share/keyrings/
total 84
-rw-r--r-- 1 root root 4037 Oct 31 14:13 brave-browser-archive-keyring.gpg
-rw-r--r-- 1 root root 2462 Jun  8  2023 brave-browser-beta-archive-keyring.gpg
-rw-r--r-- 1 root root 2462 Jun  8  2023 brave-browser-nightly-archive-keyring.gpg
-rw-r--r-- 1 root root 2247 Jan  6  2023 oracle-virtualbox-2016.gpg
-rw-rw-r-- 1 cds  cds  2223 May  5  2021 signal-desktop-keyring.gpg
-rw-r--r-- 1 root root 7399 Sep 18  2018 ubuntu-archive-keyring.gpg
-rw-r--r-- 1 root root 6713 Oct 27  2016 ubuntu-archive-removed-keys.gpg
-rw-r--r-- 1 root root 3023 Mar 27  2021 ubuntu-cloudimage-keyring.gpg
-rw-r--r-- 1 root root    0 Jan 17  2018 ubuntu-cloudimage-removed-keys.gpg
-rw-r--r-- 1 root root 1227 May 27  2010 ubuntu-master-keyring.gpg
-rw-r--r-- 1 root root 1150 Nov  7 15:23 ubuntu-pro-anbox-cloud.gpg
-rw-r--r-- 1 root root 2247 Nov  7 15:23 ubuntu-pro-cc-eal.gpg
-rw-r--r-- 1 root root 2274 Nov  7 15:23 ubuntu-pro-cis.gpg
-rw-r--r-- 1 root root 2236 Nov  7 15:23 ubuntu-pro-esm-apps.gpg
-rw-r--r-- 1 root root 2264 Nov  7 15:23 ubuntu-pro-esm-infra.gpg
-rw-r--r-- 1 root root 2275 Nov  7 15:23 ubuntu-pro-fips.gpg
-rw-r--r-- 1 root root 2275 Nov  7 15:23 ubuntu-pro-fips-preview.gpg
-rw-r--r-- 1 root root 2250 Nov  7 15:23 ubuntu-pro-realtime-kernel.gpg
-rw-r--r-- 1 root root 2235 Nov  7 15:23 ubuntu-pro-ros.gpg
```

Unfortunately these keys don't appear with sudo apt-key list. At the end of the list I get this error:
```
W: The key(s) in the keyring /etc/apt/trusted.gpg are ignored as the file has an unsupported filetype.
```

How to find out which one is the unsupported one?
Maybe the ubuntu-cloudimage-removed-keys.gpg as its size is 0?
Could I just delete it?
And the Brave-keyrings as a Brave-PPA is not listed in the "Other Software" in "Software & Updates"?

---

### Post by tellapu on 2024-03-02
In case somebody will read this in the future, I will answer the questions.

> But I am suprised that I have two Vivaldi-keys. 
> Probably I could delete one at some stage. How to find out which one?

I think Vivaldi adds two keys by default and therefore it is best to not delete any.


> W: The key(s) in the keyring /etc/apt/trusted.gpg are ignored as the file has an unsupported filetype.
> How to find out which one is the unsupported one?

As far as I can tell the trusted.gpg-file had a problem. When I deleted it, the error did not occur anymore.

From there, I **added the PPA **(I still needed) **manually** again. For a few PPAs/repositories I had to use the mentioned instructions:
[https://www.omgubuntu.co.uk/2022/06/fix-apt-key-deprecation-error-on-ubuntu](https://www.omgubuntu.co.uk/2022/06/fix-apt-key-deprecation-error-on-ubuntu)
[https://askubuntu.com/questions/1398344/apt-key-deprecation-warning-when-updating-system-key-is-stored-in-legacy-trust](https://askubuntu.com/questions/1398344/apt-key-deprecation-warning-when-updating-system-key-is-stored-in-legacy-trust)
[B]
Again, thank you very much, btindie, you made a big difference![/B]

---

### Post by caterhamfan on 2024-09-05
Sorry for the bump.

I'm encountering a similar issue [here]("https://ubuntuforums.org/showthread.php?t=2500542") 

Main error: 

E: Conflicting values set for option Signed-By regarding source [https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/](https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/) noble: /etc/apt/keyrings/boot-repair.gpg !

I have tried opening /etc/apt/sources.list and sudo nano /etc/apt/keyrings/boot-repair.gpg both are blank.

Be grateful for any assistance you can provide.

Thank you

---

### Post by tellapu on 2024-09-09
I am sorry to hear that you have this problem, @caterhamfan
Unfortunately, I don't have any tips either. Maybe @btindie can help.
I recommend to post the main error in your initial thread in order for people to see it straightaway and it can be found with a search function.
Hopefully you will find a solution for the problem! (If you do, thanks in advance for posting it in your thread.)

---

