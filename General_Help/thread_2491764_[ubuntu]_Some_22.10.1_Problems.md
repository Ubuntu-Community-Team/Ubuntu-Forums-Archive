---
title: "[ubuntu] Some 22.10.1 Problems"
date: 2023-10-19
forum: General Help
---

### Post by grumpyprogrammer on 2023-10-19
Okay, so I newly installed 22.10.1 (fresh install, no leftovers) and have a number of problems.  

First, boot and shutdown is glacially slow. Startup and shutdown services fail constantly, but eventually succeed after around 20 minutes.  

Second, the desktop freezes constantly. The biggest culprits seem to be anything that does file IO, but just about every executable will randomly freeze at times.  For several minutes at a time. This is supremely annoying with apt, as one can imagine.

I /think/ this might have something to do with AppArmor, but I'm not sure.  I keep getting  the same error filling up my dmesg:  apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/org/gnome/Mutter/IdleMonitor/Core" interface="org.gnome.Mutter.IdleMonitor" member="GetIdletime" mask="send" name=":1.32" pid=18498 label="snap.firefox.firefox" peer_pid=17508 peer_label="unconfined"  

I got similar errors for snap.snapd-desktop-integration.snapd-desktop-integration. I ended up just removing desktop-integration and that improved things substantially, but was not a cure.   

smplayer does not play video. The sound works, but no video. This is odd because totem does (after it finishes loading, several MINUTES after being started... if I'm lucky).  

I did a SMART check and fsck of the drives on the off chance I had some bad blocks or something (using a liveCD), but everything is fine there. Memcheck revealed no problems, either.  

I booted into a different distro LiveCD as well as a USB 22.10.1 and none of the problems were present. Given that and the above I don't think it's a hardware issue. 

 Does anyone have any idea what might be causing all the constant freezing, lag, error messages and just plain nonworking behavior? I confess, I'm not even sure how to begin to diagnose what might be wrong.

---

### Post by deadflowr on 2023-10-19
No such release as 22.10.1.
And even if it was it is no longer supported.
22.04.1, maybe?

Not sure.
You could try following this to output some useful information that may or may not be helpful for those willing to help.
[https://ubuntuforums.org/showthread.php?t=2475931]("https://ubuntuforums.org/showthread.php?t=2475931")

---

### Post by grumpyprogrammer on 2023-10-19
*facepalms* I meant 23.10.1. The newest. Oops. Sorry, it's been a very, very long day.

That's a neat little utility! 

Postbin with info: [https://paste.ubuntu.com/p/63WMmfYwJk/](https://paste.ubuntu.com/p/63WMmfYwJk/)

---

### Post by MAFoElffen on 2023-10-19
I see a few things

First is the you have 15GB RAM, and at rest, somehow you are using 6.5GB memory?

Please do 
```

sudo ps aux|sort -r -k4 | head -n40 | awk '{print $1 "\t" $2 "\t" $4 "\t" $11}'

```
Second may explain why you cannot play videos... Here is the GPU:
```

Bonaire XTX [Radeon R7 260X/360]

```
By my records, this GPU should be using the amdgpu driver from the kernel.

Yours, if you look at the graphics section, is using the Radeon driver. I hear that "that" is a common problem with that specific GPU model.

Your kernel boot cmdline is this:
```

BOOT_IMAGE=/boot/vmlinuz-6.5.0-9-generic root=UUID=e9d4b749-f286-4bec-88d9-22fe90e910ed ro quiet splash vt.handoff=7

```
Please edit ypur /etc/default/grub file, and add these options to line GRUB_CMDLINE_LINUX_DEFAULT=, after the words "quiet splash"
```

radeon.si_support=0 radeon.cik_support=0 amdgpu.si_support=1 amdgpu.cik_support=1

```
Then, after saving and exiting, do 
```

sudo update-grub

```
to pick up the changes. On reboot, recheck the Graphics seciot again to make sure it is using driver amdgpu...

Welcome fellow Volume Manager enthusiast... With is a Segway to the next thing I want to talk about...

With BTRFS, in your /etc/fstab file, all you have for options in your BTRFS mounts is "default". 
```

/dev/disk/by-uuid/e9d4b749-f286-4bec-88d9-22fe90e910ed / btrfs defaults 0 1
/dev/disk/by-uuid/43176799-b71b-449f-a2f4-5437cbbf7ec0 /home btrfs defaults 0 1
/dev/disk/by-uuid/ccebd15e-3174-409c-a973-36c21febfb86 /usr btrfs defaults 0 1

```
That results in these options for your mounts:
```

/dev/sda3 on / type btrfs (rw,relatime,space_cache=v2,subvolid=5,subvol=/)
/dev/sda3 on /snap type btrfs (rw,relatime,space_cache=v2,subvolid=5,subvol=/)
/dev/sda4 on /home type btrfs (rw,relatime,space_cache=v2,subvolid=5,subvol=/)
/dev/sda5 on /usr type btrfs (rw,relatime,space_cache=v2,subvolid=5,subvol=/)

```
You can do better, that will tune and improved your filsystem performance.
Thes are the options I use for BTRFS:
```

rw,noatime,compress-force=zstd:3,space_cache=v2

```
For BTRFS and ZFS, on my benchmarks, reads and writes are faster using compression. Why? The memeory used is minimal, and the then only needs to read and write "less" because they take up less room. That is the easy way to describe that.

A rule of thumb I use for figuring out which number to use there:
```

1 = NVMe, uses the most nadwidth possible
2-3 = SATA SSD, multi-disk arrays
3-5 = SATA HHD

```
If an NVMe or SSD, I also add option "ssd" right after that.

Using noatime, instead of relatime with BTRFS is like night and day. Your mounts will be faster. The overall performance of the filesystem will be faster.

Now lets talk about the last fstab field (fs_passno) you have set for each of those, "1" is for root partitions that fsck can check and repair. Ubuntu man fstab says that for other non-root mounted partitions, to change those to "2", and "0" for partitions you do not want checked. My very good friend is very much a BTRFS enthusiste and sets his root to "1" and his other BRTFS vols to "2"...

I set alll my BTRFS vols to "0". The BTRFS readthedocs say that fsck.btrfs is not needed and not to check the vols on boot. It says, if needed, use 'btrfs-check' to check a BTRFS filesystem... So, either way seems to be valid.

---

### Post by grumpyprogrammer on 2023-10-19
Hey there! Thank you so much for the reply.

> **MAFoElffen said:**
> I see a few things

First is the you have 15GB RAM, and at rest, somehow you are using 6.5GB memory?



I'm pretty sure that's due to the amount of Firefox tabs I have open. While I was researching what could be going on, I ended up with quite a few. Here's the result of sudo ps aux|sort -r -k4 | head -n40 | awk '{print $1 "\t" $2 "\t" $4 "\t" $11}':
```

USER    PID    %MEM    COMMAND
joshua    18498    4.4    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    38682    3.4    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    23537    3.2    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    17508    2.3    /usr/bin/gnome-shell
joshua    24146    2.0    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    18980    1.9    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    28875    1.8    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    27059    1.7    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    29841    1.6    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    27528    1.6    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    24143    1.4    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    27021    1.3    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    32817    1.2    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    36909    1.1    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    29558    1.1    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    27699    1.1    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    40208    1.1    /usr/bin/nautilus
joshua    22986    1.1    /usr/bin/kwrite
joshua    50799    1.0    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    32529    1.0    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    18180    1.0    /usr/libexec/xdg-desktop-portal-gnome
joshua    43304    1.0    /usr/bin/smplayer
joshua    37237    0.9    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    46145    0.9    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    37426    0.9    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    22274    0.9    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    46912    0.9    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    37361    0.9    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    36625    0.9    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    25201    0.9    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    37779    0.8    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    27389    0.8    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    39342    0.8    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    29926    0.8    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    23003    0.8    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    22810    0.8    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    36841    0.8    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    18845    0.8    /snap/firefox/3216/usr/lib/firefox/firefox
joshua    48459    0.8    /snap/firefox/3216/usr/lib/firefox/firefox


```

> 
By my records, this GPU should be using the amdgpu driver from the kernel.

Yours, if you look at the graphics section, is using the Radeon driver. I hear that "that" is a common problem with that specific GPU model.


Oh! Now I feel kinda dumb. I always thought the Radeon driver was the OS AMD driver. For some reason I had it in my head that the amdgpu driver was proprietary. 

Thanks for informing me! I changed the grub file with your suggestion.

> 
Welcome fellow Volume Manager enthusiast...


Heh. I can't help it! It's an addiction! :D

> 

[B]stuff about BTRFS and fstab
[/B]


Oh, all of those are good points. Honestly, I completely forgot about my fstab until you mentioned it. Having noatime is something I usually do, but it completely left my mind on this fresh install. I never thought about using compression, though. You're absolutely right, having things compressed will reduce a lot of file IO. I think maybe I was just sketchy about Something Going Horribly Wrong with the compression? Silly, I know.

I've changed the entries in fstab as per your recommendation. Thanks again! You've been a great help!

I decided to leave the fs_passno at 1 for the root mount and 2 for the others. You're completely right in that BTRFS shouldn't need any checking on boot like that, but it helps my paranoia should the power go out. 

I also found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1973434](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1973434)

Which seems to imply that since 22.04 there may have been some kernel malconfiguration (?) on Ubuntu that affected some users. If the suggestions you've given me don't solve things, I'll try  compiling a custom kernel and see if that helps.

Once again, thank you for all your assistance! It's greatly appreciated. I'll test those changes and get back to the thread (probably sometime tomorrow?)

---

### Post by oldfred on 2023-10-20
Do not know BTRFS.

But years ago there were issues with ASmedia ports on AMD systems. I see ASmedia ports shown in your report.
Are you using any of those ports or just the MSI ports?

---

### Post by grumpyprogrammer on 2023-10-20
> **oldfred said:**
> Do not know BTRFS.

But years ago there were issues with ASmedia ports on AMD systems. I see ASmedia ports shown in your report.
Are you using any of those ports or just the MSI ports?

Just the MSI ports as far as I'm aware. At least, the root drive is on an MSI port. I do have two archive drives that might be on ASmedia ports, but they're not mounted. Do you know if such an issue would affect non mounted drives?

Some updates!

After going through **MAFoElffen's **suggestions, I have seen a notable increase in boot time (haven't tested shutdown yet). The desktop also doesn't lag any more, which is a nice big improvement.

Unfortunately, the same cannot be said of specific applications. Anything that does file IO tends to freeze. Sometimes only briefly, but sometimes for minutes at a time. A check of htop during these freezes revealed no CPU or IO load. That leads me to think there might actually be some kind of kernel scheduling snafu, but I'm not really an expert.

Application load times are particularly bad, but that might be a result of using compression on the mounts. After something first loads, if the app is closed and is relaunched, it tends to load pretty snappily.

I confirmed that I'm now using the amgpu driver and while it DID allow me to play video in SMPlayer (though only with the output driver changed to dmabuf-wayland), it had the old problem of launching mpv in a separate window. I decided to apt remove the Ubuntu SMPlayer and used the flatpak instead. While I still get freezes during file IO, video play fine now.

Firefox in particular seems prone to freezing (I'm guessing it does a lot of file IO in the background). Launching through command line does give an error: 

```

update.go:85: cannot change mount namespace according to change mount (/var/lib/snapd/hostfs/usr/share/gimp/2.0/help /usr/share/gimp/2.0/help none bind,ro 0 0): cannot open directory "/var/lib": permission denied
update.go:85: cannot change mount namespace according to change mount (/var/lib/snapd/hostfs/usr/share/xubuntu-docs /usr/share/xubuntu-docs none bind,ro 0 0): cannot open directory "/var/lib": permission denied

```

Which is apparently a known problem. It doesn't seem to have anything to do with the lag or freezing, though.

When Firefox crashes during these freezes (happens rarely, but often enough to be annoying), I see the following errors:
```

Gtk-Message: 10:42:38.662: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.
[GFX1-]: Failed to create EGLSurface!: 0x3000
[GFX1-]: Failed to create EGLSurface. 4 renderers, 3 active.
Gdk-Message: 11:01:35.565: Error 104 (Connection reset by peer) dispatching to Wayland display.
Exiting due to channel error.
Exiting due to channel error.
Exiting due to channel error.
Exiting due to channel error.
Exiting due to channel error.
Exiting due to channel error.
Exiting due to channel error.
Exiting due to channel error.

```

The exact error given changes, but it always relates to failing to create an EGLSurface and exiting due to channel error.

Next up, I'll try compiling a kernel from source and see if that helps. I'll go with the newest non RC version then try one of the 5.11s if that doesn't work. After 5.11 seems to be when folks started having problems.

Thanks again for all your assistance! I really appreciate it.

---

### Post by oldfred on 2023-10-20
One of the comments on Asmedia ports was a user with just a DVD player on one of those ports. 
After he moved to one of the standard ports everything then worked or worked better. Found in my notes this was from a z77 system, so lot older.

Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564)

This is older info, so not sure if it still applies.
The ASMedia 106x SATA controller chipset is buggy. 
[https://www.linuxquestions.org/questions/showthread.php?p=5819208#post5819208](https://www.linuxquestions.org/questions/showthread.php?p=5819208#post5819208)
The Solution: Linux kernel boot parameter "libata.atapi_passthru16=0"

---

### Post by grumpyprogrammer on 2023-10-24
Okay, folks, I discovered the problem.

Turns out my hard drive was failing. Apparently, the problem was intermittent, which is why badblocks and SMART didn't discover it when I ran diagnostics. 

I installed on a different HD and everything works correctly! No appreciable slowdowns or hangs and boot/shutdown is quick.

Thanks again for everyone's help here. I definitely learned a few things. So if nothing else, it was educational!

I think we can mark this one solved (and maybe change the title to the correct Ubuntu version).

Once more, thanks for all your help! You're the best!

---

### Post by MAFoElffen on 2023-10-25
Glad to hear that you found that hard drive problem "before" it failed on you!

The the person who started the thread, it's you that marks it as solved. LOL. Just go to the "Thread Tools" link at the upper right of the first page of a thread you started, and mark it as "Solved". That really makes it easier for other users to find solved answers for their similar problems.

---

