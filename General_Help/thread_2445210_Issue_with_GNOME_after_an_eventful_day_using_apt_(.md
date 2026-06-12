---
title: "Issue with GNOME after an eventful day using apt (Ubuntu 18.04 - 5.3.0-59-generic)"
date: 2020-06-10
forum: General Help
---

### Post by cadmus1986 on 2020-06-10
Hello,

So I have been doing a few things on my laptop today, including a few apt commands. Later on, I noticed that gnome is acting a bit weird, and I can't show settings anymore or control volume. I tried reinstalling gnome a few times, but nothing happened. Below is a dmesg output after rebooting:

```

[   79.958201] pulseaudio[3328]: segfault at 8 ip 00007f5968f9d7f9 sp 00007ffeccc58110 error 4 in ld-2.27.so[7f5968f91000+27000][   79.958212] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[   81.024302] pulseaudio[3569]: segfault at 8 ip 00007fdced61b7f9 sp 00007ffcd46327d0 error 4 in ld-2.27.so[7fdced60f000+27000]
[   81.024309] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[   82.142517] pulseaudio[3576]: segfault at 8 ip 00007f519b5737f9 sp 00007fffee80cc50 error 4 in ld-2.27.so[7f519b567000+27000]
[   82.142528] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[   83.382137] pulseaudio[3583]: segfault at 8 ip 00007f46317527f9 sp 00007ffe40583c90 error 4 in ld-2.27.so[7f4631746000+27000]
[   83.382149] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[   85.614234] pulseaudio[3590]: segfault at 8 ip 00007f0d3b51e7f9 sp 00007fffede853f0 error 4 in ld-2.27.so[7f0d3b512000+27000]
[   85.614245] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[   91.666875] pulseaudio[3619]: segfault at 8 ip 00007f134c8af7f9 sp 00007ffff7cf1ed0 error 4 in ld-2.27.so[7f134c8a3000+27000]
[   91.666888] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[   92.453410] pulseaudio[3628]: segfault at 8 ip 00007f84c9b437f9 sp 00007fff01e328f0 error 4 in ld-2.27.so[7f84c9b37000+27000]
[   92.453413] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[  119.030375] Lockdown: Xorg: ioperm is restricted; see man kernel_lockdown.7
[  129.254309] goa-daemon[3980]: segfault at 8 ip 00007fcb4ab137f9 sp 00007ffe310bc270 error 4 in ld-2.27.so[7fcb4ab07000+27000]
[  129.254316] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[  129.293749] pulseaudio[3970]: segfault at 8 ip 00007fb46bc767f9 sp 00007ffe2ad7c2d0 error 4 in ld-2.27.so[7fb46bc6a000+27000]
[  129.293754] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[  129.523296] goa-daemon[4021]: segfault at 8 ip 00007f11dba627f9 sp 00007fffae609930 error 4 in ld-2.27.so[7f11dba56000+27000]
[  129.523300] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[  129.948290] rfkill: input handler disabled
[  130.513599] pulseaudio[4080]: segfault at 8 ip 00007ff9860387f9 sp 00007ffd3cf44880 error 4 in ld-2.27.so[7ff98602c000+27000]
[  130.513603] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[  132.349014] pulseaudio[4205]: segfault at 8 ip 00007f5f628137f9 sp 00007ffd7f693b00 error 4 in ld-2.27.so[7f5f62807000+27000]
[  132.349018] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[  135.730162] pulseaudio[4288]: segfault at 8 ip 00007f68cab617f9 sp 00007ffe7d14a810 error 4 in ld-2.27.so[7f68cab55000+27000]
[  135.730174] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[  138.726558] pulseaudio[4306]: segfault at 8 ip 00007f53842857f9 sp 00007fff7cbce900 error 4 in ld-2.27.so[7f5384279000+27000]
[  138.726571] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[  169.572129] pulseaudio[4875]: segfault at 8 ip 00007f3fafd8f7f9 sp 00007fff57d1b160 error 4 in ld-2.27.so[7f3fafd83000+27000]
[  169.572140] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[  170.451415] pulseaudio[4960]: segfault at 8 ip 00007f80f65527f9 sp 00007ffe197837a0 error 4 in ld-2.27.so[7f80f6546000+27000]
[  170.451419] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[  179.755043] pulseaudio[5105]: segfault at 8 ip 00007f4e82d2a7f9 sp 00007fffc11d50a0 error 4 in ld-2.27.so[7f4e82d1e000+27000]
[  179.755049] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[  250.858880] deja-dup-monito[5415]: segfault at 8 ip 00007f517aa897f9 sp 00007ffc16f07640 error 4 in ld-2.27.so[7f517aa7d000+27000]
[  250.858887] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[  264.571881] pulseaudio[5514]: segfault at 8 ip 00007fef45aed7f9 sp 00007ffe6a076f70 error 4 in ld-2.27.so[7fef45ae1000+27000]
[  264.571893] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[  303.326769] pulseaudio[5550]: segfault at 8 ip 00007efc7f5c37f9 sp 00007ffd3222ef50 error 4 in ld-2.27.so[7efc7f5b7000+27000]
[  303.326784] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85



```

Then when I try to show settings, I get the following:

```
[ 1036.790318] goa-daemon[7316]: segfault at 8 ip 00007f060502d7f9 sp 00007ffde4f5b8f0 error 4 in ld-2.27.so[7f0605021000+27000][ 1036.790323] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[ 1037.803099] goa-daemon[7350]: segfault at 8 ip 00007f5779cc77f9 sp 00007ffef46e4790 error 4 in ld-2.27.so[7f5779cbb000+27000]
[ 1037.803103] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85
[ 1039.195334] gnome-control-c[7335]: segfault at 8 ip 00007f438d58d7f9 sp 00007fffb7791f70 error 4 in ld-2.27.so[7f438d581000+27000]
[ 1039.195339] Code: 85 4c 12 00 00 49 83 bf f0 00 00 00 00 48 c7 85 08 ff ff ff 00 00 00 00 0f 85 39 11 00 00 49 8b 47 68 49 83 bf f8 00 00 00 00 <48> 8b 40 08 48 89 85 30 ff ff ff 0f 84 56 04 00 00 45 85 ed 0f 85



```

Any ideas what is wrong?

---

### Post by deadflowr on 2020-06-10
> So I have been doing a few things on my laptop today, including a few apt commands. 
What apt commands?

---

### Post by cadmus1986 on 2020-06-10
I was trying to install wordpress locally, and so had to use apt for this purpose (wordpress, php, mysql and apache2). Then after I finished and didn't want the packages anymore I did a few removes with autocleaning and autoremoves as well. I also did a dist-upgrade. I should have used a container or something instead of installing and uninstalling so many system wide dependencies, I admit. But for now, I just want to understand what happened to my machine.

---

### Post by cadmus1986 on 2020-06-11
I have done stack trace on gnome-control-center and it seems like there is a problem with dl-reloc.c:

```
Program received signal SIGSEGV, Segmentation fault._dl_relocate_object (scope=0x7ffff7fb2358, reloc_mode=<optimised out>, consider_profiling=consider_profiling@entry=0) at dl-reloc.c:231
231	dl-reloc.c: No such file or directory.
```

I tried reinstalling glibc but it doesn't solve the problem. Any ideas?

---

