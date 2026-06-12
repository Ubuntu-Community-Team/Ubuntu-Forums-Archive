---
title: "do-release-upgrade error bionic 18.04LTS"
date: 2022-02-17
forum: General Help
---

### Post by pw442 on 2022-02-17
Dear All,

by trying to run do-release-upgrade on my bionic, i'm getting the follwoing error:

Traceback (most recent call last): File "/usr/bin/lsb_release",

 .......

ValueError: could not convert string to float: '6.06 LTS'

Any clue?

thx in advance.

---

### Post by Impavidus on 2022-02-18
Looks like some tool tries to convert all Ubuntu version strings to floats and gives an error on the first LTS release. But why would it try to convert those strings to floats? Never heard of this error before. Maybe clear cache and redownload the upgrade tool? Maybe there are more clues in the rest of the error message?

---

### Post by schragge on 2022-02-18
Please provide the output of
```
lsb_release -a
```
as well as
```
python /usr/share/pyshared/lsb_release.py
python2 /usr/share/pyshared/lsb_release.py
python3 /usr/share/pyshared/lsb_release.py
```
The code in question is **/usr/share/pyshared/lsb_release.py**:
```
def get_distro_info(origin='Debian'):
    try:
        FileNotFoundException = FileNotFoundError
    except NameError:
        # There is no FileNotFoundError in python2
        FileNotFoundException = IOError

    try:
        csvfile = open('/usr/share/distro-info/%s.csv' % origin.lower())
    except FileNotFoundException:
        # Unknown distro, fallback to Debian
        csvfile = open('/usr/share/distro-info/debian.csv')

    reader = csv.DictReader(csvfile)
    global RELEASE_CODENAME_LOOKUP, RELEASES_ORDER, TESTING_CODENAME
    RELEASE_CODENAME_LOOKUP = { r['version']: r['series'] for r in reader if r['version']}
    RELEASES_ORDER = list(RELEASE_CODENAME_LOOKUP.items())
    RELEASES_ORDER.sort(key=lambda n: float(n[0]))
    RELEASES_ORDER = list(list(zip(*RELEASES_ORDER))[1])

    if origin.lower() == 'debian':
        TESTING_CODENAME = 'unknown.new.testing'
        RELEASES_ORDER.extend(['stable', 'proposed-updates', 'testing', 'testing-proposed-updates', 'unstable', 'sid'])

    csvfile.close()
```
By changing [FONT=monospace]origin='Debian'[/FONT] to [FONT=monospace]origin='Ubuntu'[/FONT], and then calling [FONT=monospace]get_distro_info()[/FONT], I get

**Python 2**
```
Traceback (most recent call last):
  File "di.py", line 31, in <module>
    get_distro_info()
  File "di.py", line 22, in get_distro_info
    RELEASES_ORDER.sort(key=lambda n: float(n[0]))
  File "di.py", line 22, in <lambda>
    RELEASES_ORDER.sort(key=lambda n: float(n[0]))
ValueError: invalid literal for float(): 20.04 LTS
```
**Python 3**
```
Traceback (most recent call last):
  File "di.py", line 31, in <module>
    get_distro_info()
  File "di.py", line 22, in get_distro_info
    RELEASES_ORDER.sort(key=lambda n: float(n[0]))
  File "di.py", line 22, in <lambda>
    RELEASES_ORDER.sort(key=lambda n: float(n[0]))
ValueError: could not convert string to float: '6.06 LTS'
```

Here is a small test script that induces those errors:
```
#!/usr/bin/python
from __future__ import print_function
import lsb_release

print(lsb_release.get_distro_information()['CODENAME'])
print(lsb_release.get_distro_information()['ID'])
print(lsb_release.get_os_release())
print('>>> Should work until this line <<<')
print('>>> The next line should work only on Debian and fail on Ubuntu <<<')
print(lsb_release.guess_debian_release())
```

I guess the only way to get those errors during **do-release-upgrade** is if **/usr/lib/os-release** is corrupted in some way.

If that's the case, try
```
sudo apt reinstall base-files
```

---

### Post by MAFoElffen on 2022-02-18
I would like to see the physical lsb file itself, before the Python Script reads it. (It's a fairly basic script):
```

awk '{print $0}' /etc/lsb-release

```
Because I would really like to see "why" the error said "[COLOR=#ff0000]6.06[/COLOR] LTS"(???) <<--Because that in itself is not logical at all.

---

### Post by schragge on 2022-02-18
> **MAFoElffen said:**
> Because I would really like to see "why" the error said "[COLOR=#ff0000]6.06[/COLOR] LTS"(???) <<--Because that in itself is not logical at all.
It is like **Impavidus** said above
> **Impavidus said:**
> Looks like some tool tries to convert all  Ubuntu version strings to floats and gives an error on the first LTS  release.
If **/usr/lib/os-release** is corrupted, **lsb_release** will fall back to [FONT=monospace]lsb_release.guess_debian_release()[/FONT]. Debian releases don't have **LTS** in them, so it works on Debian. Compare
```
debian-distro-info -ar
```
to
```
ubuntu-distro-info -ar
```
> **Impavidus said:**
> But why would it try to convert those strings to floats?
To sort code names in the order of their version numbers.

---

### Post by pw442 on 2022-02-20
[FONT=monospace]Hya, thank you all. With the hints, i was able to begin, but new errors:

i had a corrupted /usr/lib/os-release and python was brokem so with apt-get install --reinstall, i managed it.

Now, something is wrong when running do-release-upgrade. 

It breakes after showin the output of the apt update from focal.

apt.log shows:

```
[/FONT][FONT=monospace][COLOR=#000000]root@wolke:/var/log/dist-upgrade# cat apt.log[/COLOR]
Log time: 2022-02-20 13:51:21.142438
Log time: 2022-02-20 13:51:27.354848
Log time: 2022-02-20 13:51:57.115356
Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done
  MarkInstall libvulkan1:amd64 < 1.2.198.1-2 @ii mK NPb IPb > FU=0
  ignore old unsatisfied important dependency on mesa-vulkan-drivers:amd64
  MarkInstall linux-headers-5.4.0-90-generic:amd64 < 5.4.0-90.101~18.04.1 -> 5.4.0-90.101 @ii umU Ib > FU=0
  Installing linux-headers-5.4.0-90:amd64 as Hängt ab von of linux-headers-5.4.0-90-generic:amd64
    MarkInstall linux-headers-5.4.0-90:amd64 < none -> 5.4.0-90.101 @un uN > FU=0
  MarkInstall prosody-trunk:amd64 < 1nightly1623-1~bionic @ii mK NPb IPb > FU=0
  ignore old unsatisfied important dependency on lua-unbound:amd64
  ignore old unsatisfied important dependency on lua-readline:amd64
  python3-samba:amd64 Hängt ab von on python3:amd64 < 3.9.8-1 @ii mK > (< 3.9) can't be satisfied!
  MarkInstall python3-dnspython:amd64 < 2.2.0-2 @ii mK NPb IPb > FU=0
  ignore old unsatisfied important dependency on python3-requests-toolbelt:amd64
  MarkInstall apport-gtk:amd64 < 2.20.9-0ubuntu7.27 -> 2.20.11-0ubuntu27.21 @ii ugU NPb Ib > FU=0
  Installing whoopsie-preferences:amd64 as Hängt ab von of apport-gtk:amd64
    MarkInstall whoopsie-preferences:amd64 < none -> 22 @un uN Ib > FU=0
    Installing libwhoopsie-preferences0:amd64 as Hängt ab von of whoopsie-preferences:amd64
      MarkInstall libwhoopsie-preferences0:amd64 < none -> 22 @un uN > FU=0
    Installing libwhoopsie0:amd64 as Hängt ab von of whoopsie-preferences:amd64
      MarkInstall libwhoopsie0:amd64 < none -> 0.2.69ubuntu0.3 @un uN > FU=0
  ignore old unsatisfied important dependency on update-notifier:amd64
  MarkInstall libgcc1:amd64 < 1:8.4.0-1ubuntu1~18.04 -> 1:10.3.0-1ubuntu1~20.04 @ii umU Ib > FU=0
  Installing gcc-10-base:amd64 as Hängt ab von of libgcc1:amd64
    MarkInstall gcc-10-base:amd64 < none -> 10.3.0-1ubuntu1~20.04 @un uN > FU=0
  MarkInstall software-properties-common:amd64 < 0.96.24.32.18 -> 0.99.9.8 @ii umU Ib > FU=0
  Installing gir1.2-packagekitglib-1.0:amd64 as Hängt ab von of software-properties-common:amd64
    MarkInstall gir1.2-packagekitglib-1.0:amd64 < none -> 1.1.13-2ubuntu1.1 @un uN Ib > FU=0
    Installing libpackagekit-glib2-18:amd64 as Hängt ab von of gir1.2-packagekitglib-1.0:amd64
      MarkInstall libpackagekit-glib2-18:amd64 < none -> 1.1.13-2ubuntu1.1 @un uN IPb > FU=0
      Installing packagekit:amd64 as Empfiehlt of libpackagekit-glib2-18:amd64
        MarkInstall packagekit:amd64 < none -> 1.1.13-2ubuntu1.1 @rc uN Ib > FU=0
        Installing libglib2.0-bin:amd64 as Hängt ab von of packagekit:amd64
          libglib2.0-bin:amd64 Hängt ab von on libglib2.0-0:amd64 < 2.70.4-1 @ii mK > (= 2.64.6-1~ubuntu20.04.4) can't be satisfied!
          packagekit:amd64 Hängt ab von on libglib2.0-bin:amd64 < none @un H > can't be satisfied! (dep)
        libpackagekit-glib2-18:amd64 Empfiehlt on packagekit:amd64 < none @rc H > (= 1.1.13-2ubuntu1.1) can't be satisfied! (dep)
    software-properties-common:amd64 Hängt ab von on packagekit:amd64 < none @rc H > can't be satisfied! (dep)
  samba:amd64 Hängt ab von on python3:amd64 < 3.9.8-1 @ii mK > (< 3.9) can't be satisfied!
  MarkInstall libwbclient0:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU Ib > FU=0
  Installing libicu66:amd64 as Hängt ab von of libwbclient0:amd64
    MarkInstall libicu66:amd64 < none -> 66.1-2ubuntu2.1 @un uN > FU=0
  MarkInstall landscape-common:amd64 < 18.01-0ubuntu3.5 -> 19.12-0ubuntu4.2 @ii umU Ib > FU=0
  Installing python3-netifaces:amd64 as Hängt ab von of landscape-common:amd64
    python3-netifaces:amd64 Hängt ab von on python3:amd64 < 3.9.8-1 @ii mK > (< 3.9) can't be satisfied!
    landscape-common:amd64 Hängt ab von on python3-netifaces:amd64 < none @un H > can't be satisfied! (dep)
  MarkInstall python3-software-properties:amd64 < 0.96.24.32.18 -> 0.99.9.8 @ii umU NPb IPb > FU=0
  ignore old unsatisfied important dependency on unattended-upgrades:amd64
  MarkInstall libfcgi0ldbl:amd64 < 2.4.2-2 @ii mK NPb IPb > FU=0
  ignore old unsatisfied important dependency on libfcgi-bin:amd64
  MarkInstall update-manager-core:amd64 < 1:18.04.11.13 -> 1:20.04.10.10 @ii umU Ib > FU=0
  Installing ubuntu-advantage-tools:amd64 as Hängt ab von of update-manager-core:amd64
    MarkInstall ubuntu-advantage-tools:amd64 < none -> 27.6~20.04.1 @rc uN Ib > FU=0
    Installing distro-info:amd64 as Hängt ab von of ubuntu-advantage-tools:amd64
      MarkInstall distro-info:amd64 < none -> 0.23ubuntu1 @un uN > FU=0
  MarkInstall libpocketsphinx3:amd64 < 0.8.0+real5prealpha-1ubuntu2 -> 0.8.0+real5prealpha+1-6ubuntu4 @ii umU NPb IPb > FU=0
  ignore old unsatisfied important dependency on pocketsphinx-hmm-en-hub4wsj:amd64
  ignore old unsatisfied important dependency on pocketsphinx-lm-en-hub4:amd64
  MarkInstall libasound2-data:amd64 < 1.2.6.1-1 @ii mK NPb IPb > FU=0
  ignore old unsatisfied important dependency on alsa-ucm-conf:amd64
  ignore old unsatisfied important dependency on alsa-topology-conf:amd64
  MarkKeep distro-info:amd64 < none -> 0.23ubuntu1 @un uN > FU=0
  MarkInstall distro-info-data:amd64 < 0.52 @ii mK > FU=0
  MarkInstall grub-efi-amd64-bin:amd64 < 2.04-20 @ii mK NPb IPb > FU=0
  ignore old unsatisfied important dependency on grub-efi-amd64-signed:amd64
  MarkInstall libc-dev-bin:amd64 < 2.33-5 @ii mK NPb IPb > FU=0
  ignore old unsatisfied important dependency on libc-devtools:amd64
  MarkInstall shim-signed:amd64 < 1.38+15.4-7 -> 1.40.7+15.4-0ubuntu9 @ii umU Ib > FU=0
  Installing grub-efi-amd64-signed:amd64 as Hängt ab von of shim-signed:amd64
    grub-efi-amd64-signed:amd64 Hängt ab von on grub-efi-amd64-bin:amd64 < 2.04-20 @ii mK NPb IPb > (= 2.04-1ubuntu44.2) can't be satisfied!
    shim-signed:amd64 Hängt ab von on grub-efi-amd64-signed:amd64 < none @un mH > can't be satisfied! (dep)
  MarkInstall e2fsprogs:amd64 < 1.46.5-2 @ii mK NPb IPb > FU=0
  ignore old unsatisfied important dependency on e2fsprogs-l10n:amd64
  MarkInstall xorgxrdp:amd64 < 1:0.2.17-1 @ii mK NPb IPb > FU=0
  ignore old unsatisfied important dependency on xorg:amd64
Starting pkgProblemResolver with broken count: 4
Starting 2 pkgProblemResolver with broken count: 4
Investigating (0) ubuntu-advantage-tools:amd64 < none -> 27.6~20.04.1 @rc uN Ib >
Broken ubuntu-advantage-tools:amd64 Hängt ab von on distro-info:amd64 < none | 0.23ubuntu1 @un uH > (>= 0.18ubuntu0.18.04.1)
  Considering distro-info:amd64 0 as a solution to ubuntu-advantage-tools:amd64 6
  MarkKeep ubuntu-advantage-tools:amd64 < none -> 27.6~20.04.1 @rc uN Ib > FU=0
  Holding Back ubuntu-advantage-tools:amd64 rather than change distro-info:amd64
Investigating (0) update-manager-core:amd64 < 1:18.04.11.13 -> 1:20.04.10.10 @ii umU Ib >
Broken update-manager-core:amd64 Hängt ab von on ubuntu-advantage-tools:amd64 < none | 27.6~20.04.1 @rc uH >
  Considering ubuntu-advantage-tools:amd64 6 as a solution to update-manager-core:amd64 3
  MarkKeep update-manager-core:amd64 < 1:18.04.11.13 -> 1:20.04.10.10 @ii umU Ib > FU=0
  Removing update-manager-core:amd64 rather than change ubuntu-advantage-tools:amd64
  MarkDelete update-manager-core:amd64 < 1:18.04.11.13 | 1:20.04.10.10 @ii umH Ib > FU=0
Investigating (0) python3-samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mK NPb Ib >
Broken python3-samba:amd64 Hängt ab von on samba-libs:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU > (= 2:4.13.14+dfsg-1+b1)
  Considering samba-libs:amd64 12 as a solution to python3-samba:amd64 2
  Removing python3-samba:amd64 rather than change samba-libs:amd64
  MarkDelete python3-samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mK NPb Ib > FU=0
Investigating (0) update-notifier-common:amd64 < 3.192.1.12 -> 3.192.30.10 @ii ugU Ib >
Broken update-notifier-common:amd64 Hängt ab von on update-manager-core:amd64 < 1:18.04.11.13 | 1:20.04.10.10 @ii umR > (>= 1:17.04.2)
  Considering update-manager-core:amd64 3 as a solution to update-notifier-common:amd64 0
  MarkKeep update-notifier-common:amd64 < 3.192.1.12 -> 3.192.30.10 @ii ugU Ib > FU=0
  Removing update-notifier-common:amd64 rather than change update-manager-core:amd64
  MarkDelete update-notifier-common:amd64 < 3.192.1.12 | 3.192.30.10 @ii ugH Ib > FU=0
Investigating (0) software-properties-common:amd64 < 0.96.24.32.18 @ii umH Ib >
Broken software-properties-common:amd64 Hängt ab von on python3-software-properties:amd64 < 0.96.24.32.18 -> 0.99.9.8 @ii umU NPb IPb > (= 0.96.24.32.18)
  Considering python3-software-properties:amd64 0 as a solution to software-properties-common:amd64 -2
  Removing software-properties-common:amd64 rather than change python3-software-properties:amd64
  MarkDelete software-properties-common:amd64 < 0.96.24.32.18 @ii umH Ib > FU=0
Investigating (0) samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mK NPb Ib >
Broken samba:amd64 Hängt ab von on python3-samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mR NPb >
  Considering python3-samba:amd64 2 as a solution to samba:amd64 -2
  Removing samba:amd64 rather than change python3-samba:amd64
  MarkDelete samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mK NPb Ib > FU=0
Investigating (1) samba-common-bin:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU Ib >
Broken samba-common-bin:amd64 Hängt ab von on python3-samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mR NPb >
  Considering python3-samba:amd64 2 as a solution to samba-common-bin:amd64 7
  Added python3-samba:amd64 to the remove list
  MarkKeep python3-samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mR NPb > FU=0
  Fixing samba-common-bin:amd64 via keep of python3-samba:amd64
Investigating (1) python3-samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mK NPb Ib >
Broken python3-samba:amd64 Hängt ab von on samba-libs:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU > (= 2:4.13.14+dfsg-1+b1)
  Considering samba-libs:amd64 12 as a solution to python3-samba:amd64 2
  Removing python3-samba:amd64 rather than change samba-libs:amd64
  MarkDelete python3-samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mK NPb Ib > FU=0
Investigating (2) samba-common-bin:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU Ib >
Broken samba-common-bin:amd64 Hängt ab von on python3-samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mR NPb >
  Considering python3-samba:amd64 2 as a solution to samba-common-bin:amd64 7
  Added python3-samba:amd64 to the remove list
  MarkKeep python3-samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mR NPb > FU=0
  Fixing samba-common-bin:amd64 via keep of python3-samba:amd64
Investigating (2) python3-samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mK NPb Ib >
Broken python3-samba:amd64 Hängt ab von on samba-libs:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU > (= 2:4.13.14+dfsg-1+b1)
  Considering samba-libs:amd64 12 as a solution to python3-samba:amd64 7
  Removing python3-samba:amd64 rather than change samba-libs:amd64
  MarkDelete python3-samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mK NPb Ib > FU=0
Investigating (3) samba-common-bin:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU Ib >
Broken samba-common-bin:amd64 Hängt ab von on python3-samba:amd64 < 2:4.13.14+dfsg-1+b1 @ii mR NPb >
  Considering python3-samba:amd64 12 as a solution to samba-common-bin:amd64 7
  MarkKeep samba-common-bin:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU Ib > FU=0
  Removing samba-common-bin:amd64 rather than change python3-samba:amd64
  MarkDelete samba-common-bin:amd64 < 2:4.13.14+dfsg-1+b1 | 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umH Ib > FU=0
Investigating (3) winbind:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU Ib >
Broken winbind:amd64 Hängt ab von on samba-common-bin:amd64 < 2:4.13.14+dfsg-1+b1 | 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umR > (= 2:4.13.17~dfsg-0ubuntu0.21.04.1)
  Considering samba-common-bin:amd64 12 as a solution to winbind:amd64 0
  MarkKeep winbind:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU Ib > FU=0
  Removing winbind:amd64 rather than change samba-common-bin:amd64
  MarkDelete winbind:amd64 < 2:4.13.14+dfsg-1+b1 | 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umH Ib > FU=0
Investigating (4) libnss-winbind:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU Ib >
Broken libnss-winbind:amd64 Hängt ab von on winbind:any:any < none @un mH > (= 2:4.13.17~dfsg-0ubuntu0.21.04.1)
  Considering winbind:amd64 12 as a solution to libnss-winbind:amd64 0
  MarkKeep libnss-winbind:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU Ib > FU=0
  Removing libnss-winbind:amd64 rather than change winbind:any:any
  MarkDelete libnss-winbind:amd64 < 2:4.13.14+dfsg-1+b1 | 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umH Ib > FU=0
Investigating (4) libpam-winbind:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU Ib >
Broken libpam-winbind:amd64 Hängt ab von on winbind:any:any < none @un mH > (= 2:4.13.17~dfsg-0ubuntu0.21.04.1)
  Considering winbind:amd64 12 as a solution to libpam-winbind:amd64 0
  MarkKeep libpam-winbind:amd64 < 2:4.13.14+dfsg-1+b1 -> 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umU Ib > FU=0
  Removing libpam-winbind:amd64 rather than change winbind:any:any
  MarkDelete libpam-winbind:amd64 < 2:4.13.14+dfsg-1+b1 | 2:4.13.17~dfsg-0ubuntu0.21.04.1 @ii umH Ib > FU=0
Done
None
  MarkInstall linux-generic:amd64 < none -> 5.4.0.100.104 @un uN Ib > FU=1
  Installing linux-image-generic:amd64 as Hängt ab von of linux-generic:amd64
    MarkInstall linux-image-generic:amd64 < none -> 5.4.0.100.104 @un uN Ib > FU=0
    Installing linux-image-5.4.0-100-generic:amd64 as Hängt ab von of linux-image-generic:amd64
      MarkInstall linux-image-5.4.0-100-generic:amd64 < none -> 5.4.0-100.113 @un uN Ib > FU=0
      Installing linux-modules-5.4.0-100-generic:amd64 as Hängt ab von of linux-image-5.4.0-100-generic:amd64
        MarkInstall linux-modules-5.4.0-100-generic:amd64 < none -> 5.4.0-100.113 @un uN > FU=0
    Installing linux-modules-extra-5.4.0-100-generic:amd64 as Hängt ab von of linux-image-generic:amd64
      MarkInstall linux-modules-extra-5.4.0-100-generic:amd64 < none -> 5.4.0-100.113 @un uN > FU=0
    Installing intel-microcode:amd64 as Hängt ab von of linux-image-generic:amd64
      MarkInstall intel-microcode:amd64 < none -> 3.20210608.0ubuntu0.20.04.1 @rc uN Ib > FU=0
      Installing iucode-tool:amd64 as Hängt ab von of intel-microcode:amd64
        MarkInstall iucode-tool:amd64 < none -> 2.3.1-1 @un uN > FU=0
    Installing amd64-microcode:amd64 as Hängt ab von of linux-image-generic:amd64
      MarkInstall amd64-microcode:amd64 < none -> 3.20191218.1ubuntu1 @rc uN > FU=0
    Installing thermald:amd64 as Empfiehlt of linux-image-generic:amd64
      MarkInstall thermald:amd64 < none -> 1.9.1-1ubuntu0.6 @rc uN Ib > FU=0
      Installing libdbus-glib-1-2:amd64 as Hängt ab von of thermald:amd64
        MarkInstall libdbus-glib-1-2:amd64 < none -> 0.110-5fakssync1 @un uN > FU=0
      Installing libupower-glib3:amd64 as Hängt ab von of thermald:amd64
        MarkInstall libupower-glib3:amd64 < none -> 0.99.11-1build2 @un uN IPb > FU=0
        Installing upower:amd64 as Empfiehlt of libupower-glib3:amd64
          MarkInstall upower:amd64 < none -> 0.99.11-1build2 @rc uN > FU=0
  Installing linux-headers-generic:amd64 as Hängt ab von of linux-generic:amd64
    MarkInstall linux-headers-generic:amd64 < none -> 5.4.0.100.104 @un umN Ib > FU=0
    Installing linux-headers-5.4.0-100-generic:amd64 as Hängt ab von of linux-headers-generic:amd64
      MarkInstall linux-headers-5.4.0-100-generic:amd64 < none -> 5.4.0-100.113 @un uN Ib > FU=0
      Installing linux-headers-5.4.0-100:amd64 as Hängt ab von of linux-headers-5.4.0-100-generic:amd64
        MarkInstall linux-headers-5.4.0-100:amd64 < none -> 5.4.0-100.113 @un uN > FU=0
Log time: 2022-02-20 13:52:03.402252

[/FONT][FONT=monospace]
```

and main.log shows:
```
[/FONT][FONT=monospace][COLOR=#000000]root@wolke:/var/log/dist-upgrade# cat main.log  [/COLOR]
2022-02-20 13:51:16,432 INFO Using config files '['./DistUpgrade.cfg.bionic', '/etc/update-manager/release-upgrades.d/ubuntu-advantage-upgrades.cfg']'
2022-02-20 13:51:16,432 INFO uname information: 'Linux wolke.wollny.com.br 5.4.0-90-generic #101~18.04.1-Ubuntu SMP Fri Oct 22 09:25:04 UTC 2021 x86_64'
2022-02-20 13:51:16,662 INFO apt version: '2.3.15'
2022-02-20 13:51:16,662 INFO python version: '3.9.10 (main, Jan 15 2022, 18:56:52)  
[GCC 7.5.0]'
2022-02-20 13:51:16,665 INFO release-upgrader version '20.04.37' started
2022-02-20 13:51:16,668 INFO locale: 'de_DE' 'UTF-8'
2022-02-20 13:51:16,740 DEBUG Using 'DistUpgradeViewText' view
2022-02-20 13:51:16,777 DEBUG enable dpkg --force-overwrite
2022-02-20 13:51:16,803 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2022-02-20 13:51:20,420 DEBUG lsb-release: 'bionic'
2022-02-20 13:51:20,420 DEBUG _pythonSymlinkCheck run
2022-02-20 13:51:20,421 DEBUG openCache()
2022-02-20 13:51:20,421 DEBUG quirks: running PreCacheOpen
2022-02-20 13:51:20,421 DEBUG running Quirks.PreCacheOpen
2022-02-20 13:51:20,998 DEBUG Comparing 5.4.0-90 with  
2022-02-20 13:51:21,145 DEBUG /openCache(), new cache size 77063
2022-02-20 13:51:21,146 DEBUG need_server_mode(): can not find a desktop meta package or key deps, running in server mode
2022-02-20 13:51:21,146 DEBUG checkViewDepends()
2022-02-20 13:51:21,148 DEBUG running doUpdate() (showErrors=False)
2022-02-20 13:51:26,592 DEBUG openCache()
2022-02-20 13:51:27,218 DEBUG Comparing 5.4.0-90 with  
2022-02-20 13:51:27,365 DEBUG /openCache(), new cache size 77063
2022-02-20 13:51:27,365 DEBUG doPostInitialUpdate
2022-02-20 13:51:27,365 DEBUG quirks: running focalPostInitialUpdate
2022-02-20 13:51:27,365 DEBUG running Quirks.focalPostInitialUpdate
2022-02-20 13:51:29,072 DEBUG MetaPkgs:  
2022-02-20 13:51:30,802 DEBUG no PkgRecord found for 'linux-image-4.15.0-126-generic', skipping  
2022-02-20 13:51:30,829 DEBUG no PkgRecord found for 'linux-modules-4.15.0-126-generic', skipping  
2022-02-20 13:51:30,840 DEBUG no PkgRecord found for 'linux-modules-extra-4.15.0-126-generic', skipping  
2022-02-20 13:51:30,914 DEBUG no PkgRecord found for 'matrix-synapse-py3', skipping  
2022-02-20 13:51:30,998 DEBUG no PkgRecord found for 'proftpd-core', skipping  
2022-02-20 13:51:31,095 DEBUG no PkgRecord found for 'riot-web', skipping  
2022-02-20 13:51:31,144 DEBUG no PkgRecord found for 'trueconf', skipping  
2022-02-20 13:51:31,182 DEBUG Foreign: apt-fast et galera-4 libapache2-mod-php libapache2-mod-php7.4 libapache2-mod-php8.0 libapache2-mod-php8.1 libargon2-1 libgd3 libicu
65 libpcre3 libpython3.7-minimal libpython3.7-stdlib libpython3.8 libpython3.8-dev libpython3.8-minimal libpython3.8-stdlib libpython3.9 libpython3.9-dev libpython3.9-min
imal libpython3.9-stdlib libsodium-dev libsodium23 libzip4 mariadb-client mariadb-client-10.4 mariadb-client-core-10.4 mariadb-server mariadb-server-10.4 mariadb-server-c
ore-10.4 mysql-common netdata netdata-plugin-cups netdata-plugin-freeipmi php php-apcu php-apcu-bc php-bcmath php-cgi php-common php-curl php-fpm php-gd php-imagick php-i
map php-json php-mbstring php-mcrypt php-mysql php-pear php-redis php-smbclient php-sqlite3 php-xml php-zip php5.6-apcu php5.6-cli php5.6-common php5.6-imagick php5.6-jso
n php5.6-opcache php5.6-phpdbg php5.6-readline php7.0-apcu php7.0-apcu-bc php7.0-cli php7.0-common php7.0-imagick php7.0-json php7.0-opcache php7.0-phpdbg php7.0-readline
 php7.1-apcu php7.1-apcu-bc php7.1-cli php7.1-common php7.1-imagick php7.1-json php7.1-opcache php7.1-phpdbg php7.1-readline php7.2-apcu php7.2-apcu-bc php7.2-cli php7.2-
common php7.2-gmp php7.2-imagick php7.2-json php7.2-opcache php7.2-phpdbg php7.2-readline php7.3-apcu php7.3-apcu-bc php7.3-bcmath php7.3-bz2 php7.3-cli php7.3-common php
7.3-curl php7.3-fpm php7.3-gd php7.3-gmp php7.3-imagick php7.3-intl php7.3-json php7.3-ldap php7.3-mbstring php7.3-mysql php7.3-opcache php7.3-readline php7.3-xml php7.3-
zip php7.4 php7.4-apcu php7.4-apcu-bc php7.4-bcmath php7.4-bz2 php7.4-cgi php7.4-cli php7.4-common php7.4-curl php7.4-dev php7.4-fpm php7.4-gd php7.4-gmp php7.4-imagick p
hp7.4-intl php7.4-json php7.4-ldap php7.4-mbstring php7.4-mysql php7.4-opcache php7.4-readline php7.4-sqlite3 php7.4-xml php7.4-zip php8.0 php8.0-apcu php8.0-bcmath php8.
0-cgi php8.0-cli php8.0-common php8.0-fpm php8.0-gmp php8.0-imagick php8.0-opcache php8.0-readline php8.0-sqlite3 php8.0-xml php8.1 php8.1-apcu php8.1-bcmath php8.1-cgi p
hp8.1-cli php8.1-common php8.1-curl php8.1-fpm php8.1-gd php8.1-imagick php8.1-imap php8.1-mbstring php8.1-mcrypt php8.1-mysql php8.1-opcache php8.1-readline php8.1-redis
 php8.1-smbclient php8.1-sqlite3 php8.1-xml php8.1-zip prosody-trunk python3.7 python3.7-minimal python3.8 python3.8-dev python3.8-minimal python3.8-venv python3.9 python
3.9-dev python3.9-distutils python3.9-lib2to3 python3.9-minimal python3.9-venv speedtest syncany syncany-plugin-ftp syncany-plugin-raid0 syncany-plugin-samba syncany-plug
in-sftp syncany-plugin-webdav webmin
2022-02-20 13:51:31,182 DEBUG Obsolete: acpi-support-base bind9-dnsutils bind9-libs bsdextrautils cpp-11 dbus-bin dbus-daemon dbus-session-bus-common dbus-system-bus-comm
on dh-elpa-helper enchant-2 exfatprogs fuse3 g++-11 gcc-11 gcc-11-base intel-media-va-driver ipp-usb jicofo jigasi jitsi-meet jitsi-meet-prosody jitsi-meet-web jitsi-meet
-web-config jitsi-videobridge2 libaom3 libapt-pkg6.0 libaria2-0 libasan6 libatopology2 libavcodec58 libavdevice58 libavfilter7 libavformat58 libavutil56 libboost-iostream
s1.74.0 libboost-regex1.74.0 libboost-thread1.74.0 libbpf0 libc-l10n libcbor0.8 libcdio19 libcjson1 libcodec2-1.0 libcrypt-dev libcrypt1 libctf-nobfd0 libctf0 libcwidget4
 libdav1d5 libdc1394-25 libdebuginfod-common libdebuginfod1 libdecor-0-0 libdecor-0-plugin-1-cairo libdeflate0 libdlt2 libdns-export1110 libdvdread8 libenchant-2-2 libeve
nt-2.1-7 libevent-core-2.1-7 libevent-extra-2.1-7 libevent-openssl-2.1-7 libevent-pthreads-2.1-7 libffi8 libfido2-1 libfluidsynth3 libfmt8 libfontconfig-dev libfreeipmi17
 libfreetype-dev libfuse3-3 libgcc-11-dev libgcc-s1 libgdbm6 libgdk-pixbuf-2.0-0 libgpg-error-l10n libgssdp-1.2-0 libgupnp-1.2-1 libgutenprint-common libgutenprint9 libhi
redis0.14 libhogweed6 libhttp-parser2.9 libhunspell-1.7-0 libicu67 libidn12 libigdgmm12 libilmbase25 libimagequant0 libinstpatch-1.0-2 libip4tc2 libip6tc2 libipt2 libisc-
export1105 libisl23 libjemalloc2 libjim0.79 libjpeg62-turbo libjpeg62-turbo-dev libjson-c5 libjsoncpp25 libkadm5clnt-mit12 libkadm5srv-mit12 libkdb5-10 libldacbt-enc2 lib
ldb2 liblinear4 libllvm12 liblouis20 liblouisutdml9 liblvm2cmd2.03 liblzf1 libmagickcore-6.q16-6 libmagickcore-6.q16-6-extra libmagickwand-6.q16-6 libmfx1 libmysofa1 libn
curses-dev libncurses6 libncursesw6 libnettle8 libnftables1 libnftnl11 libnsl-dev libnsl2 libntfs-3g89 libopenaptx0 libopenexr25 libopeniscsiusr libpcre2-posix3 libperl5.
34 libpgm-5.3-0 libpipewire-0.3-0 libpipewire-0.3-common libpipewire-0.3-modules libplymouth5 libpoppler102 libpostproc55 libprocps8 libprotobuf-lite23 libprotobuf23 libp
ython2-dev libpython2-stdlib libqpdf28 libqrencode4 libreadline8 libruby2.7 libsemanage2 libsensors-config libsensors5 libsepol2 libsndio7.0 libsnmp40 libsoup2.4-common l
ibspa-0.2-modules libsrt1.4-gnutls libstdc++-11-dev libswresample3 libswscale5 libtinfo6 libtirpc-common libtirpc3 libudfread0 libunbound8 liburcu8 liburing2 libusbmuxd6 
libvidstab1.1 libvpx7 libwebsockets16 libwmf-0.2-7 libwmflite-0.2-7 libwpe-1.0-1 libwpebackend-fdo-1.0-1 libx264-160 libx265-199 libzimg2 libzxingcore1 logsave mailcap me
dia-types nmap-common pci.ids perl-modules-5.34 pipewire pipewire-bin pipewire-media-session plocate python2 python2-dev python2-minimal python3-avahi python3-importlib-m
etadata python3-jeepney python3-ldb python3-matrix-common python3-pympler python3-pyrsistent python3-samba python3-soupsieve python3-talloc python3-typing-extensions pyth
on3-zipp rpcsvc-proto ruby-rubygems ruby-xmlrpc ruby2.7 shim-helpers-amd64-signed shim-signed-common shim-unsigned subsonic unison-2.51+4.11.1 usb.ids xdg-dbus-proxy
2022-02-20 13:51:31,182 DEBUG updateSourcesList()
2022-02-20 13:51:31,194 DEBUG rewriteSourcesList() with mirror_check
2022-02-20 13:51:31,194 DEBUG ['ubuntu-minimal', 'ubuntu-standard']
2022-02-20 13:51:31,194 DEBUG Checking pkg: ubuntu-minimal
2022-02-20 13:51:31,195 DEBUG Checking pkg: ubuntu-standard
2022-02-20 13:51:31,195 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu bionic main restricted'
2022-02-20 13:51:31,195 DEBUG verifySourcesListEntry: deb http://archive.ubuntu.com/ubuntu focal main restricted
2022-02-20 13:51:31,195 DEBUG url_downloadable: http://archive.ubuntu.com/ubuntu/dists/focal/Release
2022-02-20 13:51:31,196 DEBUG s='http' n='archive.ubuntu.com' p='/ubuntu/dists/focal/Release' q='' f=''
2022-02-20 13:51:31,709 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu focal main restricted' updated to new dist
2022-02-20 13:51:31,710 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu bionic-updates main restricted'
2022-02-20 13:51:31,710 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu focal-updates main restricted' updated to new dist
2022-02-20 13:51:31,710 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu bionic universe'
2022-02-20 13:51:31,710 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu focal universe' updated to new dist
2022-02-20 13:51:31,710 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu bionic-updates universe'
2022-02-20 13:51:31,710 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu focal-updates universe' updated to new dist
2022-02-20 13:51:31,710 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu bionic multiverse'
2022-02-20 13:51:31,710 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu focal multiverse' updated to new dist
2022-02-20 13:51:31,710 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu bionic-updates multiverse'
2022-02-20 13:51:31,710 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu focal-updates multiverse' updated to new dist
2022-02-20 13:51:31,710 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse'
2022-02-20 13:51:31,710 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse' updated to new dist
2022-02-20 13:51:31,710 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu bionic-security main restricted'
2022-02-20 13:51:31,710 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu focal-security main restricted' updated to new dist
2022-02-20 13:51:31,710 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu bionic-security main'
2022-02-20 13:51:31,711 DEBUG verifySourcesListEntry: deb http://security.ubuntu.com/ubuntu focal main
2022-02-20 13:51:31,711 DEBUG url_downloadable: http://security.ubuntu.com/ubuntu/dists/focal/Release
2022-02-20 13:51:31,711 DEBUG s='http' n='security.ubuntu.com' p='/ubuntu/dists/focal/Release' q='' f=''
2022-02-20 13:51:32,229 DEBUG entry 'deb http://security.ubuntu.com/ubuntu focal-security main' updated to new dist
2022-02-20 13:51:32,230 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu bionic-security universe'
2022-02-20 13:51:32,230 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu focal-security universe' updated to new dist
2022-02-20 13:51:32,230 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu bionic-security multiverse'
2022-02-20 13:51:32,230 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu focal-security multiverse' updated to new dist
2022-02-20 13:51:32,230 DEBUG examining: 'deb http://download.webmin.com/download/repository sarge contrib'
2022-02-20 13:51:32,231 DEBUG entry '# deb http://download.webmin.com/download/repository sarge contrib # Bei Aktualisierung zu focal deaktiviert' was disabled (unknown m
irror)
2022-02-20 13:51:32,231 DEBUG examining: 'deb [arch=arm64,amd64,ppc64el] http://mariadb.mirror.liquidtelecom.com/repo/10.4/ubuntu/ bionic main'
2022-02-20 13:51:32,232 DEBUG entry '# deb [arch=arm64,amd64,ppc64el] http://mariadb.mirror.liquidtelecom.com/repo/10.4/ubuntu/ focal main # Bei Aktualisierung zu focal d
eaktiviert' was disabled (unknown mirror)
2022-02-20 13:51:32,232 DEBUG examining: 'deb http://ppa.launchpad.net/apt-fast/stable/ubuntu bionic main'
2022-02-20 13:51:32,233 DEBUG entry '# deb http://ppa.launchpad.net/apt-fast/stable/ubuntu focal main # Bei Aktualisierung zu focal deaktiviert' was disabled (unknown mir
ror)
2022-02-20 13:51:32,233 DEBUG examining: 'deb http://ppa.launchpad.net/dwmw2/openconnect/ubuntu bionic main'
2022-02-20 13:51:32,234 DEBUG entry '# deb http://ppa.launchpad.net/dwmw2/openconnect/ubuntu focal main # Bei Aktualisierung zu focal deaktiviert' was disabled (unknown m
irror)
2022-02-20 13:51:32,234 DEBUG examining: 'deb [arch=amd64,arm64] http://ppa.launchpad.net/ondrej/php/ubuntu bionic main'
2022-02-20 13:51:32,234 DEBUG entry '# deb [arch=amd64,arm64] http://ppa.launchpad.net/ondrej/php/ubuntu focal main # Bei Aktualisierung zu focal deaktiviert' was disable
d (unknown mirror)
2022-02-20 13:51:32,234 DEBUG examining: 'deb [arch=amd64,arm64] http://ftp.hosteurope.de/mirror/mariadb.org/repo/10.4/ubuntu bionic main'
2022-02-20 13:51:32,235 DEBUG entry '# deb [arch=amd64,arm64] http://ftp.hosteurope.de/mirror/mariadb.org/repo/10.4/ubuntu focal main # Bei Aktualisierung zu focal deakti
viert' was disabled (unknown mirror)
2022-02-20 13:51:32,235 DEBUG examining: 'deb https://packagecloud.io/netdata/netdata/ubuntu/ bionic main'
2022-02-20 13:51:32,236 DEBUG entry '# deb https://packagecloud.io/netdata/netdata/ubuntu/ focal main # Bei Aktualisierung zu focal deaktiviert' was disabled (unknown mir
ror)
2022-02-20 13:51:32,236 DEBUG examining: 'deb-src https://packagecloud.io/netdata/netdata/ubuntu/ bionic main'
2022-02-20 13:51:32,237 DEBUG entry '# deb-src https://packagecloud.io/netdata/netdata/ubuntu/ focal main # Bei Aktualisierung zu focal deaktiviert' was disabled (unknown
 mirror)
2022-02-20 13:51:32,237 DEBUG examining: 'deb http://archive.syncany.org/apt/release/ release main'
2022-02-20 13:51:32,238 DEBUG entry '# deb http://archive.syncany.org/apt/release/ release main # Bei Aktualisierung zu focal deaktiviert' was disabled (unknown mirror)
2022-02-20 13:51:32,238 DEBUG examining: 'deb http://ppa.launchpad.net/jgmath2000/et/ubuntu bionic main'
2022-02-20 13:51:32,239 DEBUG entry '# deb http://ppa.launchpad.net/jgmath2000/et/ubuntu focal main # Bei Aktualisierung zu focal deaktiviert' was disabled (unknown mirro
r)
2022-02-20 13:51:32,239 DEBUG examining: 'deb https://packages.prosody.im/debian bionic main'
2022-02-20 13:51:32,240 DEBUG entry '# deb https://packages.prosody.im/debian focal main # Bei Aktualisierung zu focal deaktiviert' was disabled (unknown mirror)
2022-02-20 13:51:32,240 DEBUG examining: 'deb https://apt.syncthing.net/ syncthing release'
2022-02-20 13:51:32,241 DEBUG entry '# deb https://apt.syncthing.net/ syncthing release # Bei Aktualisierung zu focal deaktiviert' was disabled (unknown mirror)
2022-02-20 13:51:32,241 DEBUG examining: 'deb http://ppa.launchpad.net/iconnor/zoneminder-master/ubuntu bionic main'
2022-02-20 13:51:32,241 DEBUG entry '# deb http://ppa.launchpad.net/iconnor/zoneminder-master/ubuntu focal main # Bei Aktualisierung zu focal deaktiviert' was disabled (u
nknown mirror)
2022-02-20 13:51:32,242 DEBUG examining: 'deb https://packagecloud.io/ookla/speedtest-cli/ubuntu/ bionic main'
2022-02-20 13:51:32,242 DEBUG entry '# deb https://packagecloud.io/ookla/speedtest-cli/ubuntu/ focal main # Bei Aktualisierung zu focal deaktiviert' was disabled (unknown
 mirror)
2022-02-20 13:51:32,242 DEBUG examining: 'deb-src https://packagecloud.io/ookla/speedtest-cli/ubuntu/ bionic main'
2022-02-20 13:51:32,243 DEBUG entry '# deb-src https://packagecloud.io/ookla/speedtest-cli/ubuntu/ focal main # Bei Aktualisierung zu focal deaktiviert' was disabled (unk
nown mirror)
2022-02-20 13:51:32,243 DEBUG examining: 'deb http://as-repository.openvpn.net/as/debian bionic main'
2022-02-20 13:51:32,244 DEBUG entry '# deb http://as-repository.openvpn.net/as/debian focal main # Bei Aktualisierung zu focal deaktiviert' was disabled (unknown mirror)
2022-02-20 13:51:32,244 DEBUG examining: 'deb http://ppa.launchpad.net/deadsnakes/ppa/ubuntu bionic main'
2022-02-20 13:51:32,245 DEBUG entry '# deb http://ppa.launchpad.net/deadsnakes/ppa/ubuntu focal main # Bei Aktualisierung zu focal deaktiviert' was disabled (unknown mirr
or)
2022-02-20 13:51:32,245 DEBUG examining: 'deb-src http://ppa.launchpad.net/deadsnakes/ppa/ubuntu bionic main'
2022-02-20 13:51:32,246 DEBUG entry '# deb-src http://ppa.launchpad.net/deadsnakes/ppa/ubuntu focal main # Bei Aktualisierung zu focal deaktiviert' was disabled (unknown 
mirror)
2022-02-20 13:51:37,940 DEBUG running doUpdate() (showErrors=True)
2022-02-20 13:51:56,427 DEBUG openCache()
2022-02-20 13:51:56,991 DEBUG Comparing 5.4.0-90 with  
2022-02-20 13:51:57,130 DEBUG /openCache(), new cache size 70531
2022-02-20 13:51:57,131 DEBUG need_server_mode(): can not find a desktop meta package or key deps, running in server mode
2022-02-20 13:51:57,131 DEBUG quirks: running PreDistUpgradeCache
2022-02-20 13:51:57,131 DEBUG running Quirks.PreDistUpgradeCache
2022-02-20 13:51:57,131 INFO checking for python-dbg (auto_inst=False)
2022-02-20 13:51:57,131 INFO checking for python-doc (auto_inst=False)
2022-02-20 13:51:57,131 INFO checking for python-minimal (auto_inst=False)
2022-02-20 13:51:57,131 INFO checking for python-dev (auto_inst=False)
2022-02-20 13:51:57,131 INFO checking for libpython-dev (auto_inst=False)
2022-02-20 13:51:57,131 INFO checking for libpython-stdlib (auto_inst=False)
2022-02-20 13:51:57,131 INFO checking for libpython-dbg (auto_inst=False)
2022-02-20 13:51:57,131 INFO checking for python-dbg (auto_inst=True)
2022-02-20 13:51:57,131 INFO checking for python-doc (auto_inst=True)
2022-02-20 13:51:57,131 INFO checking for python-minimal (auto_inst=True)
2022-02-20 13:51:57,131 INFO checking for python-dev (auto_inst=True)
2022-02-20 13:51:57,132 INFO checking for libpython-dev (auto_inst=True)
2022-02-20 13:51:57,132 INFO checking for libpython-stdlib (auto_inst=True)
2022-02-20 13:51:57,132 INFO checking for libpython-dbg (auto_inst=True)
2022-02-20 13:51:58,820 DEBUG Running KeepInstalledSection rules
2022-02-20 13:51:59,419 DEBUG Kernel uname: '5.4.0-90-generic'  
2022-02-20 13:51:59,427 DEBUG nvidiaUpdate()
2022-02-20 13:52:00,140 INFO no old nvidia driver installed, installing no new
2022-02-20 13:52:00,141 DEBUG quirks: running PostDistUpgradeCache
2022-02-20 13:52:00,141 DEBUG running Quirks.PostDistUpgradeCache
2022-02-20 13:52:00,314 DEBUG Comparing 5.4.0-90 with  
2022-02-20 13:52:00,427 INFO installing linux metapackage: linux-generic
2022-02-20 13:52:00,427 DEBUG Installing 'linux-generic' (linux metapackage may have been accidentally uninstalled)
2022-02-20 13:52:00,493 DEBUG blacklist expr 'update-manager-core' matches 'update-manager-core'
2022-02-20 13:52:00,493 DEBUG The package 'update-manager-core' is marked for removal but it's in the removal blacklist
2022-02-20 13:52:00,498 ERROR Dist-upgrade failed: 'Das Paket »update-manager-core« ist zum Löschen vorgesehen, wurde aber durch das System gesperrt.'
2022-02-20 13:52:00,516 DEBUG abort called
2022-02-20 13:52:00,518 DEBUG openCache()
2022-02-20 13:52:03,263 DEBUG Comparing 5.4.0-90 with  
2022-02-20 13:52:03,415 DEBUG /openCache(), new cache size 77063
[/FONT][FONT=monospace]
```

any hint, please?


[/FONT]

---

### Post by Impavidus on 2022-02-20
Most likely your have some non-standard versions of packages installed and the release upgrade process would have to downgrade some packages to get to the new release of Ubuntu. Best to remove such software first, or downgrade to the versions in the official repositories for 18.04. I can see error messages for libglib2.0-bin and python3-netifaces and some others and the version numbers behind in angled brackets are too new for Ubunty 20.04. You can check at [https://packages.ubuntu.com/](https://packages.ubuntu.com/)

libglib and python are rather deeply integrated in Ubuntu, so messing with those usually triggers additional errors. It may be possible to fix this, but a fresh install is much faster. Release upgrades usually work, but if they don't, it's usually better to do a fresh install.

---

