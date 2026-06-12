---
title: "Bug: .mp4 zip i/o error find piped with zip command"
date: 2023-05-27
forum: General Help
---

### Post by anmac1789 on 2023-05-27
hello, there are a number of issues when zipping .mp4 files from android. For example, I use a webdav server pro app from the olive tree from google play store to mount my internal storage of my galaxy s8 as a webdav server. Next, I connect the webdav server on linux using dav://ipaddress:8080 and then I can view my internal storage on ubuntu. Next, when I use terminal and cd into the root folder of the android phone and run this command to create a zip of all .mp4 files I am getting an error

```
find ./sdcard/DCIM/Camera -name *.mp4 -exec zip -0 /home/azeem/Documents/test.zip {} +
```

zip I/O error: Bad address
zip error: Output file write failure (write error on zip file)

working directory: ```
/run/user/1000/gvfs/dav:host=10.0.0.132,port=8080,ssl=false
```
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292299&stc=1[/IMG]

and also when comparing the same .mp4 file from the internal storage to the same file on the webdav server, there are a few differences in how ubuntu recognized the video file

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292300&stc=1[/IMG]

There is a difference in file type. What is going on and how to correct this problem ? This problem is also affecting .jpg files after a short list of files, the same error occurs when making zip files of jpg

---

### Post by SeijiSensei on 2023-05-27
Can you copy the file to your home directory then ZIP it there?

---

### Post by anmac1789 on 2023-05-27
> **SeijiSensei said:**
> Can you copy the file to your home directory then ZIP it there?

I didn't try copying files unzipped but I prefer to make zip files instead

---

### Post by anmac1789 on 2023-05-28
Any suggestions as to why video files in a webdav server cant copy appropriately with find and zip command together ?

---

### Post by Holger_Gehrke on 2023-05-28
You're going through the Gnome Virtual File system (gvfs). This makes something which isn't a file system - like a http connection - look like it is one. But there are things you can do in a real file which you can't do on a http data stream, like jumping back and forth in the file. zip is trying to do something that it can do in a real file but can't do because it isn't one so it throws it's hands up in disgust and gives up.

The obvious workaround is to download the files to the PC and if you still want to zip them do it from local storage. The less obvious solution would be not to use webdav but a real network file system like nfs or smb. I've just tried to zip some files on an smb mount done through gvfs and it worked without a problem.

Holger

---

### Post by anmac1789 on 2023-05-28
> **Holger_Gehrke said:**
> You're going through the Gnome Virtual File system (gvfs). This makes something which isn't a file system - like a http connection - look like it is one. But there are things you can do in a real file which you can't do on a http data stream, like jumping back and forth in the file. zip is trying to do something that it can do in a real file but can't do because it isn't one so it throws it's hands up in disgust and gives up.

The obvious workaround is to download the files to the PC and if you still want to zip them do it from local storage. The less obvious solution would be not to use webdav but a real network file system like nfs or smb. I've just tried to zip some files on an smb mount done through gvfs and it worked without a problem.

Holger

I see...but why does zip work with other files and not specific files...also it's not just video files like .mp4 but also a file inside the DCIM/.thumbnails folder there is a file called .thumbdata4-1763508120 and .thumbdata4--1967290299 and when I tried to zip them I got the same I/O error as before. I've tried to use fuse-zip but it's a longer process and quite tedius to re-do for files that find and zip cannot do or encounters errors with. How can I make a NFS server or SMB for android ? like how webdav works with mounting the entire android device ?

update: im getting a buffer overflow error

*** buffer overflow detected ***: terminated

Btw, this is the dmesg error log

[   54.910739] Modules linked in: uinput snd_seq_dummy snd_hrtimer nf_conntrack_netbios_ns nf_conntrack_broadcast nft_fib_inet nft_fib_ipv4 nft_fib_ipv6 nft_fib nft_reject_inet nf_reject_ipv4 nf_reject_ipv6 nft_reject nft_ct nft_chain_nat nf_nat nf_conntrack nf_defrag_ipv6 nf_defrag_ipv4 ip_set nf_tables nfnetlink qrtr sunrpc binfmt_misc vfat fat snd_hda_codec_realtek 88XXau(OE) snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_intel_sdw_acpi edac_mce_amd snd_hda_codec kvm_amd snd_hda_core ccp snd_hwdep snd_seq kvm snd_seq_device snd_pcm eeepc_wmi asus_wmi ledtrig_audio sparse_keymap mxm_wmi wmi_bmof platform_profile irqbypass snd_timer i2c_piix4 cfg80211 pcspkr fam15h_power k10temp snd soundcore rfkill acpi_cpufreq joydev loop zram amdgpu iommu_v2 drm_buddy gpu_sched hid_logitech_hidpp radeon crct10dif_pclmul crc32_pclmul drm_ttm_helper crc32c_intel ttm polyval_clmulni polyval_generic video rndis_host ghash_clmulni_intel cdc_ether drm_display_helper sha512_ssse3
[   54.910893]  usbnet mii sp5100_tco r8169 cec wmi hid_logitech_dj ip6_tables ip_tables fuse
[   54.910920] CR2: [0000000000000000]("tel:0000000000000000")
[   54.910926] ---[ end trace [0000000000000000]("tel:0000000000000000") ]---
[   54.910930] RIP: 0010:0x0
[   54.910947] Code: Unable to access opcode bytes at 0xffffffffffffffd6.
[   54.910951] RSP: 0018:ffff9c45845f7d10 EFLAGS: [00010283]("tel:00010283")
[   54.910958] RAX: [0000000000000000]("tel:0000000000000000") RBX: ffff9c4580ca4ed0 RCX: ffff9c45845f7d28
[   54.910963] RDX: ffff9c45845f7d20 RSI: ffff9c45845f7d18 RDI: ffff9c4580ca4ed0
[   54.910968] RBP: 000000000000001d R08: ffff9c45845f7d30 R09: [0000000000000000]("tel:0000000000000000")
[   54.910973] R10: [0000000000000001]("tel:0000000000000001") R11: [0000000000000100]("tel:0000000000000100") R12: [0000000000000000]("tel:0000000000000000")
[   54.910977] R13: ffff9c45845f7d68 R14: [0000000000000020]("tel:0000000000000020") R15: ffff8eec3521bbe0
[   54.910983] FS:  [0000000000000000]("tel:0000000000000000")(0000) GS:ffff8eef2ec00000(0000) knlGS:[0000000000000000]("tel:0000000000000000")
[   54.910989] CS:  0010 DS: 0000 ES: 0000 CR0: [0000000080050033]("tel:0000000080050033")
[   54.910994] CR2: ffffffffffffffd6 CR3: 00000001012e2000 CR4: 00000000000406f0
[   54.911000] note: RTW_CMD_THREAD[2212] exited with irqs disabled

update &#8212; when I connected my galaxy s8 normally as a mtp device and ran the same find and zip command, I still got random I/O errors from files in whatsapp and telegram and .mp4 files in DCIM/Camera folder. Is there a deeper problem ?

---

### Post by Holger_Gehrke on 2023-05-29
The 'sometimes it works and sometimes it doesn't' is probably due to size. If zip can produce the whole file in memory and just write it out then it works, if its buffer is full and it has to write out the file in multiple steps then it needs to move around in the output file and fails.

To set up a SMB/CIFS server on your phone, you'd need an app that does that. Searching for 'SMB server' on google play offers a few.

Another way would be to have the phone do the compression. Might actually be faster since the data wouldn't have to be send back and forth for compression. Searching for 'zip' found several on google play; on fdroid.org there's "ToGoZip".

Holger

---

### Post by anmac1789 on 2023-05-29
> **Holger_Gehrke said:**
> The 'sometimes it works and sometimes it doesn't' is probably due to size. If zip can produce the whole file in memory and just write it out then it works, if its buffer is full and it has to write out the file in multiple steps then it needs to move around in the output file and fails.

To set up a SMB/CIFS server on your phone, you'd need an app that does that. Searching for 'SMB server' on google play offers a few.

Another way would be to have the phone do the compression. Might actually be faster since the data wouldn't have to be send back and forth for compression. Searching for 'zip' found several on google play; on fdroid.org there's "ToGoZip".

Holger

I have 16 GB of ram at 1333 Mhz and also how to increase the buffer size so that failure doesnt happen ?

---

### Post by Holger_Gehrke on 2023-05-29
I don't think you can increase that buffer size without changing the source code and compiling zip yourself - if then ...

But you can use the option "-b <path>" to create a temporary zip-file in <path> and copy it automatically when done.

Holger

---

### Post by anmac1789 on 2023-05-29
> **Holger_Gehrke said:**
> I don't think you can increase that buffer size without changing the source code and compiling zip yourself - if then ...

But you can use the option "-b <path>" to create a temporary zip-file in <path> and copy it automatically when done.

Holger

The reason why I wanted a webdav swrver is because it shows hidden folders and files and I wsnted to copy that. Also, it shows the root / folder as sdcard and I wanted to zip that and its whole hierarchy. I just dont understand WHY it gives an input output error i havent read that anyone else has this problem and the fact that I have plenty lf RAM should not bottleneck it.

---

### Post by SeijiSensei on 2023-05-29
Android is very locked down. Expect permission problems to arise whenever you go outside of directories like DCIM. 

I really don't get why you can't just copy over the files then ZIP them in the destination directory. All this rigamarole you're trying seems like a lot more work than just copying then zipping.

---

### Post by anmac1789 on 2023-05-29
Because it seems like it wants to work but something weather its inside ubuntu itself ot a piece of software or the hardware is preventing it from functioning right. If anyone has a android with OS 9 and also from samsung they could do a similar test like I did and verify that it isnt just me with this problem ? Also the fact that it seems to work better at times and sometimes doesnt makes me think that something is interfering with the find command.

---

### Post by anmac1789 on 2023-06-01
Any more suggestions how to deal with this problem?

---

### Post by Holger_Gehrke on 2023-06-02
With .zip it can't work because zip needs to update the local file header after compressing the file. Because of that it needs to go back in the file it's writing which you can't do on a http stream. It seems to work for a bit, but that's an effect of write caching. If the part of the cache which holds the header is already written to the target than going back to it becomes impossible. You might try to use something else instead of zip. 'tar' was originally meant for writing to tape drives which also have a problem with going back. It specifically has an option '--no-seek' to stop it from seeking in the target file. And since the data you want to put into that archive are of types that don't compress well - since they are already highly compressed - you could use tar without any added compression meaning without the '-z', '-Z', '-j' or '-J' options.

Holger

---

### Post by anmac1789 on 2023-06-02
> **Holger_Gehrke said:**
> With .zip it can't work because zip needs to update the local file header after compressing the file. Because of that it needs to go back in the file it's writing which you can't do on a http stream. It seems to work for a bit, but that's an effect of write caching. If the part of the cache which holds the header is already written to the target than going back to it becomes impossible. You might try to use something else instead of zip. 'tar' was originally meant for writing to tape drives which also have a problem with going back. It specifically has an option '--no-seek' to stop it from seeking in the target file. And since the data you want to put into that archive are of types that don't compress well - since they are already highly compressed - you could use tar without any added compression meaning without the '-z', '-Z', '-j' or '-J' options.

Holger

that may be possible but I just found a app called FV file explorer which compressed .mp4 files properly using the same command I was using with webdav server pro from the olive tree which couldn't zip .mp4 and gave me the zip I/O error. Here is the proof

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292328&stc=1[/IMG]

I am not sure why this app worked vs. the olive tree's app webdav server pro didn't work. There seems to be a software problem. I also have a somewhat new pixel 7 device and I was using the webdav server pro app with it and I could also compress the files properly without errors (the pixel 7 has about 50 GB of space remaining as it was somewhat new). It seems to be me that webdav server needs space on the device to function properly or that there is a bug in their connection algorithms. There is another app called BestDAV which can't connect to ubuntu somehow but it works similarly on windows to FV file explorer

---

### Post by anmac1789 on 2023-11-10
Hello, the default zip also doesn't work with webdav I just retried it with ubuntu 23.10 on vmware workstation 17.5. 

the current working directory is: ```
/run/user/1000/gvfs/dav:host=192.168.1.103,port=8080,ssl=false
``` (which is the root level of my galaxy s8 mounted with webdav using webdav server pro app)
```
zip -0 "/home/username/Music/test.zip" "./sdcard/DCIM/Camera/*.mp4"
```

gives:

```
zip error: Nothing to do! (/home/username/Music/test.zip)
```

---

### Post by anmac1789 on 2023-11-13
I've tested these 2 commands in linux mint 21.2 Victoria, 21 Vanessa (both based off [COLOR=#212529][FONT=Ubuntu]Ubuntu Jammy[/FONT][/COLOR]) and linux mint LMDE 6 (without ubuntu and only debian), linux mint 20.3 Una (based off [COLOR=#212529][FONT=Ubuntu]Ubuntu Focal)[/FONT][/COLOR], ubuntu 23.10, ubuntu 20.04.6 LTS, zorin 16.3 (based off Ubuntu 20.04 LTS)

1. find ./*.mp4 -exec cp -p -v "{}" "destination/path" \;
2. find ./*.mp4 -exec zip -0 -v "destination/path.zip" "{}" \;

All of them were new installations in vmware and the ONLY distros that worked are linux mint 20.3 Una, zorin 16.3, and ubuntu 20.04.6 LTS !! All these 3 distros are based off of ubuntu 20.04 ! Which leads me to believe that SOMETHING has changed in these distros above 20.04. There's nothing wrong with my android phone, or zip, or find command, or any PC hardware, **the big problem resides in the distros themselves above ubuntu versions 20.04**. 

here is actual proof that I made a complete new installation of ubuntu 20.04.6 on vmware that I just installed an hour ago. Please take a look at this screenshot.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293059&stc=1[/IMG]

---

### Post by anmac1789 on 2023-11-20
is there anyone with some suggestions as to why this is happening ?

---

