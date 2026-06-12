---
title: "Problems with Suspend After 13.10 Upgrade (Gnome)"
date: 2013-10-26
forum: General Help
---

### Post by Dan Again on 2013-10-26
My computer is not suspending since I upgraded to 13.10. I see a Gnome notification at the bottom of my screen telling me that my computer is about to suspend due to lack of activity, but it just remains on. Where is the suspend behavior defined and where can I see log files detailing what happens when my computer tries to suspend?

---

### Post by Toz on 2013-10-26
The suspend log file is located at **/var/log/pm-suspend.log**. 

Can you suspend manually via:
```
sudo pm-suspend
```
...and resume successfully?

---

### Post by Dan Again on 2013-10-26
I was able to suspend with the command that you provided, but there was an error on resume. Prior to posting this topic, I ran ```
sudo pm-hibernate
```which executed and resumed properly.

---

### Post by Toz on 2013-10-26
Can you post back the contents of /var/log/pm-suspend.log like this:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

---

### Post by Dan Again on 2013-11-01
Hey, thanks for the reply and sorry it's taken me so long to get back. That file is actually empty.

---

### Post by Toz on 2013-11-01
> **Dan Again said:**
> Hey, thanks for the reply and sorry it's taken me so long to get back. That file is actually empty.

Can you post back the results of the following command:
```
ls -l /var/log
```

---

### Post by Dan Again on 2013-11-02
Ah, yes...look what I found

```

ls /var/log | grep pm-suspend.log
pm-suspend.log
pm-suspend.log.1
pm-suspend.log.2.gz
pm-suspend.log.3.gz
pm-suspend.log.4.gz

```

[PasteBin]("http://paste.ubuntu.com/6349788")

---

### Post by Toz on 2013-11-02
Thanks for the file. I can see from the file that hibernate is working but not suspend, unfortunately, there is nothing there to show why this is happening. Can you run the following command and post back the results:
```
cat /var/log/syslog | grep PM:
```
I'd also be interested in seeing the results of these commands:
```
cat /proc/cmdline
```
```
ls -l /etc/pm/config.d/
```
```
lspci
```
```
lspci -t
```

---

### Post by Dan Again on 2013-11-03
```

dan@MyDesktop:~$ cat /var/log/syslog | grep PM:
dan@MyDesktop:~$ 

```

```

dan@MyDesktop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=b606ea87-2c34-4c68-a9cd-f87855749b6f ro quiet splash vt.handoff=7

```

```

dan@MyDesktop:~$ ls -l /etc/pm/config.d/
total 0

```

```

dan@MyDesktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation H77 Express Chipset LPC Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 7 Series/C210 Series Chipset Family 4-port SATA Controller [IDE mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
00:1f.5 IDE interface: Intel Corporation 7 Series/C210 Series Chipset Family 2-port SATA Controller [IDE mode] (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

```

dan@MyDesktop:~$ lspci -t
-[0000:00]-+-00.0
           +-02.0
           +-14.0
           +-16.0
           +-1a.0
           +-1b.0
           +-1c.0-[01]----00.0
           +-1c.3-[02]----00.0
           +-1d.0
           +-1f.0
           +-1f.2
           +-1f.3
           \-1f.5

```

---

### Post by Dan Again on 2013-11-03
I think that the problems may be related to changes I made to the following, but I can't remember exactly what I did...

```

/usr/share/polkit-1/actions/org.freedesktop.upower.policy
/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla

```

```

dan@MyDesktop:~$ cat /usr/share/polkit-1/actions/org.freedesktop.upower.policy
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>
  <vendor>The UPower Project</vendor>
  <vendor_url>http://upower.freedesktop.org/</vendor_url>
  <icon_name>system-suspend</icon_name>

  <action id="org.freedesktop.upower.suspend">
    <description>Suspend the system</description>
    <description xml:lang="fr">Mettre le système en veille</description>
    <description xml:lang="it">Sospende il sistema</description>
    <description xml:lang="pl">Wstrzymanie systemu</description>
    <description xml:lang="sv">Försätt systemet i vänteläge</description>
    <message>Authentication is required to suspend the system</message>
    <message xml:lang="fr">Vous devez vous identifier pour mettre le système en veille</message>
    <message xml:lang="it">È richiesto autenticarsi per sospendere il sistema</message>
    <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby wstrzyma&#263; system</message>
    <message xml:lang="sv">Autentisering krävs för att försätta systemet i vänteläge</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.upower.hibernate">
    <description>Hibernate the system</description>
    <description xml:lang="fr">Mettre le système en hibernation</description>
    <description xml:lang="it">Iberna il sistema</description>
    <description xml:lang="pl">Hibernacja systemu</description>
    <description xml:lang="sv">Försätt systemet i viloläge</description>
    <message>Authentication is required to hibernate the system</message>
    <message xml:lang="fr">Vous devez vous identifier pour mettre le système en hibernation</message>
    <message xml:lang="it">È richiesto autenticarsi per ibernare il sistema</message>
    <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zahibernowa&#263; system</message>
    <message xml:lang="sv">Autentisering krävs för att försätta systemet i viloläge</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

</policyconfig>

```

```

dan@MyDesktop:~$ sudo cat /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
[sudo] password for dan: 
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

```

---

### Post by Toz on 2013-11-03
Try this command instead (it should return something):
```
cat /var/log/syslog* | grep PM:
```
...if it still returns nothing, try suspending th machine and when you recover, run the command again.

> I think that the problems may be related to changes I made to the following, but I can't remember exactly what I did...
```

/usr/share/polkit-1/actions/org.freedesktop.upower.policy
/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```
**/usr/share/polkit-1/actions/org.freedesktop.upower.policy** is the same as the one on my system, so no changes.
**/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla** I don't have. This file enables hibernation. I don't think it would affect suspend.

---

### Post by Dan Again on 2013-11-03
```

dan@MyDesktop:~$ cat /var/log/syslog* | grep PM:
Nov  3 11:33:02 MyDesktop kernel: [169813.860370] PM: Marking nosave pages: [mem 0x0009e000-0x000fffff]
Nov  3 11:33:02 MyDesktop kernel: [169813.860375] PM: Marking nosave pages: [mem 0x20000000-0x201fffff]
Nov  3 11:33:02 MyDesktop kernel: [169813.860381] PM: Basic memory bitmaps created
Nov  3 11:33:37 MyDesktop kernel: [169813.860382] PM: Syncing filesystems ... done.
Nov  3 11:33:37 MyDesktop kernel: [169813.877606] PM: Preallocating image memory... done (allocated 524643 pages)
Nov  3 11:33:37 MyDesktop kernel: [169814.123739] PM: Allocated 2098572 kbytes in 0.24 seconds (8744.05 MB/s)
Nov  3 11:33:37 MyDesktop kernel: [169814.542694] PM: freeze of devices complete after 395.673 msecs
Nov  3 11:33:37 MyDesktop kernel: [169814.542774] PM: late freeze of devices complete after 0.078 msecs
Nov  3 11:33:37 MyDesktop kernel: [169814.543202] PM: noirq freeze of devices complete after 0.427 msecs
Nov  3 11:33:37 MyDesktop kernel: [169814.543637] PM: Saving platform NVS memory
Nov  3 11:33:37 MyDesktop kernel: [169814.854877] PM: Creating hibernation image:
Nov  3 11:33:37 MyDesktop kernel: [169814.957825] PM: Need to copy 460879 pages
Nov  3 11:33:37 MyDesktop kernel: [169814.957827] PM: Normal pages needed: 86549 + 1024, available pages: 141050
Nov  3 11:33:37 MyDesktop kernel: [169814.855507] PM: Restoring platform NVS memory
Nov  3 11:33:37 MyDesktop kernel: [169814.912648] PM: noirq restore of devices complete after 12.751 msecs
Nov  3 11:33:37 MyDesktop kernel: [169814.912743] PM: early restore of devices complete after 0.070 msecs
Nov  3 11:33:37 MyDesktop kernel: [169816.881020] PM: restore of devices complete after 1880.532 msecs
Nov  3 11:33:37 MyDesktop kernel: [169816.883371] PM: Image restored successfully.
Nov  3 11:33:37 MyDesktop kernel: [169816.886468] PM: Basic memory bitmaps freed
Nov  3 11:34:38 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Nov  3 11:34:38 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Nov  3 11:34:38 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Nov  3 11:34:38 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Nov  3 11:34:38 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
Nov  3 11:34:38 MyDesktop kernel: [    0.100845] PM: Registering ACPI NVS region [mem 0xda60e000-0xda88dfff] (2621440 bytes)
Nov  3 11:34:38 MyDesktop kernel: [    0.100883] PM: Registering ACPI NVS region [mem 0xda893000-0xda8d5fff] (274432 bytes)
Nov  3 11:34:38 MyDesktop kernel: [    0.929565] PM: Hibernation image not present or could not be loaded.

```

---

### Post by Toz on 2013-11-03
There is nothing there. Lets try this again.

1. Suspend the computer:
```
sudo pm-suspend
```

2. Wait about 5 minutes (to see time difference in logs).

3. Resume the computer and make note of whether it resumed properly or not.

4. Post back /var/log/pm-suspend.log:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

5. Post back syslog messges:
```
cat /var/log/syslog | grep PM:
```

---

### Post by Dan Again on 2013-11-04
So, the problem doesn't seem to be with suspend, per se, but rather with resume. The systems suspends successfully, but then when I attempt to resume it just crashes. So, I did what you suggested, Toz (to be clear, resume was not successful). [Here is the PasteBin link]("http://paste.ubuntu.com/6359322"), and here are the syslog messages...
```

dan@MyDesktop:~$ cat /var/log/syslog | grep PM:
Nov  4 09:18:23 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Nov  4 09:18:23 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Nov  4 09:18:23 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Nov  4 09:18:23 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Nov  4 09:18:23 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
Nov  4 09:18:23 MyDesktop kernel: [    0.100865] PM: Registering ACPI NVS region [mem 0xda60e000-0xda88dfff] (2621440 bytes)
Nov  4 09:18:23 MyDesktop kernel: [    0.100903] PM: Registering ACPI NVS region [mem 0xda893000-0xda8d5fff] (274432 bytes)
Nov  4 09:18:23 MyDesktop kernel: [    0.914505] PM: Hibernation image not present or could not be loaded.
Nov  4 09:22:56 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Nov  4 09:22:56 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Nov  4 09:22:56 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Nov  4 09:22:56 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Nov  4 09:22:56 MyDesktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
Nov  4 09:22:56 MyDesktop kernel: [    0.100975] PM: Registering ACPI NVS region [mem 0xda60e000-0xda88dfff] (2621440 bytes)
Nov  4 09:22:56 MyDesktop kernel: [    0.101014] PM: Registering ACPI NVS region [mem 0xda893000-0xda8d5fff] (274432 bytes)
Nov  4 09:22:56 MyDesktop kernel: [    0.908702] PM: Hibernation image not present or could not be loaded.
Nov  4 09:24:00 MyDesktop kernel: [   67.668248] PM: Marking nosave pages: [mem 0x0009e000-0x000fffff]
Nov  4 09:24:00 MyDesktop kernel: [   67.668252] PM: Marking nosave pages: [mem 0x20000000-0x201fffff]
Nov  4 09:24:00 MyDesktop kernel: [   67.668259] PM: Basic memory bitmaps created
Nov  4 09:24:46 MyDesktop kernel: [   67.668259] PM: Syncing filesystems ... done.
Nov  4 09:24:46 MyDesktop kernel: [   67.682041] PM: Preallocating image memory... done (allocated 303018 pages)
Nov  4 09:24:46 MyDesktop kernel: [   67.869742] PM: Allocated 1212072 kbytes in 0.18 seconds (6733.73 MB/s)
Nov  4 09:24:46 MyDesktop kernel: [   68.268400] PM: freeze of devices complete after 397.518 msecs
Nov  4 09:24:46 MyDesktop kernel: [   68.268480] PM: late freeze of devices complete after 0.078 msecs
Nov  4 09:24:46 MyDesktop kernel: [   68.268908] PM: noirq freeze of devices complete after 0.427 msecs
Nov  4 09:24:46 MyDesktop kernel: [   68.269338] PM: Saving platform NVS memory
Nov  4 09:24:46 MyDesktop kernel: [   68.580608] PM: Creating hibernation image:
Nov  4 09:24:46 MyDesktop kernel: [   68.689191] PM: Need to copy 302076 pages
Nov  4 09:24:46 MyDesktop kernel: [   68.689193] PM: Normal pages needed: 56212 + 1024, available pages: 171380
Nov  4 09:24:46 MyDesktop kernel: [   68.581237] PM: Restoring platform NVS memory
Nov  4 09:24:46 MyDesktop kernel: [   68.638365] PM: noirq restore of devices complete after 12.986 msecs
Nov  4 09:24:46 MyDesktop kernel: [   68.638458] PM: early restore of devices complete after 0.069 msecs
Nov  4 09:24:46 MyDesktop kernel: [   70.590752] PM: restore of devices complete after 1892.405 msecs
Nov  4 09:24:46 MyDesktop kernel: [   70.593220] PM: Image restored successfully.
Nov  4 09:24:46 MyDesktop kernel: [   70.598327] PM: Basic memory bitmaps freed

```

I also found [this post]("http://ubuntuforums.org/showthread.php?t=2036201") I made some time ago that seems to be about a similar problem with this system. The solution I came to for that problem was to change the default suspend behavior to be hibernate. Since hibernation seems to be working fine, I would be totally happy with just re-configuring my machine to hibernate on suspend, but I can't remember how I did that.

---

### Post by Dan Again on 2013-11-04
Well, okay...I guess the crash on resume from suspend isn't my only problem. The system still refuses to suspend on inactivity (again, I see a Gnome notification that the system will suspend shortly due to inactivity, but then it never does).

---

### Post by Dan Again on 2013-11-04
So, here's what I see, but suspend never happens.

[ATTACH=CONFIG]247561[/ATTACH]

---

### Post by Toz on 2013-11-04
What I find very interesting is that hibernate works but suspend does not. Can you look in your bios and see if there is a sleep setting in there (might be something like S1 S2 S3, etc). Make sure its enabled - preferrably set to S3 mode.

Also, can you try the **acpi_sleep=nonvs** kernel parameter? To do so, follow the "Temporarily Add a Kernel Boot Parameter for Testing" from [this]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") link to see if it helps? Post back /var/log/pm-suspend.log after you attempt a suspend with that kernel parameter.

---

### Post by Dan Again on 2013-11-10
Changing the BIOS setting solved the crash on resume problem, but my computer still isn't suspending automatically on inactivity. Harumph.

---

### Post by Toz on 2013-11-10
> **Dan Again said:**
> but my computer still isn't suspending automatically on inactivity. Harumph.
If suspend works using the lower-level suspend commands, but a higher-level DE suspend function doesn't, I would think that this might be a Gnome 3 issue. Had a quick look for open bug reports but couldn't find any. I don't have any experience with Gnome 3. Perhaps you should create a bug report for this.

---

### Post by imdrowninginaccounts on 2013-11-17
I have the same/a similar problem since the Saucy upgrade, unfortunately it's only happening every 1 time out of 3 (approximately): sometimes the computer simply doesn't do anything when it should suspend. It doesn't suspend automatically as it should, is doesn't react to manually clicking 'Suspend' in the dropdown menu, when typing 'suspend' on the command line it just hangs, doing nothing. As I said, this happens in about 20%-30% of cases, otherwise it suspends normally.

I am running a dual-user system, unfortunately I couldn't so far identify anything that causes this problem; no direct correlation to programs that are open or which users are logged on. Interestingly, the 'sudo pm-suspend' mentioned above works. But I can't find any helpful entry in any of the logs either, neither in syslog nor pm-suspend.log

So... any pointers to identifying the cause of this would be highly appreciated, because it is extremely annoying. Oh, and I'm on Unity (as Gnome3 was mentioned above...)

---

### Post by kjaspan on 2014-01-06
I can suspend manually but not automatically - such as changing the power settings to suspend after an hour of inactivity.

Here are the contents of my /etc/default/grub

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force resume=/dev/sda5"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force"
GRUB_CMDLINE_LINUX=""

Any suggestions out there? I would be grateful for a fix.

---

