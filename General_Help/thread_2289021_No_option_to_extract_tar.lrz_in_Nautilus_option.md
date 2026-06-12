---
title: "No option to extract tar.lrz in Nautilus option"
date: 2015-07-31
forum: General Help
---

### Post by monkeybrain20122 on 2015-07-31
I have a .tar.lrz file and right click doesn't show the option "extract here", only "compress". lrzip is already installed and I can extract it with the command lrzuntar. The "extract here" option does show for other archive formats like  tar.gz, zip etc. Am I missing a nautilus extension? Nautilus version 1:3.14.2-0ubuntu9.1(vivid-updates)

The .tar.lrz file is from [http://www.cecm.sfu.ca/sage/linux/64bit/index.html](http://www.cecm.sfu.ca/sage/linux/64bit/index.html)

Thanks.

---

### Post by QDR06VV9 on 2015-07-31
Don't know for sure, maybe 7zip?
It was about  a 2 hour download for me so i did not try.
Looks like command line is the way to do it.
[http://www.hecticgeek.com/2012/11/use-lrzip-to-get-high-data-compression-ratios-ubuntu/](http://www.hecticgeek.com/2012/11/use-lrzip-to-get-high-data-compression-ratios-ubuntu/)
sorry not more helpful.

---

### Post by steeldriver on 2015-07-31
Maybe need to install the lrzip package (from the universe repo)?

```
 lrzip - compression program with a very high compression ratio
```

[http://packages.ubuntu.com/vivid/lrzip](http://packages.ubuntu.com/vivid/lrzip)

---

### Post by monkeybrain20122 on 2015-07-31
I did install lrzip and extract with command as said in my first post. Just wonder why nautilus doesn't have an extract option,-- and it seemed to have it before since I always used 'extract here" for downloaded sage archives without much thought,-- unless sage has changed the archive's format without me noticing.

---

### Post by steeldriver on 2015-07-31
oops sorry missed that - I installed it on my 14.04 box and nautilus seemed to recognise it via the 'Open with archive manager...' rightclick menu item

I guess nautilus does things differently in 15.04

---

### Post by CantankRus on 2015-07-31
May have been tar.gz you were downloading before as indicated from this download page.... [http://mirror.aarnet.edu.au/pub/sage/linux/64bit/index.html](http://mirror.aarnet.edu.au/pub/sage/linux/64bit/index.html)

---

### Post by mc4man on 2015-07-31
It's not nautilus per se, "Extract Here" is provided by file-roller, specially /usr/lib/nautilus/extensions-3.0/libnautilus-fileroller.so
So .tar.lzr would need to be added to fr source for the extension, pretty simple - see screen

(- if you want to test out, figuring 15.04 *amd64*
```
wget https://launchpad.net/~mc3man/+archive/ubuntu/vivid-prop/+files/file-roller_3.14.2-0ubuntu5.1%7Eppa_amd64.deb
```
upgrade with package, quit/start nautilus or log out/in & see...

---

### Post by monkeybrain20122 on 2015-08-02
> **mc4man said:**
> It's not nautilus per se, "Extract Here" is provided by file-roller, specially /usr/lib/nautilus/extensions-3.0/libnautilus-fileroller.so
So .tar.lzr would need to be added to fr source for the extension, pretty simple - see screen

(- if you want to test out, figuring 15.04 *amd64*
```
wget https://launchpad.net/~mc3man/+archive/ubuntu/vivid-prop/+files/file-roller_3.14.2-0ubuntu5.1%7Eppa_amd64.deb
```
upgrade with package, quit/start nautilus or log out/in & see...

Hi, while the option 'extract here' shows up it doesn't actually extract. It is stuck in "reading archive" like forever with nothing happening. 

The command lrzuntar decompresses the archive 
> Total time: 00:03:01.64 

Probably a problem or file roller.

---

### Post by monkeybrain20122 on 2015-08-02
> **steeldriver said:**
> oops sorry missed that - I installed it on my 14.04 box and nautilus seemed to recognise it via the 'Open with archive manager...' rightclick menu item

I guess nautilus does things differently in 15.04

It does have that, but no "extract here"

---

### Post by monkeybrain20122 on 2015-08-02
> **CantankRus said:**
> May have been tar.gz you were downloading before as indicated from this download page.... [http://mirror.aarnet.edu.au/pub/sage/linux/64bit/index.html](http://mirror.aarnet.edu.au/pub/sage/linux/64bit/index.html)

I think they used to be .lzma

---

