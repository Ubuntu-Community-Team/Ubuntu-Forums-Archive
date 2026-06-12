---
title: "Kernel 3.13.0-58 won’t boot [14.04]"
date: 2015-07-24
forum: General Help
---

### Post by seanos on 2015-07-24
-57 boots fine. Can anyone help me diagnose this? dpkg.log shows no errors. I’m a little uncertain about what to look for in other logs.

Boot gets as far as Plymouth (i.e. logo appears) but is then unresponsive and I have to reset.

---

### Post by TheDreamer on 2015-07-24
Had intended to respond sooner....

My headless (vm) server, at home, wouldn't boot after auto upgrade and reboot to this kernel, it couldn't find my lvm root (/dev/mapper/uzen-root)  Rolled it back to bi-weekly snapshot which had last taken place just hours before unattended-upgrades ran.  My first thought was something had gotten corrupted, forced an fsck, etc. everything seemed fine....until unattended-upgrades ran this morning and took it to 3.13.0-58 again.  While I was mulling things over and I happened to do a search on "3.13.0-58" and found this post.  So, I caught the boot and switched back to -57 and its working.

But, the problem isn't limited to 14.04 servers, as I found my 12.04 systems at work (the ones where we have unattended-upgrades working...) were down....same problem.  Upgraded to 3.2.0-88, can't find /dev/mapper/vg0-root .... rebooting it to previous kernel (3.2.0-87) got it going again.  Though now that I think of it, I forgot to change GRUB default...should make the stay on this kernel for now (though they don't reboot unpredictably like my stuff at home ;)

The Dreamer

---

### Post by seanos on 2015-07-28
Kernel 3.13.0-58 arrived today and it’s the same story.

Booting in recovery mode worked, but I don’t know why. I think this is the end of kernel.log before my latest hard boot...

```
Jul 28 18:24:38 nung kernel: [   10.433455] vboxdrv: Found 8 processor cores.
Jul 28 18:24:38 nung kernel: [   10.433940] vboxdrv: fAsync=0 offMin=0x22f offMax=0x15a1
Jul 28 18:24:38 nung kernel: [   10.433999] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jul 28 18:24:38 nung kernel: [   10.434001] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
Jul 28 18:24:38 nung kernel: [   10.444952] vboxpci: IOMMU not found (not registered)
Jul 28 18:24:38 nung kernel: [   10.591173] BUG: unable to handle kernel NULL pointer dereference at           (null)
Jul 28 18:24:38 nung kernel: [   10.591177] IP: [<ffffffff81729f8b>] __down_common+0x4c/0x144
Jul 28 18:24:38 nung kernel: [   10.591181] PGD 0 
Jul 28 18:24:38 nung kernel: [   10.591183] Oops: 0002 [#1] SMP 
Jul 28 18:24:38 nung kernel: [   10.591184] Modules linked in: pci_stub vboxpci(OX) vboxnetadp(OX) vboxnetflt(OX) vboxdrv(OX) rfcomm bnep binfmt_misc snd_hda_codec_hdmi nvidia(POX+) intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp snd_hda_intel(+) kvm_intel snd_hda_codec snd_ctxfi snd_hwdep kvm snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul snd_rawmidi ghash_clmulni_intel snd_seq aesni_intel aes_x86_64 snd_seq_device snd_timer lrw gf128mul gpio_ich glue_helper snd joydev mxm_wmi btusb ablk_helper bluetooth soundcore cryptd drm parport_pc mei_me mei ppdev wmi shpchp serio_raw lpc_ich mac_hid lp parport nls_iso8859_1 hid_generic hid_microsoft usbhid hid ahci psmouse r8169 libahci mii
Jul 28 18:24:38 nung kernel: [   10.591209] CPU: 0 PID: 1476 Comm: Xorg Tainted: P           OX 3.13.0-59-generic #98-Ubuntu
Jul 28 18:24:38 nung kernel: [   10.591211] Hardware name: MSI MS-7681/Z68A-GD55 (G3) (MS-7681), BIOS V23.7 02/21/2012
Jul 28 18:24:38 nung kernel: [   10.591212] task: ffff880464214800 ti: ffff88000ba80000 task.ti: ffff88000ba80000
Jul 28 18:24:38 nung kernel: [   10.591213] RIP: 0010:[<ffffffff81729f8b>]  [<ffffffff81729f8b>] __down_common+0x4c/0x144
Jul 28 18:24:38 nung kernel: [   10.591215] RSP: 0018:ffff88000ba81b18  EFLAGS: 00010096
Jul 28 18:24:38 nung kernel: [   10.591216] RAX: 0000000000000000 RBX: ffffffffa0e21430 RCX: 0000000000000000
Jul 28 18:24:38 nung kernel: [   10.591217] RDX: ffffffffa0e21438 RSI: ffff88000ba81b20 RDI: ffffffffa0e21430
Jul 28 18:24:38 nung kernel: [   10.591218] RBP: ffff88000ba81b68 R08: 0000000000000296 R09: ffffffffa0a1f8eb
Jul 28 18:24:38 nung kernel: [   10.591218] R10: 0000000000000035 R11: ffffffffffffffc0 R12: 7fffffffffffffff
Jul 28 18:24:38 nung kernel: [   10.591219] R13: ffff880464214800 R14: 0000000000000002 R15: 0000000000000000
Jul 28 18:24:38 nung kernel: [   10.591221] FS:  00007f1e366f09c0(0000) GS:ffff88047f400000(0000) knlGS:0000000000000000
Jul 28 18:24:38 nung kernel: [   10.591222] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jul 28 18:24:38 nung kernel: [   10.591223] CR2: 0000000000000000 CR3: 000000043e673000 CR4: 00000000000407f0
Jul 28 18:24:38 nung kernel: [   10.591223] Stack:
Jul 28 18:24:38 nung kernel: [   10.591224]  ffff88047f7eee08 ffffffffa0e21438 0000000000000000 ffff88046355b778
Jul 28 18:24:38 nung kernel: [   10.591226]  0000000000000000 ffffffffa0e21430 ffff880466930000 ffff8804633be800
Jul 28 18:24:38 nung kernel: [   10.591228]  0000000000000002 00000000000000ff ffff88000ba81b78 ffffffff8172a0a0
Jul 28 18:24:38 nung kernel: [   10.591230] Call Trace:
Jul 28 18:24:38 nung kernel: [   10.591233]  [<ffffffff8172a0a0>] __down+0x1d/0x1f
Jul 28 18:24:38 nung kernel: [   10.591235]  [<ffffffff810b0f71>] down+0x41/0x50
Jul 28 18:24:38 nung kernel: [   10.591285]  [<ffffffffa0a1fcc7>] nvidia_open+0x467/0x930 [nvidia]
Jul 28 18:24:38 nung kernel: [   10.591322]  [<ffffffffa0a2abb9>] nvidia_frontend_open+0x49/0xa0 [nvidia]
Jul 28 18:24:38 nung kernel: [   10.591324]  [<ffffffff811c2ccf>] chrdev_open+0x9f/0x1d0
Jul 28 18:24:38 nung kernel: [   10.591327]  [<ffffffff811bb803>] do_dentry_open+0x233/0x2e0
Jul 28 18:24:38 nung kernel: [   10.591328]  [<ffffffff811c2c30>] ? cdev_put+0x30/0x30
Jul 28 18:24:38 nung kernel: [   10.591330]  [<ffffffff811bbb39>] vfs_open+0x49/0x50
Jul 28 18:24:38 nung kernel: [   10.591332]  [<ffffffff811ccee4>] do_last+0x564/0x1240
Jul 28 18:24:38 nung kernel: [   10.591334]  [<ffffffff811ca9a1>] ? link_path_walk+0x71/0x880
Jul 28 18:24:38 nung kernel: [   10.591336]  [<ffffffff81315ebb>] ? apparmor_file_alloc_security+0x5b/0x180
Jul 28 18:24:38 nung kernel: [   10.591338]  [<ffffffff811cdc7b>] path_openat+0xbb/0x650
Jul 28 18:24:38 nung kernel: [   10.591341]  [<ffffffff812d80ae>] ? security_inode_alloc+0x1e/0x20
Jul 28 18:24:38 nung kernel: [   10.591343]  [<ffffffff811d7eac>] ? inode_init_always+0x11c/0x1e0
Jul 28 18:24:38 nung kernel: [   10.591346]  [<ffffffff811e4508>] ? simple_xattr_get+0x68/0xb0
Jul 28 18:24:38 nung kernel: [   10.591348]  [<ffffffff811cf07a>] do_filp_open+0x3a/0x90
Jul 28 18:24:38 nung kernel: [   10.591350]  [<ffffffff811dbf17>] ? __alloc_fd+0xa7/0x130
Jul 28 18:24:38 nung kernel: [   10.591351]  [<ffffffff811bd659>] do_sys_open+0x129/0x280
Jul 28 18:24:38 nung kernel: [   10.591353]  [<ffffffff811de334>] ? mntput+0x24/0x40
Jul 28 18:24:38 nung kernel: [   10.591355]  [<ffffffff811c803e>] ? path_put+0x1e/0x30
Jul 28 18:24:38 nung kernel: [   10.591356]  [<ffffffff811bd7ce>] SyS_open+0x1e/0x20
Jul 28 18:24:38 nung kernel: [   10.591358]  [<ffffffff81734294>] system_call_fastpath+0x16/0x1b
Jul 28 18:24:38 nung kernel: [   10.591359] Code: 54 49 89 d4 48 8d 57 08 53 48 89 fb 48 83 e4 f0 48 83 ec 28 48 8b 47 10 48 8d 74 24 08 48 89 54 24 08 48 89 44 24 10 48 89 77 10 <48> 89 30 4c 89 f0 4c 89 6c 24 18 83 e0 01 c6 44 24 20 00 48 89 
Jul 28 18:24:38 nung kernel: [   10.591375] RIP  [<ffffffff81729f8b>] __down_common+0x4c/0x144
Jul 28 18:24:38 nung kernel: [   10.591376]  RSP <ffff88000ba81b18>
Jul 28 18:24:38 nung kernel: [   10.591377] CR2: 0000000000000000
Jul 28 18:24:38 nung kernel: [   10.591379] ---[ end trace 770f826f5a198c95 ]---
Jul 28 18:24:38 nung kernel: [   10.984476] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.1/0000:02:00.1/sound/card2/input15
Jul 28 18:24:38 nung kernel: [   10.984559] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.1/0000:02:00.1/sound/card2/input14
Jul 28 18:24:38 nung kernel: [   10.984629] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.1/0000:02:00.1/sound/card2/input13
Jul 28 18:24:38 nung kernel: [   10.984694] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/0000:02:00.1/sound/card2/input12
Jul 28 18:24:38 nung kernel: [   10.985197] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
Jul 28 18:24:38 nung kernel: [   10.985256] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
Jul 28 18:24:40 nung kernel: [   12.604604] r8169 0000:08:00.0 eth0: link up
Jul 28 18:24:40 nung kernel: [   12.604612] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 28 18:24:41 nung kernel: [   13.838741] FS-Cache: Loaded
Jul 28 18:24:41 nung kernel: [   13.846311] FS-Cache: Netfs 'cifs' registered for caching
Jul 28 18:24:41 nung kernel: [   13.846360] Key type cifs.spnego registered
Jul 28 18:24:41 nung kernel: [   13.846367] Key type cifs.idmap registered
Jul 28 18:25:08 nung kernel: [   40.156130] audit_printk_skb: 150 callbacks suppressed
Jul 28 18:25:08 nung kernel: [   40.156133] type=1400 audit(1438071908.285:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1832 comm="apparmor_parser"
Jul 28 18:25:08 nung kernel: [   40.156138] type=1400 audit(1438071908.285:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1832 comm="apparmor_parser"
Jul 28 18:25:08 nung kernel: [   40.156415] type=1400 audit(1438071908.285:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1832 comm="apparmor_parser"
```

Any ideas?

---

### Post by dino99 on 2015-07-28
Looks like a buggy kernel (report against it with the above dmesg oops) then you can unistall it & ignore it

---

### Post by seanos on 2015-07-28
Seems odd that it&#8217;s two releases in a row. I just tried choosing &#8220;Advanced options&#8230;&#8221; from the grub menu and loading the *same* kernel version (3.13.0-59) and had no problem!

I wonder if it&#8217;s something to do with grub?

---

### Post by TheDreamer on 2015-08-02
Don't know about selecting 3.13.0-59 through advanced options (it got autoremoved by the time I thought to revisit this, and not do the reason I was on the server ;)...but letting my system boot from 3.13.0-61 still fails, and selecting it through advanced options also fails.  Staying put with 3.13.0-57

---

### Post by seanos on 2015-08-03
3.13.0-61 works for me.

---

### Post by TheDreamer on 2015-09-06
3.13.0-61 still doesn't work for me, neither does 3.13.0-63

Had noticed that acpi_reserve_resources is missing in Symbols between 57 and 63, tracked down a reference of this:

[http://ubuntu.5.x6.nabble.com/3-13-y-ckt-stable-Patch-quot-ACPI-PNP-Reserve-ACPI-resources-at-the-fs-initcall-sync-stage-quot-has-e-td5108495.html](http://ubuntu.5.x6.nabble.com/3-13-y-ckt-stable-Patch-quot-ACPI-PNP-Reserve-ACPI-resources-at-the-fs-initcall-sync-stage-quot-has-e-td5108495.html)

where the 3.13 tag that comes after it was 28 hours ago, which seems to match me getting -63 yesterday.

Meanwhile....have let it sit at the '(initramfs)' prompt....it emitted a messages of:

    random: lvm urandom read with 111 bits of entropy available
    random: random: nonblocking pool is initialized

Around 51.xx seconds.

After which doing an 'lvm vgchange -ay' and exit got things up and running.

So, I tried a rootdelay=60,  The messages where then delayed to 61.xx seconds with it still giving up.

So, I tried a rootdelay=100, The messages where then delayed to 102.xx seconds with it still giving up.

If I set rootdelay=31536000, it'll probably still not work.

Not sure why it needs to wait at all...its a VM with virtualized storage on SSD, not a drum.

So, did some more digging around....noticed that on July 15th, udev in initframfs-tools got touched for some reason...which is after -57....

Hmmm, never mind....had snuck in a patch that was supposed to fix another lvm boot problem I've been plagued with...which made things worse instead....though its an old problem that I've found launchpad bugs currently against 14.10, still getting recent comments, an older one that was again 12.04 (where I first ran into the issue myself), but saw references going back to edgy...

Probably explains why there were no differences in any of the udev files that got newer.  But, perhaps upstream is also working on the issue.... the latest finger pointed at udev being the issue...  my fix attempt was a modification to a udev rule. 

Though with the rule changed back...boots now take longer....about 25 seconds for root, but to finish the other vg and lv's its 104s....   When it kills the udev process, and then some more delay to 120+ before it takes off... but at least things are working...  until the other problem is hit again....  had disabled reboots on servers remote from me (which normally aren't, except that I've been working remote lately ;)  Guess I'll continue with trying to perfect my unattended reboot script.

The Dreamer.

---

