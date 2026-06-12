---
title: "Unable to change screen resolution today,what has changed?"
date: 2016-02-03
forum: General Help
---

### Post by RobertoRecordo on 2016-02-03
I am using Ubuntu Gnome 15.10, I have had no issues since upgrading on 16 January 2016

Today I booted and the screen resolution was 640x480, and when I opened setting=> display there were two problems:
[LIST=1]
[*]only available setting was 640x480 
[*]I was unable to drag the dialog box fully into the display area 
[/LIST]

I wiggled the cables, rebooted, it was still the same. I booted a live CD, the resolution was 1024x768

Then I reverted to an earlier kernel ( latest I have is 4.2.0-27)
```
$ uname -a
Linux dell-t1500 4.2.0-25-generic #30-Ubuntu SMP Mon Jan 18 12:31:50 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

And all is well. 
Can anyone tell me how to determine what specifically changed? Can I find and fix the problem?

My thanks in advance,

---

### Post by RobertoRecordo on 2016-02-04
New information on this problem:

The New, problem kernel ```
$ uname -r 
4.2.0-27-generic
$
$ sudo lshw -c video
  *-**display UNCLAIMED**
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fb800000-fbbfffff memory:d0000000-dfffffff ioport:ec00(size=8)
```
The Older, working kernel```
$ uname -r
4.2.0-25-generic
$
$ sudo lshw -c video
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: **driver=i915** latency=0
       resources: irq:24 memory:fb800000-fbbfffff memory:d0000000-dfffffff ioport:ec00(size=8)]
```

I think this demonstrates that the new kernel fails to identify the video controller, and does not load the the i915 driver.
I don't know how to did deeper into the cause, so I'm going to see if i can reinstall the new kerne. I will just delete the new kernel if I have to.


Thoughts? Comments? Advice?

-Rob

---

### Post by RobertoRecordo on 2016-02-04
It took me some time to get advice that I could understand, and trusted to be complete, but i fount it here
[HTML]http://community.linuxmint.com/tutorial/view/1718[/HTML] my thanks to Jahid!

Tha I pulled the trigger
```
sudo apt-get purge linux-image-4.2.0-27-generic
sudo apt-get purge linux-headers-4.2.0-27-generic 

sudo update-grub
reboot
```

and I am now booting the older kernel.

The last time I tried something like this I made a mistake and thrashed the system to the point I just had to start over from scratch.

I marked this SOLVED, even though I  never learned if there was a bug in the newest version, a corrupted download, or it it was something I had accidentally caused. I'm over it for now.

-Rob

---

### Post by RobertoRecordo on 2016-02-11
> I marked this SOLVED, even though I  never learned if there was a bug in the newest version, a corrupted download, or it it was something I had accidentally caused. I'm over it for now.

-Rob

Update: I accidentally allowed a system update and once again have the kernal that I had thought caused the problem.```
$ cat /proc/version_signature 
Ubuntu 4.2.0-27.32-generic 4.2.8-ckt1
$ sudo lshw -c video
[sudo] password for xx: 
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:24 memory:fb800000-fbbfffff memory:d0000000-dfffffff ioport:ec00(size=8)

```

Observe that the video hardware is correctly identified, and the correct driver installed.
Conclusion: the update package did not cause my problem, I presume that something happened on my system to cause the problem.
Result, I am really done with this now!

---

