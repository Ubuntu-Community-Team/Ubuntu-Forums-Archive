---
title: "Moving files using “mv” command causes unknown system crash"
date: 2018-09-23
forum: General Help
---

### Post by skatman88 on 2018-09-23
[COLOR=#282A2D][FONT=plexeina-regular]Hi all,[/FONT][/COLOR]
[COLOR=#282A2D][FONT=plexeina-regular]
I am currently running Ubuntu Desktop 18.04.1 LTS on an old laptop as my Media Server using Plex Media Server to fulfil this role.

I have been running this server for about 3/4 years now and have conducted the customary rebuilds along the way when required, but always updating the server regularly. 

Files are downloaded to a specific directory on my NAS, which is mounted manually on boot to */mnt/nas*. This is mounted manually rather than using CRON or FSTAB because I had problems on reboot a few times and I work away a lot (hence the use of the media server) and use TeamViewer to remote manage the server. As a result, I am more happy to just remote in and conduct the mounting of the NAS, than not be able to remote in at all if, for whatever reason, it fails to boot in FSTAB. Once I have downloaded files, I move them to my home directory under *~/Videos* so that Filebot can rename them (for some reason it can&#8217;t rename them on the NAS - a different issue that I&#8217;ll try and sort another time). Once the files were renamed, I usually just do *sudo mv * /mnt/nas/plexmedia/filename* and the files eventually move across. 

However this time, for some reason, it&#8217;s causing something within Ubuntu to crash which then completely stops PMS from running. I can&#8217;t open the crash log because it just endlessly loads and I can&#8217;t manually restart the PMS services as they also end up in an endless loop. The only way of fixing this issue that I&#8217;ve found so far is to conduct a full reboot of the server. I tried doing it again, but it crashed a second time, and I can&#8217;t do it via the GUI as only root has access to the NAS. 

So far, the only way I&#8217;ve figured out of moving the files back to my NAS is via the NAS&#8217; web interface which takes AGES, talking like 12 hours for a TV series.[/FONT][/COLOR]
[COLOR=#282A2D][FONT=plexeina-regular]
[/FONT][/COLOR]
[COLOR=#282A2D][FONT=plexeina-regular]Appreciate any direction you can give me and I can upload any log files you like. Just let me know which ones.[/FONT][/COLOR]
[COLOR=#282A2D][FONT=plexeina-regular]
Thanks in advance,[/FONT][/COLOR]

---

### Post by TheFu on 2018-09-23
Crashing shouldn't happen.  Check for hardware issues in the log files.

PlexMS doesn't like bad permissions.  Solve that too. There are many guides for the necessary permissions to make Plex happy.  There isn't anything special about them.  Plex needs either read or read-write permissions, depending on whether you want plex interfaces to be capabable of managing the files at all. 

Abuse of sudo **can** cause problems.  Using a GUI with sudo can easily trash file and directory permissions unintentionally.

Not sure what cron has to do with mounting anything. 

Really shouldn't need to move files anywhere to rename them.

---

### Post by ajgreeny on 2018-09-23
Have you added yourself as user to the group plex and also added plex to your username group?  That can make all the difference in my experience, though I've no experience of using a NAS system and that could be adding to your problems.

---

### Post by skatman88 on 2018-09-23
> **TheFu said:**
> Crashing shouldn't happen.  Check for hardware issues in the log files.

Definitely shouldn't be happening, you're right! It certainly shouldn't be happening randomly like it is.

> **TheFu said:**
> PlexMS doesn't like bad permissions.  Solve that too. There are many guides for the necessary permissions to make Plex happy.  There isn't anything special about them.  Plex needs either read or read-write permissions, depending on whether you want plex interfaces to be capabable of managing the files at all. 

Yeah, it's definitely not a PMS issue, and I'm pretty sure that it's not a permissions issue either. Plex can read the files without an issue, they are set before moving to '555', just like they were before this crash thing started happening. Nothing like that has changed since.

> **TheFu said:**
> Abuse of sudo **can** cause problems.  Using a GUI with sudo can easily trash file and directory permissions unintentionally.

Yeah, I'm aware. Just not sure what could have caused it though. An update perhaps? Again, happy to upload any logs you think may be useful here.

> **TheFu said:**
> Not sure what cron has to do with mounting anything. 

I was advised that you can set up a CRON job to mount devices after a restart - just to stop me having to manually mount it upon every restart.

> **TheFu said:**
> Really shouldn't need to move files anywhere to rename them.

Yeah, I know. Unfortunately, this is down to Filebot not being able to write to files on my NAS. This part most likely does have issues with permissions, I'm just not sure what and I'll leave this issue to another day.

Thanks for your help so far!

---

### Post by TheFu on 2018-09-23
**Permissions of 555 can't be moved. **The NAS shouldn't allow it and if it does, then Ubuntu is getting conflicting data.

You have a permissions issue that needs to be fixed.  THAT is the main issue to be fixed, IMHO.

If the fstab isn't mounting the storage, then you have other issues. Fix those.  BTW, it could be a permissions issue too.

If you want help with the permissions, start posting **ls -l** output for the mount point, a few directories and some files.  We don't need much, assuming everything is the same everywhere.  Also, the protocol used to access the storage would help.  CIFS should be avoided. Use NFS, whenever possible.  And avoid using NTFS, since permissions controls are weak.
```
$ ls -al
drwxrwsr-x 1228 thefu plex 57344 Aug  1 23:15 ./
....
drwxr-sr-x    2 thefu plex  4096 Apr 20  2014 Zombie_Apocalypse_Redemption/
drwxrwsr-x    2 thefu plex  4096 Aug  3  2014 Zombieland/
```
example.  Plex can't manage Zombie_Apocalypse_Redemption, but it can manage Zombieland. 

BTW, /D is an NFS mount. The underlying file system is ext4.
```
$ df -Th
istar:/D                          nfs       3.5T  3.4T  132G  97% /D
```

The output from **df -hT** would be helpful too - mainly just need to see the NAS mount locations, nothing else.

---

### Post by skatman88 on 2018-09-23
> **ajgreeny said:**
> Have you added yourself as user to the group plex and also added plex to your username group?  That can make all the difference in my experience, though I've no experience of using a NAS system and that could be adding to your problems.

No, I don't think so. I'll have a quick check, but my memory is saying that I haven't changed anything to do with permission groups on the server at all. 

Either way, I don't think it's to do with permissions or Plex. Plex is reading the files fine and I'm setting the same permissions I was before this started crashing. I'm wondering if there's something wrong with my installation of Ubuntu more than anything else.

---

### Post by skatman88 on 2018-09-23
> **TheFu said:**
> **Permissions of 555 can't be moved. **The NAS shouldn't allow it and if it does, then Ubuntu is getting conflicting data.

You have a permissions issue that needs to be fixed.  THAT is the main issue to be fixed, IMHO.

Even if I move them with the Sudo command? I didn't think that would cause an issue and I certainly didn't think that would cause Ubuntu to crash in the way that it does?

> **TheFu said:**
> If the fstab isn't mounting the storage, then you have other issues. Fix those.  BTW, it could be a permissions issue too.

FSTAB does work, but I've had it before where, for some reason, it wouldn't read my NAS upon restart. As a result, I'd rather just not take the chance.

> **TheFu said:**
> If you want help with the permissions, start posting **ls -l** output for the mount point, a few directories and some files.  We don't need much, assuming everything is the same everywhere.  Also, the protocol used to access the storage would help.  CIFS should be avoided. Use NFS, whenever possible.  And avoid using NTFS, since permissions controls are weak.

The output from **df -hT** would be helpful too - mainly just need to see the NAS mount locations, nothing else.

Pretty sure it's an NFS share on my NAS, but I'll check, and sure, I'll get onto those outputs now.

---

### Post by TheFu on 2018-09-23
> **skatman88 said:**
> Even if I move them with the Sudo command? I didn't think that would cause an issue and I certainly didn't think that would cause Ubuntu to crash in the way that it does?

Ubuntu should never crash.  I think that is a hardware issue. Did the log files show anything?
sudo doesn't provide **any** controls over remote storage.  See why that would be a huge problem (i.e. total security failure!)? It is valid for local files only.

> **skatman88 said:**
> 
FSTAB does work, but I've had it before where, for some reason, it wouldn't read my NAS upon restart. As a result, I'd rather just not take the chance.


> **skatman88 said:**
> Pretty sure it's an NFS share on my NAS, but I'll check, and sure, I'll get onto those outputs now.
That will be helpful.

I add my account to the "plex" group.  I do not add the plex userid to my group.  No way would I allow the plex userid any more access than it needs to work if I'd signed up for a plex online account.  NO FREAKIN' WAY!  BTW, there is no need to have a plex online account to use plex and you can use it from remote locations without it as well, but the security of that setup is under your control, no some 3rd party.

---

### Post by skatman88 on 2018-09-23
> **TheFu said:**
> Ubuntu should never crash.  I think that is a hardware issue. Did the log files show anything?

Which log file should I be looking at in-particular?

I've just replicated the fault again, and the only output I received on the console was "Segmentation Fault (Core Dumped)". Any ideas?

> **TheFu said:**
> sudo doesn't provide **any** controls over remote storage.  See why that would be a huge problem (i.e. total security failure!)? It is valid for local files only.

Fair point.

> **TheFu said:**
> That will be helpful.

I add my account to the "plex" group.  I do not add the plex userid to my group.  No way would I allow the plex userid any more access than it needs to work if I'd signed up for a plex online account.  NO FREAKIN' WAY!  BTW, there is no need to have a plex online account to use plex and you can use it from remote locations without it as well, but the security of that setup is under your control, no some 3rd party.

Yeah, that's what I thought too.

---

### Post by skatman88 on 2018-09-23
Here is the output of the Syslog file:

```
Sep 23 18:15:36 MediaServer org.gnome.Shell.desktop[2279]: Window manager warning: Window 0x40001c1 (win0) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.Sep 23 18:15:36 MediaServer org.gnome.Shell.desktop[2279]: Window manager warning: Invalid WM_TRANSIENT_FOR window 0x0 specified for 0x40001c1 (win0).
Sep 23 18:15:36 MediaServer org.gnome.Shell.desktop[2279]: Window manager warning: Invalid WM_TRANSIENT_FOR window 0x0 specified for 0x40001c1 (win0).
Sep 23 18:17:01 MediaServer CRON[11068]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 23 18:17:28 MediaServer kernel: [635977.327900] general protection fault: 0000 [#1] SMP PTI
Sep 23 18:17:28 MediaServer kernel: [635977.327906] Modules linked in: md4 nls_utf8 cifs ccm fscache bnep nls_iso8859_1 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_codec_realtek snd_hda_codec_generic ghash_clmulni_intel arc4 btusb btrtl btbcm btintel iwldvm bluetooth mac80211 ecdh_generic cryptd snd_hda_intel snd_hda_codec intel_cstate uvcvideo intel_rapl_perf videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 snd_hda_core snd_hwdep snd_pcm videobuf2_core videodev media snd_seq_midi snd_seq_midi_event snd_rawmidi joydev input_leds iwlwifi snd_seq snd_seq_device snd_timer serio_raw cfg80211 mei_me snd mei asus_nb_wmi asus_wmi sparse_keymap wmi_bmof shpchp soundcore mac_hid lpc_ich sch_fq_codel sunrpc parport_pc ppdev lp parport ip_tables x_tables autofs4 nouveau
Sep 23 18:17:28 MediaServer kernel: [635977.327976]  i915 mxm_wmi ttm i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm psmouse ahci libahci atl1c video wmi
Sep 23 18:17:28 MediaServer kernel: [635977.327995] CPU: 7 PID: 11066 Comm: mv Not tainted 4.15.0-34-generic #37-Ubuntu
Sep 23 18:17:28 MediaServer kernel: [635977.327998] Hardware name: ASUSTeK Computer Inc. N55SL/N55SL, BIOS N55SL.204 10/24/2012
Sep 23 18:17:28 MediaServer kernel: [635977.328006] RIP: 0010:prefetch_freepointer+0x15/0x30
Sep 23 18:17:28 MediaServer kernel: [635977.328008] RSP: 0018:ffffafc8432b7a98 EFLAGS: 00010206
Sep 23 18:17:28 MediaServer kernel: [635977.328012] RAX: 0000000000000000 RBX: 51fc561e5a132c5c RCX: 00000000001c269a
Sep 23 18:17:28 MediaServer kernel: [635977.328015] RDX: 00000000001c2699 RSI: 51fc561e5a132c5c RDI: ffff9f79c4cc2a00
Sep 23 18:17:28 MediaServer kernel: [635977.328018] RBP: ffffafc8432b7a98 R08: ffff9f79c6beb5b0 R09: 0000000000000000
Sep 23 18:17:28 MediaServer kernel: [635977.328020] R10: ffffafc8432b7c88 R11: 0000000000000000 R12: 0000000001011200
Sep 23 18:17:28 MediaServer kernel: [635977.328023] R13: ffff9f79c4cc2a00 R14: ffff9f793f86d500 R15: ffff9f79c4cc2a00
Sep 23 18:17:28 MediaServer kernel: [635977.328027] FS:  00007faab5121800(0000) GS:ffff9f79c6bc0000(0000) knlGS:0000000000000000
Sep 23 18:17:28 MediaServer kernel: [635977.328030] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Sep 23 18:17:28 MediaServer kernel: [635977.328033] CR2: 00007fecb2d9c138 CR3: 0000000167516001 CR4: 00000000000606e0
Sep 23 18:17:28 MediaServer kernel: [635977.328035] Call Trace:
Sep 23 18:17:28 MediaServer kernel: [635977.328043]  kmem_cache_alloc+0xa2/0x1b0
Sep 23 18:17:28 MediaServer kernel: [635977.328050]  ? mempool_alloc_slab+0x15/0x20
Sep 23 18:17:28 MediaServer kernel: [635977.328056]  ? wait_woken+0x80/0x80
Sep 23 18:17:28 MediaServer kernel: [635977.328061]  mempool_alloc_slab+0x15/0x20
Sep 23 18:17:28 MediaServer kernel: [635977.328065]  mempool_alloc+0x71/0x190
Sep 23 18:17:28 MediaServer kernel: [635977.328070]  ? update_cfs_group+0xc4/0xe0
Sep 23 18:17:28 MediaServer kernel: [635977.328099]  ? cifs_page_mkwrite+0x50/0x50 [cifs]
Sep 23 18:17:28 MediaServer kernel: [635977.328120]  cifs_small_buf_get+0x1a/0x30 [cifs]
Sep 23 18:17:28 MediaServer kernel: [635977.328143]  small_smb2_init+0x62/0xb0 [cifs]
Sep 23 18:17:28 MediaServer kernel: [635977.328162]  ? cifs_page_mkwrite+0x50/0x50 [cifs]
Sep 23 18:17:28 MediaServer kernel: [635977.328184]  smb2_async_writev+0x9b/0x380 [cifs]
Sep 23 18:17:28 MediaServer kernel: [635977.328189]  ? copyin+0x26/0x30
Sep 23 18:17:28 MediaServer kernel: [635977.328193]  ? copy_page_from_iter+0x110/0x220
Sep 23 18:17:28 MediaServer kernel: [635977.328211]  cifs_write_from_iter.isra.26+0x383/0x5a0 [cifs]
Sep 23 18:17:28 MediaServer kernel: [635977.328228]  ? cifs_write_from_iter.isra.26+0x383/0x5a0 [cifs]
Sep 23 18:17:28 MediaServer kernel: [635977.328247]  cifs_user_writev+0x126/0x270 [cifs]
Sep 23 18:17:28 MediaServer kernel: [635977.328265]  cifs_strict_writev+0x137/0x290 [cifs]
Sep 23 18:17:28 MediaServer kernel: [635977.328271]  new_sync_write+0xe7/0x140
Sep 23 18:17:28 MediaServer kernel: [635977.328275]  __vfs_write+0x29/0x40
Sep 23 18:17:28 MediaServer kernel: [635977.328279]  vfs_write+0xb1/0x1a0
Sep 23 18:17:28 MediaServer kernel: [635977.328282]  SyS_write+0x55/0xc0
Sep 23 18:17:28 MediaServer kernel: [635977.328288]  do_syscall_64+0x73/0x130
Sep 23 18:17:28 MediaServer kernel: [635977.328294]  entry_SYSCALL_64_after_hwframe+0x3d/0xa2
Sep 23 18:17:28 MediaServer kernel: [635977.328297] RIP: 0033:0x7faab45ff154
Sep 23 18:17:28 MediaServer kernel: [635977.328300] RSP: 002b:00007ffc6acfea18 EFLAGS: 00000246 ORIG_RAX: 0000000000000001
Sep 23 18:17:28 MediaServer kernel: [635977.328304] RAX: ffffffffffffffda RBX: 0000000000020000 RCX: 00007faab45ff154
Sep 23 18:17:28 MediaServer kernel: [635977.328306] RDX: 0000000000020000 RSI: 000056135d0f8000 RDI: 0000000000000004
Sep 23 18:17:28 MediaServer kernel: [635977.328309] RBP: 000056135d0f8000 R08: 0000000000020000 R09: 0000000000000000
Sep 23 18:17:28 MediaServer kernel: [635977.328311] R10: 0000000000020000 R11: 0000000000000246 R12: 000056135d0f8000
Sep 23 18:17:28 MediaServer kernel: [635977.328314] R13: 0000000000000004 R14: 000056135d0f8000 R15: 0000000000000001
Sep 23 18:17:28 MediaServer kernel: [635977.328317] Code: eb bb 49 8b 74 24 60 48 c7 c7 c8 be 8e 8d e8 33 bb ea ff eb 90 90 66 66 66 66 90 55 48 85 f6 48 89 e5 74 14 48 63 47 20 48 01 c6 <48> 33 36 48 33 b7 40 01 00 00 0f 18 0e 5d c3 66 90 66 2e 0f 1f 
Sep 23 18:17:28 MediaServer kernel: [635977.328370] RIP: prefetch_freepointer+0x15/0x30 RSP: ffffafc8432b7a98
Sep 23 18:17:28 MediaServer kernel: [635977.328374] ---[ end trace aba3b329ed439698 ]---
Sep 23 18:17:32 MediaServer kernel: [635981.259605] general protection fault: 0000 [#2] SMP PTI
Sep 23 18:17:32 MediaServer kernel: [635981.259616] Modules linked in: md4 nls_utf8 cifs ccm fscache bnep nls_iso8859_1 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_codec_realtek snd_hda_codec_generic ghash_clmulni_intel arc4 btusb btrtl btbcm btintel iwldvm bluetooth mac80211 ecdh_generic cryptd snd_hda_intel snd_hda_codec intel_cstate uvcvideo intel_rapl_perf videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 snd_hda_core snd_hwdep snd_pcm videobuf2_core videodev media snd_seq_midi snd_seq_midi_event snd_rawmidi joydev input_leds iwlwifi snd_seq snd_seq_device snd_timer serio_raw cfg80211 mei_me snd mei asus_nb_wmi asus_wmi sparse_keymap wmi_bmof shpchp soundcore mac_hid lpc_ich sch_fq_codel sunrpc parport_pc ppdev lp parport ip_tables x_tables autofs4 nouveau
Sep 23 18:17:32 MediaServer kernel: [635981.259740]  i915 mxm_wmi ttm i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm psmouse ahci libahci atl1c video wmi
Sep 23 18:17:32 MediaServer kernel: [635981.259775] CPU: 7 PID: 10285 Comm: Plex Transcoder Tainted: G      D          4.15.0-34-generic #37-Ubuntu
Sep 23 18:17:32 MediaServer kernel: [635981.259780] Hardware name: ASUSTeK Computer Inc. N55SL/N55SL, BIOS N55SL.204 10/24/2012
Sep 23 18:17:32 MediaServer kernel: [635981.259795] RIP: 0010:kmem_cache_alloc+0x81/0x1b0
Sep 23 18:17:32 MediaServer kernel: [635981.259800] RSP: 0018:ffffafc8434c7b28 EFLAGS: 00010206
Sep 23 18:17:32 MediaServer kernel: [635981.259807] RAX: 51fc561e5a132c5c RBX: 51fc561e5a132c5c RCX: 00000000001c269b
Sep 23 18:17:32 MediaServer kernel: [635981.259812] RDX: 00000000001c269a RSI: 0000000001011200 RDI: 000000000002b5b0
Sep 23 18:17:32 MediaServer kernel: [635981.259818] RBP: ffffafc8434c7b58 R08: ffff9f79c6beb5b0 R09: 0000000000003881
Sep 23 18:17:32 MediaServer kernel: [635981.259823] R10: 0000000000000000 R11: 0000000000003000 R12: 0000000001011200
Sep 23 18:17:32 MediaServer kernel: [635981.259828] R13: ffff9f79c4cc2a00 R14: 51fc561e5a132c5c R15: ffff9f79c4cc2a00
Sep 23 18:17:32 MediaServer kernel: [635981.259835] FS:  00007fc5eaee0740(0000) GS:ffff9f79c6bc0000(0000) knlGS:0000000000000000
Sep 23 18:17:32 MediaServer kernel: [635981.259840] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Sep 23 18:17:32 MediaServer kernel: [635981.259846] CR2: 0000558092125e00 CR3: 000000016749a003 CR4: 00000000000606e0
Sep 23 18:17:32 MediaServer kernel: [635981.259851] Call Trace:
Sep 23 18:17:32 MediaServer kernel: [635981.259866]  ? mempool_alloc_slab+0x15/0x20
Sep 23 18:17:32 MediaServer kernel: [635981.259879]  ? wait_woken+0x80/0x80
Sep 23 18:17:32 MediaServer kernel: [635981.259887]  mempool_alloc_slab+0x15/0x20
Sep 23 18:17:32 MediaServer kernel: [635981.259895]  mempool_alloc+0x71/0x190
Sep 23 18:17:32 MediaServer kernel: [635981.259904]  ? ip_finish_output+0x198/0x270
Sep 23 18:17:32 MediaServer kernel: [635981.259958]  cifs_small_buf_get+0x1a/0x30 [cifs]
Sep 23 18:17:32 MediaServer kernel: [635981.260003]  smb2_new_read_req.constprop.12+0x4f/0xf0 [cifs]
Sep 23 18:17:32 MediaServer kernel: [635981.260047]  smb2_async_readv+0xce/0x2f0 [cifs]
Sep 23 18:17:32 MediaServer kernel: [635981.260086]  cifs_send_async_read.isra.27+0x2a3/0x370 [cifs]
Sep 23 18:17:32 MediaServer kernel: [635981.260122]  cifs_user_readv+0x110/0x280 [cifs]
Sep 23 18:17:32 MediaServer kernel: [635981.260155]  cifs_strict_readv+0xe2/0x100 [cifs]
Sep 23 18:17:32 MediaServer kernel: [635981.260167]  new_sync_read+0xe4/0x130
Sep 23 18:17:32 MediaServer kernel: [635981.260174]  __vfs_read+0x29/0x40
Sep 23 18:17:32 MediaServer kernel: [635981.260180]  vfs_read+0x8e/0x130
Sep 23 18:17:32 MediaServer kernel: [635981.260187]  SyS_read+0x55/0xc0
Sep 23 18:17:32 MediaServer kernel: [635981.260197]  do_syscall_64+0x73/0x130
Sep 23 18:17:32 MediaServer kernel: [635981.260207]  entry_SYSCALL_64_after_hwframe+0x3d/0xa2
Sep 23 18:17:32 MediaServer kernel: [635981.260213] RIP: 0033:0x7fc5e9cf40b4
Sep 23 18:17:32 MediaServer kernel: [635981.260218] RSP: 002b:00007ffe06bcf820 EFLAGS: 00000246 ORIG_RAX: 0000000000000000
Sep 23 18:17:32 MediaServer kernel: [635981.260225] RAX: ffffffffffffffda RBX: 0000000000000004 RCX: 00007fc5e9cf40b4
Sep 23 18:17:32 MediaServer kernel: [635981.260230] RDX: 0000000000008000 RSI: 0000000002e7e490 RDI: 0000000000000004
Sep 23 18:17:32 MediaServer kernel: [635981.260235] RBP: 0000000002e7e490 R08: 0000000000000000 R09: 0000000000008000
Sep 23 18:17:32 MediaServer kernel: [635981.260240] R10: 0000000000000000 R11: 0000000000000246 R12: 0000000000008000
Sep 23 18:17:32 MediaServer kernel: [635981.260244] R13: 0000000000708c20 R14: 0000000000000005 R15: 0000000000000000
Sep 23 18:17:32 MediaServer kernel: [635981.260250] Code: 88 5c 73 49 83 78 10 00 4d 8b 30 0f 84 00 01 00 00 4d 85 f6 0f 84 f7 00 00 00 49 63 5f 20 49 8b 3f 48 8d 4a 01 4c 89 f0 4c 01 f3 <48> 33 1b 49 33 9f 40 01 00 00 65 48 0f c7 0f 0f 94 c0 84 c0 74 
Sep 23 18:17:32 MediaServer kernel: [635981.260349] RIP: kmem_cache_alloc+0x81/0x1b0 RSP: ffffafc8434c7b28
Sep 23 18:17:32 MediaServer kernel: [635981.260371] ---[ end trace aba3b329ed439699 ]---
Sep 23 18:19:32 MediaServer kernel: [636101.474249] general protection fault: 0000 [#3] SMP PTI
Sep 23 18:19:32 MediaServer kernel: [636101.474260] Modules linked in: md4 nls_utf8 cifs ccm fscache bnep nls_iso8859_1 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_codec_realtek snd_hda_codec_generic ghash_clmulni_intel arc4 btusb btrtl btbcm btintel iwldvm bluetooth mac80211 ecdh_generic cryptd snd_hda_intel snd_hda_codec intel_cstate uvcvideo intel_rapl_perf videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 snd_hda_core snd_hwdep snd_pcm videobuf2_core videodev media snd_seq_midi snd_seq_midi_event snd_rawmidi joydev input_leds iwlwifi snd_seq snd_seq_device snd_timer serio_raw cfg80211 mei_me snd mei asus_nb_wmi asus_wmi sparse_keymap wmi_bmof shpchp soundcore mac_hid lpc_ich sch_fq_codel sunrpc parport_pc ppdev lp parport ip_tables x_tables autofs4 nouveau
Sep 23 18:19:32 MediaServer kernel: [636101.474365]  i915 mxm_wmi ttm i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm psmouse ahci libahci atl1c video wmi
Sep 23 18:19:32 MediaServer kernel: [636101.474382] CPU: 7 PID: 2752 Comm: cifsd Tainted: G      D          4.15.0-34-generic #37-Ubuntu
Sep 23 18:19:32 MediaServer kernel: [636101.474384] Hardware name: ASUSTeK Computer Inc. N55SL/N55SL, BIOS N55SL.204 10/24/2012
Sep 23 18:19:32 MediaServer kernel: [636101.474395] RIP: 0010:kmem_cache_alloc+0x81/0x1b0
Sep 23 18:19:32 MediaServer kernel: [636101.474398] RSP: 0018:ffffafc842d57db0 EFLAGS: 00010206
Sep 23 18:19:32 MediaServer kernel: [636101.474400] RAX: 51fc561e5a132c5c RBX: 51fc561e5a132c5c RCX: 00000000001c269b
Sep 23 18:19:32 MediaServer kernel: [636101.474402] RDX: 00000000001c269a RSI: 0000000001011200 RDI: 000000000002b5b0
Sep 23 18:19:32 MediaServer kernel: [636101.474404] RBP: ffffafc842d57de0 R08: ffff9f79c6beb5b0 R09: 0000000000000000
Sep 23 18:19:32 MediaServer kernel: [636101.474406] R10: afb504000afb5041 R11: 0000000000000237 R12: 0000000001011200
Sep 23 18:19:32 MediaServer kernel: [636101.474408] R13: ffff9f79c4cc2a00 R14: 51fc561e5a132c5c R15: ffff9f79c4cc2a00
Sep 23 18:19:32 MediaServer kernel: [636101.474411] FS:  0000000000000000(0000) GS:ffff9f79c6bc0000(0000) knlGS:0000000000000000
Sep 23 18:19:32 MediaServer kernel: [636101.474414] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Sep 23 18:19:32 MediaServer kernel: [636101.474416] CR2: 00007f86f50d7880 CR3: 000000014d20a006 CR4: 00000000000606e0
Sep 23 18:19:32 MediaServer kernel: [636101.474418] Call Trace:
Sep 23 18:19:32 MediaServer kernel: [636101.474428]  ? mempool_alloc_slab+0x15/0x20
Sep 23 18:19:32 MediaServer kernel: [636101.474436]  ? wait_woken+0x80/0x80
Sep 23 18:19:32 MediaServer kernel: [636101.474439]  mempool_alloc_slab+0x15/0x20
Sep 23 18:19:32 MediaServer kernel: [636101.474442]  mempool_alloc+0x71/0x190
Sep 23 18:19:32 MediaServer kernel: [636101.474480]  cifs_small_buf_get+0x1a/0x30 [cifs]
Sep 23 18:19:32 MediaServer kernel: [636101.474520]  cifs_demultiplex_thread+0x5c7/0xaf0 [cifs]
Sep 23 18:19:32 MediaServer kernel: [636101.474527]  ? __schedule+0x299/0x8a0
Sep 23 18:19:32 MediaServer kernel: [636101.474533]  kthread+0x121/0x140
Sep 23 18:19:32 MediaServer kernel: [636101.474560]  ? cifs_handle_standard+0x190/0x190 [cifs]
Sep 23 18:19:32 MediaServer kernel: [636101.474570]  ? kthread_create_worker_on_cpu+0x70/0x70
Sep 23 18:19:32 MediaServer kernel: [636101.474579]  ret_from_fork+0x35/0x40
Sep 23 18:19:32 MediaServer kernel: [636101.474585] Code: 88 5c 73 49 83 78 10 00 4d 8b 30 0f 84 00 01 00 00 4d 85 f6 0f 84 f7 00 00 00 49 63 5f 20 49 8b 3f 48 8d 4a 01 4c 89 f0 4c 01 f3 <48> 33 1b 49 33 9f 40 01 00 00 65 48 0f c7 0f 0f 94 c0 84 c0 74 
Sep 23 18:19:32 MediaServer kernel: [636101.474698] RIP: kmem_cache_alloc+0x81/0x1b0 RSP: ffffafc842d57db0
Sep 23 18:19:32 MediaServer kernel: [636101.474706] ---[ end trace aba3b329ed43969a ]---
Sep 23 18:19:41 MediaServer update-notifier[2764]: GtkDialog mapped without a transient parent. This is discouraged.
Sep 23 18:19:44 MediaServer gnome-shell[2279]: JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13#012pushModal@resource:///org/gnome/shell/ui/modalDialog.js:226:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012open@resource:///org/gnome/shell/ui/modalDialog.js:155:14#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_ensureOpen@resource:///org/gnome/shell/ui/components/polkitAgent.js:212:14#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_onSessionRequest@resource:///org/gnome/shell/ui/components/polkitAgent.js:310:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
Sep 23 18:19:44 MediaServer gnome-shell[2279]: JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13
Sep 23 18:19:49 MediaServer gnome-shell[2279]: message repeated 14 times: [ JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13]
Sep 23 18:20:06 MediaServer kernel: [636135.668160] ACPI: \_SB_.PCI0.PEG0.GFX0: failed to evaluate _DSM
Sep 23 18:22:45 MediaServer update-notifier[2764]: GtkDialog mapped without a transient parent. This is discouraged.
Sep 23 18:22:48 MediaServer gnome-shell[2279]: JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13#012pushModal@resource:///org/gnome/shell/ui/modalDialog.js:226:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012open@resource:///org/gnome/shell/ui/modalDialog.js:155:14#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_ensureOpen@resource:///org/gnome/shell/ui/components/polkitAgent.js:212:14#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_onSessionRequest@resource:///org/gnome/shell/ui/components/polkitAgent.js:310:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
Sep 23 18:22:48 MediaServer gnome-shell[2279]: JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13
Sep 23 18:22:53 MediaServer gnome-shell[2279]: message repeated 14 times: [ JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13]
Sep 23 18:23:07 MediaServer kernel: [636316.656568] ACPI: \_SB_.PCI0.PEG0.GFX0: failed to evaluate _DSM
Sep 23 18:25:49 MediaServer update-notifier[2764]: GtkDialog mapped without a transient parent. This is discouraged.
Sep 23 18:25:51 MediaServer gnome-shell[2279]: JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13#012pushModal@resource:///org/gnome/shell/ui/modalDialog.js:226:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012open@resource:///org/gnome/shell/ui/modalDialog.js:155:14#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_ensureOpen@resource:///org/gnome/shell/ui/components/polkitAgent.js:212:14#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_onSessionRequest@resource:///org/gnome/shell/ui/components/polkitAgent.js:310:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
Sep 23 18:25:51 MediaServer gnome-shell[2279]: JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13
Sep 23 18:25:56 MediaServer gnome-shell[2279]: message repeated 14 times: [ JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13]
Sep 23 18:26:09 MediaServer whoopsie[1069]: [18:26:09] Parsing /var/crash/_usr_bin_sudo.0.crash.
Sep 23 18:26:09 MediaServer update-notifier.desktop[2764]: ERROR: hook /usr/share/apport/package-hooks/source_sudo.py crashed:
Sep 23 18:26:09 MediaServer update-notifier.desktop[2764]: Traceback (most recent call last):
Sep 23 18:26:09 MediaServer update-notifier.desktop[2764]:   File "/usr/lib/python3/dist-packages/apport/report.py", line 198, in _run_hook
Sep 23 18:26:09 MediaServer update-notifier.desktop[2764]:     symb['add_info'](report, ui)
Sep 23 18:26:09 MediaServer update-notifier.desktop[2764]:   File "/usr/share/apport/package-hooks/source_sudo.py", line 20, in add_info
Sep 23 18:26:09 MediaServer update-notifier.desktop[2764]:     response = ui.yesno("The contents of your /etc/sudoers file may help developers diagnose your bug more quickly, however, it may contain sensitive information.  Do you want to include it in your bug report?")
Sep 23 18:26:09 MediaServer update-notifier.desktop[2764]: AttributeError: 'NoneType' object has no attribute 'yesno'
Sep 23 18:26:09 MediaServer whoopsie[1069]: [18:26:09] Uploading /var/crash/_usr_bin_sudo.0.crash.
Sep 23 18:28:25 MediaServer whoopsie[1069]: [18:28:25] Sent; server replied with: No error
Sep 23 18:28:25 MediaServer whoopsie[1069]: [18:28:25] Response code: 200
Sep 23 18:28:25 MediaServer whoopsie[1069]: [18:28:25] Reported OOPS ID 12b3b2ac-bf56-11e8-8edd-fa163e102db1
```

This is the output of /var/crash/_usr_bin_sudo.0.crash (There is more, but a lot of it is a base64 encoded dump of the core):

```
ProblemType: Crash
Architecture: amd64
CurrentDesktop: ubuntu:GNOME
Date: Sun Sep 23 18:17:29 2018
DistroRelease: Ubuntu 18.04
ExecutablePath: /usr/bin/sudo
ExecutableTimestamp: 1516234096
ProcCmdline: sudo mv Ballers\ -\ 3x01\ -\ Seeds\ of\ Expansion.mkv Ballers\ -\ 3x02\ -\ Bull\ Rush.mkv Ballers\ -\ 3x03\ -\ In\ the\ Teeth.mkv Ballers\ -\ 3x04\ -\ Ride\ and\ Die.mkv Ballers\ -\ 3x05\ -\ Make\ Believe.mkv Ballers\ -\ 3x06\ -\ I\ Hate\ New\ York.mkv Ballers\ -\ 3x07\ -\ Ricky-Leaks.mkv Ballers\ -\ 3x08\ -\ Alley-Oops.mkv Ballers\ -\ 3x09\ -\ Crackback.mkv Ballers\ -\ 3x10\ -\ Yay\ Area.mkv /mnt/nas/TV\ Series/
ProcCwd: /home/rich/Videos
ProcEnviron:
 LANG=en_GB.UTF-8
 TERM=xterm-256color
 SHELL=/bin/bash
 XDG_RUNTIME_DIR=<set>
 PATH=(custom, no user)
ProcMaps:
 56259c1b2000-56259c1d4000 r-xp 00000000 08:02 787693                     /usr/bin/sudo
 56259c3d4000-56259c3d5000 r--p 00022000 08:02 787693                     /usr/bin/sudo
 56259c3d5000-56259c3d6000 rw-p 00023000 08:02 787693                     /usr/bin/sudo
 56259c3d6000-56259c3d8000 rw-p 00000000 00:00 0 
 56259da8e000-56259daec000 rw-p 00000000 00:00 0                          [heap]
 7fd07997c000-7fd079983000 r-xp 00000000 08:02 1184997                    /lib/x86_64-linux-gnu/librt-2.27.so
 7fd079983000-7fd079b82000 ---p 00007000 08:02 1184997                    /lib/x86_64-linux-gnu/librt-2.27.so
 7fd079b82000-7fd079b83000 r--p 00006000 08:02 1184997                    /lib/x86_64-linux-gnu/librt-2.27.so
 7fd079b83000-7fd079b84000 rw-p 00007000 08:02 1184997                    /lib/x86_64-linux-gnu/librt-2.27.so
 7fd079b84000-7fd079bc0000 r-xp 00000000 08:02 1179851                    /lib/x86_64-linux-gnu/libnss_systemd.so.2
 7fd079bc0000-7fd079dbf000 ---p 0003c000 08:02 1179851                    /lib/x86_64-linux-gnu/libnss_systemd.so.2
 7fd079dbf000-7fd079dc2000 r--p 0003b000 08:02 1179851                    /lib/x86_64-linux-gnu/libnss_systemd.so.2
 7fd079dc2000-7fd079dc3000 rw-p 0003e000 08:02 1179851                    /lib/x86_64-linux-gnu/libnss_systemd.so.2
 7fd079dc3000-7fd079dd0000 r-xp 00000000 08:02 1184965                    /lib/x86_64-linux-gnu/libpam.so.0.83.1
 7fd079dd0000-7fd079fcf000 ---p 0000d000 08:02 1184965                    /lib/x86_64-linux-gnu/libpam.so.0.83.1
 7fd079fcf000-7fd079fd0000 r--p 0000c000 08:02 1184965                    /lib/x86_64-linux-gnu/libpam.so.0.83.1
 7fd079fd0000-7fd079fd1000 rw-p 0000d000 08:02 1184965                    /lib/x86_64-linux-gnu/libpam.so.0.83.1
 7fd079fd1000-7fd07a024000 r-xp 00000000 08:02 795401                     /usr/lib/sudo/sudoers.so
 7fd07a024000-7fd07a224000 ---p 00053000 08:02 795401                     /usr/lib/sudo/sudoers.so
 7fd07a224000-7fd07a225000 r--p 00053000 08:02 795401                     /usr/lib/sudo/sudoers.so
 7fd07a225000-7fd07a228000 rw-p 00054000 08:02 795401                     /usr/lib/sudo/sudoers.so
 7fd07a228000-7fd07a233000 r-xp 00000000 08:02 1184946                    /lib/x86_64-linux-gnu/libnss_files-2.27.so
 7fd07a233000-7fd07a432000 ---p 0000b000 08:02 1184946                    /lib/x86_64-linux-gnu/libnss_files-2.27.so
 7fd07a432000-7fd07a433000 r--p 0000a000 08:02 1184946                    /lib/x86_64-linux-gnu/libnss_files-2.27.so
 7fd07a433000-7fd07a434000 rw-p 0000b000 08:02 1184946                    /lib/x86_64-linux-gnu/libnss_files-2.27.so
 7fd07a434000-7fd07a43a000 rw-p 00000000 00:00 0 
 7fd07a43a000-7fd07a451000 r-xp 00000000 08:02 1184940                    /lib/x86_64-linux-gnu/libnsl-2.27.so
 7fd07a451000-7fd07a650000 ---p 00017000 08:02 1184940                    /lib/x86_64-linux-gnu/libnsl-2.27.so
 7fd07a650000-7fd07a651000 r--p 00016000 08:02 1184940                    /lib/x86_64-linux-gnu/libnsl-2.27.so
 7fd07a651000-7fd07a652000 rw-p 00017000 08:02 1184940                    /lib/x86_64-linux-gnu/libnsl-2.27.so
 7fd07a652000-7fd07a654000 rw-p 00000000 00:00 0 
 7fd07a654000-7fd07a65f000 r-xp 00000000 08:02 1184957                    /lib/x86_64-linux-gnu/libnss_nis-2.27.so
 7fd07a65f000-7fd07a85e000 ---p 0000b000 08:02 1184957                    /lib/x86_64-linux-gnu/libnss_nis-2.27.so
 7fd07a85e000-7fd07a85f000 r--p 0000a000 08:02 1184957                    /lib/x86_64-linux-gnu/libnss_nis-2.27.so
 7fd07a85f000-7fd07a860000 rw-p 0000b000 08:02 1184957                    /lib/x86_64-linux-gnu/libnss_nis-2.27.so
 7fd07a860000-7fd07a868000 r-xp 00000000 08:02 1184942                    /lib/x86_64-linux-gnu/libnss_compat-2.27.so
 7fd07a868000-7fd07aa68000 ---p 00008000 08:02 1184942                    /lib/x86_64-linux-gnu/libnss_compat-2.27.so
 7fd07aa68000-7fd07aa69000 r--p 00008000 08:02 1184942                    /lib/x86_64-linux-gnu/libnss_compat-2.27.so
 7fd07aa69000-7fd07aa6a000 rw-p 00009000 08:02 1184942                    /lib/x86_64-linux-gnu/libnss_compat-2.27.so
 7fd07aa6a000-7fd07b439000 r--p 00000000 08:02 793181                     /usr/lib/locale/locale-archive
 7fd07b439000-7fd07b453000 r-xp 00000000 08:02 1184989                    /lib/x86_64-linux-gnu/libpthread-2.27.so
 7fd07b453000-7fd07b652000 ---p 0001a000 08:02 1184989                    /lib/x86_64-linux-gnu/libpthread-2.27.so
 7fd07b652000-7fd07b653000 r--p 00019000 08:02 1184989                    /lib/x86_64-linux-gnu/libpthread-2.27.so
 7fd07b653000-7fd07b654000 rw-p 0001a000 08:02 1184989                    /lib/x86_64-linux-gnu/libpthread-2.27.so
 7fd07b654000-7fd07b658000 rw-p 00000000 00:00 0 
 7fd07b658000-7fd07b65b000 r-xp 00000000 08:02 1184879                    /lib/x86_64-linux-gnu/libdl-2.27.so
 7fd07b65b000-7fd07b85a000 ---p 00003000 08:02 1184879                    /lib/x86_64-linux-gnu/libdl-2.27.so
 7fd07b85a000-7fd07b85b000 r--p 00002000 08:02 1184879                    /lib/x86_64-linux-gnu/libdl-2.27.so
 7fd07b85b000-7fd07b85c000 rw-p 00003000 08:02 1184879                    /lib/x86_64-linux-gnu/libdl-2.27.so
 7fd07b85c000-7fd07b8cc000 r-xp 00000000 08:02 1184978                    /lib/x86_64-linux-gnu/libpcre.so.3.13.3
 7fd07b8cc000-7fd07bacc000 ---p 00070000 08:02 1184978                    /lib/x86_64-linux-gnu/libpcre.so.3.13.3
 7fd07bacc000-7fd07bacd000 r--p 00070000 08:02 1184978                    /lib/x86_64-linux-gnu/libpcre.so.3.13.3
 7fd07bacd000-7fd07bace000 rw-p 00071000 08:02 1184978                    /lib/x86_64-linux-gnu/libpcre.so.3.13.3
 7fd07bace000-7fd07bad2000 r-xp 00000000 08:02 1184859                    /lib/x86_64-linux-gnu/libcap-ng.so.0.0.0
 7fd07bad2000-7fd07bcd1000 ---p 00004000 08:02 1184859                    /lib/x86_64-linux-gnu/libcap-ng.so.0.0.0
 7fd07bcd1000-7fd07bcd2000 r--p 00003000 08:02 1184859                    /lib/x86_64-linux-gnu/libcap-ng.so.0.0.0
 7fd07bcd2000-7fd07bcd3000 rw-p 00004000 08:02 1184859                    /lib/x86_64-linux-gnu/libcap-ng.so.0.0.0
 7fd07bcd3000-7fd07beba000 r-xp 00000000 08:02 1184856                    /lib/x86_64-linux-gnu/libc-2.27.so
 7fd07beba000-7fd07c0ba000 ---p 001e7000 08:02 1184856                    /lib/x86_64-linux-gnu/libc-2.27.so
 7fd07c0ba000-7fd07c0be000 r--p 001e7000 08:02 1184856                    /lib/x86_64-linux-gnu/libc-2.27.so
 7fd07c0be000-7fd07c0c0000 rw-p 001eb000 08:02 1184856                    /lib/x86_64-linux-gnu/libc-2.27.so
 7fd07c0c0000-7fd07c0c4000 rw-p 00000000 00:00 0 
 7fd07c0c4000-7fd07c0d8000 r-xp 00000000 08:02 795396                     /usr/lib/sudo/libsudo_util.so.0.0.0
 7fd07c0d8000-7fd07c2d7000 ---p 00014000 08:02 795396                     /usr/lib/sudo/libsudo_util.so.0.0.0
 7fd07c2d7000-7fd07c2d8000 r--p 00013000 08:02 795396                     /usr/lib/sudo/libsudo_util.so.0.0.0
 7fd07c2d8000-7fd07c2d9000 rw-p 00014000 08:02 795396                     /usr/lib/sudo/libsudo_util.so.0.0.0
 7fd07c2d9000-7fd07c2db000 r-xp 00000000 08:02 1185021                    /lib/x86_64-linux-gnu/libutil-2.27.so
 7fd07c2db000-7fd07c4da000 ---p 00002000 08:02 1185021                    /lib/x86_64-linux-gnu/libutil-2.27.so
 7fd07c4da000-7fd07c4db000 r--p 00001000 08:02 1185021                    /lib/x86_64-linux-gnu/libutil-2.27.so
 7fd07c4db000-7fd07c4dc000 rw-p 00002000 08:02 1185021                    /lib/x86_64-linux-gnu/libutil-2.27.so
 7fd07c4dc000-7fd07c501000 r-xp 00000000 08:02 1185001                    /lib/x86_64-linux-gnu/libselinux.so.1
 7fd07c501000-7fd07c700000 ---p 00025000 08:02 1185001                    /lib/x86_64-linux-gnu/libselinux.so.1
 7fd07c700000-7fd07c701000 r--p 00024000 08:02 1185001                    /lib/x86_64-linux-gnu/libselinux.so.1
 7fd07c701000-7fd07c702000 rw-p 00025000 08:02 1185001                    /lib/x86_64-linux-gnu/libselinux.so.1
 7fd07c702000-7fd07c704000 rw-p 00000000 00:00 0 
 7fd07c704000-7fd07c721000 r-xp 00000000 08:02 1184846                    /lib/x86_64-linux-gnu/libaudit.so.1.0.0
 7fd07c721000-7fd07c921000 ---p 0001d000 08:02 1184846                    /lib/x86_64-linux-gnu/libaudit.so.1.0.0
 7fd07c921000-7fd07c922000 r--p 0001d000 08:02 1184846                    /lib/x86_64-linux-gnu/libaudit.so.1.0.0
 7fd07c922000-7fd07c923000 rw-p 0001e000 08:02 1184846                    /lib/x86_64-linux-gnu/libaudit.so.1.0.0
 7fd07c923000-7fd07c92d000 rw-p 00000000 00:00 0 
 7fd07c92d000-7fd07c954000 r-xp 00000000 08:02 1184828                    /lib/x86_64-linux-gnu/ld-2.27.so
 7fd07cb3a000-7fd07cb40000 rw-p 00000000 00:00 0 
 7fd07cb52000-7fd07cb53000 r--p 00000000 08:02 1313324                    /usr/share/locale-langpack/en_GB/LC_MESSAGES/Linux-PAM.mo
 7fd07cb53000-7fd07cb54000 r--p 00000000 08:02 1319369                    /usr/share/locale-langpack/en_GB/LC_MESSAGES/sudoers.mo
 7fd07cb54000-7fd07cb55000 r--p 00027000 08:02 1184828                    /lib/x86_64-linux-gnu/ld-2.27.so
 7fd07cb55000-7fd07cb56000 rw-p 00028000 08:02 1184828                    /lib/x86_64-linux-gnu/ld-2.27.so
 7fd07cb56000-7fd07cb57000 rw-p 00000000 00:00 0 
 7ffe8fd18000-7ffe8fd39000 rw-p 00000000 00:00 0                          [stack]
 7ffe8fd78000-7ffe8fd7b000 r--p 00000000 00:00 0                          [vvar]
 7ffe8fd7b000-7ffe8fd7d000 r-xp 00000000 00:00 0                          [vdso]
 ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
ProcStatus:
 Name:	sudo
 Umask:	0022
 State:	S (sleeping)
 Tgid:	11065
 Ngid:	0
 Pid:	11065
 PPid:	11054
 TracerPid:	0
 Uid:	0	0	0	0
 Gid:	0	0	0	0
 FDSize:	256
 Groups:	0 
 NStgid:	11065
 NSpid:	11065
 NSpgid:	11065
 NSsid:	11054
 VmPeak:	   72972 kB
 VmSize:	   49716 kB
 VmLck:	       0 kB
 VmPin:	       0 kB
 VmHWM:	    4348 kB
 VmRSS:	    3996 kB
 RssAnon:	     540 kB
 RssFile:	    3456 kB
 RssShmem:	       0 kB
 VmData:	     612 kB
 VmStk:	     132 kB
 VmExe:	     136 kB
 VmLib:	    3908 kB
 VmPTE:	     132 kB
 VmSwap:	       0 kB
 HugetlbPages:	       0 kB
 CoreDumping:	1
 Threads:	1
 SigQ:	0/31161
 SigPnd:	0000000000000000
 ShdPnd:	0000000000000000
 SigBlk:	0000000000000000
 SigIgn:	0000000000001000
 SigCgt:	0000000180096a07
 CapInh:	0000000000000000
 CapPrm:	0000003fffffffff
 CapEff:	0000003fffffffff
 CapBnd:	0000003fffffffff
 CapAmb:	0000000000000000
 NoNewPrivs:	0
 Seccomp:	0
 Speculation_Store_Bypass:	thread vulnerable
 Cpus_allowed:	ffff
 Cpus_allowed_list:	0-15
 Mems_allowed:	00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000001
 Mems_allowed_list:	0
 voluntary_ctxt_switches:	9
 nonvoluntary_ctxt_switches:	0
Signal: 11
Uname: Linux 4.15.0-34-generic x86_64
UserGroups: 
CoreDump:
```

---

### Post by TheFu on 2018-09-23
A failing program isn't the same as a system crashing.  Which is it?

Looks like sudo mv and access to a CIFS share is the problem.  CIFS permissions are set at mount time. chmod doesn't have any effect. Neither does sudo from remote systems.

18.04 is an important detail.  I don't have any 18.04 systems here. There are some CIFS differences in the defaults.  If you can, use NFS, not CIFS.  NFS supports native file and directory permissions.

Which logs?  Any that have errors or warnings.  Use grep to find those.

But I'm back to the my first point.  Fix the permissions issues. That is likely causing the problems.  If you need to use sudo, then the setup is wrong.  IMHO.

---

