---
title: "Accessing files I don\t have access to."
date: 2017-06-25
forum: General Help
---

### Post by Nargluj on 2017-06-25
Hello!

My PC is old and half/broken and does stuff that makes me hate it. Now root is full and I\m stuck typing this on a bootable USB/drive with a keyboard layout I don\t know. Please help, even moving my mouse is hard and I\m already starting to feel slight pain in my wrist.

[img]http://i.imgur.com/BKdEQcM.jpg[/img]

I\ve found the files I need to delete *13 gigs of log files_ amazing!(. Unfortunately I\m bad at doing things in Linux. My original partition with OS is un/bootable.

Please help
Very much sincere and soon desperate
Lukas

---

### Post by oldos2er on 2017-06-25
Try ```
sudo rm /var/log/*.gz
``` in a terminal to remove archived log files. I don't think that will gain you much space though.

Which version of Ubuntu are you using? You may have unneeded kernels installed.

---

### Post by deadflowr on 2017-06-25
You should really look at what those rather large log files are trying to tell you.
They are an indicator of something not right.
Removing them would only be a stopgap and soon enough, you'll have to remove them again... and again... and again.

Take a quick peak at what the end of the file tells you with tail, like
```
tail /var/log/syslog
```
typically rogue logfiles contain repeating lines of which can show whatever the problems are.

---

### Post by efflandt on 2017-06-25
The reason your system cut you off after using 18.5 GB of 20 GB is because it reserves a certain percentage for root (to possibly log what went wrong or so root could fix things).

Did you disable cron or something? Normally a logrotate script in /etc/cron.daily/ starts new logs, compresses old ones, and eventually deletes old compressed logs. For example this is what my system shows for those logs:```
/var/log$ ls -l syslog*
-rw-r----- 1 syslog adm 199161 Jun 25 10:58 syslog
-rw-r----- 1 syslog adm  78924 Jun 25 07:35 syslog.1
-rw-r----- 1 syslog adm  61036 Jun 24 07:35 syslog.2.gz
-rw-r----- 1 syslog adm 260710 Jun 23 07:35 syslog.3.gz
-rw-r----- 1 syslog adm  79036 Jun 22 07:35 syslog.4.gz
-rw-r----- 1 syslog adm  22775 Jun 21 07:35 syslog.5.gz
-rw-r----- 1 syslog adm  15820 Jun 20 07:35 syslog.6.gz
-rw-r----- 1 syslog adm   7195 Jun 19 07:35 syslog.7.gz

/var/log$ ls -l kern*
-rw-r----- 1 syslog adm 117950 Jun 25 10:58 kern.log
-rw-r----- 1 syslog adm 746772 Jun 25 07:35 kern.log.1
-rw-r----- 1 syslog adm  33844 Jun 19 07:35 kern.log.2.gz
-rw-r----- 1 syslog adm  32872 Jun 11 07:35 kern.log.3.gz
-rw-r----- 1 syslog adm 100205 Jun  5 07:35 kern.log.4.gz
```As you can see, they are just multiple KB files, not single GB files.

My first thought was to have you try using "gksu nautilus" (to run the File Manager as root), but I do not know if that would allow you to "Delete" files or would only allow you to "Move to Trash" (which you do not have room for). But the old fashioned way (using the terminal) should work.

From the live/install system in a live session, press Ctrl+Alt+T to open a terminal, then```
cd /media/ubuntu
ls
```If there is only on thing listed that is the hex UUID of your Ubuntu partition on your had drive type cd, then a space, then the first few letters/numbers of the UUID, then Tab key. That should bring in the whole UUID and hit Enter key. From there```
cd var/log
ls
```You should now be in a path similar to /media/ubuntu/uuid_of_partition/var/log and see a list of logs including that syslog and kern.log. Then do```
sudo rm syslog* kern*
ls
```And those logs should be gone. Shut down the live system and see if your hard drive boots.

I am not sure why logrotate (or cron) is not working on your system, so you will need to keep an eye on those logs and make sure they do not become too big. If they do, try to run the following from a terminal and see if you get any errors (don't just delete them while running on that system)(carefully blindly enter your normal password when sudo asks for it)```
sudo /etc/cron.daily/logrotate
```

---

### Post by Nargluj on 2017-06-25
Hello again and thanks for the replays.

My USB-drive crashed some where while opening up the log files. Which deleted my first attempt at a reply.

I've got the files removed and I'm up and running again. No more panic. *Deep sigh of relief*

Before I deleted the log file I got some, which I thought was, useful pieces. Will try to post it in a friendly-to-read way.

```
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.859467] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.867469] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.868968] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889264] ieee80211 phy0: rt2800pci_mcu_status: Error - MCU request failed, no response from hardware 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889283] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889291] BUG: scheduling while atomic: ksoftirqd/5/33/0x00000100 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889293] Modules linked in: snd_hda_codec_hdmi binfmt_misc nvidia_uvm(POE) kvm_amd kvm irqbypass edac_mce_amd drbg serio_raw edac_core ansi_cprng k10temp xts arc4 gf128mul rt2800pci dm_crypt rt2800mmio rt2800lib rt2x00pci rt2x00mmio rt2x00lib mac80211 snd_hda_codec_realtek snd_hda_codec_generic input_leds joydev snd_hda_intel cfg80211 snd_hda_codec snd_seq_midi snd_seq_midi_event snd_hda_core snd_rawmidi snd_hwdep eeprom_93cx6 crc_ccitt snd_seq snd_pcm snd_seq_device snd_timer snd soundcore shpchp i2c_piix4 ite_cir 8250_fintek tpm_infineon rc_core wmi mac_hid parport_pc ppdev lp parport autofs4 dm_mirror dm_region_hash dm_log uas usb_storage hid_generic usbhid hid nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper psmouse syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 drm mii ahci libahci fjes 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889334] CPU: 5 PID: 33 Comm: ksoftirqd/5 Tainted: P           OE   4.4.0-81-generic #104-Ubuntu 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889336] Hardware name: Packard Bell ixtreme M5140/ixtreme M5140, BIOS P01-A2 04/21/2010 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889338]  0000000000000286 00000000b3641c6c ffff88019835fb50 ffffffff813f9683 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889340]  ffff88019fd56dc0 0000000000000000 ffff88019835fb60 ffffffff810a64db 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889342]  ffff88019835fbb0 ffffffff8183c616 0000000000000000 0000000000000005 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889344] Call Trace: 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889350]  [<ffffffff813f9683>] dump_stack+0x63/0x90 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889354]  [<ffffffff810a64db>] __schedule_bug+0x4b/0x60 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889357]  [<ffffffff8183c616>] __schedule+0x726/0xa30 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889359]  [<ffffffff8183c955>] schedule+0x35/0x80 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889361]  [<ffffffff8183cbfe>] schedule_preempt_disabled+0xe/0x10 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889364]  [<ffffffff810ca570>] mutex_optimistic_spin+0x170/0x1b0 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889366]  [<ffffffff8183e7bf>] __mutex_lock_slowpath+0x3f/0x130 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889369]  [<ffffffff81003079>] ? trace_raw_output_sys_enter+0x79/0xa0 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889371]  [<ffffffff8183e8cf>] mutex_lock+0x1f/0x30 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889377]  [<ffffffffc0fdfb14>] rt2800_mcu_request.part.14+0x44/0xf0 [rt2800lib] 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889381]  [<ffffffffc0fdfbe5>] rt2800_mcu_request+0x25/0x30 [rt2800lib] 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889384]  [<ffffffffc10004b0>] rt2800pci_set_device_state+0x120/0x144 [rt2800pci] 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889387]  [<ffffffffc0fe98b6>] rt2800_config+0x256/0x2e0 [rt2800lib] 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889391]  [<ffffffffc0ffac37>] rt2800mmio_autowake_tasklet+0x67/0xe0 [rt2800mmio] 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889394]  [<ffffffff810857fb>] tasklet_action+0xfb/0x110 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889396]  [<ffffffff81085e01>] __do_softirq+0x101/0x290 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889399]  [<ffffffff810a3ed0>] ? sort_range+0x30/0x30 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889401]  [<ffffffff81085fb8>] run_ksoftirqd+0x28/0x50 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889403]  [<ffffffff810a3fd5>] smpboot_thread_fn+0x105/0x160 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889405]  [<ffffffff810a0c25>] kthread+0xe5/0x100 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889407]  [<ffffffff810a0b40>] ? kthread_create_on_node+0x1e0/0x1e0 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889410]  [<ffffffff81840e0f>] ret_from_fork+0x3f/0x70 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889412]  [<ffffffff810a0b40>] ? kthread_create_on_node+0x1e0/0x1e0 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889465] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889472] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889476] NOHZ: local_softirq_pending 40 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889587] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889594] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889598] NOHZ: local_softirq_pending 40 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889655] NOHZ: local_softirq_pending 40 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889712] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889717] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889725] NOHZ: local_softirq_pending 40 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889836] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889841] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889849] NOHZ: local_softirq_pending 40 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889961] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889966] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.889971] NOHZ: local_softirq_pending 40 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.890086] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.890090] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.890094] NOHZ: local_softirq_pending 40 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.890211] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.890215] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.890219] NOHZ: local_softirq_pending 50 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.890763] NOHZ: local_softirq_pending 40 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.894101] NOHZ: local_softirq_pending 40 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.903470] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.903479] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.904212] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.904216] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.910964] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.910969] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.912466] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.912470] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.929299] ieee80211 phy0: rt2800pci_mcu_status: Error - MCU request failed, no response from hardware 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.929303] softirq: huh, entered softirq 6 TASKLET ffffffff81085700 with preempt_count 00000100, exited with 00000000? 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  495.959267] ieee80211 phy0: rt2800pci_mcu_status: Error - MCU request failed, no response from hardware 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  496.191304] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  496.191348] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  496.191417] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  496.198665] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  496.199417] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  496.206918] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  496.208417] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  496.221308] ieee80211 phy0: rt2800pci_mcu_status: Error - MCU request failed, no response from hardware 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  496.221435] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  496.221913] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  496.229914] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:14:02 lukas-ixtreme-M5140 kernel: [  496.231410] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
 
 
 
  
 
//This is my cut in the text, no one else's. 
 
 
 
 
 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155218] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155227] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155230] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155237] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155245] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155255] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155258] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155265] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155274] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155284] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155286] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155294] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155302] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155314] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155318] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155324] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155335] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155338] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155345] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155355] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155364] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155367] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155374] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155383] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155392] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155395] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155402] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155410] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155420] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155422] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155430] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155438] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155448] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155451] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155458] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155466] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155474] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155484] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155487] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155494] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155502] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155512] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155514] ieee80211 phy0: rt2800mmio_txdone: Warning - Got TX status for an empty queue 3, dropping 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155525] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155534] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report 
Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155543] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report
```
The last part kept on repeating.

Also, I forgot to add and/or clarify, I'm quite sure I've got something in my hardware that's broken. About ten year old PC that's been used _a lot_. I've had some issues with it starting to work endlessly for no reason, some times it freezes when it does that.

---

### Post by CatKiller on 2017-06-25
From a tiny letterbox view of the output you posted (I'm reading the forum on my phone), it seems to me like memory dumps from a wireless driver.

---

### Post by Habitual on 2017-06-26
> **Nargluj said:**
> Jun 25 13:16:48 lukas-ixtreme-M5140 kernel: [  662.155543] ieee80211 phy0: rt2800mmio_txstatus_interrupt: Warning - TX status FIFO overrun, drop tx status report[/CODE]
The last part kept on repeating.
Network card, driver, kerrnel?

---

