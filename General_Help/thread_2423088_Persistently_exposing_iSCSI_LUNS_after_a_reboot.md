---
title: "Persistently exposing iSCSI LUNS after a reboot"
date: 2019-07-17
forum: General Help
---

### Post by Neil_Sherin on 2019-07-17
Hiya,

I've just set up an Ubuntu 18.04 VM with a second 10GB drive as a test  that I want to set up as block storage over iSCSI. The problem is, when I  reboot the iSCSI target VM, the LUN dos not show up when running [COLOR=#000000][FONT=&amp][FONT=courier new]tgtadm --mode target --op show[/FONT][FONT=arial]

Running a [FONT=century gothic]systemctl restart [/FONT]fixes the issue and the LUN shows up as LUN 1 when running [/FONT][FONT=courier new]tgtadm --mode target --op show[/FONT]

[FONT=arial]Here's what I did to set up an iSCSI target:

[/FONT][/FONT][FONT=Arial]Assume:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][FONT=courier new]/dev/sdb[/FONT] is the disk to use as an iSCSI LUN[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]iqn.2019-07.local.nsnetworks:netstorage[/FONT][FONT=Arial][FONT=courier new] [/FONT]is the target name[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]192.168.1.30 [/FONT][FONT=Arial]is the IP address of the iSCSI target portal[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Setting up the target:[/FONT][/COLOR]



[LIST]
[*]Install required packages: 
[/LIST]


[FONT=courier new][COLOR=#000000]sudo su -[/COLOR]
[COLOR=#000000]apt install -y tgt[/COLOR][/FONT]



[LIST]
[*]Create iSCSI target (tid 1) 
[/LIST]


[FONT=courier new][COLOR=#000000]tgtadm --lld iscsi --op new --mode target --tid 1 -T iqn.2019-07.local.nsnetworks:netstorage[/COLOR][/FONT]



[LIST]
[*]Add logical Unit (lun 1) to iSCSI target (Target ID 1) 
[/LIST]

[FONT=courier new]
[COLOR=#000000]tgtadm --lld iscsi --op new --mode logicalunit --tid 1 --lun 1 -b /dev/sdb[/COLOR][/FONT]



[LIST]
[*]Publish iSCSI target (tid 1) to all IP address 
[/LIST]
[FONT=courier new]

[COLOR=#000000]tgtadm --lld iscsi --op bind --mode target --tid 1 -I ALL[/COLOR][/FONT]



[LIST]
[*]Save configuration for iSCSI target. If you do not save configuration, configuration will be removed after restarting tgtd 
[/LIST]
[FONT=courier new]

[COLOR=#000000]tgt-admin --dump |grep -v default-driver > /etc/tgt/conf.d/disk.conf
[/COLOR][/FONT]


[LIST]
[*]Enable service: 
[/LIST]


[FONT=courier new][COLOR=#000000]systemctl enable tgt[/COLOR][/FONT]



[LIST]
[*]Show status 
[/LIST]
[FONT=courier new]

[/FONT][COLOR=#000000][FONT=&amp][FONT=courier new]tgtadm --mode target --op show


[FONT=arial]I then tried to set up a udev mapping to see if that would resolve the issue:[/FONT]

[/FONT][/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]Create udev rule for proper device mapping of sdX to iscsi_X on boot[/FONT][/COLOR] 
[/LIST]

[COLOR=#000000][FONT=Arial]Change /etc/tgt/conf.d/disks.conf to read:

[FONT=courier new]<target iqn.2019-07.local.nsnetworks:netstorage>
        backing-store /dev/iscsi_1
</target>[/FONT]

Using sdb as an example:

[/FONT][/COLOR][FONT=courier new][COLOR=#000000]udevadm info --query=property --name=/dev/sdb[/COLOR][/FONT]

[COLOR=#000000][FONT=Arial]Make a note of the values of:[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ID_SCSI_SERIAL[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ID_SERIAL[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ID_SERIAL_SHORT[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Create symbolic link for iscsi_1 mapping:[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]ln -s /dev/sdb /dev/iscsi_1[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Set up udev rule:[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]nano /etc/udev/rules.d/70-persistent-drive.rules[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Add the following:[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]SUBSYSTEM=="block",  ENV{ID_SCSI_SERIAL}=="6000c29831ec9a7d45dc007e6439a6d6",  ENV{ID_SERIAL}=="36000c29831ec9a7d45dc007e6439a6d6",  ENV{ID_SERIAL_SHORT}="6000c29831ec9a7d45dc007e6439a6d6".  SYMLINK+="iscsi_1"[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Reload udev rules:[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]udevadm control --reload-rules && udevadm trigger
[FONT=arial]
On reboot, it still does not expose the LUN. I have to do the following to get the LUN exposed:

[FONT=courier new]ln -s /dev/sdb /dev/iscsi_1
[/FONT][/FONT][/FONT][/COLOR][FONT=courier new][COLOR=#000000]udevadm control --reload-rules && udevadm trigger
systemctl tgt restart


[SIZE=2][FONT=arial]Any help would be much appreciated! Many thanks in advance![/FONT][/SIZE][/COLOR]
[/FONT][COLOR=#000000][FONT=&amp][FONT=courier new]
[/FONT]
[/FONT][/COLOR]

---

### Post by Irihapeti on 2019-07-17
Thread closed.[B][I]
[/I][/B]
Please do not post duplicate messages. It causes confusion and makes it harder for people to help.

---

