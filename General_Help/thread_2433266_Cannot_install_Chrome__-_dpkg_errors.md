---
title: "Cannot install Chrome  - dpkg errors"
date: 2019-12-16
forum: General Help
---

### Post by rh2050mexico on 2019-12-16
I cannot install Chrome. When I use the sudo dpkg -i google-chrome-stable_current_amd64.deb, I get the following errors...

```
(Reading database ... 180314 files and directories currently installed.)
Preparing to unpack google-chrome-stable_current_amd64.deb ...
Unpacking google-chrome-stable (79.0.3945.79-1) ...
dpkg-deb (subprocess): cannot copy archive member from 'google-chrome-stable_current_amd64.deb' to decompressor pipe: unexpected end of file or stream
dpkg-deb (subprocess): decompressing archive member: lzma error: unexpected end of input
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive google-chrome-stable_current_amd64.deb (--install):
 cannot copy extracted data for './opt/google/chrome/nacl_helper' to '/opt/google/chrome/nacl_helper.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 google-chrome-stable_current_amd64.deb


```

Your help would be most appreciated.

---

### Post by howefield on 2019-12-16
I'd proffer that the download is corrupt and that you should download the file again, then perhaps use apt to install.

I might be misremembering but I don't think that dpkg handles dependencies whereas apt does.

```
sudo apt install /path/to/deb/file
```

---

### Post by dragonfly41 on 2019-12-16
There is also GDebi package Installer which lists *.deb installation dependencies.

---

### Post by Hewjr100 on 2019-12-16
Well all I know is that I download Google Chrome 64 bit deb file from google website.  I then click on deb file and let software app install it.

Henry

---

