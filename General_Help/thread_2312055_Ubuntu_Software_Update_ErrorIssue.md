---
title: "Ubuntu Software Update Error/Issue"
date: 2016-02-01
forum: General Help
---

### Post by derek_stewart2 on 2016-02-01
I installed 14.04.3 on a new laptop at the weekend and when trying to run updates I'm getting an error "Error:Broken Count>0" I've hunted around looking for some guidance but come up empty. I did run 2 commands in Terminal (sudo apt-get update and sudo apt-get upgrade) following a suggestion on another thread. Results below:

```
                         derek@derek-Aspire-ES1-512:~$ sudo apt-get update  
 Ign http://archive.ubuntu.com trusty InRelease  
 Hit http://archive.ubuntu.com trusty-updates InRelease  
 Hit http://archive.ubuntu.com trusty-backports InRelease  
 Hit http://archive.ubuntu.com trusty-security InRelease  
 Hit http://archive.ubuntu.com trusty Release.gpg  
 Hit http://archive.ubuntu.com trusty-updates/main Sources  
 Hit http://archive.ubuntu.com trusty-updates/restricted Sources  
 Hit http://archive.ubuntu.com trusty-updates/universe Sources  
 Hit http://archive.ubuntu.com trusty-updates/multiverse Sources  
 Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages  
 Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages  
 Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages  
 Hit http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages  
 Hit http://archive.ubuntu.com trusty-updates/main i386 Packages  
 Hit http://archive.ubuntu.com trusty-updates/restricted i386 Packages  
 Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages  
 Hit http://archive.ubuntu.com trusty-updates/multiverse i386 Packages  
 Hit http://archive.ubuntu.com trusty-updates/main Translation-en  
 Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en  
 Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en  
 Hit http://archive.ubuntu.com trusty-updates/universe Translation-en  
 Hit http://archive.ubuntu.com trusty-backports/main Sources  
 Hit http://archive.ubuntu.com trusty-backports/restricted Sources  
 Hit http://archive.ubuntu.com trusty-backports/universe Sources  
 Hit http://archive.ubuntu.com trusty-backports/multiverse Sources  
 Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages  
 Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages  
 Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages  
 Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages  
 Hit http://archive.ubuntu.com trusty-backports/main i386 Packages  
 Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages  
 Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages  
 Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages  
 Hit http://archive.ubuntu.com trusty-backports/main Translation-en  
 Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en  
 Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en  
 Hit http://archive.ubuntu.com trusty-backports/universe Translation-en  
 Hit http://archive.ubuntu.com trusty-security/main Sources  
 Hit http://archive.ubuntu.com trusty-security/restricted Sources  
 Hit http://archive.ubuntu.com trusty-security/universe Sources  
 Hit http://archive.ubuntu.com trusty-security/multiverse Sources  
 Hit http://archive.ubuntu.com trusty-security/main amd64 Packages  
 Hit http://archive.ubuntu.com trusty-security/restricted amd64 Packages  
 Hit http://archive.ubuntu.com trusty-security/universe amd64 Packages  
 Hit http://archive.ubuntu.com trusty-security/multiverse amd64 Packages  
 Hit http://archive.ubuntu.com trusty-security/main i386 Packages  
 Hit http://archive.ubuntu.com trusty-security/restricted i386 Packages          
 Hit http://archive.ubuntu.com trusty-security/universe i386 Packages            
 Hit http://archive.ubuntu.com trusty-security/multiverse i386 Packages          
 Hit http://archive.ubuntu.com trusty-security/main Translation-en               
 Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en         
 Hit http://archive.ubuntu.com trusty-security/restricted Translation-en         
 Hit http://archive.ubuntu.com trusty-security/universe Translation-en           
 Hit http://archive.ubuntu.com trusty Release                                    
 Hit http://archive.ubuntu.com trusty/main Sources                               
 Hit http://archive.ubuntu.com trusty/restricted Sources                         
 Hit http://archive.ubuntu.com trusty/universe Sources                           
 Hit http://archive.ubuntu.com trusty/multiverse Sources                         
 Hit http://archive.ubuntu.com trusty/main amd64 Packages                        
 Hit http://archive.ubuntu.com trusty/restricted amd64 Packages                  
 Hit http://archive.ubuntu.com trusty/universe amd64 Packages                    
 Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages                  
 Hit http://archive.ubuntu.com trusty/main i386 Packages                         
 Hit http://archive.ubuntu.com trusty/restricted i386 Packages                   
 Hit http://archive.ubuntu.com trusty/universe i386 Packages                     
 Hit http://archive.ubuntu.com trusty/multiverse i386 Packages                   
 Hit http://archive.ubuntu.com trusty/main Translation-en_GB                     
 Hit http://archive.ubuntu.com trusty/main Translation-en                        
 Hit http://archive.ubuntu.com trusty/multiverse Translation-en_GB               
 Hit http://archive.ubuntu.com trusty/multiverse Translation-en                  
 Hit http://archive.ubuntu.com trusty/restricted Translation-en_GB               
 Hit http://archive.ubuntu.com trusty/restricted Translation-en                  
 Hit http://archive.ubuntu.com trusty/universe Translation-en_GB                 
 Hit http://archive.ubuntu.com trusty/universe Translation-en                    
 Reading package lists... Done                                                   
 W: Encountered status field in a non-version description  
 W: Encountered status field in a non-version description  
 W: You may want to run apt-get update to correct these problems  
 derek@derek-Aspire-ES1-512:~$ sudo apt-get upgrade  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 You might want to run ‘apt-get -f install’ to correct these.  
 The following packages have unmet dependencies.  
  apparmor : Depends: libapparmor-perl but it is not installed  
  appmenu-qt5 : Depends: libdbusmenu-qt5 but it is not installed  
  dmsetup : Depends: util-linux (> 2.16)  
  e2fsprogs : PreDepends: util-linux (>= 2.15~rc1-1)  
  hardening-includes : Depends: make  
  hud : Depends: libdbusmenu-qt5 but it is not installed  
  initramfs-tools : Depends: util-linux (> 2.15~rc1)  
  udev : Depends: util-linux (>= 2.16)  
 E: Unmet dependencies. Try using -f.  
 derek@derek-Aspire-ES1-512:~$ 
  
```

I noted the message at the end of this second command and therefore ran  "apt-get -f install" as suggested and got the following:

```
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 44905 package 'libdbusmenu-qt5':
 field name `' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Well and truly bamboozled. Can anyone help?

---

### Post by matt_symes on 2016-02-01
Hi

Please post the output of these commands

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

and

```
sed '44900,44910!d' /var/lib/dpkg/status
```

That may give a place to start looking.

Kind regards

---

### Post by derek_stewart2 on 2016-02-01
Results posted below. Cheers.

```
derek@derek-Aspire-ES1-512:~$ grep "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty main restricted
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu trusty main restricted
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu trusty-updates main restricted
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty universe
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu trusty universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty-updates universe
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu trusty-updates universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty multiverse
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu trusty multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty-updates multiverse
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu trusty-updates multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu trusty-security multiverse
grep: /etc/apt/sources.list.d/*: No such file or directory
derek@derek-Aspire-ES1-512:~$ 
```

```
derek@derek-Aspire-ES1-512:~$ sed '44900,44910!d' /var/lib/dpkg/status
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubunt{"id":"13","pnrResults":[]}
&#65533;&#65533;5MO&#65533;V&#65533;&#65533;kV&#65533;&#65533;l<`;~1454344881,:https://localhost:26143/skypectoc/v1/pnr/parsesecurity-infoFnhllAKWRHGAlo+ESXykKAAAAAAAAAAAwAAAAAAAAEaphjojH6pBabDSgSnsfLHeAAQAAgAAAAAAAAAAAAAAAAAAAAAB4vFIJp5wRkeyPxAQ9RJGKPqbqVvKO0mKuIl8ec8o/uhmCjImkVxP+7sgiYWmMt8F+O2DZM7ZTG6GukivU8OT5gAAAAAAAAMsMIIDKDCCAhCgAwIBAgIQMcFzWV3pwZpBZib4bG41BjANBgkqhkiG9w0BAQsFADBQMRIwEAYDVQQDEwlsb2NhbGhvc3QxHDAaBgNVBAoTE1NreXBlIENsaWNrIHRvIENhbGwxHDAaBgNVBAsTE1NreXBlIENsaWNrIHRvIENhbGwwHhcNMTYwMTAxMTQ1OTM2WhcNMzYwMTAxMTQ1OTM2WjBQMRIwEAYDVQQDEwlsb2NhbGhvc3QxHDAaBgNVBAoTE1NreXBlIENsaWNrIHRvIENhbGwxHDAaBgNVBAsTE1NreXBlIENsaWNrIHRvIENhbGwwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQChmk0V4bKxwq7IO5Ixc35sr2U3GMeUx2ZhgIbRqlpy2NqkwM/BdebJKGq8DTtcHie+DkajgDTgARkntL7R0RP2eTH2UOcmqZBvU2vQLSAT0V+bJSorEcTvsA7NkYMjnvG2xOg0VcfWsy73uboAefjUNTtLTs9aoRNcI1MuhtdOgodvs2xsMYKlS4rWp8/ov6PiTSwVmF6l+NWnJIChbmR1hz313ZWXQpzXg3ZHFPRfdLPCdJ+HzpsraetQWoHpDMxtLodhO9bivor197WQLKIMioMaZlrvWQvh2/NQcG7SV4O7SNtdDgYfxensROXWRbz7uHactMN3J2dLCnCQuzhvAgMBAAEwDQYJKoZIhvcNAQELBQADggEBACHWxR5+1d9VDCOmk+lo4lXz30p8j9f3alcRGdP+9I9Tz8+2DFzYVoqgO0B3uV6VoKwqHdEH1F/1g9kX4lVgS0yO5acwUJk1+jxTfDl3zZqSdqoml2moPSbMqianvDwUsaXKXwhOvBOpM7Irh3gS9MskDXB34rB/1Hgzyj7dzn1evXb+xEOlX/KPsMBDGhoYlI+S5wPSiVXbVpmFRRCVjjXntfdFJnwhfihjTpFmfaSon6dwlEXlXLo+CKDfnrQW4K9zCoJ90oLHwCvnKhl4AcenwncX0o/0vCj97X/E0F3wHhXV/1oZmgGBSH3+HxRmoHl+3+pFGcVb0TVVX2gYztLAFAADAAAAAAEBAAA=request-methodPOSTresponse-headHTTP/1.1 200 OK
Content-Length: 28
Content-Type: application/json
Server: Microsoft-HTTPAPI/2.0
Date: Mon, 01 Feb 2016 16:48:43 GMT
le-rc (>= 0.8.16)
Pre-Depends: libblkid1 (>= 2.20.1), libc6 (>= 2.15), libncurses5 (>= 5.5-5~), libselinux1 (>= 1.32), libslang2 (>= 2.2.4), libtinfo5, libuuid1 (>= 2.16), zlib1g (>= 1:1.1.4)
Suggests: util-linux-locales, kbd | console-tools, dosfstools
Breaks: mac-fdisk (<< 0.1-16ubuntu3~), pmac-fdisk (<< 0.1-16ubuntu3~)
Conflicts: console-tools (<< 1:0.2.3-21), fdisk, fstrim, kbd (<< 1.05-3), linux32, schedutils, setterm
derek@derek-Aspire-ES1-512:~$ 

```

---

### Post by matt_symes on 2016-02-01
Hi

> I installed 14.04.3 on a new laptop at the weekend

```
grep: /etc/apt/sources.list.d/*: No such file or directory
```

```
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubunt{"id":"13","pnrResults":[]}
&#65533;&#65533;5MO&#65533;V&#65533;&#65533;kV&#65533;&#65533;l<`;~1454344881,:https://localhost:26143/skypectoc/v1/pnr/parsesecurity-infoFnhllAKWRHGAlo+ESXykKAAAAAAAAAAAwAAAAAAAAEaphjojH6pBabDSgSnsfLHeAAQAAgAAAAAAAAAAAAAAAAAAAAAB4vFIJp5wRkeyPxAQ9RJGKPqbqVvKO0mKuIl8ec8o/uhmCjImkVxP+7sgiYWmMt8F+O2DZM7ZTG6GukivU8OT5gAAAAAAAAMsMIIDKDCCAhCgAwIBAgIQMcFzWV3pwZpBZib4bG41BjANBgkqhkiG9w0BAQsFADBQMRIwEAYDVQQDEwlsb2NhbGhvc3QxHDAaBgNVBAoTE1NreXBlIENsaWNrIHRvIENhbGwxHDAaBgNVBAsTE1NreXBlIENsaWNrIHRvIENhbGwwHhcNMTYwMTAxMTQ1OTM2WhcNMzYwMTAxMTQ1OTM2WjBQMRIwEAYDVQQDEwlsb2NhbGhvc3QxHDAaBgNVBAoTE1NreXBlIENsaWNrIHRvIENhbGwxHDAaBgNVBAsTE1NreXBlIENsaWNrIHRvIENhbGwwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQChmk0V4bKxwq7IO5Ixc35sr2U3GMeUx2ZhgIbRqlpy2NqkwM/BdebJKGq8DTtcHie+DkajgDTgARkntL7R0RP2eTH2UOcmqZBvU2vQLSAT0V+bJSorEcTvsA7NkYMjnvG2xOg0VcfWsy73uboAefjUNTtLTs9aoRNcI1MuhtdOgodvs2xsMYKlS4rWp8/ov6PiTSwVmF6l+NWnJIChbmR1hz313ZWXQpzXg3ZHFPRfdLPCdJ+HzpsraetQWoHpDMxtLodhO9bivor197WQLKIMioMaZlrvWQvh2/NQcG7SV4O7SNtdDgYfxensROXWRbz7uHactMN3J2dLCnCQuzhvAgMBAAEwDQYJKoZIhvcNAQELBQADggEBACHWxR5+1d9VDCOmk+lo4lXz30p8j9f3alcRGdP+9I9Tz8+2DFzYVoqgO0B3uV6VoKwqHdEH1F/1g9kX4lVgS0yO5acwUJk1+jxTfDl3zZqSdqoml2moPSbMqianvDwUsaXKXwhOvBOpM7Irh3gS9MskDXB34rB/1Hgzyj7dzn1evXb+xEOlX/KPsMBDGhoYlI+S5wPSiVXbVpmFRRCVjjXntfdFJnwhfihjTpFmfaSon6dwlEXlXLo+CKDfnrQW4K9zCoJ90oLHwCvnKhl4AcenwncX0o/0vCj97X/E0F3wHhXV/1oZmgGBSH3+HxRmoHl+3+pFGcVb0TVVX2gYztLAFAADAAAAAAEBAAA=request-methodPOSTresponse-headHTTP/1.1 200 OK
Content-Length: 28
```

You package system is shot to pieces !

You have no sources.list.d directory.

```
dpkg: error: parsing file '/var/lib/dpkg/status' near line 44905 package 'libdbusmenu-qt5':
```

There is no mention of libdbusmenu-qt5 in the output from your last command around line 44905. The does assume that sed and your package manager are reading the files correctly. I suspect this is not the case.

At line 44901 you have junk and referenced in that junk is

```
https://localhost:26143/skypectoc/v1/pnr
```

Does this look familiar ?
 
Anyway, my advice is to reinstall. You've only just installed the system so don't even try to fix it. Reinstall it's quicker.

That said, i'm interested in how your system got into that state just after a fresh install as I don;t want it to happen to you again.

Did you check the hash of the ISO file before you used it ?

What did you do, post installation of Ubuntu, to your system ?

What extra software did you install and what further configuration have you performed ?

Kind regards

---

### Post by derek_stewart2 on 2016-02-01
Thanks for the quick replies. No, I didn't check the hash after downloading the ISO. Hadn't got round to installing that much - few chess game/ databases, calibre, vlc player - and I don't recall any issues while installing. I'm also pretty sure that I ran the updates after installation without issues. 
Anyway I'll take your advice and do a reinstall - after checking the ISO this time.
Many thanks for your help.

---

### Post by Habitual on 2016-02-01
Googly shows skype-related hits on skypectoc
What version of skype is installed?

No matter. I could fix this, but I'm running away now.

---

### Post by matt_symes on 2016-02-01
Hi

> **derek_stewart2 said:**
> Thanks for the quick replies. No, I didn't check the hash after downloading the ISO. Hadn't got round to installing that much - few chess game/ databases, calibre, vlc player - and I don't recall any issues while installing. I'm also pretty sure that I ran the updates after installation without issues. 
Anyway I'll take your advice and do a reinstall - after checking the ISO this time.
Many thanks for your help.

You may find this link useful.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

As something went really wrong with your system and you are new to Ubuntu, you may want to post in these forums to ask questions, just after you next install Ubuntu, while you are still finding your feet.

Kind regards

---

