---
title: "Screen saver / Screen lock causes auto logout"
date: 2017-09-24
forum: General Help
---

### Post by olsiron on 2017-09-24
Hi,

When my Ubuntu 17.10 gnome laptop locks screen, it also logs me out. How do I stop this behaviour? (or troubleshoot further...)

Cheers,

olsiron

--
me@me-laptop:~$ uname -a
Linux me-laptop 4.13.0-11-generic #12-Ubuntu SMP Tue Sep 12 16:03:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

me@me-laptop:~$ cat /etc/os-release 
NAME="Ubuntu"
VERSION="17.10 (Artful Aardvark)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Artful Aardvark (development branch)"
VERSION_ID="17.10"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=artful
UBUNTU_CODENAME=artful

me@me-laptop:~$ gnome-panel --version
gnome-panel 3.24.1

---

### Post by mc4man on 2017-09-24
What makes you think you're getting logged out? If the screen says "unlock" you're locked out, if it says "sign in"  you're logged out.

---

### Post by olsiron on 2017-09-24
When the screen locks, I'm now back out at login screen. When I log back in there are no running applications. last command also indicates my session has ended. So back to my original question:

When my Ubuntu 17.10 gnome laptop locks screen, it also logs me out. How do I stop this behaviour? (or troubleshoot further...)

---

### Post by mc4man on 2017-09-24
Here going to a lock screen does not log out or stop any running apps unless it's also being suspended.
As far as the lock screen it can be turned off in Settings > Privacy 
Note that if coming out of suspend the above setting is not used, always goes to a lockscreen

---

### Post by olsiron on 2017-09-24
According to Settings > Power > "Automatic Suspend" is off.
Settings > Privacy > Screen Lock is on when "Screen Turns Off" but it's not clear why that would cause a Suspend

So question is why is Suspend Activating? (And doesn't suspend mean exactly that? Why is it also ending login session?)

---

### Post by olsiron on 2017-09-24
Guesstimate is that Ubuntu isn't happy when my screen goes idle. Any way to troubleshoot this further or provide additional info I should add for a bug?

```

Sep 24 23:10:04 me-laptop gnome-shell[11173]: g_object_get_data: assertion 'G_IS_OBJECT (object)' failedSep 24 23:10:04 me-laptop gnome-shell[11173]: Settings schema 'org.gnome.shell.overrides' does not contain a key named 'button-layout'
Sep 24 23:10:04 me-laptop kernel: [31448.575142] traps: gnome-shell[11173] trap int3 ip:7f7fa4227921 sp:7fffef382be0 error:0 in libglib-2.0.so.0.5400.0[7f7fa41d7000+11
1000]
Sep 24 23:10:04 me-laptop gnome-terminal-[11744]: Error reading events from display: Broken pipe
Sep 24 23:10:04 me-laptop update-notifier[11665]: Error reading events from display: Broken pipe
Sep 24 23:10:04 me-laptop systemd[1948]: gnome-terminal-server.service: Main process exited, code=exited, status=1/FAILURE
Sep 24 23:10:04 me-laptop systemd[1948]: gnome-terminal-server.service: Unit entered failed state.
Sep 24 23:10:04 me-laptop systemd[1948]: gnome-terminal-server.service: Failed with result 'exit-code'.
Sep 24 23:10:04 me-laptop org.gnome.Shell.desktop[11173]: (EE)
Sep 24 23:10:04 me-laptop org.gnome.Shell.desktop[11173]: Fatal server error:
Sep 24 23:10:04 me-laptop org.gnome.Shell.desktop[11173]: (EE) failed to read Wayland events: Broken pipe
Sep 24 23:10:04 me-laptop org.gnome.Shell.desktop[11173]: (EE)
Sep 24 23:10:04 me-laptop gnome-session[11140]: gnome-session-binary[11140]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 5
Sep 24 23:10:04 me-laptop gnome-session-binary[11140]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 5
Sep 24 23:10:04 me-laptop gnome-session-binary[11140]: Unrecoverable failure in required component org.gnome.Shell.desktop
Sep 24 23:10:04 me-laptop chrome-gbchcmhmhahfdphkhkmpfmihenigjmpp-Default.desktop[13376]: [13445:13445:0924/231004.430924:ERROR:x11_util.cc(89)] X IO error received (X server probably went away)
Sep 24 23:10:04 me-laptop gsd-media-keys[11270]: gsd-media-keys: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
Sep 24 23:10:04 me-laptop chrome-gbchcmhmhahfdphkhkmpfmihenigjmpp-Default.desktop[13376]: [13376:13376:0924/231004.431985:ERROR:chrome_browser_main_extra_parts_x11.cc(62)] X IO error received (X server probably went away)
Sep 24 23:10:04 me-laptop bluetoothd[939]: Endpoint unregistered: sender=:1.638 path=/MediaEndpoint/A2DPSource
Sep 24 23:10:04 me-laptop bluetoothd[939]: Endpoint unregistered: sender=:1.638 path=/MediaEndpoint/A2DPSink
Sep 24 23:10:04 me-laptop gsd-rfkill[11222]: g_object_notify: object class 'CcRfkillGlib' has no property named 'kernel-noinput'
Sep 24 23:10:04 me-laptop chromium-browser.desktop[11397]: [11471:11471:0924/231004.440891:ERROR:x11_util.cc(89)] X IO error received (X server probably went away)
Sep 24 23:10:04 me-laptop chromium-browser.desktop[11397]: [11397:11397:0924/231004.441733:ERROR:chrome_browser_main_extra_parts_x11.cc(62)] X IO error received (X server probably went away)
Sep 24 23:10:04 me-laptop gsd-keyboard[11266]: gsd-keyboard: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
Sep 24 23:10:04 me-laptop gsd-color[11263]: gsd-color: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
Sep 24 23:10:04 me-laptop gsd-a11y-keyboa[11255]: gsd-a11y-keyboard: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
Sep 24 23:10:04 me-laptop kerneloops-applet.desktop[11341]: kerneloops-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
Sep 24 23:10:04 me-laptop org.a11y.atspi.Registry[2039]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
Sep 24 23:10:04 me-laptop org.a11y.atspi.Registry[2039]:       after 33437 requests (33437 known processed) with 0 events remaining.
Sep 24 23:10:05 me-laptop kernel: [31448.774086] rfkill: input handler enabled

```

---

### Post by mc4man on 2017-09-24
Here the setting Privacy > Screen Lock is to Off. So the only time the laptop suspends is when the lid is closed which is also the only time it goes to a lockscreen
To turn that off (i.e. do something else), that can only be done in dconf (dconf-editor) @ org.gnome.settings-daemon.power

Edit : so my preference is to just have the laptop blank the screen when lid is closed. In unity you still had a menu option to suspend on demand, that doesn't appear to be the case with gnome-shell (or I can't find the dialog...
(- Well  one could set the power button to suspend, Ubuntu changed that to a shutdown  'interactive'

One thing to keep in mind is Ubuntu has made changes to the defaults but those changes may not be represented in Settings or dconf. Toggling a setting assures it's actually showing the actual setting
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1719217](https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1719217)

---

### Post by Brandon Hoult on 2017-10-02
Having the same issue using an HDMI display Ubuntu 17.10... if I turn off the monitor it logs me out.  So basically I can't leave anything running without leaving the monitor on all the time.

---

### Post by yookoala on 2017-10-04
I also have to same issue with a desktop computer. The session logouts whenever I turn off the screen.

It's a desktop and I've turned off auto-suspend. Still the problem exists.

---

### Post by yookoala on 2017-10-04
I have created an issue here:
[https://bugs.launchpad.net/gnome-shell/+bug/1721428](https://bugs.launchpad.net/gnome-shell/+bug/1721428)

Please help to improve the issue. Thanks.

---

### Post by mc4man on 2017-10-05
> **yookoala said:**
> I also have to same issue with a desktop computer. The session logouts whenever I turn off the screen.

It's a desktop and I've turned off auto-suspend. Still the problem exists.

i don't have a Desktop here, what do you mean by "turn off the screen"?, like you hit the power button on your display?

---

### Post by P-I H on 2017-10-05
I don't have this problem on my desktop. It works as intended when I power off the display with the power button.
This is the computer's specifications
```
p-i@pi-MS-7A34:~$ inxi -F
System:    Host: pi-MS-7A34 Kernel: 4.13.0-12-generic x86_64 bits: 64
           Desktop: Gnome 3.26.0
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: N/A
           UEFI: American Megatrends v: 1.70 date: 07/27/2017
CPU:       Octa core AMD Ryzen 7 1700 Eight-Core (-HT-MCP-) cache: 4096 KB
           clock speeds: max: 3724 MHz 1: 3724 MHz 2: 3724 MHz 3: 3724 MHz
           4: 3724 MHz 5: 3724 MHz 6: 3724 MHz 7: 3724 MHz 8: 3724 MHz
           9: 3724 MHz 10: 3724 MHz 11: 3724 MHz 12: 3724 MHz 13: 3724 MHz
           14: 3724 MHz 15: 3724 MHz 16: 3724 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tonga PRO [Radeon R9 285/380]
           Display Server: wayland (X.Org 1.19.3 ) driver: amdgpu
           Resolution: 1920x1200@59.88hz
           OpenGL: renderer: AMD Radeon R9 380 Series (AMD TONGA / DRM 3.18.0 / 4.13.0-12-generic, LLVM 5.0.0)
           version: 4.5 Mesa 17.2.1
Audio:     Card-1 C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso
           Card-2 Advanced Micro Devices [AMD/ATI] Tonga HDMI Audio [Radeon R9 285/380]
           driver: snd_hda_intel
           Card-3 Logitech Webcam C250 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.13.0-12-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp33s0 state: up speed: 1000 Mbps duplex: full
           mac: 
Drives:    HDD Total Size: 490.1GB (12.4% used)
           ID-1: /dev/nvme0n1 model: N/A size: 250.1GB
           ID-2: /dev/sda model: SanDisk_Ultra_II size: 240.1GB
           ID-3: /dev/sdb model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 228G used: 57G (27%) fs: ext4 dev: /dev/nvme0n1p2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 34.0C mobo: 37.0C gpu: 44.0
           Fan Speeds (in rpm): cpu: N/A fan-1: 637 fan-2: 586 fan-3: 860 fan-4: 0 fan-5: 666
Info:      Processes: 377 Uptime: 2 min Memory: 1641.6/16057.3MB
           Client: Shell (bash) inxi: 2.3.37 
p-i@pi-MS-7A34:~$

```

This is my power settings:

---

### Post by jib2-form on 2017-10-05
Same problem for me (xorg and wayland). My setting is: the screen turns off after X min. 
When waking the screen, I get the GDM login screen and a new session opens. Previous session is lost.
I added a few logs to the bug report.

---

### Post by rrnbtter on 2017-10-05
Greetings,
If I open the settings tool box, click on Power, set the blank screen to one minute, then leaving some apps open I wait for the screen blank to activate. 
When I move my mouse to activate the display I am back where I started with all of my apps still open. No problem.

In addition if I sleep my session, when I push my power button to wake the session it returns to its previous state with my apps still open. 

It is possible the the one's having problems with this have an ACPI problem. If their computer is not fully linux compatible then there may be some ACPI functions missing. I have a Lenovo computer and all of my Fn functions work as they should. 

 inxi -SxxSystem:    Host: rrnbtter-110-15ISK Kernel: 4.13.0-15-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.0 (Gtk 3.22.21-0ubuntu1) dm: gdm3
           Distro: Ubuntu Artful Aardvark (development branch)
$DESKTOP_SESSION
gnome
$XDG_SESSION_TYPE
wayland
GNOME Shell 3.26.0
Version: 3.26.0-0ubuntu2
loginctl type
Type=wayland
rrnbtter@rrnbtter-110-15ISK:~$

---

### Post by jib2-form on 2017-10-05
Well, my computer ran previously Ubuntu Gnome 17.04 and had no problem with ACPI so there must be something else... Perhaps display driver (mine's Intel)?

---

### Post by rrnbtter on 2017-10-05
Greetings,
Given that your F9 key has a lock icon.  Open you browser and then press the F9 key. Your display should blank out, lock and then the system should sleep.  Press the F9 key again and you system should wake to the Login Password prompt. After entering the pw you should have a desktop with the Browser still open just as you left it after pressing the original F9 key.

---

### Post by mc4man on 2017-10-05
Anyone seeing this 'issue', (I don't) should first try to determine if their machine is going to standby. (usually easy to see on a laptop, don't remember about desktop's
Standby will always go to the security lockscreen, there is no setting to change this.

---

### Post by yookoala on 2017-10-05
> **mc4man said:**
> i don't have a Desktop here, what do you mean by "turn off the screen"?, like you hit the power button on your display?

Yes. I hit the power button of my screen to turn it off. When I turn it back on (say 2 seconds afterwards), I'm logout.

And it is not a lock screen issue. If I trigger the screen lock manually (with keyboard shortcut) without the screen stays on, I can unlock the screen and restore my session.

---

### Post by yookoala on 2017-10-05
@olsiron: What video card is on your machine? And what driver are you using?

I'm on an Nvidia card (Geforce GTX 1050 Ti) with [nouveau](https://nouveau.freedesktop.org/wiki/).
(Note: Switching to close source Nvidia driver got me black screen. Seems another issue.)

---

### Post by yookoala on 2017-10-06
Just changed my grub config to "nomodeset" and it doesn't log me off now. (But of course my video quality is crappy now).

Please try and see if it works for you.

---

### Post by yookoala on 2017-10-06
Installed the latest close source driver (nvidia-387) from ppa:graphics-drivers/ppa. The problem appears again.

Seems not to be a driver specific issue. Any proper driver could trigger it.

---

### Post by mc4man on 2017-10-06
> **yookoala said:**
> Installed the latest close source driver (nvidia-387) from ppa:graphics-drivers/ppa. The problem appears again.

Seems not to be a driver specific issue. Any proper driver could trigger it.
With no desktop hardware clearly I have no idea. Am curious though - prior to 17.10 did auto login work with desktop hardware when nvidia drivers were in use?

---

### Post by olsiron on 2017-10-16
I have a crash report located as /var/crash/_usr_bin_gnome-shell.1000.crash which coincides with issue. apport retrac doesn't want to play (I'm new to this...):

apport-retrace --confirm --gdb --sandbox system --verbose --cache /tmp/cache/apport-retrace /var/crash/_usr_bin_gnome-shell.1000.crash
ERROR: report file does not contain one of the required fields: Package

Any tips on getting a stack trace from the CoreDump?

---

### Post by olsiron on 2017-10-22
This issue has moved onto gnome's Bugzilla here:
[https://bugzilla.gnome.org/show_bug.cgi?id=789166](https://bugzilla.gnome.org/show_bug.cgi?id=789166)

via:
[https://bugs.launchpad.net/gnome-shell/+bug/1721428](https://bugs.launchpad.net/gnome-shell/+bug/1721428)

---

### Post by cariboo on 2017-10-22
Moved to General Help as Artful has been released.

---

### Post by olsiron on 2017-10-22
For other future beginners with apport-retrace, this error "ERROR: report file does not contain one of the required fields: Package", means the .crash file literally doesn't contain a Package line in it (have a look at the top of a .crash file and it makes more sense). For my issue with gnome-shell this means adding this line:

[COLOR=#000000]Package: gnome-shell

at the top of the .crash file. 

You'll also need debug packages (which contain header symbols, needed for the stacktrace). Follow steps 1,6 and 7 from here (and possibly step 2, although the -proposed source led to mismatches when I tried to install some -dbgsym packages):
[/COLOR]https://wiki.ubuntu.com/DebuggingProgramCrash#Non-built-in_debug_symbol_packages_.28.2A-dbgsym.29

Then install the matching -dbgsym packages:

gnome-shell-dbgsym (and possibly libgtk-3-0-dbgsym). 

[COLOR=#000000]


[/COLOR]

---

### Post by sam0th-e on 2017-10-24
same problem.

---

### Post by florisjuh on 2017-10-25
According to the Bugzilla this crash might be caused by a GNOME extension. 

I for example had a problem with my laptop logging me out after turning my external monitor off. I solved it by disabling all my extensions. You can probably try disabling them one by one and see if the crash stops occurring.

---

### Post by lonewohlf42 on 2017-10-31
I have the same problem. I get kicked out to the login screen after about 1 minute or so. I've logged in to Unity instead of Ubuntu and the problem goes away. It seems to be a problem with Ubuntu gnome desktop because Unity works fine. Please help.

---

### Post by scarpam72 on 2017-11-11
Hi all,
I have the same issue with an HP desktop PC running Ubuntu Desktop 17.10 gnome.
Each time i switch off the monitor the session stops and all my running apps are closed (logout).

My PC has a DisplayPort interface and surely talks with my 4K Samsung monitor with 1.2 protocol.
I am really afraid about this bug because before the upgrade (i was running 17.04) everything was running as expected and smootly. I don't know what to do... change distribution may help?

---

### Post by richb05 on 2018-04-12
+1 for this issue. We have to run Windows 10 @ work so I use Ubuntu in VMWare player. Every time I lock the Windows machine I get logged out of the Ubuntu VM and it closes all open applications/windows, it's incredibly frustrating.

---

### Post by dries4 on 2018-04-12
I am experiencing the same issue. 

I'm running 17.10 on a NUC. 

The NUC is connected to a Yamaha AV receiver via HDMI, which is connected to an LG TV also via HDMI. If either the AVR or the TV is switched off, the session is lost. Any open windows or apps are killed.

I found this thread by looking at this page: [https://bugs.launchpad.net/gnome-shell/+bug/1721428](https://bugs.launchpad.net/gnome-shell/+bug/1721428)

On both the above mentioned page and this thread, I see a lot of time and effort is being put into arguing over whether this problem really exists or not. The more users state their facts, the more they get told how wrong they are, how incompetent they are, how misinformed they are, how little they know and how it is somehow their fault, and their problem.  

I understand that developers need to be able to recreate issues. But surely the point has been reached where we can safely say that this is a bug, and that it needs rectification?

---

