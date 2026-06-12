---
title: "Stuck on BusyBox / initramfs on Ubuntu 18.04"
date: 2020-10-29
forum: General Help
---

### Post by gerbili on 2020-10-29
Hi, please help... My server with Ubuntu Mate 18.04 won't start up. It get stuck on BusyBox v1.27.2 (initramfs)

After reading several threads I've tried to 
- repair the disk with parted (with a live USB Ubuntu 18.04). 
- check the disk (clean)
- set the root
- use boot-repair. 

Maybe someone can find the error. The result of boot-repair is:

[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303[/TD]
[TD="class: code"][COLOR=#000000]boot-repair-4ppa125                                              [COLOR=#666666][[/COLOR]20201029_2204[COLOR=#666666]][/COLOR]

[COLOR=#666666]=============================[/COLOR] Boot Repair [COLOR=#B8860B]Summary[/COLOR] [COLOR=#666666]==============================[/COLOR]




Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will purge [COLOR=#666666]([/COLOR]in order to reset grubenv[COLOR=#666666])[/COLOR] and reinstall the grub2 of
sda1 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s


chroot /mnt/boot-sav/sda1 apt-get -y update
Purge the GRUB of sda1
grub-pc available


The following packages were automatically installed and are no longer required:
libllvm7 libllvm9 libqt5sensors5 libqt5webkit5 libqt5xml5
linux-headers-4.15.0-101 linux-headers-4.15.0-101-generic
linux-headers-4.15.0-99 linux-headers-4.15.0-99-generic
linux-image-4.15.0-101-generic linux-image-4.15.0-99-generic
linux-modules-4.15.0-101-generic linux-modules-4.15.0-99-generic
linux-modules-extra-4.15.0-101-generic linux-modules-extra-4.15.0-99-generic
Use [COLOR=#BB4444]'sudo apt autoremove'[/COLOR] to remove them.
[COLOR=#666666]0[/COLOR] upgraded, [COLOR=#666666]0[/COLOR] newly installed, [COLOR=#666666]1[/COLOR] reinstalled, [COLOR=#666666]0[/COLOR] to remove and [COLOR=#666666]1[/COLOR] not upgraded.
DEBCHECK debOK, grub-pc
DEBCHECK debOK
shim-signed available
Please type: sudo chroot [COLOR=#BB4444]"/mnt/boot-sav/sda1"[/COLOR] dpkg --configure -ansudo chroot [COLOR=#BB4444]"/mnt/boot-sav/sda1"[/COLOR] apt-get install -fynsudo chroot [COLOR=#BB4444]"/mnt/boot-sav/sda1"[/COLOR] apt-get purge -y grub*-common shim-signed
Then type: sudo chroot [COLOR=#BB4444]"/mnt/boot-sav/sda1"[/COLOR] apt-get install -y grub-pc

Unhide GRUB boot menu in sda1/etc/default/grub

[COLOR=#666666]========================[/COLOR] Reinstall the grub-pc of [COLOR=#B8860B]sda1[/COLOR] [COLOR=#666666]=========================[/COLOR]

grub-install --version
grub-install [COLOR=#666666]([/COLOR]GRUB[COLOR=#666666])[/COLOR] [COLOR=#666666]2[/COLOR].02-2ubuntu8.18

[COLOR=#666666]==[/COLOR]> Reinstall the GRUB of sda1 into the MBR of sda

grub-install /dev/sda
Installing [COLOR=#AA22FF]**for**[/COLOR] i386-pc platform.
Installation finished. No error reported.

chroot /mnt/boot-sav/sda1 update-grub
Sourcing file [COLOR=#BB4444]`[/COLOR]/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-122-generic
Found initrd image: /boot/initrd.img-4.15.0-122-generic
Found linux image: /boot/vmlinuz-4.15.0-106-generic
Found initrd image: /boot/initrd.img-4.15.0-106-generic
Found linux image: /boot/vmlinuz-4.15.0-101-generic
Found initrd image: /boot/initrd.img-4.15.0-101-generic
Found linux image: /boot/vmlinuz-4.15.0-99-generic
Found initrd image: /boot/initrd.img-4.15.0-99-generic

Unhide GRUB boot menu in sda1/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.


[COLOR=#666666]============================[/COLOR] Boot Info After [COLOR=#B8860B]Repair[/COLOR] [COLOR=#666666]============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector [COLOR=#666666]1[/COLOR] of 
    the same hard drive [COLOR=#AA22FF]**for**[/COLOR] core.img. core.img is at this location and looks 
    [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],msdos1[COLOR=#666666])[/COLOR]/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 [COLOR=#666666]=[/COLOR]> Syslinux MBR [COLOR=#666666]([/COLOR][COLOR=#666666]3[/COLOR].61-4.03[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu [COLOR=#666666]18[/COLOR].04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX [COLOR=#666666]4[/COLOR].03 0x4d8ae235
    Boot sector info:  Syslinux looks at sector [COLOR=#666666]4054976[/COLOR] of /dev/sdb1 [COLOR=#AA22FF]**for**[/COLOR] its 
                       second stage. SYSLINUX is installed in the / 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys


[COLOR=#666666]================================[/COLOR] [COLOR=#666666]1[/COLOR] OS [COLOR=#B8860B]detected[/COLOR] [COLOR=#666666]=================================[/COLOR]

OS#1:   Ubuntu [COLOR=#666666]18[/COLOR].04.5 LTS on [COLOR=#B8860B]sda1[/COLOR]

[COLOR=#666666]============================[/COLOR] Architecture/Host [COLOR=#B8860B]Info[/COLOR] [COLOR=#666666]============================[/COLOR]

CPU architecture: [COLOR=#666666]64[/COLOR]-bit
Live-session OS is Ubuntu [COLOR=#666666]64[/COLOR]-bit [COLOR=#666666]([/COLOR]Ubuntu [COLOR=#666666]18[/COLOR].04 LTS, bionic, x86_64[COLOR=#666666])[/COLOR]


[COLOR=#666666]=====================================[/COLOR] [COLOR=#B8860B]UEFI[/COLOR] [COLOR=#666666]=====================================[/COLOR]

This live-session is not in EFI-mode.
EFI in dmesg.
[COLOR=#666666][[/COLOR]    [COLOR=#666666]0[/COLOR].000000[COLOR=#666666]][/COLOR] ACPI: UEFI 0x000000007924D610 [COLOR=#666666]000042[/COLOR] [COLOR=#666666]([/COLOR]v01 INTEL  NUC6CAYB [COLOR=#666666]00000000[/COLOR]      [COLOR=#666666]00000000[/COLOR][COLOR=#666666])[/COLOR]



[COLOR=#666666]=============================[/COLOR] Drive/Partition [COLOR=#B8860B]Info[/COLOR] [COLOR=#666666]=============================[/COLOR]

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    [COLOR=#666666]2048[/COLOR] sectors * [COLOR=#666666]512[/COLOR] bytes

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

sda1    : is-os,    [COLOR=#666666]64[/COLOR], apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ng,    update-grub,    farbios

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]2[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

sda1    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]3[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

sda1    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ___________________________________________________________

Disk sda: [COLOR=#666666]465[/COLOR].8 GiB, [COLOR=#666666]500107862016[/COLOR] bytes, [COLOR=#666666]976773168[/COLOR] sectors
Disk identifier: 0xef1ba534
      Boot Start       End   Sectors   Size Id Type
sda1  *     [COLOR=#666666]2048[/COLOR] [COLOR=#666666]976771071[/COLOR] [COLOR=#666666]976769024[/COLOR] [COLOR=#666666]465[/COLOR].8G [COLOR=#666666]83[/COLOR] Linux
Disk sdb: [COLOR=#666666]28[/COLOR].9 GiB, [COLOR=#666666]31027363840[/COLOR] bytes, [COLOR=#666666]60600320[/COLOR] sectors
Disk identifier: 0x00000000
      Boot Start      End  Sectors  Size Id Type
sdb1  *     [COLOR=#666666]8192[/COLOR] [COLOR=#666666]60600319[/COLOR] [COLOR=#666666]60592128[/COLOR] [COLOR=#666666]28[/COLOR].9G  c W95 FAT32 [COLOR=#666666]([/COLOR]LBA[COLOR=#666666])[/COLOR]

parted -lm [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _________________________________________________________

sda:500GB:scsi:512:4096:msdos:ATA CT500MX500SSD1:;
[COLOR=#666666]1[/COLOR]:1049kB:500GB:500GB:ext4::boot;
sdb:31.0GB:scsi:512:512:msdos: USB DISK Pro:;
[COLOR=#666666]1[/COLOR]:4194kB:31.0GB:31.0GB:fat32::boot, lba;

blkid [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL PARTLABEL
sda                                                                                             
&#9492;&#9472;sda1 ext4     [COLOR=#666666]64667959[/COLOR]-3ee3-4afa-bffa-5762deaa4944 ef1ba534-01                                
sdb                                                                                             
&#9492;&#9472;sdb1 vfat     B997-4B05                                                                       

df [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _________________________________________________________________

       Avail Use% Mounted on
sda1   [COLOR=#666666]386[/COLOR].2G  [COLOR=#666666]11[/COLOR]% /mnt/boot-sav/sda1
sdb1      27G   [COLOR=#666666]7[/COLOR]% /cdrom

Mount options: __________________________________________________________________

sda1   rw,relatime,data[COLOR=#666666]=[/COLOR]ordered
sdb1   ro,noatime,fmask[COLOR=#666666]=[/COLOR][COLOR=#666666]0022[/COLOR],dmask[COLOR=#666666]=[/COLOR][COLOR=#666666]0022[/COLOR],codepage[COLOR=#666666]=[/COLOR][COLOR=#666666]437[/COLOR],iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro

[COLOR=#666666]======================[/COLOR] sda1/boot/grub/grub.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]======================[/COLOR]

Ubuntu   [COLOR=#666666]64667959[/COLOR]-3ee3-4afa-bffa-5762deaa4944
Ubuntu, with Linux [COLOR=#666666]4[/COLOR].15.0-122-generic   [COLOR=#666666]64667959[/COLOR]-3ee3-4afa-bffa-5762deaa4944
Ubuntu, with Linux [COLOR=#666666]4[/COLOR].15.0-106-generic   [COLOR=#666666]64667959[/COLOR]-3ee3-4afa-bffa-5762deaa4944
Ubuntu, with Linux [COLOR=#666666]4[/COLOR].15.0-101-generic   [COLOR=#666666]64667959[/COLOR]-3ee3-4afa-bffa-5762deaa4944
Ubuntu, with Linux [COLOR=#666666]4[/COLOR].15.0-99-generic   [COLOR=#666666]64667959[/COLOR]-3ee3-4afa-bffa-5762deaa4944
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_uefi-firmware ###*[/COLOR]

[COLOR=#666666]==========================[/COLOR] sda1/etc/fstab [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]===========================[/COLOR]

[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
[COLOR=#008800]*# / was on /dev/sda1 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]64667959[/COLOR]-3ee3-4afa-bffa-5762deaa4944 /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro [COLOR=#666666]0[/COLOR]       [COLOR=#666666]1[/COLOR]
/swapfile                                 none            swap    sw              [COLOR=#666666]0[/COLOR]       [COLOR=#B8860B]0[/COLOR]

[COLOR=#666666]=======================[/COLOR] sda1/etc/default/grub [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]=======================[/COLOR]

[COLOR=#B8860B]GRUB_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT_STYLE[/COLOR][COLOR=#666666]=[/COLOR]hidden
[COLOR=#B8860B]GRUB_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]10[/COLOR]
[COLOR=#B8860B]GRUB_DISTRIBUTOR[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]`[/COLOR]lsb_release -i -s [COLOR=#666666]2[/COLOR]> /dev/null [COLOR=#666666]||[/COLOR] [COLOR=#AA22FF]echo[/COLOR] Debian[COLOR=#BB4444]`[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash"[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]

[COLOR=#666666]====================[/COLOR] sda1: Location of files loaded by [COLOR=#B8860B]Grub[/COLOR] [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]
   [COLOR=#666666]0[/COLOR].000988007 [COLOR=#666666]=[/COLOR] [COLOR=#666666]0[/COLOR].001060864    boot/grub/grub.cfg                             [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]10[/COLOR].472316742 [COLOR=#666666]=[/COLOR] [COLOR=#666666]11[/COLOR].244564480   boot/grub/i386-pc/core.img                     [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]38[/COLOR].340808868 [COLOR=#666666]=[/COLOR] [COLOR=#666666]41[/COLOR].168130048   boot/vmlinuz-4.15.0-101-generic                [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]23[/COLOR].176746368 [COLOR=#666666]=[/COLOR] [COLOR=#666666]24[/COLOR].885841920   boot/vmlinuz-4.15.0-106-generic                [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]30[/COLOR].872062683 [COLOR=#666666]=[/COLOR] [COLOR=#666666]33[/COLOR].148624896   boot/vmlinuz-4.15.0-122-generic                [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]74[/COLOR].793933868 [COLOR=#666666]=[/COLOR] [COLOR=#666666]80[/COLOR].309374976   boot/vmlinuz-4.15.0-99-generic                 [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]30[/COLOR].872062683 [COLOR=#666666]=[/COLOR] [COLOR=#666666]33[/COLOR].148624896   vmlinuz                                        [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]23[/COLOR].176746368 [COLOR=#666666]=[/COLOR] [COLOR=#666666]24[/COLOR].885841920   vmlinuz.old                                    [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]30[/COLOR].819892883 [COLOR=#666666]=[/COLOR] [COLOR=#666666]33[/COLOR].092608000   boot/initrd.img-4.15.0-101-generic             [COLOR=#666666]2[/COLOR]
  [COLOR=#666666]64[/COLOR].263767242 [COLOR=#666666]=[/COLOR] [COLOR=#666666]69[/COLOR].002694656   boot/initrd.img-4.15.0-106-generic             [COLOR=#666666]7[/COLOR]
  [COLOR=#666666]31[/COLOR].069919586 [COLOR=#666666]=[/COLOR] [COLOR=#666666]33[/COLOR].361072128   boot/initrd.img-4.15.0-122-generic             [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]30[/COLOR].913635254 [COLOR=#666666]=[/COLOR] [COLOR=#666666]33[/COLOR].193263104   boot/initrd.img-4.15.0-99-generic              [COLOR=#666666]3[/COLOR]
  [COLOR=#666666]31[/COLOR].069919586 [COLOR=#666666]=[/COLOR] [COLOR=#666666]33[/COLOR].361072128   initrd.img                                     [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]64[/COLOR].263767242 [COLOR=#666666]=[/COLOR] [COLOR=#666666]69[/COLOR].002694656   initrd.img.old                                 [COLOR=#B8860B]7[/COLOR]

[COLOR=#666666]=====================[/COLOR] sda1: ls -l /etc/grub.d/ [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]======================[/COLOR]

-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]12808[/COLOR] Aug [COLOR=#666666]24[/COLOR] [COLOR=#666666]08[/COLOR]:45 10_linux
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]11298[/COLOR] Aug [COLOR=#666666]24[/COLOR] [COLOR=#666666]08[/COLOR]:45 20_linux_xen
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]12059[/COLOR] Aug [COLOR=#666666]24[/COLOR] [COLOR=#666666]08[/COLOR]:45 30_os-prober
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root  [COLOR=#666666]1418[/COLOR] Aug [COLOR=#666666]24[/COLOR] [COLOR=#666666]08[/COLOR]:45 30_uefi-firmware
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root   [COLOR=#666666]214[/COLOR] Aug [COLOR=#666666]24[/COLOR] [COLOR=#666666]08[/COLOR]:45 40_custom
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root   [COLOR=#666666]216[/COLOR] Aug [COLOR=#666666]24[/COLOR] [COLOR=#666666]08[/COLOR]:45 [COLOR=#B8860B]41_custom[/COLOR]

[COLOR=#666666]======================[/COLOR] sdb1/boot/grub/grub.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]======================[/COLOR]

Try Ubuntu MATE without installing
Install Ubuntu MATE
OEM install [COLOR=#666666]([/COLOR][COLOR=#AA22FF]**for**[/COLOR] manufacturers[COLOR=#666666])[/COLOR]
Check disc [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#B8860B]defects[/COLOR]

[COLOR=#666666]=========================[/COLOR] sdb1/syslinux.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]=========================[/COLOR]

default menu.c32
prompt [COLOR=#666666]0[/COLOR]
menu title UNetbootin
timeout [COLOR=#666666]100[/COLOR]
label unetbootindefault
menu label Default
kernel /ubnkern
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu-mate.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash ---
label ubnentry0
menu label ^Help
kernel /ubnkern
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit 
label ubnentry1
menu label ^Try Ubuntu MATE without installing
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu-mate.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper  quiet splash ---
label ubnentry2
menu label ^Install Ubuntu MATE
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu-mate.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper only-ubiquity  quiet splash ---
label ubnentry3
menu label ^Check disc [COLOR=#AA22FF]**for**[/COLOR] defects
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper integrity-check  quiet splash ---
label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit 
label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit 
label ubnentry6
menu label Try Ubuntu MATE without installing
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu-mate.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash ---
label ubnentry7
menu label Install Ubuntu MATE
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu-mate.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper only-ubiquity quiet splash ---
label ubnentry8
menu label OEM install [COLOR=#666666]([/COLOR][COLOR=#AA22FF]**for**[/COLOR] manufacturers[COLOR=#666666])[/COLOR]
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu-mate.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper only-ubiquity quiet splash oem-config/enable[COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR] ---
label ubnentry9
menu label Check disc [COLOR=#AA22FF]**for**[/COLOR] defects
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper integrity-check quiet splash ---

[COLOR=#666666]====================[/COLOR] sdb1: Location of files loaded by [COLOR=#B8860B]Grub[/COLOR] [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]
            ?? [COLOR=#666666]=[/COLOR] ??             boot/grub/grub.cfg                             [COLOR=#B8860B]1[/COLOR]

[COLOR=#666666]==================[/COLOR] sdb1: Location of files loaded by [COLOR=#B8860B]Syslinux[/COLOR] [COLOR=#666666]==================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]
            ?? [COLOR=#666666]=[/COLOR] ??             syslinux.cfg                                   [COLOR=#666666]1[/COLOR]
            ?? [COLOR=#666666]=[/COLOR] ??             ldlinux.sys                                    [COLOR=#666666]1[/COLOR]
            ?? [COLOR=#666666]=[/COLOR] ??             menu.c32                                       [COLOR=#B8860B]1[/COLOR]

[COLOR=#666666]===============[/COLOR] sdb1: Version of COM32[COLOR=#666666]([/COLOR]R[COLOR=#666666])[/COLOR] files used by [COLOR=#B8860B]Syslinux[/COLOR] [COLOR=#666666]===============[/COLOR]

 menu.c32                           :  COM32R module [COLOR=#666666]([/COLOR]v4.xx[COLOR=#666666])[/COLOR]


[COLOR=#666666]===============================[/COLOR] StdErr [COLOR=#B8860B]Messages[/COLOR] [COLOR=#666666]================================[/COLOR]

File descriptor [COLOR=#666666]63[/COLOR] [COLOR=#666666]([/COLOR]pipe:[COLOR=#666666][[/COLOR][COLOR=#666666]58256[/COLOR][COLOR=#666666]])[/COLOR] leaked on lvs invocation. Parent PID [COLOR=#666666]3902[/COLOR]: /bin/bash[/COLOR][/TD]
[/TR]
[/TABLE]

---

