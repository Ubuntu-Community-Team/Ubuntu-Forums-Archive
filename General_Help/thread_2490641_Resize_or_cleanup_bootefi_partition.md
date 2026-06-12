---
title: "Resize or cleanup /boot/efi partition"
date: 2023-09-10
forum: General Help
---

### Post by bomberb17 on 2023-09-10
I am triple-booting my system with one Windows 11 + two Ubuntu 22.04 OSes. However I somehow ended up getting warnings that my /boot/efi partition is full (probably because I migrated the disk from an HP laptop to a Dell laptop), and can no longer perform updates that require writing to the /boot/efi partition. Below is my partition configuration from GParted and the contents of the /boot/efi partition. I used GParted using a bootable USB and attempted to move the one partition after the /boot/efi and resize the /boot/efi, but I was getting warnings that my system would not be bootable and I could not even resize the /boot/efi, just move it. I didn't apply the changes in GParted to be safe. What is the best course of action here? Try to somehow grow the /boot/efi partition or try to clean some files up? (Not sure which though)

[https://i.imgur.com/hY8mvrS.png](https://i.imgur.com/hY8mvrS.png)

```
/boot/efi# ls -la -R
.:
total 7
drwx------ 4 root root 1024 Dec 31  1969  .
drwxr-xr-x 4 root root 4096 Sep 10 08:41  ..
drwx------ 7 root root 1024 Jul  8 09:03  EFI
drwx------ 4 root root 1024 May  2  2020 'System Volume Information'

./EFI:
total 7
drwx------ 7 root root 1024 Jul  8 09:03 .
drwx------ 4 root root 1024 Dec 31  1969 ..
drwx------ 2 root root 1024 May  2  2020 Boot
drwx------ 4 root root 1024 Jul  8 09:03 Dell
drwx------ 7 root root 1024 Jan  1  2019 HP
drwx------ 4 root root 1024 Mar 16 15:30 Microsoft
drwx------ 3 root root 1024 Mar 16 15:13 ubuntu

./EFI/Boot:
total 1868
drwx------ 2 root root   1024 May  2  2020 .
drwx------ 7 root root   1024 Jul  8 09:03 ..
-rwx------ 1 root root 960472 Apr  7 08:20 bootx64.efi
-rwx------ 1 root root  88296 Apr  7 08:20 fbx64.efi
-rwx------ 1 root root 860824 Apr  7 08:20 mmx64.efi

./EFI/Dell:
total 6
drwx------ 4 root root 1024 Jul  8 09:03 .
drwx------ 7 root root 1024 Jul  8 09:03 ..
drwx------ 3 root root 1024 Jul  1 18:22 Bios
drwx------ 2 root root 3072 Jul  8 09:03 logs

./EFI/Dell/Bios:
total 3
drwx------ 3 root root 1024 Jul  1 18:22 .
drwx------ 4 root root 1024 Jul  8 09:03 ..
drwx------ 2 root root 1024 Jul  1 18:22 Recovery

./EFI/Dell/Bios/Recovery:
total 2
drwx------ 2 root root 1024 Jul  1 18:22 .
drwx------ 3 root root 1024 Jul  1 18:22 ..
-rwx------ 1 root root    0 Jul  1 18:22 tmp.rcv

./EFI/Dell/logs:
total 6
drwx------ 2 root root 3072 Jul  8 09:03 .
drwx------ 4 root root 1024 Jul  8 09:03 ..
-rwx------ 1 root root  879 Jul  8 09:03 diags_current.xml
-rwx------ 1 root root  879 Jul  8 09:03 diags_previous.xml

./EFI/HP:
total 23
drwx------ 7 root root 1024 Jan  1  2019  .
drwx------ 7 root root 1024 Jul  8 09:03  ..
drwx------ 4 root root 1024 Mar 16 15:28  BIOS
drwx------ 2 root root 4096 Aug 13  2022  BIOSUpdate
drwx------ 5 root root 2048 May  3  2020  DEVFW
-rwx------ 1 root root 8390 Dec 13  2022  diw.efi
drwx------ 3 root root 1024 Jan  1  2019 'HP Support Framework'
drwx------ 2 root root 4096 Jan  1  2019  SystemDiags

./EFI/HP/BIOS:
total 4
drwx------ 4 root root 1024 Mar 16 15:28 .
drwx------ 7 root root 1024 Jan  1  2019 ..
drwx------ 2 root root 1024 Aug 13  2022 Current
drwx------ 2 root root 1024 Aug 13  2022 New

./EFI/HP/BIOS/Current:
total 16387
drwx------ 2 root root     1024 Aug 13  2022 .
drwx------ 4 root root     1024 Mar 16 15:28 ..
-rwx------ 1 root root 16777216 Aug 13  2022 086AA.bin
-rwx------ 1 root root      256 Aug 13  2022 086AA.sig

./EFI/HP/BIOS/New:
total 3
drwx------ 2 root root 1024 Aug 13  2022 .
drwx------ 4 root root 1024 Mar 16 15:28 ..
-rwx------ 1 root root  256 Aug 13  2022 086AA.s12

./EFI/HP/BIOSUpdate:
total 1858
drwx------ 2 root root    4096 Aug 13  2022 .
drwx------ 7 root root    1024 Jan  1  2019 ..
-rwx------ 1 root root 1433400 Jun 10  2020 BiosMgmt.efi
-rwx------ 1 root root     256 Jun 10  2020 BiosMgmt.s09
-rwx------ 1 root root     256 Jun 10  2020 BiosMgmt.s12
-rwx------ 1 root root     256 Jun 10  2020 BiosMgmt.s14
-rwx------ 1 root root  443904 May 29  2020 CryptRSA.efi
-rwx------ 1 root root   16292 Aug 13  2022 HpBiosUpdate.log

./EFI/HP/DEVFW:
total 580
drwx------ 5 root root   2048 May  3  2020 .
drwx------ 7 root root   1024 Jan  1  2019 ..
drwx------ 2 root root   1024 May  3  2020 Current
-rwx------ 1 root root 141168 Dec 27  2021 DevFwUpdate32.efi
-rwx------ 1 root root    256 Dec 27  2021 DevFwUpdate32.s12
-rwx------ 1 root root 149200 Dec 27  2021 DevFwUpdate.efi
-rwx------ 1 root root    256 Dec 27  2021 DevFwUpdate.s12
-rwx------ 1 root root 139320 Dec 27  2021 HpDevFwUpdate32.efi
-rwx------ 1 root root    256 Dec 27  2021 HpDevFwUpdate32.s12
-rwx------ 1 root root 147096 Dec 27  2021 HpDevFwUpdate.efi
-rwx------ 1 root root    256 Dec 27  2021 HpDevFwUpdate.s12
drwx------ 2 root root   1024 May  3  2020 New
drwx------ 2 root root   1024 May  3  2020 Previous
-rwx------ 1 root root   2112 Dec 27  2021 ReadMe.txt
-rwx------ 1 root root   1969 Dec 27  2021 ReleaseNote.txt

./EFI/HP/DEVFW/Current:
total 3
drwx------ 2 root root 1024 May  3  2020 .
drwx------ 5 root root 2048 May  3  2020 ..

./EFI/HP/DEVFW/New:
total 3
drwx------ 2 root root 1024 May  3  2020 .
drwx------ 5 root root 2048 May  3  2020 ..

./EFI/HP/DEVFW/Previous:
total 3
drwx------ 2 root root 1024 May  3  2020 .
drwx------ 5 root root 2048 May  3  2020 ..

'./EFI/HP/HP Support Framework':
total 3
drwx------ 3 root root 1024 Jan  1  2019 .
drwx------ 7 root root 1024 Jan  1  2019 ..
drwx------ 2 root root 1024 Jan  1  2019 Logs

'./EFI/HP/HP Support Framework/Logs':
total 23
drwx------ 2 root root 1024 Jan  1  2019 .
drwx------ 3 root root 1024 Jan  1  2019 ..
-rwx------ 1 root root 7257 Oct 27  2022 1084536892.xml
-rwx------ 1 root root 4594 Jan  1  2019 2574058217.xml
-rwx------ 1 root root 7260 Oct 17  2022 4097873854.xml

./EFI/HP/SystemDiags:
total 17098
drwx------ 2 root root     4096 Jan  1  2019 .
drwx------ 7 root root     1024 Jan  1  2019 ..
-rwx------ 1 root root   443904 May 29  2020 CryptRSA.efi
-rwx------ 1 root root     8390 Dec 13  2022 diw.efi
-rwx------ 1 root root 16789624 Jun 10  2020 SysDiags.efi
-rwx------ 1 root root      256 Jun 10  2020 SysDiags.s09
-rwx------ 1 root root      256 Jun 10  2020 SysDiags.s12
-rwx------ 1 root root      256 Jun 10  2020 SysDiags.s14
-rwx------ 1 root root    14642 Jan  1  2019 SystemDiags-5CD0098NB9.html
-rwx------ 1 root root    18985 Jan  1  2019 SystemDiagsCeeHistory.log
-rwx------ 1 root root       33 Oct 17  2022 SystemDiags.ini
-rwx------ 1 root root   219506 Jan  1  2019 SystemDiags.log

./EFI/Microsoft:
total 9
drwx------  4 root root 1024 Mar 16 15:30 .
drwx------  7 root root 1024 Jul  8 09:03 ..
drwx------ 41 root root 6144 Mar 16 15:30 Boot
drwx------  2 root root 1024 Mar 16 15:30 Recovery

./EFI/Microsoft/Boot:
total 7611
drwx------ 41 root root    6144 Mar 16 15:30 .
drwx------  4 root root    1024 Mar 16 15:30 ..
-rwx------  1 root root   45056 Sep  7 19:18 BCD
-rwx------  1 root root   65536 Mar 16 15:30 BCD.LOG
-rwx------  1 root root       0 Mar 16 15:30 BCD.LOG1
-rwx------  1 root root       0 Mar 16 15:30 BCD.LOG2
drwx------  2 root root    1024 May  2  2020 bg-BG
-rwx------  1 root root 2026304 Aug 11 08:43 bootmgfw.efi
-rwx------  1 root root 2009424 Aug 11 08:43 bootmgr.efi
-rwx------  1 root root   65536 Aug 11 08:51 BOOTSTAT.DAT
-rwx------  1 root root   10895 May 15 09:26 boot.stl
drwx------  3 root root    1024 Mar 16 15:30 CIPolicies
drwx------  2 root root    1024 May  2  2020 cs-CZ
drwx------  2 root root    1024 May  2  2020 da-DK
drwx------  2 root root    1024 May  2  2020 de-DE
drwx------  2 root root    1024 May  2  2020 el-GR
drwx------  2 root root    1024 May  2  2020 en-GB
drwx------  2 root root    1024 May  2  2020 en-US
drwx------  2 root root    1024 May  2  2020 es-ES
drwx------  2 root root    1024 May  2  2020 es-MX
drwx------  2 root root    1024 May  2  2020 et-EE
drwx------  2 root root    1024 May  2  2020 fi-FI
drwx------  2 root root    2048 Mar 16 15:30 Fonts
drwx------  2 root root    1024 May  2  2020 fr-CA
drwx------  2 root root    1024 May  2  2020 fr-FR
drwx------  2 root root    1024 May  2  2020 hr-HR
drwx------  2 root root    1024 May  2  2020 hu-HU
drwx------  2 root root    1024 May  2  2020 it-IT
drwx------  2 root root    1024 May  2  2020 ja-JP
-rwx------  1 root root   65864 Jun  5  2021 kd_02_10df.dll
-rwx------  1 root root  434504 Jun  5  2021 kd_02_10ec.dll
-rwx------  1 root root   62824 May 13  2022 kd_02_1137.dll
-rwx------  1 root root  270656 Jun  5  2021 kd_02_14e4.dll
-rwx------  1 root root   82248 Jun  5  2021 kd_02_15b3.dll
-rwx------  1 root root   78144 Jun  5  2021 kd_02_1969.dll
-rwx------  1 root root   65864 Jun  5  2021 kd_02_19a2.dll
-rwx------  1 root root   57672 Jun  5  2021 kd_02_1af4.dll
-rwx------  1 root root  328008 Jun  5  2021 kd_02_8086.dll
-rwx------  1 root root   53568 Jun  5  2021 kd_07_1415.dll
-rwx------  1 root root   82240 Jun  5  2021 kd_0C_8086.dll
-rwx------  1 root root   53576 Jun  5  2021 kdnet_uart16550.dll
-rwx------  1 root root   83280 Nov 11  2022 kdstub.dll
drwx------  2 root root    1024 May  2  2020 ko-KR
drwx------  2 root root    1024 May  2  2020 lt-LT
drwx------  2 root root    1024 May  2  2020 lv-LV
-rwx------  1 root root 1783616 Aug 11 08:43 memtest.efi
drwx------  2 root root    1024 May  2  2020 nb-NO
drwx------  2 root root    1024 May  2  2020 nl-NL
drwx------  2 root root    1024 May  2  2020 pl-PL
drwx------  2 root root    1024 May  2  2020 pt-BR
drwx------  2 root root    1024 May  2  2020 pt-PT
drwx------  2 root root    1024 May  2  2020 qps-ploc
drwx------  3 root root    1024 Mar 16 15:30 Resources
drwx------  2 root root    1024 May  2  2020 ro-RO
drwx------  2 root root    1024 May  2  2020 ru-RU
drwx------  2 root root    1024 May  2  2020 sk-SK
drwx------  2 root root    1024 May  2  2020 sl-SI
drwx------  2 root root    1024 May  2  2020 sr-Latn-RS
drwx------  2 root root    1024 May  2  2020 sv-SE
drwx------  2 root root    1024 May  2  2020 tr-TR
drwx------  2 root root    1024 May  2  2020 uk-UA
-rwx------  1 root root    9992 Sep 13  2021 winsipolicy.p7b
drwx------  2 root root    1024 May  2  2020 zh-CN
drwx------  2 root root    1024 May  2  2020 zh-TW

./EFI/Microsoft/Boot/bg-BG:
total 167
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 81232 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 81232 Dec 17  2021 bootmgr.efi.mui

./EFI/Microsoft/Boot/CIPolicies:
total 8
drwx------  3 root root 1024 Mar 16 15:30 .
drwx------ 41 root root 6144 Mar 16 15:30 ..
drwx------  2 root root 1024 Mar 16 15:30 Active

./EFI/Microsoft/Boot/CIPolicies/Active:
total 52
drwx------ 2 root root  1024 Mar 16 15:30 .
drwx------ 3 root root  1024 Mar 16 15:30 ..
-rwx------ 1 root root 10564 Feb 12  2022 {5DAC656C-21AD-4A02-AB49-649917162E70}.cip
-rwx------ 1 root root 28456 Nov 11  2022 {82443e1e-8a39-4b4a-96a8-f40ddc00b9f3}.cip
-rwx------ 1 root root 10972 Feb 12  2022 {CDD5CB55-DB68-4D71-AA38-3DF2B6473A52}.cip

./EFI/Microsoft/Boot/cs-CZ:
total 210
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 80208 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 80208 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45384 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/da-DK:
total 208
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 79176 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 79184 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45384 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/de-DE:
total 216
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 83280 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 83280 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45888 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/el-GR:
total 219
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 84296 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 84296 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 46400 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/en-GB:
total 159
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 77136 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 77120 Dec 17  2021 bootmgr.efi.mui

./EFI/Microsoft/Boot/en-US:
total 203
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 77136 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 77136 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 44872 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/es-ES:
total 212
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 81232 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 81232 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45896 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/es-MX:
total 167
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 81232 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 81232 Dec 17  2021 bootmgr.efi.mui

./EFI/Microsoft/Boot/et-EE:
total 161
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 78144 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 78160 Dec 17  2021 bootmgr.efi.mui

./EFI/Microsoft/Boot/fi-FI:
total 210
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 80208 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 80208 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45376 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/Fonts:
total 13353
drwx------  2 root root    2048 Mar 16 15:30 .
drwx------ 41 root root    6144 Mar 16 15:30 ..
-rwx------  1 root root 3695636 Mar 16 15:30 chs_boot.ttf
-rwx------  1 root root 3878332 Mar 16 15:30 cht_boot.ttf
-rwx------  1 root root 1985788 Mar 16 15:30 jpn_boot.ttf
-rwx------  1 root root 2372892 Mar 16 15:30 kor_boot.ttf
-rwx------  1 root root  195288 Mar 16 15:30 malgun_boot.ttf
-rwx------  1 root root  192844 Mar 16 15:30 malgunn_boot.ttf
-rwx------  1 root root  164804 Mar 16 15:30 meiryo_boot.ttf
-rwx------  1 root root  163168 Mar 16 15:30 meiryon_boot.ttf
-rwx------  1 root root  182336 Mar 16 15:30 msjh_boot.ttf
-rwx------  1 root root  180376 Mar 16 15:30 msjhn_boot.ttf
-rwx------  1 root root  174228 Mar 16 15:30 msyh_boot.ttf
-rwx------  1 root root  172428 Mar 16 15:30 msyhn_boot.ttf
-rwx------  1 root root   44776 Mar 16 15:30 segmono_boot.ttf
-rwx------  1 root root  101636 Mar 16 15:30 segoen_slboot.ttf
-rwx------  1 root root  101884 Mar 16 15:30 segoe_slboot.ttf
-rwx------  1 root root   48984 Mar 16 15:30 wgl4_boot.ttf

./EFI/Microsoft/Boot/fr-CA:
total 171
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 83264 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 83272 Dec 17  2021 bootmgr.efi.mui

./EFI/Microsoft/Boot/fr-FR:
total 216
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 83264 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 83280 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45896 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/hr-HR:
total 165
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 80192 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 80200 Dec 17  2021 bootmgr.efi.mui

./EFI/Microsoft/Boot/hu-HU:
total 216
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 83280 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 83280 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45888 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/it-IT:
total 210
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 80704 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 80720 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45384 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/ja-JP:
total 187
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 70512 May  5 12:22 bootmgfw.efi.mui
-rwx------  1 root root 70512 May  5 12:22 bootmgr.efi.mui
-rwx------  1 root root 42824 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/ko-KR:
total 185
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 68944 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 68944 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 42824 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/lt-LT:
total 163
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 79184 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 79176 Dec 17  2021 bootmgr.efi.mui

./EFI/Microsoft/Boot/lv-LV:
total 163
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 79176 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 79184 Dec 17  2021 bootmgr.efi.mui

./EFI/Microsoft/Boot/nb-NO:
total 206
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 78664 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 78672 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45384 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/nl-NL:
total 212
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 81216 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 81224 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45384 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/pl-PL:
total 212
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 81728 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 81744 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45888 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/pt-BR:
total 210
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 80208 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 80208 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45384 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/pt-PT:
total 210
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 80208 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 80208 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45896 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/qps-ploc:
total 60
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 54088 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/Resources:
total 177
drwx------  3 root root   1024 Mar 16 15:30 .
drwx------ 41 root root   6144 Mar 16 15:30 ..
-rwx------  1 root root 172368 Mar 16 15:30 bootres.dll
drwx------  2 root root   1024 Mar 16 15:30 en-US

./EFI/Microsoft/Boot/Resources/en-US:
total 15
drwx------ 2 root root  1024 Mar 16 15:30 .
drwx------ 3 root root  1024 Mar 16 15:30 ..
-rwx------ 1 root root 12600 Mar 16 15:30 bootres.dll.mui

./EFI/Microsoft/Boot/ro-RO:
total 163
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 79696 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 79696 Dec 17  2021 bootmgr.efi.mui

./EFI/Microsoft/Boot/ru-RU:
total 209
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 80712 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 80720 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 44872 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/sk-SK:
total 165
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 80712 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 80704 Dec 17  2021 bootmgr.efi.mui

./EFI/Microsoft/Boot/sl-SI:
total 163
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 79688 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 79688 Dec 17  2021 bootmgr.efi.mui

./EFI/Microsoft/Boot/sr-Latn-RS:
total 165
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 80712 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 80704 Dec 17  2021 bootmgr.efi.mui

./EFI/Microsoft/Boot/sv-SE:
total 207
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 79696 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 79696 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 44864 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/tr-TR:
total 208
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 79184 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 79176 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 45384 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/uk-UA:
total 167
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 81752 Sep 18  2022 bootmgfw.efi.mui
-rwx------  1 root root 81752 Sep 18  2022 bootmgr.efi.mui

./EFI/Microsoft/Boot/zh-CN:
total 177
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 64848 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 64848 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 42312 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Boot/zh-TW:
total 177
drwx------  2 root root  1024 May  2  2020 .
drwx------ 41 root root  6144 Mar 16 15:30 ..
-rwx------  1 root root 64848 Dec 17  2021 bootmgfw.efi.mui
-rwx------  1 root root 64840 Dec 17  2021 bootmgr.efi.mui
-rwx------  1 root root 42312 Jun  5  2021 memtest.efi.mui

./EFI/Microsoft/Recovery:
total 58
drwx------ 2 root root  1024 Mar 16 15:30 .
drwx------ 4 root root  1024 Mar 16 15:30 ..
-rwx------ 1 root root 24576 Mar 16 15:30 BCD
-rwx------ 1 root root 32768 Mar 16 15:30 BCD.LOG
-rwx------ 1 root root     0 Mar 16 15:30 BCD.LOG1
-rwx------ 1 root root     0 Mar 16 15:30 BCD.LOG2

./EFI/ubuntu:
total 4381
drwx------ 3 root root    1024 Mar 16 15:13 .
drwx------ 7 root root    1024 Jul  8 09:03 ..
-rwx------ 1 root root     108 Apr  7 08:20 BOOTX64.CSV
drwx------ 2 root root    1024 Sep 10 20:37 fw
-rwx------ 1 root root   64280 Jan 26  2023 fwupdx64.efi
-rwx------ 1 root root     117 Apr  7 08:20 grub.cfg
-rwx------ 1 root root 2594696 Apr  7 08:20 grubx64.efi
-rwx------ 1 root root  860824 Apr  7 08:20 mmx64.efi
-rwx------ 1 root root  960472 Apr  7 08:20 shimx64.efi

./EFI/ubuntu/fw:
total 2
drwx------ 2 root root 1024 Sep 10 20:37 .
drwx------ 3 root root 1024 Mar 16 15:13 ..

'./System Volume Information':
total 4
drwx------ 4 root root 1024 May  2  2020 .
drwx------ 4 root root 1024 Dec 31  1969 ..
drwx------ 2 root root 1024 May  2  2020 AadRecoveryPasswordDelete
drwx------ 2 root root 1024 May  2  2020 ClientRecoveryPasswordRotation

'./System Volume Information/AadRecoveryPasswordDelete':
total 2
drwx------ 2 root root 1024 May  2  2020 .
drwx------ 4 root root 1024 May  2  2020 ..

'./System Volume Information/ClientRecoveryPasswordRotation':
total 2
drwx------ 2 root root 1024 May  2  2020 .
drwx------ 4 root root 1024 May  2  2020 ..

```

---

### Post by oldfred on 2023-09-10
If system is now Dell and was HP, why keep the HP folders?
I might back them up & delete them. Not required for a Dell.

---

### Post by grahammechanical on 2023-09-11
The rule that must be followed is to use Windows tools to manage (shrink, expand, move) Windows partitions and Linux tools to manage Linux partitions. I understand that Windows partitions should be de-fragmented  before and after working on them and reboot being tested as well.

A partition cannot be expanded if there is not any unallocated space to expand the partition into. So, you need to shrink a partition to create unallocated space either before or after the partition. Then the unallocated space has to be "moved" so that is after the partition you want to expand. We do this by moving the partitions that are in the way and it seems as if the unallocated space is moving.

You need unallocated space between the EFI Systems partition (nmve0n1p2) and the Microsoft Reserved partition (nmve0n1p3). Then you can expand the EFI Systems partition into the unallocated space.

My EFI Systems partition is 537MB with only 1.4% full. I do not have Windows. Just 3 versions of Ubuntu.

Regards

---

### Post by bomberb17 on 2023-09-11
> **oldfred said:**
> If system is now Dell and was HP, why keep the HP folders?
I might back them up & delete them. Not required for a Dell.

I thought about the same thing, but I am not confident about deleting stuff from that partition. Maybe I can try to move them to another partition in the disk and put them back if I encounter issues with booting.

> **grahammechanical said:**
> The rule that must be followed is to use Windows tools to manage (shrink, expand, move) Windows partitions and Linux tools to manage Linux partitions. I understand that Windows partitions should be de-fragmented  before and after working on them and reboot being tested as well.

A partition cannot be expanded if there is not any unallocated space to expand the partition into. So, you need to shrink a partition to create unallocated space either before or after the partition. Then the unallocated space has to be "moved" so that is after the partition you want to expand. We do this by moving the partitions that are in the way and it seems as if the unallocated space is moving.

You need unallocated space between the EFI Systems partition (nmve0n1p2) and the Microsoft Reserved partition (nmve0n1p3). Then you can expand the EFI Systems partition into the unallocated space.

My EFI Systems partition is 537MB with only 1.4% full. I do not have Windows. Just 3 versions of Ubuntu.

Regards

So I will have to shrink then move the 4th partition which contains windows, then move the 3rd MS reserved partition, then grow the 2nd partition. I guess this whole process will likely make the system non-bootable, right?

---

### Post by kurt18947 on 2023-09-11
If you have Windows install media, you could boot that and I think you should be offered a repair option. Failing that you could create a Windows recovery drive. There are plenty of directions on line for that. Of course if you use these options you probably won't be able to boot any non-Windows OSs. There are people here that can help with that, I'm of no use there, I'm afraid.

Most importantly, before doing any manipulation, be certain to create restorable back-ups of your data. Personally I don't worry about backing up system files, those are simple and quick to restore from installation media. Losing important data on the other hand ......

---

### Post by MAFoElffen on 2023-09-11
oldfred explained that you should make a copy of that folder "somewhere else" before deleting it, just in case there is something there you might need. I do not know of anything that might be, but to be safe.

You should take a backup periodically always. Especially before making changes to a system.

Next, yes, you should use Windows tools to resize Windows partitions... Unfortunately, Windows Disk Management isn't going to be much use to you. That will only give you room to expand if you shrink a partition either immediately before or after the partition you are trying to expand. It's not like GParted where you are given the choice to "move it" left or right by the User's choice.

But saying that, On my Windows Installs, I used EaseUS Partition Master Free Edition, where that Windows Program does give me those choices and capabilities. It will also give you the capabilities to do backups and migrations. Google it. 

When I do installs, (I do dual-boot's) by choice, I usually create EFI partition about 750 MiB. Yours is 99MiB. Microsoft doc's say the minimum, for Windows OS, all by itself is 100MiB. RedHat says 250MiB.  

Like I said, I make mine 750 MiB, because I know that dual-booting exists... And having been an HP, Dell, and Lenovo On-site Warranty Tech, all 3 of those have UEFI utilities that load for UEFI for diagnostics and other things. I have seen most set by others at 500 MiB. There is no set standard for that, and I have not seen anyone say there is any problem with having "too much room." Though the max size limit for vfat is 32GB.

---

