---
title: "Problem after installing."
date: 2008-05-20
forum: General Help
---

### Post by Blaake on 2008-05-20
I recently installed Ubuntu through wubi.exe (Not from the site, from the one included when I downloaded the desktop version of Ubuntu or whatever) and I had no error messages or anything after being installed. I usually use Windows Vista but when I chose Ubuntu I get the message
> /etc/rcS.d/510udev: 105: uspash_write: not found
/etc/rcS.d/510udev: 105: usplash_write:/usr/bin/tput: not found
/etc/init.d/rc: 317: usplash_write: not found
/etc/init.d/rc: 317: sed: not found
init: rcS main process (5669) killed by SEGV signal
init: Unable to execute "bin/sh" for rc-default: no such file or directory
init: rc-default main provess (6845) terminated with status 255
Don't flame me for asking a stupid question or anything, I'm not amazing with computers. How can I fix this?
When I use ctrl+alt+delete I get the first 3 lines again.

Thanks.

---

### Post by Blaake on 2008-05-20
Can't use umenu.exe because I need a CD?
I try to put it on a DVD-R and it says it's 698.4 MB, the disk is 702 MB and I need 2.44 MB more space.

---

### Post by danwood76 on 2008-05-20
Check the install CD for errors, you can do this by booting off the CD and selecting CD or Media check from the boot menu.
You might also want to check the install image for errors also using an MD5 generator.

Did you download the image via http (the web)?

You may have to change the boot order in your BIOS to get it to boot.

---

### Post by Blaake on 2008-05-20
It won't fit on the CD, I'm seeing if I can compress it and keep it the same format.
Yes, the latest desktop version via the web.

---

### Post by danwood76 on 2008-05-20
The desktop version on the web should fit on to one 700MB CD, I know it fits on to one of mine.
If not you can just burn it to a DVD-R I did that last year when I had no CDs left :)

---

### Post by Blaake on 2008-05-20
Not fitting on a DVD-R.

---

### Post by danwood76 on 2008-05-20
What software are you using to burn the image?

---

### Post by Blaake on 2008-05-20
Sorry, I was away.
Just windows..
I got it wrong before.
The file is 702 MB, there is 696 MB left from 700 on the disk which I've done nothing to.

---

### Post by danwood76 on 2008-05-20
The file size should be 699MB for the standard i386 version.

DVD decrypter is a good ISO burning tool, I think you are trying to burn the image directly to the disk, this is not right as the .iso is the disk image.
Windows doesnt have an iso burning utility.

I would try DVD decrypter and try to burn with that.

---

### Post by Blaake on 2008-05-20
Ah ok, I'll try that. I was trying nero but it wasn't autorunning.

---

### Post by Blaake on 2008-05-20
Did that, got to 2 and 4/5 bars on the GUI and it stayed there for 5 minutes then said
> /etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
Segmentation fault
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
Segmentation fault
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found
/etc/init.d/rc: 317: sed: not found

---

### Post by danwood76 on 2008-05-20
Is this running the CD test from the CDs boot menu?
If so I would re download the ISO as it is probably corrupt.

You can test the ISO by checking its md5 sum against the one online.

I would download the ISO over bit torrent as there is constant error checking with that method.

---

### Post by Blaake on 2008-05-21
Where can I find the md5 sum online?

When I use it to boot my computer it asks me what language.
When I boot it through Windows it says
AutoPlay
Install or run program
Run umenu.exe
 Publisher not specified.
General options
Open folder to view items
 Using Windows explorer

Then it goes to the CD menu and asks to try ubuntu, install ubuntu or install ubuntu inside windows.

---

### Post by danwood76 on 2008-05-21
What you need to do is actually boot from the CD.
So insert the disk and then reboot, if it doesnt boot to the Ubuntu BootCD menu then you need to enable CD booting in your BIOS.
Or you may be able to press a button upon boot which presents you with a choice to boot from the CD.

When you have booted from the CD you should be able to choose the CD check.

The md5 sums are as follows:
```

7d0ac92c56361949d099dd9337c975e7 *ubuntu-8.04-alternate-amd64.iso
166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso
8895167a794c5d8dedcc312fc62f1f1f *ubuntu-8.04-desktop-i386.iso
8a73cf85b04f37d5d91fb436525ea395 *ubuntu-8.04-server-amd64.iso
c3162b21757746c64a0a22cdd060b164 *ubuntu-8.04-server-i386.iso
a96aa69961f3ed80dd7a88fae1e28196 *wubi.exe

```
you will need to generate the ISOs md5 with something like md5win:
[http://www.p6c.com/FREEBIES/MD5WIN.html](http://www.p6c.com/FREEBIES/MD5WIN.html)

---

### Post by Blaake on 2008-05-21
```
c15ee19fd81dd0c2800397f5b913d3c8  ./casper/filesystem.manifest
62d20d5168ce34daee90cb5ece46659c  ./casper/filesystem.manifest-desktop
7644d1c78b8cb48da410daecf5a8879b  ./casper/initrd.gz
3879aa51ef0b4b1b7bf9472744208417  ./casper/filesystem.squashfs
1bf6dca81a4496dd2c29d517b30f087a  ./casper/vmlinuz
0c7052fa9cbd707205c7e8115c4edf62  ./dists/hardy/Release
385eae08cded6080bfdaf09bbbf87d12  ./dists/hardy/restricted/binary-i386/Packages.gz
285c43d848f34ba43ce2e23414e22cf9  ./dists/hardy/restricted/binary-i386/Release
cdd99ba95148c483c8d357f24c09999e  ./dists/hardy/restricted/binary-i386/Packages
86cfbe2aa52dfa6f125124a668a2b15f  ./dists/hardy/Release.gpg
6663f1177324b04294d2dbf92d588ee1  ./dists/hardy/main/binary-i386/Packages.gz
b5c09269e28533a41ce04df0fd4cff0c  ./dists/hardy/main/binary-i386/Release
448e46af7f075c5cd06eb47fef17206c  ./dists/hardy/main/binary-i386/Packages
461cbc7ff94fdea8008cab34b611abb8  ./pics/blue-upperright.png
cd8aa5e7fa11b1362ef1869ac6b1aa56  ./pics/blue-lowerleft.png
a025c46d5daf227adfda51d81eb90f25  ./pics/blue-upperleft.png
92091902d3ca753bb858d4682b3fc26b  ./pics/logo-50.jpg
3c129ee10f707bd9dec10209d28840eb  ./pics/red-upperright.png
cde56251d6cae5214227d887dee3bab7  ./pics/red-upperleft.png
20d4bdecfa6d980d663fb5b93d37a842  ./pics/red-lowerright.png
0730e775a72519aaa450a3774fca5f55  ./pics/red-lowerleft.png
16ff51c168405e575d32bae001f280e4  ./pics/debian.jpg
9e18ae797773b2677b1b7b86e2aff28d  ./pics/blue-lowerright.png
290da440a5a89a767130d329bde5e2a3  ./.disk/casper-uuid-generic
be233bfa837a357bc2fdac401b9ac950  ./.disk/release_notes_url
08e49e563656628ce92e5b5697aefe17  ./.disk/info
206c23980e79d79d4876a2a9509f987a  ./umenu.exe
aa52d459f0631148974436fab1749dd1  ./autorun.inf
8d6a2a045d7c0f48fe2e088f3f87b6ce  ./install/README.sbm
5a93a111efeb5305075c5e077715b6cd  ./install/sbm.bin
3b268753a2b1d44b6b75716e0c85a7d2  ./install/mt86plus
23d9bfe897b4264f2465e8a592ebb6e3  ./preseed/ubuntu.seed
ef8a9571087ec72a80d0ac5416767ec6  ./preseed/ltsp.seed
7e3aa6d1958baf72d369392fdb175486  ./preseed/cli.seed
a69b413b3f00e33190f9370facb51eb0  ./pool/restricted/d/drdsl/drdsl_1.2.0-1_i386.deb
cb9f7dae5b08ae0a34e47e912a781d6f  ./pool/restricted/l/linux-meta/avm-fritz-firmware_2.6.24.16.18_i386.deb
e9bbcb3519e7102ee19d7ff9ded2785c  ./pool/restricted/l/linux-restricted-modules-2.6.24/avm-fritz-firmware-2.6.24-16_3.11+2.6.24.12-16.34_i386.deb
7946e5212fa9494e4391ae2dd2f36b44  ./pool/restricted/s/sl-modem/sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5ubuntu4_i386.deb
43b9858b5cd8b661e7bf49ba3897c857  ./pool/main/n/ndisgtk/ndisgtk_0.8.3-1_i386.deb
19f8b3d3ccbc56cb48e32ea38fdd3b3d  ./pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb
9ede35a11c0894a09217b932aea32856  ./pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb
dbf21241506cb04fc6f67a93aaaf991b  ./pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb
089772451f71f4a696a8c30118338d51  ./pool/main/b/bpalogin/bpalogin_2.0.2-11_i386.deb
bd566c9b29d13c9c0bbd71ba559678ab  ./pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb
b390db00c909b52a58e86a43dbfebb80  ./pool/main/d/dpkg/dpkg-dev_1.14.16.6ubuntu3_all.deb
60f1b7060ea77403d049e5516678e826  ./pool/main/g/glibc/libc6-dev_2.7-10ubuntu3_i386.deb
27333f45b45f635c29fa7570affbd887  ./pool/main/g/gcc-4.2/g++-4.2_4.2.3-2ubuntu7_i386.deb
428223c0b7f433038e7bd0f0359145aa  ./pool/main/g/gcc-4.2/libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb
a94d0a0247106efe2939404173b984a6  ./pool/main/g/gcc-defaults/g++_4.2.3-1ubuntu3_i386.deb
b25719cb6478b097d55fad64cc73dd40  ./pool/main/m/mouseemu/mouseemu_0.15-8ubuntu3_i386.deb
e08504c477baefaaa39ba08811ccc12b  ./pool/main/i/isdnutils/ipppd_3.12.20071127-0ubuntu1_i386.deb
eb3e623b83925dfeb9ebd2096ac7740f  ./pool/main/i/isdnutils/capiutils_3.12.20071127-0ubuntu1_i386.deb
d1b95dae7c8d91cd306aa4364974706a  ./pool/main/i/isdnutils/libcapi20-dev_3.12.20071127-0ubuntu1_i386.deb
6672c8daabc06068666bc0f6dc64701d  ./pool/main/i/isdnutils/libcapi20-3_3.12.20071127-0ubuntu1_i386.deb
fe7fc75775679bcc235dbbb5e0515826  ./pool/main/i/isdnutils/pppdcapiplugin_3.12.20071127-0ubuntu1_i386.deb
2a48188c55d37ebb1adc1fd8e20ea054  ./pool/main/i/isdnutils/isdnutils-xtools_3.12.20071127-0ubuntu1_i386.deb
edce480ca7ee1e7866936049cb1bbc6a  ./pool/main/i/isdnutils/isdnutils-base_3.12.20071127-0ubuntu1_i386.deb
4b7c7c763306a72b369a45d39fbe272b  ./pool/main/f/fakeroot/fakeroot_1.9ubuntu1_i386.deb
e4a04b2f054b65169fd2c5a5e3cfa499  ./pool/main/p/pptp-linux/pptp-linux_1.7.0-2ubuntu2_i386.deb
7b6bf543b7ce805c931bc3e0a6b7ab5e  ./pool/main/p/patch/patch_2.5.9-4_i386.deb
037257b9ff5a2088fbd53ebd5e7eb000  ./pool/main/o/oem-config/oem-config_1.37_i386.deb
6721ca9cd810ff0d9bbdef1ceab948ae  ./pool/main/o/oem-config/oem-config-gtk_1.37_i386.deb
81f3469ce2479c9fa476fe4dd9995fd4  ./pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.8+svn1839+dfsg-2ubuntu4_i386.deb
cc40596f50c8da74bb24f91c47475c37  ./pool/main/l/linux-atm/libatm1_2.4.1-17.1build1_i386.deb
01fcd8a91cd31258cfcfee447b9c8d4d  ./pool/main/l/localechooser/localechooser-data_1.42ubuntu5_all.deb
00e0cbe33d51469a9022322d0b0354f7  ./pool/main/l/lupin/lupin-support_0.16_all.deb
f201b89d02de729103c94da16b303418  ./pool/main/l/linux/linux-libc-dev_2.6.24-16.30_i386.deb
e04cb7b27152cbb3cc3ad523b78da9d5  ./pool/main/t/timedate/libtimedate-perl_1.1600-9_all.deb
439013edf9427d7e9eba0926beffb14c  ./pool/main/s/setserial/setserial_2.17-44_i386.deb
a96aa69961f3ed80dd7a88fae1e28196  ./wubi.exe
d947a8bc3b84ce87570624873e94412c  ./README.diskdefines

```
I guess I'll just redownload.

---

### Post by danwood76 on 2008-05-22
You should be checking th md5 of the actual *.iso file.
If you look in that list you just posted the md5 is correct for wubi.exe so maybe your install CD is ok.

---

