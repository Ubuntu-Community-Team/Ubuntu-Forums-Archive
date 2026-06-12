---
title: "Key error while updating using apt-get"
date: 2014-10-15
forum: General Help
---

### Post by Ankush_Menat on 2014-10-15
Whenever I try to use sudo apt-get update it gives me these errors
```
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: https://download.01.org trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9

```

I tried manually getting keys but didnt worked.

Tried updating another time! Now different errors
```
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://us.archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://us.archive.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://us.archive.ubuntu.com trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: https://download.01.org trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366
```

---

### Post by Ankush_Menat on 2014-10-15
When I add keys manually I get these errors-
```
ankush@ankush:~$ sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 52B709720F164EEB[sudo] password for ankush: 
gpg: WARNING: unsafe ownership on configuration file `/home/ankush/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
ankush@ankush:~$ sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 75CFD31C9E5DB0C8
gpg: WARNING: unsafe ownership on configuration file `/home/ankush/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
ankush@ankush:~$ 
```

Now Only 2 keys are not working/broken

---

### Post by slickymaster on 2014-10-15
See this: [http://askubuntu.com/questions/330755/unsafe-permissions-on-configuration-file-home-david-gnupg-gpg-conf-what-doe](http://askubuntu.com/questions/330755/unsafe-permissions-on-configuration-file-home-david-gnupg-gpg-conf-what-doe)

---

### Post by Ankush_Menat on 2014-10-15
> **slickymaster said:**
> See this: [http://askubuntu.com/questions/330755/unsafe-permissions-on-configuration-file-home-david-gnupg-gpg-conf-what-doe](http://askubuntu.com/questions/330755/unsafe-permissions-on-configuration-file-home-david-gnupg-gpg-conf-what-doe)

Not working. I even removed gpg conf file as explained in last lines

---

### Post by slickymaster on 2014-10-15
What did you do exactly? What commands did you run?

---

### Post by Ankush_Menat on 2014-10-15
> **slickymaster said:**
> What did you do exactly? What commands did you run?
```
ls -l ~/.gnupg/gpg.conf



chown $(whoami):$(whoami) ~/.gnupg/gpg.conf
```

Then checked sudo apt-get update, still didn't worked so..

```
rm -r ~/.gnupg/gpg.conf
```

Before this I also tried - [http://askubuntu.com/questions/131601/how-to-overcome-signature-verification-error](http://askubuntu.com/questions/131601/how-to-overcome-signature-verification-error) and [http://ubuntuforums.org/showthread.php?t=2232401](http://ubuntuforums.org/showthread.php?t=2232401)

Currently I am getting this two errors...
```
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 52B709720F164EEBW: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 75CFD31C9E5DB0C8

```

---

### Post by slickymaster on 2014-10-15
> **Ankush_Menat said:**
> ```
ls -l ~/.gnupg/gpg.conf



chown $(whoami):$(whoami) ~/.gnupg/gpg.conf
```

Thing is that you should had to run```
chmod 600 ~/.gnupg/gpg.conf
```after running **chown $(whoami):$(whoami) ~/.gnupg/gpg.conf**
> **Ankush_Menat said:**
> Then checked sudo apt-get update, still didn't worked so..

```
rm -r ~/.gnupg/gpg.conf
```

Before this I also tried - [http://askubuntu.com/questions/131601/how-to-overcome-signature-verification-error](http://askubuntu.com/questions/131601/how-to-overcome-signature-verification-error) and [http://ubuntuforums.org/showthread.php?t=2232401](http://ubuntuforums.org/showthread.php?t=2232401)
This only had to be run if some of the above commands failed.

---

### Post by Ankush_Menat on 2014-10-16
After trying all stuffs I mentioned above I uncheked all Items in software centre... updated...rechecked all items...update...downloaded missing keys from keyserver. Its working now. 
[IMG]http://i.imgur.com/hZvZVA6.png[/IMG]
Thanks a lot for helping :)



[COLOR=#ff0000]UPDATE:


[/COLOR][COLOR=#000000]Another problem I am facing is some important packeges are marked as not required!!
[/COLOR]```
The following packages were automatically installed and are no longer required:  cli-common libdb5.3:i386 libdbus-glib1.0-cil libdbus-glib2.0-cil
  libdbus1.0-cil libdbus2.0-cil libgconf2.0-cil libgdata2.1-cil libgdiplus
  libgkeyfile1.0-cil libglib2.0-cil libgtk-sharp-beans-cil libgtk2.0-cil
  libgudev1.0-cil libmono-addins0.2-cil libmono-cairo4.0-cil
  libmono-corlib4.0-cil libmono-corlib4.5-cil libmono-data-tds4.0-cil
  libmono-i18n-west4.0-cil libmono-i18n4.0-cil libmono-posix4.0-cil
  libmono-security4.0-cil libmono-sharpzip4.84-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-data4.0-cil libmono-system-drawing4.0-cil
  libmono-system-enterpriseservices4.0-cil libmono-system-numerics4.0-cil
  libmono-system-runtime-serialization4.0-cil libmono-system-security4.0-cil
  libmono-system-transactions4.0-cil libmono-system-xml-linq4.0-cil
  libmono-system-xml4.0-cil libmono-system4.0-cil libmono-zeroconf1.0-cil
  libnewtonsoft-json5.0-cil libnotify0.4-cil libtaglib2.1-cil mono-4.0-gac
  mono-gac mono-runtime mono-runtime-common mono-runtime-sgen

```[COLOR=#000000]
[/COLOR]

---

### Post by Ankush_Menat on 2014-10-16
Bump??

---

### Post by slickymaster on 2014-10-17
**apt** implements an _Auto-Installed_ state flag to keep track of packages that were never installed explicitly, i.e. packages that you have not explicitly requested their installation and that the system should be free to remove them as soon as they are no longer needed. You can verify that this is effectively the case with **apt-mark showauto** (it returns a list of the automatically installed packages).

I would have a look at the list of packages and decide if they are worth keeping. Sometimes packages which you may want to keep are marked _Auto-Installed_ by default.
You can get information on what the various packages do by doing **apt-cache show package_name**. If you decide to keep some, you can use **apt-mark manual** followed by the names of the packages you want to keep.

Here's a good read on this subject: [How I learned to stop worrying and love metapackages]("http://forums.debian.net/viewtopic.php?f=16&t=104157")

---

