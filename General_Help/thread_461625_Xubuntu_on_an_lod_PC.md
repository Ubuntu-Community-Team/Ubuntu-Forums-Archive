---
title: "Xubuntu on an lod PC"
date: 2007-06-01
forum: General Help
---

### Post by disco2000 on 2007-06-01
ok. I have burned Xubuntu 6.10 ISO on a DVD. I load my old laptop with it, it boots and then it tells me:

"Linux decompressing.OK  Loading the Kernel.
(17179569.1840001) ACPI: unable to find RSDP."

and then blank screen and nothing more happens. My laptop is an AMD K6 3D 333Mh with 128Mb of RAM and a Hard Drive of 3Gb.It presently runs Win98.


Any help would be welcome

Danny.

---

### Post by ryanVickers on 2007-06-01
Well, if you actually got windows running, then anything else should be easy!  Have you cured the common cold yet? :p

It sounds like there's something missing from the disk.  Are you sure it's supposed to be on a DVD?

---

### Post by disco2000 on 2007-06-01
Thanks for the response. You say:
"It sounds like there's something missing from the disk."

Like what? what do you mean??

---

### Post by ryanVickers on 2007-06-01
It could have burned incorrectly, or the download itself might have gotten messed up, nut most likely the problem is neither of these; I was just suggesting that possibly it was burned incorrectly, like at a speed to great for the device/disk, and I thought they were CD's not DVD's?

---

### Post by disco2000 on 2007-06-01
I wrote that I burned a DVD when it was actually a CD but I doubt very much that it has anything to do with it.

Danny

---

### Post by disco2000 on 2007-06-01
Yes I made sure that I burned the CD at half the speed . But when I open the CD with Windows I see this folder that says md5sum and it has all these checks. Which one would I use to verify it with md5sum Checker??

danny

5dd4df6cccf75b1e1df442d2c70fa4b5  ./dists/dapper/main/binary-i386/Release
2fd0a18a16e16d081888f20224c37f20  ./dists/dapper/main/binary-i386/Packages
59b5524f0721b59b81e6bf23f7b8c2ba  ./dists/dapper/main/binary-i386/Packages.gz
45d36759cbb14292b44498dac9262247  ./dists/dapper/restricted/binary-i386/Release
609969c561e265d61f37a0a43c407267  ./dists/dapper/restricted/binary-i386/Packages
8261b5e67219174e8f6b8f801f8567a9  ./dists/dapper/restricted/binary-i386/Packages.gz
b88ec3421b69aee499fe8b2430092cc2  ./dists/dapper/Release
ee4fce0e6f6a110d4a01d09d0552ddeb  ./dists/dapper/Release.gpg
d192e72866a431932d92633786bbcb63  ./.disk/info
f0f9d9afa7854b3d37b785469c8e73ef  ./README.diskdefines
cd8aa5e7fa11b1362ef1869ac6b1aa56  ./pics/blue-lowerleft.png
9e18ae797773b2677b1b7b86e2aff28d  ./pics/blue-lowerright.png
a025c46d5daf227adfda51d81eb90f25  ./pics/blue-upperleft.png
461cbc7ff94fdea8008cab34b611abb8  ./pics/blue-upperright.png
16ff51c168405e575d32bae001f280e4  ./pics/debian.jpg
92091902d3ca753bb858d4682b3fc26b  ./pics/logo-50.jpg
0730e775a72519aaa450a3774fca5f55  ./pics/red-lowerleft.png
20d4bdecfa6d980d663fb5b93d37a842  ./pics/red-lowerright.png
cde56251d6cae5214227d887dee3bab7  ./pics/red-upperleft.png
3c129ee10f707bd9dec10209d28840eb  ./pics/red-upperright.png
5a93a111efeb5305075c5e077715b6cd  ./install/sbm.bin
8d6a2a045d7c0f48fe2e088f3f87b6ce  ./install/README.sbm
200e9354c8202baaa9f0704e2870647d  ./install/mt86plus
9f9cfcd961d893878b07fb58df76ad25  ./preseed/ltsp.seed
bd16198f4dc9ffd9d00837b652451eea  ./preseed/server.seed
ec8df283d19ec30535ac099ccec57663  ./preseed/xubuntu.seed
7fef182abb0cbe2eda432111d700fde4  ./pool/restricted/l/linux-meta/avm-fritz-firmware_2.6.15.24_i386.deb
f874584e73b7f4feb27df781a8e78a62  ./pool/restricted/l/linux-restricted-modules-2.6.15/avm-fritz-firmware-2.6.15-26_3.11+2.6.15.11-3_i386.deb
e4c3406397f365f35c439a77c24d9cba  ./pool/restricted/d/drdsl/drdsl_1.2.0-0ubuntu1_i386.deb
4499747cec6bb1463f7b85144d59f466  ./pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb
f1d288db8b9f62b11e182cef430c6288  ./pool/main/b/bpalogin/bpalogin_2.0.2-6ubuntu1_i386.deb
a08a59d3a8ed6c952300762bcb23ebb5  ./pool/main/b/build-essential/build-essential_11.1_i386.deb
6e02edd9ff18f573a3c7d542ddf1556c  ./pool/main/i/isdnutils/capiutils_3.8.2005-12-06-2ubuntu4_i386.deb
fd168242e971e331bb136565c253d235  ./pool/main/i/isdnutils/ipppd_3.8.2005-12-06-2ubuntu4_i386.deb
c44a28783d0b0c87358ac3a58bc43719  ./pool/main/i/isdnutils/isdnutils-base_3.8.2005-12-06-2ubuntu4_i386.deb
42428de62d09cae8d76c1f261995e409  ./pool/main/i/isdnutils/isdnutils-xtools_3.8.2005-12-06-2ubuntu4_i386.deb
6f5e3d7b5f6fe04250c98edb2acc64fb  ./pool/main/i/isdnutils/libcapi20-3_3.8.2005-12-06-2ubuntu4_i386.deb
104bf0d589c9d89b130623e47a8af7a9  ./pool/main/i/isdnutils/libcapi20-dev_3.8.2005-12-06-2ubuntu4_i386.deb
cdd973748ea0b3a155b07fa2c0ce455e  ./pool/main/i/isdnutils/pppdcapiplugin_3.8.2005-12-06-2ubuntu4_i386.deb
750279e9a9c5213dcbf8de7ff325768f  ./pool/main/g/gcc-defaults/cpp_4.0.3-1_i386.deb
aff505809394fa97ca118fbe2121020d  ./pool/main/g/gcc-defaults/g++_4.0.3-1_i386.deb
dfc1bcea4b13e5d28668f70bc0a1cb67  ./pool/main/g/gcc-defaults/gcc_4.0.3-1_i386.deb
dadba9c2a61126808fce35b16adf7b0f  ./pool/main/g/gcc-4.0/cpp-4.0_4.0.3-1ubuntu5_i386.deb
af1eee74c842df453d3daada62f4d48e  ./pool/main/g/gcc-4.0/g++-4.0_4.0.3-1ubuntu5_i386.deb
ffd5a01012a81269443ca057a96ee4ba  ./pool/main/g/gcc-4.0/gcc-4.0_4.0.3-1ubuntu5_i386.deb
6f49dc0b5e5a066996c18afbdf316efd  ./pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb
8a9f57ed51a49e8e7ea1619e9bf3f440  ./pool/main/g/glibc/libc6-dev_2.3.6-0ubuntu20_i386.deb
849d2ca5696d0f6eab86579f3bd1c8a6  ./pool/main/d/dpkg/dpkg-dev_1.13.11ubuntu6_all.deb
5ac1b117264e2d2115dcf4a1f3a99cbf  ./pool/main/e/eagle-usb/eagle-usb-data_2.1.1-2_all.deb
05a7c8d250f3920d54f52df8577542c4  ./pool/main/e/eagle-usb/eagle-usb-utils_2.1.1-2_i386.deb
21edfd3c8939d2f13b6146aff1a1ec53  ./pool/main/f/fakeroot/fakeroot_1.5.6ubuntu2_i386.deb
245f16de0196793b159380d0f9182334  ./pool/main/l/linux-atm/libatm1_2.4.1-17_i386.deb
936d19f8917ae5e05224390595e1ca2e  ./pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26_2.6.15-26.46_i386.deb
2962068982a4a35fc449914e453500d5  ./pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26-386_2.6.15-26.46_i386.deb
69393ab0cbca5db79039ed7ef8fb5808  ./pool/main/l/linux-meta/linux-headers-386_2.6.15.24_i386.deb
af9814c9f8d5e5aa538530a15ac11127  ./pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu18_i386.deb
38cec2067384ede773f1b2111aba182c  ./pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.3-1ubuntu7_i386.deb
984a347383e53e343b4566aa4641ca24  ./pool/main/m/make/make_3.80+3.81.b4-1_i386.deb
15bf250f0a1114686655232175339cc2  ./pool/main/n/ndiswrapper/ndiswrapper-utils_1.8-0ubuntu2_i386.deb
063e72260c39f0cb85ca8743e9e7a72e  ./pool/main/p/pptp-linux/pptp-linux_1.7.0-1ubuntu1_i386.deb
e9c14f4a5a1a7f930d676d335b326fb0  ./pool/main/s/setserial/setserial_2.17-43_i386.deb
48f6c0c86ae16fb04703cba2a53ef24a  ./casper/filesystem.squashfs
3866b4df0132d96fa88a0a798617f683  ./casper/initrd.gz
3cbe8e5ffdc5a7e17a7e8cb49dba4449  ./casper/filesystem.manifest
02a0ce9681ca575607a4e3b15b7879b6  ./casper/filesystem.manifest-desktop
618e4c8dc4bf3080ddee01c4dfd48bd9  ./casper/vmlinuz

---

### Post by ryanVickers on 2007-06-01
I'm not quite sure what you mean by any of this, checks, ms5sum, etc.

---

### Post by disco2000 on 2007-06-01
md5sum is an application to verify the integrity of the Xubuntu download one does. With Ubuntu, every download you do, you have a haxadecimal number associated with it that you enter in the md5sum hecker application and what it does is compare the 2 numbers to make sure the integrity of the CD ISO is ok.

But as you can see, I am not sure which hexa number to type into the md5sum application.

---

### Post by southernman on 2007-06-02
> **disco2000 said:**
> md5sum is an application to verify the integrity of the Xubuntu download one does. With Ubuntu, every download you do, you have a haxadecimal number associated with it that you enter in the md5sum hecker application and what it does is compare the 2 numbers to make sure the integrity of the CD ISO is ok.

But as you can see, I am not sure which hexa number to type into the md5sum application.
That is because the md5 number you need to verify will be found where you d/l'ed the iso from... not on the disk.

Amazingly you knew (sorta) what the md5sums was.

---

### Post by Cable on 2007-06-02
If you would like to check the md5sum of your CD, you'll want to look at [this]("https://help.ubuntu.com/community/HowToMD5SUM") wiki page.  It explains how to do so using Linux, OS X, or Windows.

You'll also want to obtain what the md5sum of the CD *should* be from wherever you downloaded it.  For example, if you got it [here]("http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/"), you need to download the very first file (called "MD5SUMS") as it contains the md5sum for each image available on that page.  Then, use whatever method you want from the wiki page I linked earlier, and compare it to the corresponding md5sum listed in the file you downloaded.  If they don't match up, you need to download the image again.

Also, when you boot from the CD, the very first menu will have an option to check the disc's integrity (provided that you have a LiveCD as opposed to the alternate CD).  Try this as well, as the CD has a self test on it.  If this test fails, you need to download the image again.

---

### Post by disco2000 on 2007-06-02
Actually, I don't need to check md5sum. It's been done. My real problem is the following:

"ok. I have burned Xubuntu 6.10 ISO on a CD. I load my old laptop with it, it boots and then it tells me:

"Linux decompressing.OK Loading the Kernel.
(17179569.1840001) ACPI: unable to find RSDP."

and then blank screen and nothing more happens. My laptop is an AMD K6 3D 333Mh with 128Mb of RAM and a Hard Drive of 3Gb.It presently runs Win98.


Any help would be welcome

---

### Post by ryanVickers on 2007-06-02
Well, I think that's it for me on this post, you seem to be in good hands, and we were getting a bit over my head in this area anyways.  Sorry if I couldn't be of much use :(

---

### Post by happy-and-lost on 2007-06-03
The CD is fine. You probably just need to disable ACPI. Do this by adding *acpi=off* to the boot options on the liveCD.

It may be a bit heavy for those specs. You could try a Debian netinstall.

---

### Post by Ptero-4 on 2007-12-12
Or maybe a fluxbuntu install.

---

### Post by louieb on 2007-12-12
> **disco2000 said:**
> ... My laptop is an AMD K6 3D 333Mh with 128Mb of RAM and a Hard Drive of 3Gb.It presently runs Win98.
Don't believe any of the Ubuntu flavor Live CDs will run in 128MB ram. 
Even xUbuntu although lighter that the other two still needs 192MB. 
Your going to need the text installer (alternate CD).
My new favorite light weight distro. [PCFluxboxOS:]("http://pcfluxboxos.wikidot.com/")

---

