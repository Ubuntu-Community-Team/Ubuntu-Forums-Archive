---
title: "Wubi does not run"
date: 2013-04-16
forum: General Help
---

### Post by seacher on 2013-04-16
I have already formated 40GB of memory in Windows 8 for a Ubuntu 11.04 install and tried installing the 12.04 version as well.

Both give me the same log message:
```

04-16 01:58 INFO   root: === wubi 12.10 rev273 ===
04-16 01:58 DEBUG  root: Logfile is c:\users\aaron\appdata\local\temp\wubi-12.10-rev273.log
04-16 01:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Aaron\\Downloads\\wubi.exe"']
04-16 01:58 DEBUG  CommonBackend: data_dir=C:\Users\Aaron\AppData\Local\Temp\pyl1231.tmp\data
04-16 01:58 DEBUG  WindowsBackend: 7z=C:\Users\Aaron\AppData\Local\Temp\pyl1231.tmp\bin\7z.exe
04-16 01:58 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-16 01:58 DEBUG  CommonBackend: Fetching basic info...
04-16 01:58 DEBUG  CommonBackend: original_exe=C:\Users\Aaron\Downloads\wubi.exe
04-16 01:58 DEBUG  CommonBackend: platform=win32
04-16 01:58 DEBUG  CommonBackend: osname=nt
04-16 01:58 DEBUG  CommonBackend: language=en_US
04-16 01:58 DEBUG  CommonBackend: encoding=cp1252
04-16 01:58 DEBUG  WindowsBackend: arch=amd64
04-16 01:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\Aaron\AppData\Local\Temp\pyl1231.tmp\data\isolist.ini
04-16 01:58 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-16 01:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-16 01:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-16 01:58 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-16 01:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-16 01:58 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-16 01:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-16 01:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-16 01:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-16 01:58 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-16 01:58 DEBUG  WindowsBackend: Fetching host info...
04-16 01:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-16 01:58 DEBUG  WindowsBackend: windows version=vista
04-16 01:58 DEBUG  WindowsBackend: windows_version2=Windows 8
04-16 01:58 DEBUG  WindowsBackend: windows_sp=None
04-16 01:58 DEBUG  WindowsBackend: windows_build=9200
04-16 01:58 DEBUG  WindowsBackend: gmt=-6
04-16 01:58 DEBUG  WindowsBackend: country=US
04-16 01:58 DEBUG  WindowsBackend: timezone=America/Chicago
04-16 01:58 DEBUG  WindowsBackend: windows_username=Aaron
04-16 01:58 DEBUG  WindowsBackend: user_full_name=Aaron
04-16 01:58 DEBUG  WindowsBackend: user_directory=C:\Users\Aaron

```
Are there any others that have had this problem and can help me out?

I have searched countless hours on web and forums and cannot find any information related to this issue.

---

### Post by Shpitzick on 2013-04-16
Don't use Wubi. It will be removed along with the next version of Ubuntu.

---

### Post by seacher on 2013-04-16
Thank you for the heads up.

Have you installed Ubuntu on a Windows 8 system before?

---

### Post by Cheesemill on 2013-04-16
Did Windows 8 come pre-installed on your machine? If so then it uses GPT disk partitioning which isn't compatible with Wubi.

There is currently no way to get Wubi to work on a GPT partitioned disk and there probbaly won't ever be one, as Wubi has lost all of its developers and so far no one else has stepped in to take over.

---

### Post by seacher on 2013-04-16
I already partitioned 32GB of space to a new drive but cannot get the downloaded disk to work.  So is instaling a stand alone Ubuntu the only way?

---

### Post by Cheesemill on 2013-04-16
Yes it is.

What errors are you getting when trying to install from a DVD/USB?

Did you check the [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") of your downloaded iso file to make sure that it wasn't corrupt?

How did you create the DVD/USB? Instructions can be found here...
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by seacher on 2013-04-16
The problem I encounter is as simple as nothing happens.

It goes through the entire install process and when I restart my computer it goes straight to Windows 8.  I donot even get the option to choose an OS.

The DVD was downloaded from Ubuntu.com so I believe it is a reliable version and has been used and installed properly on other computers.

I will check the MD5SUM still though.

---

### Post by seacher on 2013-04-16
The file does not seem to be corrupt.

Here is what it says:

4aa66b9da42e1a3f667ab0c8009cc801  ./casper/initrd.lz
b0f3dbfb5c3e00e6ec898ea90767c6d5  ./casper/filesystem.manifest
c2b76c30f0c5b7db3f210e85746ac36d  ./casper/filesystem.manifest-desktop
e2ebd3e79dd9aee744075c345fbafee6  ./casper/filesystem.squashfs
45a7bee6779b8cd75634a70fd7a566dd  ./casper/vmlinuz
2f9fc6b7f4cbb76081ba73a91332ac9c  ./casper/filesystem.size
e411086e5451ebef51b01f63ea546d32  ./dists/natty/Release
37b8f7ae07531c68d575ac5d2089d33e  ./dists/natty/restricted/binary-amd64/Packages.gz
a98ce953e8230e5570d381acc2fb03b9  ./dists/natty/restricted/binary-amd64/Release
9497d6a920e2662650289b5e53711748  ./dists/natty/Release.gpg
20e8263f5ed6dc0c4005a970d3bb89b0  ./dists/natty/main/binary-amd64/Packages.gz
b04fa0bb77c19ba1f9de5ec8756db9c5  ./dists/natty/main/binary-amd64/Release
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
24b776751b2279b018a3aa472e9d1d5f  ./.disk/casper-uuid-generic
8c68254b7ffc1d3933aa98c6291c9880  ./.disk/release_notes_url
728cb968a88534e0c50a9d99621f13eb  ./.disk/cd_type
d41d8cd98f00b204e9800998ecf8427e  ./.disk/base_installable
579d27eac9e7479f815397355141dc0f  ./.disk/info
bd0bc5c70877e6ecc8703f179c14d016  ./efi/boot/bootx64.efi
62bf7841341b7faa69062fd0095af116  ./autorun.inf
98575bdc69b476cbe7401ca22b4d97d2  ./install/mt86plus
fe6fa04c981a9d3835f12f27bd6dda71  ./usb-creator.exe
24ec176894c781355f9ccb08ba69919e  ./preseed/ubuntu.seed
0391854d1af5a015a667f29fa0442e78  ./preseed/ltsp.seed
7e3aa6d1958baf72d369392fdb175486  ./preseed/cli.seed
1899fdecd74446561f595e68f7f06064  ./pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3_amd64.deb
99f9c505903bb3e088e6610cd2894934  ./pool/restricted/s/sl-modem/sl-modem-daemon_2.9.11~20100718-4_amd64.deb
58bca8098cef15ee2cbe9303a229e81d  ./pool/main/n/ndisgtk/ndisgtk_0.8.5-1_amd64.deb
9d492114681c47fe1efecbbb7522e2c3  ./pool/main/n/ndiswrapper/ndiswrapper-common_1.56+r2729-1_all.deb
314139e485c3fc0f89b5ec662f1f9db0  ./pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56+r2729-1_amd64.deb
550bc581881e884e8e29e59f1a22a620  ./pool/main/b/b43-fwcutter/b43-fwcutter_013-3_amd64.deb
bd24229d377f21714c53076630617074  ./pool/main/d/dkms/dkms_2.1.1.2-5ubuntu1_all.deb
7c807453dc06ab3730bd4b500a984f03  ./pool/main/g/grub2/grub-efi-amd64_1.99~rc1-13ubuntu3_amd64.deb
4115992f77bcd1c761957672e6d71192  ./pool/main/g/grub2/grub-efi_1.99~rc1-13ubuntu3_amd64.deb
d378e80386da62793fb55a6c3289fbf2  ./pool/main/u/ubiquity-slideshow-ubuntu/oem-config-slideshow-ubuntu_40_all.deb
fa5a54d2bfa2a8caa0ef4cd75b941a63  ./pool/main/u/ubiquity/oem-config_2.6.10_all.deb
36006aa99c62cd9a87080648b9867fc0  ./pool/main/u/ubiquity/oem-config-gtk_2.6.10_all.deb
fd7013ef5ff7450da60d9db05e5563e1  ./pool/main/m/mouseemu/mouseemu_0.16-0ubuntu7_amd64.deb
7ff1150b2ca5c8df353d9138b3cd4a09  ./pool/main/w/wvstreams/libwvstreams4.6-base_4.6.1-1ubuntu1_amd64.deb
cc32a00561be337fdaa49a621fec6756  ./pool/main/w/wvstreams/libwvstreams4.6-extras_4.6.1-1ubuntu1_amd64.deb
5770494093d6569f7e0f8870e187be65  ./pool/main/w/wvstreams/libuniconf4.6_4.6.1-1ubuntu1_amd64.deb
3393ede11006bf6555eb67746c42a636  ./pool/main/w/wvdial/wvdial_1.61-2_amd64.deb
4b665a7bdc158e3d8001d0c064ae18b7  ./pool/main/e/eglibc/libc6-i386_2.13-0ubuntu13_amd64.deb
bc91d21ad8a0728932f31a5d5c7f4bef  ./pool/main/e/efibootmgr/efibootmgr_0.5.4-2ubuntu1_amd64.deb
264f7e54ca1af1ac75bee5e00d13956d  ./pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.9+dfsg-4_amd64.deb
3aafaec3951819c3e353e6fd635bc289  ./pool/main/l/linux-wlan-ng/linux-wlan-ng-doc_0.2.9+dfsg-4_all.deb
b6acf68e1be5e4d910df278911d18300  ./pool/main/l/lupin/lupin-support_0.34_amd64.deb
f5f782f7c93e8cb1ebfcf38cf53afec7  ./pool/main/a/alsa-lib/lib32asound2_1.0.24.1-0ubuntu5_amd64.deb
fb0099fca94cbe437b97e483ebc0b9e6  ./pool/main/s/setserial/setserial_2.17-45.3ubuntu1_amd64.deb
5ffc1945bd865e08961d5bef2c4010e1  ./boot/grub/grub.cfg
e18e311de072fdb8cd481d2b273940bb  ./boot/grub/font.pf2
c04b187ff01e1a29d445eddb4f9a53f7  ./boot/grub/x86_64-efi/trig.mod
4c429a180c0e2a45ae4f1882e41f1fac  ./boot/grub/x86_64-efi/grub.cfg
989de98a59951f5b93eab321d439862a  ./boot/grub/x86_64-efi/scsi.mod
269326a0b233552b124a320bb56deb01  ./boot/grub/x86_64-efi/setpci.mod
e8b543c800093460a7ce466144c5d090  ./boot/grub/x86_64-efi/mdraid1x.mod
24c54dc5f440e798ac506c4d5d14121c  ./boot/grub/x86_64-efi/ext2.mod
9f29004320dfcd04afa7f0e227336951  ./boot/grub/x86_64-efi/part_gpt.mod
3603c9d8d0235a2ef184aad79a4b5da6  ./boot/grub/x86_64-efi/usbserial_pl2303.mod
944836276e2ae235c50cb57ae89256b3  ./boot/grub/x86_64-efi/probe.mod
9285225edcfdb7f17769a9929a1e12d9  ./boot/grub/x86_64-efi/gcry_blowfish.mod
cac355ebd790268ba6be5e9b11ff521e  ./boot/grub/x86_64-efi/gcry_whirlpool.mod
ffc7f0a1bbb4a81bd8d168866bf089ec  ./boot/grub/x86_64-efi/efi_gop.mod
4c1f6a3e725ca4ec4ccfda4f9cec2a5c  ./boot/grub/x86_64-efi/cs5536.mod
7a390013d68b283fd019a0334f314b53  ./boot/grub/x86_64-efi/fat.mod
9fa631e3c80b7f3068a2a790f9fbbdbe  ./boot/grub/x86_64-efi/gcry_md4.mod
9224bbbb373cd21d1dc7b756d9777dc2  ./boot/grub/x86_64-efi/jpeg.mod
caa2cd35438c0ae44f65c0cca65caf68  ./boot/grub/x86_64-efi/cpio.mod
54af0cffbc6fc76e177a37c2621498c3  ./boot/grub/x86_64-efi/loadbios.mod
75fc972bc0b5686f368dfe92eb67e824  ./boot/grub/x86_64-efi/halt.mod
507893a22281fa366795d24fc889bb2e  ./boot/grub/x86_64-efi/gcry_crc.mod
08690aae4289279d6ac592feb29b5ec0  ./boot/grub/x86_64-efi/elf.mod
a8fc11ace127e3fe10c211228eeeae4a  ./boot/grub/x86_64-efi/setjmp.mod
6210a7dc8764953aee047b3918b574b2  ./boot/grub/x86_64-efi/part_amiga.mod
adbf79c654781cab2fa5ca7d1277bfc2  ./boot/grub/x86_64-efi/terminal.lst
95541c19fcda579b710257a24d1045c3  ./boot/grub/x86_64-efi/true.mod
ee21df5a8abae03f00db7cb996e4e8a4  ./boot/grub/x86_64-efi/crypto.mod
cb0b8e7ef4fc3ca1ac022a97b3d6f51b  ./boot/grub/x86_64-efi/pci.mod
9656bee9563d79a43bed6822b74ff1c0  ./boot/grub/x86_64-efi/ohci.mod
0897ddc8ae26b9cd9c4a09410515b23c  ./boot/grub/x86_64-efi/ntfs.mod
1af27cc55772b9a6f15d4a6d3164e243  ./boot/grub/x86_64-efi/hfs.mod
826d54b4321f5f238947a90014c31d4d  ./boot/grub/x86_64-efi/msdospart.mod
335c4fcfd67fa33130010dba3fee1147  ./boot/grub/x86_64-efi/read.mod
078eae0a2fcc8ba7a6d651326c606294  ./boot/grub/x86_64-efi/command.lst
7d86acc3d68833f22603dc5859e8ebdc  ./boot/grub/x86_64-efi/video.lst
3d0b692ecd727d713554523069d22e9b  ./boot/grub/x86_64-efi/dm_nv.mod
1ee8f5b487628c9c3c0ade2460fa0599  ./boot/grub/x86_64-efi/tga.mod
9713dd2e582418e4f455a6194b781134  ./boot/grub/x86_64-efi/usbserial_common.mod
0c40cc155e6ed8dba8bea9233ea2891c  ./boot/grub/x86_64-efi/usb_keyboard.mod
f9f4ab8d3468b40bf3bbc08f42517fe6  ./boot/grub/x86_64-efi/loadenv.mod
4822484cf918cc91f04afbc5c3718247  ./boot/grub/x86_64-efi/usbms.mod
fac1002079aa070faae1ed1ca9037880  ./boot/grub/x86_64-efi/ufs2.mod
b7351baf359c514b17e3660c2509680a  ./boot/grub/x86_64-efi/terminal.mod
7b0e3d3e08755f1722d012195e5be463  ./boot/grub/x86_64-efi/reiserfs.mod
a293fc06efde43f39791d7c7801cd7e0  ./boot/grub/x86_64-efi/hashsum.mod
340aba63078f29d55a66c2d9fcbf75c5  ./boot/grub/x86_64-efi/sleep.mod
b3e44334db5f71eb043bca55bc11af2b  ./boot/grub/x86_64-efi/minix2.mod
84c3362a0e93d39ec6e78fb45e2e5c00  ./boot/grub/x86_64-efi/videotest.mod
e529675a90cbb114c788a89a2959ac45  ./boot/grub/x86_64-efi/bitmap.mod
94088f18d9bc232114b45b731b5d6ab6  ./boot/grub/x86_64-efi/gcry_sha512.mod
da8a6983e88bfe1571abada886b0957c  ./boot/grub/x86_64-efi/xnu.mod
b79b0014f5237e5342896a2b66c98706  ./boot/grub/x86_64-efi/xnu_uuid.mod
b1c89379dc9209e51066d133c0fa19a5  ./boot/grub/x86_64-efi/ls.mod
ebcdf03ad54b6852ce255559021e61b3  ./boot/grub/x86_64-efi/test_blockarg.mod
19f912f78daa28348944c0047ed870c8  ./boot/grub/x86_64-efi/lsacpi.mod
aca71dd9ea780ad5257c5691725979b5  ./boot/grub/x86_64-efi/usbserial_ftdi.mod
a34a5fcd3a990a38f9223a14f6420cf3  ./boot/grub/x86_64-efi/iorw.mod
deeff8e530e2036d12d5f6777069b5b1  ./boot/grub/x86_64-efi/relocator.mod
4f08a06f93d015cc9df25f682658dc57  ./boot/grub/x86_64-efi/video_cirrus.mod
f50a978ad74c7d13f97bd9c5b4c38853  ./boot/grub/x86_64-efi/blocklist.mod
75634add58ce0babe697e2fbf36ca420  ./boot/grub/x86_64-efi/password.mod
de304e343c8300896c5340e77171a7d5  ./boot/grub/x86_64-efi/datetime.mod
e7574651c752a2e5559e27f430a9121d  ./boot/grub/x86_64-efi/video.mod
768a78bc7b81977f10fc827a846c296a  ./boot/grub/x86_64-efi/usb.mod
400b311a3280446f0fff0cc1f7f53233  ./boot/grub/x86_64-efi/multiboot.mod
0410541dbf0fa99372c5d1fcfb139c19  ./boot/grub/x86_64-efi/test.mod
662b086fd761741ebfcb9a3d11ba85cd  ./boot/grub/x86_64-efi/mdraid09.mod
343f2cd9f6be94063d66da3a0448d7ab  ./boot/grub/x86_64-efi/uhci.mod
461681d47b437d588f22089950557068  ./boot/grub/x86_64-efi/usbtest.mod
983c3217be63fe49181f55628823eafe  ./boot/grub/x86_64-efi/crypto.lst
059e91d6e07d9c8b356e7feaf3642fc6  ./boot/grub/x86_64-efi/lsefisystab.mod
a0a58f8ffd8a62eadd4aea08548e5301  ./boot/grub/x86_64-efi/gfxterm.mod
f57535cf5e99c3f4c20fbfe4b7c5735d  ./boot/grub/x86_64-efi/testload.mod
274bd58747cfa95c5eda1e6cd54cb4b8  ./boot/grub/x86_64-efi/xzio.mod
594c14f5bb655c3c7be664db8f611803  ./boot/grub/x86_64-efi/datehook.mod
93b76ea3434f680839ba6e77c50a77db  ./boot/grub/x86_64-efi/fixvideo.mod
b308c14b1f9f5da0eeecfef4ea881d90  ./boot/grub/x86_64-efi/echo.mod
29ee5cdd86b0113afa27698aad5bc199  ./boot/grub/x86_64-efi/loopback.mod
ee7c9b3af7b16d5fc534e1085272cb49  ./boot/grub/x86_64-efi/gcry_serpent.mod
36663448d013d665b06f7d0b129af5cb  ./boot/grub/x86_64-efi/gcry_arcfour.mod
9c1f8c3515dc26862e8dcfea93391b64  ./boot/grub/x86_64-efi/video_bochs.mod
28780ceb571a2ea7f931296c95ab1004  ./boot/grub/x86_64-efi/minicmd.mod
59a053648c0ec637886f0b8631131a5d  ./boot/grub/x86_64-efi/ata_pthru.mod
7f34baae2b89d77bd0eaa67122d83e8a  ./boot/grub/x86_64-efi/gcry_tiger.mod
93a7f6a226dd0d9dccf193d76a233a12  ./boot/grub/x86_64-efi/gcry_rfc2268.mod
0c614cfbdf6584ac60dc60c65bbbbe3c  ./boot/grub/x86_64-efi/gettext.mod
e9adfcc4a4fc7ab2db093bf430cd15c8  ./boot/grub/x86_64-efi/gcry_seed.mod
e35d3c94597c4cd55d5966617a38ea23  ./boot/grub/x86_64-efi/udf.mod
1400519ddb817e2086ba1f8d22dcdc2a  ./boot/grub/x86_64-efi/font.mod
6a298868a7bab26e9c8aaf5c6d6088de  ./boot/grub/x86_64-efi/png.mod
e988470d893464af1836c1a66b095e34  ./boot/grub/x86_64-efi/hexdump.mod
70e24c1660d9e8ec86821c751c4c64b4  ./boot/grub/x86_64-efi/gzio.mod
1027d059cb8773594076c7314c32cbf6  ./boot/grub/x86_64-efi/gcry_twofish.mod
7050f0f2ff43386cd4da89098a1b3c9a  ./boot/grub/x86_64-efi/help.mod
6fde65788901f2f6639fe8d6d299867a  ./boot/grub/x86_64-efi/bufio.mod
4f76680031780ccd77c26b06c0e16ac0  ./boot/grub/x86_64-efi/btrfs.mod
d622743e3bd36eac375482f2913ebe56  ./boot/grub/x86_64-efi/partmap.lst
53b46ac90862674c1174cc1bb9438a4e  ./boot/grub/x86_64-efi/gptsync.mod
a4477de49f6aa94cc0565a981da1f73a  ./boot/grub/x86_64-efi/appleldr.mod
433f90993ab66ac297f89d8580888ee2  ./boot/grub/x86_64-efi/lsmmap.mod
3b8f0eb22c6b0faff30dae646ea962e9  ./boot/grub/x86_64-efi/cpuid.mod
9cd63e3092b71faedc89422de5979591  ./boot/grub/x86_64-efi/part_msdos.mod
3ea19d9bcf55ad87a93998328ab8a755  ./boot/grub/x86_64-efi/hfsplus.mod
34a161f5bd486a5e9dc070c46acd6038  ./boot/grub/x86_64-efi/at_keyboard.mod
0757dff9dfd10ba80fe17bb90360609c  ./boot/grub/x86_64-efi/part_acorn.mod
1c1c45c90e66c4b990e5a653951c5c74  ./boot/grub/x86_64-efi/gcry_md5.mod
d8229ee2f153cff41db08deeea54995e  ./boot/grub/x86_64-efi/video_fb.mod
73dbf0bd99619a178fb8af64b35c3758  ./boot/grub/x86_64-efi/regexp.mod
43ed8c67ba55172b53c3feacee2bfb37  ./boot/grub/x86_64-efi/lssal.mod
511d917dcddedff8fed8645f8e2db7c1  ./boot/grub/x86_64-efi/squash4.mod
aa241527e1d70274fe6a6b5283203ba0  ./boot/grub/x86_64-efi/keystatus.mod
ce7f92bcc947e5ad98be4523b8c9005b  ./boot/grub/x86_64-efi/ufs1.mod
34381edb10ed92af1b4b4588f6f6ebd3  ./boot/grub/x86_64-efi/efi_uga.mod
61947998385faa9797b0f044a2c9c1c1  ./boot/grub/x86_64-efi/keylayouts.mod
95447483a081b5a9b8bd1992bb0bdc07  ./boot/grub/x86_64-efi/gcry_sha1.mod
b53d45b61ceef0b3b52774817120e02c  ./boot/grub/x86_64-efi/pbkdf2.mod
bcf2869934059801240c4a028a698057  ./boot/grub/x86_64-efi/part_apple.mod
e3c2167cb3d218e862c70ff0b0892f93  ./boot/grub/x86_64-efi/linux.mod
510925f5d599b6f99bede032c4a98c04  ./boot/grub/x86_64-efi/gfxmenu.mod
9f8f276fb0a8e6d0f49b8c2418facc26  ./boot/grub/x86_64-efi/bsd.mod
e9977d15cbfb675f42964e553162abc6  ./boot/grub/x86_64-efi/videoinfo.mod
bed9eae2d6ca3ccc0551510f440ce38c  ./boot/grub/x86_64-efi/mmap.mod
8251c2a7bcd77d81ec78215a928df033  ./boot/grub/x86_64-efi/play.mod
b90d125da249f7fcf41e809651ea5f5e  ./boot/grub/x86_64-efi/password_pbkdf2.mod
c6d0112a1039c5e350644f9d6d8634d0  ./boot/grub/x86_64-efi/bitmap_scale.mod
a2bf9dbedb3ce7ad00739b26f4339558  ./boot/grub/x86_64-efi/moddep.lst
938d80ebbc657f3530db49cde63127e1  ./boot/grub/x86_64-efi/jfs.mod
c1890337293aa5ecfe9232dbe291ea88  ./boot/grub/x86_64-efi/gcry_sha256.mod
4fc7079f036661987a38f6dd26e37c63  ./boot/grub/x86_64-efi/multiboot2.mod
d87e0481c1ab8f13a6fa4626272b5aed  ./boot/grub/x86_64-efi/xfs.mod
79980472378c3bc847154b741eefb7af  ./boot/grub/x86_64-efi/raid5rec.mod
5aaca51a9b88f4eb63aa41fbb1057446  ./boot/grub/x86_64-efi/gcry_cast5.mod
f3cd64d6ac767e6f340b2b9ddd7f6dc8  ./boot/grub/x86_64-efi/ata.mod
11e5e768a01e13c20688b7260695e96d  ./boot/grub/x86_64-efi/gcry_rmd160.mod
92264e99f8442315fbff95c78ee9cddd  ./boot/grub/x86_64-efi/aout.mod
148b9af5d01e8c43f32bd4145b1a2a49  ./boot/grub/x86_64-efi/serial.mod
4051ae0d602fd1a75e14b1b5c6ad39f5  ./boot/grub/x86_64-efi/lsefimmap.mod
36de23ae4034be5742f3814774840cc3  ./boot/grub/x86_64-efi/memrw.mod
cb638d12dc76ddbe55aa442a3b61cb95  ./boot/grub/x86_64-efi/cmp.mod
dfb42bdba7aba7b5f694be7e288b0ea5  ./boot/grub/x86_64-efi/hdparm.mod
f93ba57d1b1820af6b66b2837ff1be03  ./boot/grub/x86_64-efi/parttool.mod
f91b850837ac5c65a25e9ec9909d76d8  ./boot/grub/x86_64-efi/gcry_des.mod
3390e9263e42189866cb3a8feca8e2a8  ./boot/grub/x86_64-efi/lvm.mod
75742f8279095e61eeb3b221c5cbb6da  ./boot/grub/x86_64-efi/raid6rec.mod
0ae029c1d455fe58f0f452c96c0ea680  ./boot/grub/x86_64-efi/gcry_rijndael.mod
93531f2989d62c20a15c46f1f9eba8a1  ./boot/grub/x86_64-efi/ntfscomp.mod
3190a91d3075032543740d0998971d77  ./boot/grub/x86_64-efi/parttool.lst
42099a009106c63133c73f9796fad1f9  ./boot/grub/x86_64-efi/acpi.mod
1970ae489b6305b086e64aab112eff67  ./boot/grub/x86_64-efi/chain.mod
fff81d0e0f5d5fed97bac2168a9d8a68  ./boot/grub/x86_64-efi/boot.mod
eaf49dd877d5d88c383615c6ea4250cb  ./boot/grub/x86_64-efi/fs.lst
d805508f60fee067714b99eadff4d81c  ./boot/grub/x86_64-efi/reboot.mod
c630e74be4538d3c6d0e5ee38fd51c06  ./boot/grub/x86_64-efi/terminfo.mod
bee508f52828d80e9a77d8ea08360c55  ./boot/grub/x86_64-efi/raid.mod
265bb9c237b1dab86dc0fc8407ad5c8b  ./boot/grub/x86_64-efi/date.mod
046de913c3471f11d8be38da7702236c  ./boot/grub/x86_64-efi/part_sun.mod
fc49169512252cd99a579255164d8dc0  ./boot/grub/x86_64-efi/part_bsd.mod
3117e22fc0e2e7879fdf860909764eb0  ./boot/grub/x86_64-efi/cat.mod
71f107d6035161ef7b061f8178c73306  ./boot/grub/x86_64-efi/part_sunpc.mod
0d19db6438990e86ccb3ff8c6d73be08  ./boot/grub/x86_64-efi/gcry_camellia.mod
d4ef911e62430221397c229aafe999f9  ./boot/grub/x86_64-efi/lspci.mod
4a3deceb73996fb2fe95e40b46eeca03  ./boot/grub/efi.img
d0230badd879dcf9c6bd9f680c854b6f  ./boot/grub/loopback.cfg
39f805cae8be546747c492935ce0fcdd  ./wubi.exe
68a135bc59e3407cbcf86ea858e96f67  ./README.diskdefines

What other issues have you seen, because, I am at a loss.

---

### Post by Cheesemill on 2013-04-16
If this is a new machine with UEFI instead of BIOS then the installation procedure will vary from machine to machine. Check out the UEFI documentation here...

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by seacher on 2013-04-16
I will try this and let you know what comes of it.

Thanks for the help so far.

---

