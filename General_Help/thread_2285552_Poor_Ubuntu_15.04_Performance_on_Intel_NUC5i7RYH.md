---
title: "Poor Ubuntu 15.04 Performance on Intel NUC5i7RYH"
date: 2015-07-06
forum: General Help
---

### Post by neltnerb on 2015-07-06
I have been using Ubuntu for many many years, and recently purchased a new computer, the NUC5i7RYH mini-PC from Intel. It uses one of the latest 5th generation core i7 mobile processors with Iris 6100 graphics, 16GB of RAM, and a spinning hard disk.

Overall, the system appears to work, with no showstopper bugs, for which I am very pleased. I even have VMWare Workstation 10 working with accelerated graphics after a bit of tweaking, so I'm not even sure where I can file this since it doesn't feel like a bug so much as a strange quirk that I can't isolate.

The problem I'm having is peculiar and persistent window hangs under light load.

Pidgin, for example, just periodically graying out without any clear cause. Not crashing, just... hanging for a long time. Evolution does it, firefox does it a lot, movie player, even pidgin.

Everything is having some kind of system-wide issue that I can't identify. The windows all recover within some time ranging from a few seconds to tens of seconds, but it's pretty disruptive in regular use.

Given how modern the processor is, the reasonably high end graphics, and the large amount of RAM (I don't have swap, but 16GB...), this is really incomprehensible. I never had issues like this back in 12.04 on much worse hardware, and I expected this computer to work smoothly with few glitches.

Can anyone give me some clues or log files to look for to try to figure this one out? I tried to install preload, but it wanted to install systemd which dpkg didn't like. I'm just at a loss as to how to even diagnose this kind of issue.

When the windows hang, I can even go to a VTTY and top reports minimal CPU load, so it has to be something else. Hard drive thrashing? Some kind of strange other issue? The disk is a spinner, but it is still SATA 6GB/s, so combined with lots of RAM that doesn't seem likely. The disk is using full disk encryption, maybe it's not properly using the CPU integrated encryption system?

In any event, that's all I can think of. If anyone has any ideas I'd love to get this so that my experience is more seamless. Right now it's performing worse than Windows 8.1 on a 4th gen core i5, and I know that it can do better...

---

### Post by kerry_s on 2015-07-06
first i don't recommend preload, ubuntu has it's own thing. preload just gets in the way.

look in /var/log for log files.

personally, with intel everytime compiz is involved there's problems. intel+compiz+unity your lucky you have a desktop at all most times it'll just be a mouse in the center background. lol

try a different de for a while, ubuntu-mate or xubuntu don't seem to give as many issues.

i missed that encryption part, that takes a lot of processing, i think i saw some reports on issues with that. try googling.

---

### Post by neltnerb on 2015-07-07
Thanks for the thoughts and advice. I have a few questions/comments based on this that would help me figure it out a bit better.

I've actually been using full disk encryption for many years with previous versions of Ubuntu dating back to before it was easy to set up (I think as early as 2010 when I got my first core i7 processor).

It does cause a slowdown, but I've never seen it perform this badly and with AES-NI support in the processor it seems like this shouldn't be a major bottleneck. The CPU in any event is not being heavily loaded, so if it is an issue it has to do with something beyond my understanding of how encryption works. I saw from some googling that ~20% drops in hard disk read performance might be typical.

What I'm seeing is behaviour such as Pidgin being open on my screen, with me doing nothing in the foreground (although there are hard disk transfers going on) and the window will just briefly grey out. This is strange to me because at this stage of program execution it should all be loaded into RAM. If it's hitting the hard disk I don't know why, especially since I don't have any swap and have 16GB of RAM. It is of course worse when VMware is running, but even with only 2/4 cores allocated to the host and 10GB of RAM it's certainly not pegging the CPU and there's still much more RAM than I've ever had on a computer before.

Is there a way to monitor when a program tries to use the hard disk to see if there is a correlation? That's a bit more advanced than anything I've tried before, and it's not really showing up in logs in a way that I know how to interpret. It's also happening across applications, which makes me suspect a kernel setting or system wide daemon behaving poorly.

Another really big and consistent one is that when I am using Evolution Email Client and try to move a message, sometimes it hangs for 10-20 seconds. I think this has to do with unity trying to figure out how to handle the drag operation because it looks willing to let me drag it to the unity taskbar, but it's rather annoying. Probably unrelated, and that might be worth filing as a bug for evolution, but another instance of window hangs that don't seem to be correlated to CPU pegging.

With regard to the graphics possibility, on my desktop I was using an NVidia GPU which didn't have problems as often, but did occasionally. Usually only in Evolution when dragging messages or when having many tabs open in Chrome though, so I'm comfortable assuming that was a different issue.

Is there a way to get useful logging information out of the graphics card?

Xorg.0.log doesn't have any events coinciding with the hangs.

gpu-manager.log shows
> 
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
grep dmesg status 256
dmesg status 256 == 0? No
grep dmesg status 256
dmesg status 256 == 0? No
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? no
Is fglrx kernel module available? no
Is nvidia kernel module available? no
Vendor/Device Id: 8086:162b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
        HDMIA connector
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Current core alternative: (null)
Is nvidia enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is nvidia available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is pxpress available? no
Is prime available? no
Single card detected
Nothing to do
No change - nothing to do


syslog shows a fair number of events and seeming warnings/errors but I don't know how to read them. Some things that look like they could be related are
> 
Jul  7 12:08:06 zeeman systemd[1]: Job dev-mapper-ubuntu\x2d\x2dvg\x2dswap_1.device/start timed out.
Jul  7 12:08:06 zeeman systemd[1]: Timed out waiting for device dev-mapper-ubuntu\x2d\x2dvg\x2dswap_1.device.
Jul  7 12:08:06 zeeman systemd[1]: Dependency failed for /dev/mapper/ubuntu--vg-swap_1.
Jul  7 12:08:06 zeeman systemd[1]: Job dev-mapper-ubuntu\x2d\x2dvg\x2dswap_1.swap/start failed with result 'dependency'.
Jul  7 12:08:06 zeeman systemd[1]: Job dev-mapper-ubuntu\x2d\x2dvg\x2dswap_1.device/start failed with result 'timeout'.

which repeats with some frequency.

lightdm.log shows nothing out of the ordinary other than some debug messages that don't look scary.

Anywhere else worth looking? Do these messages provide any insight as to an incorrectly configured system?

---

