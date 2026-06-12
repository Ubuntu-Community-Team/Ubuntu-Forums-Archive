---
title: "XFCE Desktop wacked after upgrade"
date: 2015-02-16
forum: General Help
---

### Post by chris.curry on 2015-02-16
Xubuntu 14.04 and after this morning's update prompt my desktop has no wallpaper, the cursor is an "X", only the icons I placed on the panel are visible and Firefox won't show bookmarks.  Yikes!  The only thing I can think is that I may have shut down the laptop inadvertently before the update process fininshed.

I've tried booting to older kernels, and everything in recovery mode:  "Fix broken packages"  "Check disks" etc.  I updated the display driver.  I did a "sudo apt-get upgrade". Nothing seems to help.

I'm hoping for some suggestions!

Chris

---

### Post by Bashing-om on 2015-02-16
chris.curry; Hello;

Ya want to try and revert the desktop to default values ? You will loose all your config changes.
key combo ctl+alt+F1 to gain a console:
```

xfce4-panel --quit
pkill xfconfd
rm -rf ~/.config/xfce4/panel
rm -rf ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml

```
Restart the panel:
```

xfce4-panel

```
This will respawn xfconfd automatically.
(Note if you need or want to restart xfconfd manually know that on my installation it was in /usr/lib/x86_64-linux-gnu/xfce4/xfconf/xfconfd which was outside of $PATH.
This clears it for the running session, regenerates the files, and sets up the default for future sessions. )

[INDENT][INDENT][INDENT]maybe yes 
[/INDENT][/INDENT][/INDENT]

---

### Post by chris.curry on 2015-02-16
Thanks very much for your response.  I'm currently backing everything up with Deja-vu so I'll wait until that finishes to try your suggestion.  I can access everything on the panel, and I have a link to the terminal, firefox etc there, so I can still run applications. The windows are fried, they have no control buttons on the top, left click doesn't work etc.

I'll post here later today with an update.

Chris

---

### Post by kc1di on 2015-02-16
have your rebooted since the upgrade?  sometimes that will help.

---

### Post by chris.curry on 2015-02-16
I just tried your suggestion Bashing-om, but no joy.  It comes back after a hard boot with the same behaviour:  Black screen except for top panel, the applications all work but most of the control buttons such as minimize, favourites, settings do not.  Left mouse click does nothing anywhere.  Login screen appears after the prescribed period of inactivity, and it shows the wallpaper until the password prompt is entered, then goes away and I'm back to a black screen with an "X" for a mouse pointer and only the top panel to use.

Maybe it has nothing to do with the desktop as such, but something more fundamental that also affects the mouse?



Chris

---

### Post by Bashing-om on 2015-02-16
chris.curry; Strange indeed;

OK, let's poke at it a bit more:
```

mv ~/.config/xfce4  ~/.config/xfce4.bak
cp -r /etc/xdg/xfce4 ~/.config

```
which will reset to a default Xfce desktop.
Then log out and log in again to effectuate the new configuration.

[INDENT][INDENT]maybe now
[/INDENT][/INDENT]

---

### Post by chris.curry on 2015-02-16
OK some progress or a change at least.  The last set of commands followed by logout login produced a familiar desktop with a standard cursor, but still no leff mouse button activity or controls on the application windows.

There is an error message dialogue:  :  "Ubuntu 14.04 has experienced a serious error."

"...path /usr/bin/Xorg        Crash"

"/usr/bin/X-core :1 -seat seat0 -auth /var/run/lightdm /root : 1 nolisten tcp ut8 -nwkswitch"

That's all Greek to me however!

Chris

---

### Post by Bashing-om on 2015-02-16
chris.curry; Yeah, 

It does give us some pointers and some hints:
this one:
> 
.path /usr/bin/Xorg Crash

says take a look at the log files. To do that:
```

cat /var/log/lightdm/lightdm.log
cat /var/log/lightdm/x-0-greeter.log
cat /var/log/Xorg.0.log

```
see  if that gives us some additional hints.

and:
> 
"/usr/bin/X-core :1 -seat seat0 -auth /var/run/lightdm /root : 1 nolisten tcp ut8 -nwkswitch"

presently a mystery to me also. What in the  world is the connection between 'lightdm', the display manager, and networking ?
Is 'lightdm' set as the default ?
```

apt-cache policy xubuntu-desktop
cat /etc/X11/default-display-manager
ls /usr/share/xsessions
echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP

```

Consider:
The login screen is usually handled by a Display Manger that handles logging in and choosing and launching the Desktop Environment.  I think for vanila xbuntu that would be lightdm, which handles graphic configuration in /etc/lightdm/lightdm.conf. and maybe /usr/share/lightdm/lightdm.conf.d/ When lightdm hands off to the desktop, the configuration is handled by files in /etc/Xorg/ like xorg.conf and xorg.conf.d/*
For most systems, the details are auto-configured at startup, but if you've configured something manually , the handoff might be failing.
------------------
There is a nagging thought that I am missing something here, but I am tired. Perhaps when I am rested and look at the outputs it will come to me.

[INDENT][INDENT]it be a process in learning
[/INDENT][/INDENT]

---

### Post by chris.curry on 2015-02-17
Ok, I had some sleep and I think we may be making progress.

It's this from cat /var/log/lightdm/x-0-greeter.log that seems to be the big issue:

**  (lightdm-gtk-greeter:2245): WARNING **: Failed to load user image:  Failed to open file '/home/chrls/.face': No such file or directory

(lightdm-gtk-greeter:2245): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed

(lightdm-gtk-greeter:2245): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
init: indicator-power main process (2296) killed by TERM signal
init: indicator-application main process (2298) killed by TERM signal

From lightdm.log all seems OK until the end:

[+4.81s] DEBUG: Creating shared data directory /var/lib/lightdm-data/chrls
[+4.81s] DEBUG: Session pid=1396: Logging to .xsession-errors
[+4.84s] DEBUG: Activating VT 7
[+4.85s] DEBUG: Activating login1 session c1
[+6.27s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+200.58s] DEBUG: User /org/freedesktop/Accounts/User1000 changed

The ouput of Xorg.0.log is very long but these lines stand out:

[    22.203] (WW) Falling back to old probe method for fglrx
[    22.215] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    22.218] ukiDynamicMajor: found major device number 250
[    22.219] (--) Assigning device section with no busID to primary device
[    22.219] (--) Chipset Supported AMD Graphics Processor (0x9830) found
[    22.220] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
[    22.221] (II) fglrx(0): pEnt->device->identifier=0x7fba9369db57
[    22.221] (WW) Falling back to old probe method for modesetting
[    22.221] (EE) open /dev/dri/card0: No such file or directory
[    22.221] (WW) Falling back to old probe method for fbdev
[    22.221] (II) Loading sub module "fbdevhw"
[    22.221] (II) LoadModule: "fbdevhw"
[    22.230] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.230] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.230]     compiled for 1.15.1, module version = 0.0.2
[    22.230]     ABI class: X.Org Video Driver, version 15.0
[    22.231] (WW) Falling back to old probe method for vesa
[    22.231] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === begin
[    22.231] (II) Loading sub module "vgahw"
[    22.231] (II) LoadModule: "vgahw"
[    22.231] (II) Loading /usr/lib/xorg/modules/libvgahw.sois
[    22.231] (II) Module vgahw: vendor="X.Org Foundation"

Does any of this make sense?  Thanks for all your help here Bashing-om.

Chris

---

### Post by Bashing-om on 2015-02-17
chris.curry; Welll ...

I see " Failed to load user image: Failed to open file '/home/chrls/.face': No such file or directory " as non standard. You have changed the greeter ?
Let's try a simpler attempt before we get the more drastic;
What results:
```

sudo dpkg-reconfigure unity-greeter

```
See if the system reports any problems.

As to the Xorg.0.log I presently see nothing to be concerned about. So long as a driver is loaded. I always like to verify what Xorg relates:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```
Make sure the system and the log file agree .

As this situation arose after an upgrade, might be a good idea to "see" that all is well with the package management system:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

```

----------------------
What we have here is a failure to communicate;
[INDENT][INDENT]we be look'n for who said what, and who failed to respond
[/INDENT][/INDENT]

---

### Post by chris.curry on 2015-02-17
Glad to see you're still with me on this Bashing-om.

So, we have this, I wonder if Xubuntu uses a different greeter?:

dpkg-query: package 'unity-greeter' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: unity-greeter is not installed

And then:

chrls@chrls-HP-Pavilion-15-Notebook-PC:~$ lspci -vnn | grep VGA -A 12
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8400] [1002:9830] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device [103c:216f]
    Flags: bus master, fast devsel, latency 0, IRQ 82
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0800000 (64-bit, prefetchable) [size=8M]
    I/O ports at 4000 [size=256]
    Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at f0360000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci

00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:9840]
    Subsystem: Hewlett-Packard Company Device [103c:216f]

And:

chrls@chrls-HP-Pavilion-15-Notebook-PC:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Kabini [Radeon HD 8400]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:82 memory:e0000000-efffffff memory:f0800000-f0ffffff ioport:4000(size=256) memory:f0300000-f033ffff memory:f0360000-f037ffff

I stick with the LTS versions, and I'm in 14.04 already, so no dist-upgrade, but after an update and upgrade I get:

chrls@chrls-HP-Pavilion-15-Notebook-PC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I'll try a reboot now as xorg-core was upgraded, see what happens and report back.

Chris

---

### Post by chris.curry on 2015-02-17
Rebooted but no change.

I tried restoring the infamous missing .face with:  deja-dup --restore .face from my backup of the original install of Xubuntu, but DejaDup says there is no such file in the backup.

Is it time to give up and reinstall the whole distro?  Or maybe try dist-upgrade to 14.10 first?


Chris

---

### Post by Bashing-om on 2015-02-17
chris.curry; Yeah;

I did not have my head on straight in looking for "unity-greeter' in an xubuntu install. (lightdm is a fairly recent addition to xubuntu as the login/display manager)
So what results, now:
```

sudo dpkg-reconfigure lightdm

```
graphics:
 looks good to me, proprietary driver installed, and I bet Xorg file shows it as built.
There were a number of update this day for Xorg and related libs and drivers. How have the updates altered your situation ?
Aside: "apt-get dist-upgrade" has nothing to do with a release upgrade to the next release. 'apt-get update' only updates packages and will not install anything new, where as 'dist-upgrade' does and will install new packages ( as in a new kernel ) .

[INDENT][INDENT]who what when and where
[INDENT][INDENT][INDENT]why, oh why; we just do not know - yet
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris.curry on 2015-02-18
OK, progress!

Neither:  
sudo dpkg-reconfigure lightdm nor apt-get dist-upgrade did anything.  (Thanks for straighting me out on the dist-upgrade command though.)

However, I thought I'd try setting up a new user, and that worked!  Logging in with the new user account makes everything perform as expected.

There still is no login screen presented on booting up, it goes straight to my original user, and there is no mouse pointer visible on the screen until it happens to land on an action button.

I've set the logon screen to ask for a password on boot, but it doesn't do this.  If I logoff, and logon as guest, everything works.

If I logon as chris, it's all still screwy.

OK, figured out how to give my new user access to the other account's folders, now just to sort out the logon and see if there's a way to fix the original one.


Chris

---

### Post by Bashing-om on 2015-02-18
chris.curry; Welp'

Yeah, the new account with no problems sure do say the problem is a config issue in the original account.. As we have already attempted to reset to defaults, and no joy, let's see if we can get some additional info:
Boot to terminal, and start the GUI from terminal:
boot to the grub boot menu, press the 'e' key for edit mode -> boot parameters screen;
arrow down to the line similar " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff" and across to "quiet splash" replace these terms with the term "text" - without the quotes;
key combo ctl+x to continue the boot process to TTY1.
Login here with your username and password ( no response to the screen when pass word is enter, enter pass word blindly and hit the enter key).
Now start the GUI:
```

sudo service lightdm start

```
What errors does the system report ?
Key combos:
ctl+alt+F7 is the GUI
ctl+alt+F1 is the TTY1 terminal
ctl+alt+f2 3 4 5 6  are the other available terminals.
IF the GUI does not start you can reboot from TTY1 with terminal code:
```

sudo shutdown -r now

```

[INDENT][INDENT][INDENT]we be look'n
[INDENT][INDENT][INDENT]for which way to go, George
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris.curry on 2015-02-18
Wow, curiosier and curiouser!

I can't login as chris from the command prompt after following your instructions to the letter:  "Incorrect user password combo".

I can login as guest (my new user) but when I sudo service lightdm start, I end up logged in as chris with no errors!

Yikes!

---

### Post by Bashing-om on 2015-02-18
chris.curry; Yeayah, curiouser yet;

> **chris.curry said:**
> Wow, curiosier and curiouser!

I can't login as chris from the command prompt after following your instructions to the letter:  "Incorrect user password combo".

I can login as guest (my new user) but when I sudo service lightdm start, I end up logged in as chris with no errors!

Yikes!

With "you" not able to log into "your" account it do present a situation.
I sleep on it, see what I can come up with to see what we can find out when there is no access to the administration level.....
(hummm, root recovery console ?) (Humm .... change your password ?)

Can you do:
```

cat /etc/passwd

```
IF there is output, are "you" in the list ?
For instance:
My output:
```

sysop:x:1000:1000:sysop,,,:/home/sysop:/bin/bash

```
where 'sysop' is my username.


I got to think about how to find a way to look at things from "your" perspective on system access.

[INDENT][INDENT]now, this may get real interesting
[/INDENT][/INDENT]

---

### Post by chris.curry on 2015-02-18
Now that produced some interesting output:

chrls@chrls-HP-Pavilion-15-Notebook-PC:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
libuuid:x:100:101::/var/lib/libuuid:
syslog:x:101:104::/home/syslog:/bin/false
messagebus:x:102:106::/var/run/dbus:/bin/false
usbmux:x:103:46:usbmux daemon,,,:/home/usbmux:/bin/false

gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
libuuid:x:100:101::/var/lib/libuuid:
syslog:x:101:104::/home/syslog:/bin/false
messagebus:x:102:106::/var/run/dbus:/bin/false
usbmux:x:103:46:usbmux daemon,,,:/home/usbmux:/bin/false
dnsmasq:x:104:65534:dnsmasq,,,:/var/lib/misc:/bin/false
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
kernoops:x:106:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
rtkit:x:107:114:RealtimeKit,,,:/proc:/bin/false
saned:x:108:115::/home/saned:/bin/false
whoopsie:x:109:116::/nonexistent:/bin/false
speech-dispatcher:x:110:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
avahi:x:111:117:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
lightdm:x:112:118:Light Display Manager:/var/lib/lightdm:/bin/false
colord:x:113:121:colord colour management daemon,,,:/var/lib/colord:/bin/false
hplip:x:114:7:HPLIP system user,,,:/var/run/hplip:/bin/false
pulse:x:115:122:PulseAudio daemon,,,:/var/run/pulse:/bin/false
chrls:x:1000:1000:Chris,,,,:/home/chrls:/bin/bash
debian-spamd:x:116:126::/var/lib/spamassassin:/bin/sh
guest:x:1001:1001:Guest,,,,:/home/guest:/bin/bash






Whole buncha nobodies and falses in there.  I get no logon screen until I logout and then I need to produce a password  either chris or guest.

Must..........get..............sleep.  

Chris

---

### Post by Bashing-om on 2015-02-19
chris.curry; Humm ..

Not sure what to make of this:
[quote]
[color=red]chrls[/color]:x:1000:1000:Chris,,,,:/home/[color=red]chrls[/color]:/bin/bash
The user 'chrls' owns 'chris's /home directory ???
How does 'chrls' play into this ?
Let's try and do some deeper poking:

Is this a standard install ? The following "assumes" that the operating system is installed to the 'sda1' partition.
Boot to the grub menu -> advanced options -> choose a recovery kernel, enter to boot it to the recovery console.
In the recovery console menu choose "root terminal".
Here you are root, slow down and think and make sure prior to hitting the enter key ! ( we have not enabled write access, so fairly safe) Else, A typo here can be fatal . The system will not question what you are doing. even wrong it will do as told -when you have r/w access. Careful !
Here we are just look'n .
We want to confirm who has authority to what:
IF I have my mind right for the paths, then ->
who has authority to access X ?
```

cd /
ls -al .Xauthority
ls -al .ICEauthority

```

Who owns the /home directory ?
```

ls -al /home

```
To get out of the "root terminal" type
```

exit

```
Now back to the recovery console menu; 
What results when "resume normal boot" is selected ( degraded graphics is expected) ?
We are done for now, carry in with what you need to do.
When we know who owns /home, we next look and see who owns the files contained in /home.

Then we see about changing to the user you want as that primary account that has the administrative authority.
Once we have admin authority regained, we can look at 'who' has what levels of access.

[INDENT][INDENT]it's all about
[INDENT][INDENT][INDENT]acess, authority and permissions
I think ![/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris.curry on 2015-02-21
OK, finally got back to this project after having to get some work done!

Booting to a root consol:
cd /
ls -al .Xauthority
ls -al .ICEauthority 

Both produced "No such file or directory"  I tried from a couple of different directories as well.

ls -al /home said "drwxr-xr-x 75 chrls" and "drwxr-xr-x 27 guest"

chrls was a typo when I set up xubuntu and should have been chris.

Since nothing has presented itself as a solution I'm wondering if it isn't time to give up and reinstall?

At some point in any enterprise like this it becomes a question of how best to spend one's time.

I am always amazed at how much I learn on a venture like this, and that's what keeps me going!

Chris

---

### Post by Bashing-om on 2015-02-21
chris.curry; Welp;

.Xauthority, and .ICEauthority should exist, else "you" do not have authorization to access the GUI .
Let me - later on - reboot into a 14.04 standard install via grub and confirm that the path I gave you is correct.

Presently, this is but a matter of having (creating) the proper files, and setting who has authorizations and as well the permissions to access "your" /home.

There is always that nuclear option to (RE-)install at any time your frustration level is exceeded. With good backups, and a plan of operations it is but a matter of 30 minutes to (RE-)install and back in business ! (fast internet connection assumed)

[INDENT][INDENT]a matter of what you want to do
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-02-21
chris.curry; Well, well .... oooppss;

In respect to the location of .Xauthority and .ICEauthgority, I was out in left field. Guilty, not think'n it through . As those files allow access to a particular directory, they must reside within that directory; so:
we look in "your" /home for them.
Boot to the 'root' console as before.
what now returns:
```

ls -al /home

```
Is it of the form :
```

drwxr-xr-x 29 [color=red]chris chris[/color]  4096 Feb 21 14:17 [color=red]chris[/color]

```
note 'chris' in three places.

Now we continue to see if 'chris' has authorization :
```

ls -al /home/chris/.Xauthority
ls -al /home/chris/.ICEauthority

```
As in my output:
```

sysop@1404mini:~$ ls -al /home/sysop/.Xauthority
-rw------- 1 sysop sysop 209 Feb  4 15:15 /home/sysop/.Xauthority

sysop@1404mini:~$ ls -al /home/sysop/.ICEauthority
-rw------- 1 sysop sysop 652 Feb 21 14:17 /home/sysop/.ICEauthority
sysop@1404mini:~$

```
where I am 'sysop', you should see 'chris' in the respective fields.
Remember, CaSe is important ! Chris does not equal chris. Where 'c' is upper case or lower case .

[INDENT][INDENT]now I expect I am
[INDENT][INDENT][INDENT]on the right track
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris.curry on 2015-02-22
Well we haven't given up yet, have we Bashing-om!  Real troopers, we are.

The output to each of your commands is exactly as expected and as appear on your terminal, with the exception that rather than user chris they appear as user chrls.  You remember I made a typo when I set up 14.04 in the begining so I went and changed the user ID from chrls to chris.  This may be the root of the problem?

I checked in users and groups and both chris and guest have admin status and are members of the chrls group.

I had a look and there is no lightdm.conf file in /etc/, which seems strange as well.


Chris

---

### Post by Bashing-om on 2015-02-22
chris.curry; Hummm ...

I am scratching my head, and wondering what the consequences of making 'chris' grouped and owned to /home/chris  might be.
'chris' is your preferred username, yes ?

I am bothered greatly that you do not find "lightdm.conf" // check again :
```

ls -al /etc/lightdm/lightdm.conf

``` I do think that as 'lightdm' is the login/display manager that the file should exist there even in (x)ubuntu.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by chris.curry on 2015-02-22
It seems I was mistaken.  I was looking for the contents of /etc from nautilus, and didn't find it.

From the root consol:  -rw-rw-r-- 1 root root 119 Dec 8 06:44 /etc/lightdm/lightdm.conf


Chris

---

### Post by Bashing-om on 2015-02-22
chris.curry; .......

Let's take a poke at it and change the ownership and group of the /home directory.

Do you know for sure the password associated to the 'chris' account ?

I could be wrong, wrong, wrong here, but

[INDENT][INDENT]I do think
[/INDENT][/INDENT]

---

### Post by chris.curry on 2015-02-23
OK, did that using sudo nautilus, and now the /home shows owner "me" when I'm logged on as chris.  But still no joy.  Rebooting still presents no logon screen although it is set to ask for one.  When it does boot up it goes to a black screen and  the cursor doesn't show, but is usable when it lights up a hot spot.  Logging out and back in I am presented with a password prompt for chris, and now the screen is not black and the cursor shows, but is a cross.  Applications have no minimize or close buttons on their windows.

If I logout and log back in as guest, things are slightly better:  cursor is normal etc. But applications still behave strangely.  And I still get a "Ubuntu 14.04 has experienced an internal error"  related to Xorg every so often.

Thanks for all you help Bashing-om I really appreciate you're staying with me on this journey.  I've leared a lot, but I think I will make some space with Gparted and install another instance of Xubuntu.  Hopefully Grub will boot to either, but maybe I should install 14.10 so it can distinguish between them?  Once I have all the files I need moved over I'll delete the current partition and use update-grub and grub-install.

Sound like a plan?


Chris

---

### Post by Bashing-om on 2015-02-23
chris.curry; Sure;

That is a great option to dual boot . That way when you mess one system, there is that alternate goto.
I do multi-boot and to keep my partitions systems straight I label the partitions.
run terminal commands:
```

sudo fdisk -lu
sudo blkid

```
to know what partition is which and to label, again from terminal:
```

sudo tune2fs -L "my-xubuntu" /dev/sda1
sudo tune2fs -L "xubuntu-alt" /dev/sda5

``` for an example, where what is in the quotes is arbitrary and can be what ever you want.
I prefer my "stable" system to be a LTS (14.04 currently), and I 'test' with the short term release (14.10)
[I do have 15.04 on system as a bootable .iso as well as others]

To be upfront. My work/stable system is 14.04 as a "core-install" With only what I want for added applications installed. It is fast, lean and mean on this old antique of a system - that still does well with a standard install. I place a high value on fast and simple and configurable and that is what I run.
I boot to terminal, and decide what I want from there. IF I want a DE my preference is xfce . What can I say, I like what I understand (KISS).

When you are ready to go back to fighting this we go back to it . We know it is but a configuration issue(s), somewhere. Just a matter of finding where/what .

[INDENT][INDENT][INDENT]once you know
[INDENT][INDENT][INDENT]noth'n to it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

