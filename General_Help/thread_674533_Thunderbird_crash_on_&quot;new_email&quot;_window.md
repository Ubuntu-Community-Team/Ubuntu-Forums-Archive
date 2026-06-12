---
title: "Thunderbird crash on &quot;new email&quot; window"
date: 2008-01-21
forum: General Help
---

### Post by anthropop on 2008-01-21
I am using Thunderbird 2.0.0.0 and Gutsy and it was working just fine.  Then something happened and now when I try and open a new email window to write an email, or reply to an email it crashes.  I have tried disabling my advanced Visual Effects for the desktop as that is something I had started using, but that has no effect.  

The other interesting symptom is that if I log into the machine with "ssh -X [email]username@my_ip.com[/email]" and launch thunderbird it works just fine.  In that case it is using all the same mail folders, and program executable, the only difference is that the X display output is going to the remote machine.  Not only that, but other accounts on the SAME machine can send email without crashing, so this appears to be related to files in my personal account.  I suspect it is related to X display files.

I have backup respositories of the linux / and /home partitions, so I could try reverting, but I would like some advice on what files to revert?  Could this be a Gutsy display issue, or should I reinstall thunderbird?

Note that doing an strace (full list below) produces the following key crash line at the point at which I hit the "start new email" button:
wait4(-1, *** glibc detected *** /usr/thunderbird/thunderbird-bin: free(): invalid next size (normal): 0x0972b250 ***

This may not be related, but I also had the linux partition fill up by accident a few days ago when I did a backup to the wrong target.  That created some temporary negative effects, but after fixing the problem and rebooting all was well again.

---

### Post by anthropop on 2008-01-21
I have done an strace on the output, here is the first part:
$ strace /usr/thunderbird/thunderbird
execve("/usr/thunderbird/thunderbird", ["/usr/thunderbird/thunderbird"], [/* 37 vars */]) = 0
brk(0)                                  = 0x805f000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f41000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=65326, ...}) = 0
mmap2(NULL, 65326, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f31000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260a\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1339816, ...}) = 0
mmap2(NULL, 1349136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7de7000
mmap2(0xb7f2b000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x143) = 0xb7f2b000
mmap2(0xb7f2e000, 9744, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f2e000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7de6000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7de66b0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7f2b000, 4096, PROT_READ)   = 0
munmap(0xb7f31000, 65326)               = 0
getpid()                                = 1945
rt_sigaction(SIGCHLD, {SIG_DFL}, {SIG_DFL}, 8) = 0
geteuid32()                             = 1000
brk(0)                                  = 0x805f000
brk(0x8080000)                          = 0x8080000
getppid()                               = 1944
stat64("/home/daniel", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/thunderbird/thunderbird", O_RDONLY) = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {0x80551b0, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL}, NULL, 8) = 0

---

### Post by anthropop on 2008-01-21
2nd part:

read(10, "#!/bin/sh\n#\n# ***** BEGIN LICENS"..., 8192) = 5205
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7de66f8) = 1946
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "/usr/thunderbird\n", 128)      = 17
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 1946
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7de66f8) = 1947
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 1947
--- SIGCHLD (Child exited) @ 0 (0) ---
stat64("/usr/thunderbird/run-mozilla.sh", {st_mode=S_IFREG|0755, st_size=10492, ...}) = 0
geteuid32()                             = 1000
getgid32()                              = 1004
getegid32()                             = 1004
getgroups32(0, NULL)                    = 18
getgroups32(18, [4, 20, 21, 24, 25, 29, 30, 44, 46, 109, 111, 114, 119, 124, 125, 1004, 1006, 1007]) = 18
open("/usr/thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
getdents(3, /* 3 entries */, 4096)      = 52
getdents(3, /* 0 entries */, 4096)      = 0
close(3)                                = 0
open("/home/daniel/.thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = -1 ENOENT (No such file or directory)
stat64("/usr/thunderbird/init.d/S*", 0xbfb8e44c) = -1 ENOENT (No such file or directory)
stat64("/home/daniel/.thunderbird/init.d/S*", 0xbfb8e44c) = -1 ENOENT (No such file or directory)
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7de66f8) = 1948
wait4(-1, *** glibc detected *** /usr/thunderbird/thunderbird-bin: munmap_chunk(): invalid pointer: 0x098230d0 ***

---

### Post by anthropop on 2008-01-21
3rd Part:

read(10, "#!/bin/sh\n#\n# ***** BEGIN LICENS"..., 8192) = 5205
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7de66f8) = 1946
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "/usr/thunderbird\n", 128)      = 17
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 1946
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7de66f8) = 1947
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 1947
--- SIGCHLD (Child exited) @ 0 (0) ---
stat64("/usr/thunderbird/run-mozilla.sh", {st_mode=S_IFREG|0755, st_size=10492, ...}) = 0
geteuid32()                             = 1000
getgid32()                              = 1004
getegid32()                             = 1004
getgroups32(0, NULL)                    = 18
getgroups32(18, [4, 20, 21, 24, 25, 29, 30, 44, 46, 109, 111, 114, 119, 124, 125, 1004, 1006, 1007]) = 18
open("/usr/thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
getdents(3, /* 3 entries */, 4096)      = 52
getdents(3, /* 0 entries */, 4096)      = 0
close(3)                                = 0
open("/home/daniel/.thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = -1 ENOENT (No such file or directory)
stat64("/usr/thunderbird/init.d/S*", 0xbfb8e44c) = -1 ENOENT (No such file or directory)
stat64("/home/daniel/.thunderbird/init.d/S*", 0xbfb8e44c) = -1 ENOENT (No such file or directory)
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7de66f8) = 1948
wait4(-1, *** glibc detected *** /usr/thunderbird/thunderbird-bin: munmap_chunk(): invalid pointer: 0x098230d0 ***

---

### Post by anthropop on 2008-01-21
Best part:


======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb72f492b]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb784e961]
/usr/thunderbird/thunderbird-bin[0x826be52]
/usr/thunderbird/thunderbird-bin[0x826c98d]
/usr/thunderbird/thunderbird-bin[0x826aaa2]
/usr/thunderbird/thunderbird-bin[0x82be98c]
/usr/thunderbird/thunderbird-bin[0x82bdd0c]
/usr/thunderbird/thunderbird-bin[0x82fb444]
/usr/thunderbird/thunderbird-bin[0x83e1110]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x82f8454]
/usr/thunderbird/thunderbird-bin[0x82f836f]
/usr/thunderbird/thunderbird-bin[0x82f8317]
/usr/thunderbird/thunderbird-bin[0x82de573]
/usr/thunderbird/thunderbird-bin[0x84e5782]
/usr/thunderbird/thunderbird-bin[0x84e981c]
/usr/thunderbird/thunderbird-bin[0x84e9218]
/usr/thunderbird/thunderbird-bin[0x84e7fbb]
/usr/thunderbird/thunderbird-bin[0x84ead94]
/usr/thunderbird/thunderbird-bin[0x84e50e6]
/usr/thunderbird/thunderbird-bin[0x829bf89]
/usr/thunderbird/thunderbird-bin[0x8293f6b]
/usr/thunderbird/thunderbird-bin[0x8298e80]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7b781de]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb78e3772]
/usr/lib/libgobject-2.0.so.0[0xb78f4323]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb78f560f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb78f5a09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c96498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x475)[0xb7b726f5]
/usr/lib/libgdk-x11-2.0.so.0[0xb79c806f]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0xba)[0xb79c873a]
/usr/lib/libgdk-x11-2.0.so.0[0xb79c879b]
/usr/lib/libgdk-x11-2.0.so.0[0xb79ae5e8]
/usr/lib/libglib-2.0.so.0[0xb7845551]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb784711c]
/usr/lib/libglib-2.0.so.0[0xb784a55f]
======= Memory map: ========
08048000-08d00000 r-xp 00000000 08:01 5046689    /usr/thunderbird/thunderbird-bin
08d00000-08d19000 rwxp 00cb7000 08:01 5046689    /usr/thunderbird/thunderbird-bin
08d19000-09c3c000 rwxp 08d19000 00:00 0          [heap]
b120b000-b12fe000 rwxp b120b000 00:00 0 
b12fe000-b12ff000 ---p b12fe000 00:00 0 
b12ff000-b1aff000 rwxp b12ff000 00:00 0 
b1aff000-b1b00000 ---p b1aff000 00:00 0 
b1b00000-b235b000 rwxp b1b00000 00:00 0 
b235b000-b2400000 ---p b235b000 00:00 0 
b242c000-b242d000 ---p b242c000 00:00 0 
b242d000-b2c2d000 rwxp b242d000 00:00 0 
b2c2d000-b2c2e000 ---p b2c2d000 00:00 0 
b2c2e000-b342e000 rwxp b2c2e000 00:00 0 
b342e000-b3432000 r-xp 00000000 08:01 12959755   /lib/tls/i686/cmov/libnss_dns-2.6.1.so
b3432000-b3434000 rwxp 00003000 08:01 12959755   /lib/tls/i686/cmov/libnss_dns-2.6.1.so
b3434000-b3436000 r-xp 00000000 08:01 16777311   /lib/libnss_mdns4_minimal.so.2
b3436000-b3437000 rwxp 00001000 08:01 16777311   /lib/libnss_mdns4_minimal.so.2
b3447000-b3448000 ---p b3447000 00:00 0 
b3448000-b3c49000 rwxp b3448000 00:00 0 
b3c49000-b3c4d000 r-xp 00000000 08:01 5046516    /usr/thunderbird/components/libmozgnome.so
b3c4d000-b3c4e000 rwxp 00003000 08:01 5046516    /usr/thunderbird/components/libmozgnome.so
b3c4e000-b3c86000 r-xp 00000000 08:01 5046626    /usr/thunderbird/libnssckbi.so
b3c86000-b3c8f000 rwxp 00038000 08:01 5046626    /usr/thunderbird/libnssckbi.so
b3c8f000-b3ccb000 r-xp 00000000 08:01 5046621    /usr/thunderbird/libfreebl3.so
b3ccb000-b3ccc000 rwxp 0003c000 08:01 5046621    /usr/thunderbird/libfreebl3.so
b3ccc000-b3ccd000 ---p b3ccc000 00:00 0 
b3ccd000-b44cd000 rwxp b3ccd000 00:00 0 
b44cd000-b44ce000 ---p b44cd000 00:00 0 
b44ce000-b4ccf000 rwxp b44ce000 00:00 0 
b4ccf000-b4d2f000 rwxs 00000000 00:09 3833865    /SYSV00000000 (deleted)
b4d2f000-b4db3000 r-xp 00000000 08:01 2933153    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b4db3000-b4db5000 r-xp 00000000 08:01 2998367    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4db5000-b4db6000 rwxp 00001000 08:01 2998367    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4db6000-b4e41000 r-xp 00000000 08:01 2933152    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4e41000-b4ecc000 r-xp 00000000 08:01 2933152    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4ecc000-b4edc000 r-xp 00000000 08:01 5046541    /usr/thunderbird/components/libspellchecker.so
b4edc000-b4edd000 rwxp 0000f000 08:01 5046541    /usr/thunderbird/components/libspellchecker.so
b4edd000-b4f00000 r-xp 00000000 08:01 2965676    /usr/share/fonts/type1/gsfonts/n021003l.pfb
b4f00000-b4f06000 r-xs 00000000 08:01 11813226   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b4f06000-b4f09000 r-xs 00000000 08:01 11813224   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b4f09000-b4f0a000 r-xs 00000000 08:01 11813249   /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b4f0a000-b4f0c000 r-xs 00000000 08:01 11813223   /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b4f0c000-b4f0d000 r-xs 00000000 08:01 11813248   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b4f0d000-b4f0e000 r-xs 00000000 08:01 11813247   /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b4f0e000-b4f12000 r-xs 00000000 08:01 11813222   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b4f12000-b4f13000 r-xs 00000000 08:01 11813221   /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b4f13000-b4f16000 r-xs 00000000 08:01 11813220   /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86.cache-2
b4f16000-b4f17000 r-xs 00000000 08:01 11813219   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b4f17000-b4f19000 r-xs 00000000 08:01 11813246   /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b4f19000-b4f1c000 r-xs 00000000 08:01 11813245   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b4f1c000-b4f1e000 r-xs 00000000 08:01 11813240   /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b4f1e000-b4f1f000 r-xs 00000000 08:01 11813218   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b4f1f000-b4f21000 r-xs 00000000 08:01 11813239   /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b4f21000-b4f27000 r-xs 00000000 08:01 11813217   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b4f27000-b4f29000 r-xs 00000000 08:01 11813182   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4f29000-b4f2b000 r-xs 00000000 08:01 11813164   /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b4f2b000-b4f33000 r-xs 00000000 08:01 11813163   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b4f33000-b4f39000 r-xs 00000000 08:01 11813234   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b4f39000-b4f3a000 r-xs 00000000 08:01 11813216   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4f3a000-b4f51000 r-xs 00000000 08:01 11813238   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b4f51000-b4f53000 r-xs 00000000 08:01 11813159   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b4f53000-b4f59000 r-xs 00000000 08:01 11813158   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b4f59000-b4f5c000 r-xs 00000000 08:01 11813237   /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b4f5c000-b4f60000 r-xs 00000000 08:01 11813263   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4f60000-b4f67000 r-xs 00000000 08:01 11813232   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b4f67000-b4f68000 r-xs 00000000 08:01 11813267   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b4f68000-b4f69000 r-xs 00000000 08:01 11813265   /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b4f69000-b4f6a000 r-xs 00000000 08:01 11813138   /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b4f6a000-b4f6c000 r-xs 00000000 08:01 11813262   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b4f6c000-b4f6f000 r-xs 00000000 08:01 11813276   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b4f6f000-b4f78000 r-xs 00000000 08:01 11813260   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b4f78000-b4f7b000 r-xs 00000000 08:01 11813137   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b4f7b000-b4f7c000 r-xs 00000000 08:01 11813258   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b4f7c000-b4f7e000 r-xs 00000000 08:01 11813136   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b4f7e000-b4f83000 r-xs 00000000 08:01 11813255   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b4f83000-b4f87000 r-xs 00000000 08:01 11813135   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b4f87000-b4f8c000 r-xs 00000000 08:01 11813253   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b4f8c000-b4f8f000 r-xs 00000000 08:01 11813210   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b4f8f000-b4f95000 r-xs 00000000 08:01 11813233   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b4f95000-b4f9b000 r-xs 00000000 08:01 11813275   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b4f9b000-b4fa3000 r-xs 00000000 08:01 11813089   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b4fa3000-b4fa4000 ---p b4fa3000 00:00 0 
b4fa4000-b57a4000 rwxp b4fa4000 00:00 0 
b57a4000-b57da000 r-xp 00000000 08:01 16777329   /lib/libsepol.so.1
b57da000-b57db000 rwxp 00035000 08:01 16777329   /lib/libsepol.so.1
b57db000-b57e5000 rwxp b57db000 00:00 0 
b57e5000-b5834000 r-xp 00000000 08:01 2720419    /usr/lib/libgcrypt.so.11.2.3
b5834000-b5836000 rwxp 0004e000 08:01 2720419    /usr/lib/libgcrypt.so.11.2.3
b5836000-b5839000 r-xp 00000000 08:01 2720093    /usr/lib/libgpg-error.so.0.3.0
b5839000-b583a000 rwxp 00002000 08:01 2720093    /usr/lib/libgpg-error.so.0.3.0
b583a000-b5849000 r-xp 00000000 08:01 2720767    /usr/lib/libtasn1.so.3.0.9
b5849000-b584a000 rwxp 0000e000 08:01 2720767    /usr/lib/libtasn1.so.3.0.9
b584a000-b590b000 r-xp 00000000 08:01 2720950    /usr/lib/libasound.so.2.0.0
b590b000-b5910000 rwxp 000c0000 08:01 2720950    /usr/lib/libasound.so.2.0.0
b5910000-b5914000 r-xp 00000000 08:01 2722749    /usr/lib/libORBitCosNaming-2.so.0.1.0
b5914000-b5915000 rwxp 00003000 08:01 2722749    /usr/lib/libORBitCosNaming-2.so.0.1.0
b5915000-b5917000 r-xp 00000000 08:01 12959766   /lib/tls/i686/cmov/libutil-2.6.1.so
b5917000-b5919000 rwxp 00001000 08:01 12959766   /lib/tls/i686/cmov/libutil-2.6.1.so
b5919000-b592d000 r-xp 00000000 08:01 16777434   /lib/libselinux.so.1
b592d000-b592f000 rwxp 00013000 08:01 16777434   /lib/libselinux.so.1
b592f000-b593e000 r-xp 00000000 08:01 12959762   /lib/tls/i686/cmov/libresolv-2.6.1.so
b593e000-b5940000 rwxp 0000f000 08:01 12959762   /lib/tls/i686/cmov/libresolv-2.6.1.so
b5940000-b5942000 rwxp b5940000 00:00 0 
b5942000-b5950000 r-xp 00000000 08:01 2719786    /usr/lib/libavahi-client.so.3.2.2
b5950000-b5951000 rwxp 0000e000 08:01 2719786    /usr/lib/libavahi-client.so.3.2.2
b5951000-b595b000 r-xp 00000000 08:01 2719788    /usr/lib/libavahi-common.so.3.4.4
b595b000-b595c000 rwxp 00009000 08:01 2719788    /usr/lib/libavahi-common.so.3.4.4
b595c000-b59c6000 r-xp 00000000 08:01 2720778    /usr/lib/libgnutls.so.13.3.0
b59c6000-b59cc000 rwxp 0006a000 08:01 2720778    /usr/lib/libgnutls.so.13.3.0
b59cc000-b5a00000 r-xp 00000000 08:01 2719768    /usr/lib/libdbus-1.so.3.3.0
b5a00000-b5a01000 rwxp 00033000 08:01 2719768    /usr/lib/libdbus-1.so.3.3.0
b5a01000-b5a1b000 r-xp 00000000 08:01 2721096    /usr/lib/libdbus-glib-1.so.2.1.0
b5a1b000-b5a1c000 rwxp 0001a000 08:01 2721096    /usr/lib/libdbus-glib-1.so.2.1.0
b5a1c000-b5b34000 r-xp 00000000 08:01 2720742    /usr/lib/libxml2.so.2.6.30
b5b34000-b5b39000 rwxp 00118000 08:01 2720742    /usr/lib/libxml2.so.2.6.30
b5b39000-b5b3a000 rwxp b5b39000 00:00 0 
b5b3a000-b5b5a000 r-xp 00000000 08:01 2720573    /usr/lib/libaudiofile.so.0.0.2
b5b5a000-b5b5c000 rwxp 00020000 08:01 2720573    /usr/lib/libaudiofile.so.0.0.2
b5b5c000-b5b6f000 r-xp 00000000 08:01 2720981    /usr/lib/libbonobo-activation.so.4.0.0
b5b6f000-b5b71000 rwxp 00013000 08:01 2720981    /usr/lib/libbonobo-activation.so.4.0.0
b5b71000-b5bc3000 r-xp 00000000 08:01 2720292    /usr/lib/libbonobo-2.so.0.0.0
b5bc3000-b5bcd000 rwxp 00051000 08:01 2720292    /usr/lib/libbonobo-2.so.0.0.0
b5bcd000-b5c23000 r-xp 00000000 08:01 2719928    /usr/lib/libgnomevfs-2.so.0.2000.0
b5c23000-b5c26000 rwxp 00055000 08:01 2719928    /usr/lib/libgnomevfs-2.so.0.2000.0
b5c26000-b5c3a000 r-xp 00000000 08:01 2722319    /usr/lib/libgnome-2.so.0.2000.0
b5c3a000-b5c3b000 rwxp 00014000 08:01 2722319    /usr/lib/libgnome-2.so.0.2000.0
b5c3b000-b5c3c000 r-xs 00000000 08:01 11813256   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b5c3c000-b5c3d000 r-xs 00000000 08:01 11813134   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b5c3d000-b5c3e000 r-xs 00000000 08:01 11813133   /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b5c3e000-b5c42000 r-xs 00000000 08:01 11813229   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b5c42000-b5c46000 r-xs 00000000 08:01 11813085   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b5c46000-b5c4b000 r-xs 00000000 08:01 11813228   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b5c4b000-b5cab000 rwxs 00000000 00:09 3801096    /SYSV00000000 (deleted)
b5cab000-b5cf4000 r-xp 00000000 08:01 2720289    /usr/lib/libORBit-2.so.0.1.0
b5cf4000-b5cfd000 rwxp 00049000 08:01 2720289    /usr/lib/libORBit-2.so.0.1.0
b5cfd000-b5cfe000 rwxp b5cfd000 00:00 0 
b5cfe000-b5cff000 ---p 00000000 00:0e 2802       /dev/zero
b5cff000-b5dff000 rwxp 00001000 00:0e 2802       /dev/zero
b5dff000-b5e00000 ---p 00101000 00:0e 2802       /dev/zero
b5e00000-b5f00000 rwxp b5e00000 00:00 0 
b5f00000-b5f02000 r-xs 00000000 08:01 11813277   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b5f02000-b5f0b000 r-xp 00000000 08:01 2721180    /usr/lib/libesd.so.0.2.38
b5f0b000-b5f0c000 rwxp 00009000 08:01 2721180    /usr/lib/libesd.so.0.2.38
b5f0c000-b5f13000 r-xp 00000000 08:01 12959763   /lib/tls/i686/cmov/librt-2.6.1.so
b5f13000-b5f15000 rwxp 00006000 08:01 12959763   /lib/tls/i686/cmov/librt-2.6.1.so
b5f15000-b5f19000 r-xp 00000000 08:01 27607089   /usr/lib/libgthread-2.0.so.0.1400.1
b5f19000-b5f1a000 rwxp 00003000 08:01 27607089   /usr/lib/libgthread-2.0.so.0.1400.1
b5f1a000-b5f49000 r-xp 00000000 08:01 2720081    /usr/lib/libgconf-2.so.4.1.2
b5f49000-b5f4c000 rwxp 0002e000 08:01 2720081    /usr/lib/libgconf-2.so.4.1.2
b5f4c000-b5f4d000 r-xs 00000000 08:01 11813110   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b5f4d000-b5f54000 r-xp 00000000 08:01 16777266   /lib/libpopt.so.0.0.0
b5f54000-b5f55000 rwxp 00006000 08:01 16777266   /lib/libpopt.so.0.0.0
b5f55000-b5f5b000 r-xp 00000000 08:01 2769733    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b5f5b000-b5f5c000 rwxp 00005000 08:01 2769733    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b5f5c000-b5f7d000 r-xp 00000000 08:01 5046599    /usr/thunderbird/extensions/talkback@mozilla.org/components/talkback/talkback.so
b5f7d000-b5f7f000 rwxp 00021000 08:01 5046599    /usr/thunderbird/extensions/talkback@mozilla.org/components/talkback/talkback.so
b5f7f000-b5f86000 rwxp b5f7f000 00:00 0 
b5f86000-b5f87000 ---p b5f86000 00:00 0 
b5f87000-b6787000 rwxp b5f87000 00:00 0 
b6787000-b6793000 r-xp 00000000 08:01 2768937    /usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
b6793000-b6794000 rwxp 0000c000 08:01 2768937    /usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
b6794000-b67ab000 r-xp 00000000 08:01 5046413    /usr/thunderbird/components/libjar50.so
b67ab000-b67ac000 rwxp 00016000 08:01 5046413    /usr/thunderbird/components/libjar50.so
b67ac000-b67ad000 ---p b67ac000 00:00 0 
b67ad000-b6fad000 rwxp b67ad000 00:00 0 
b6fad000-b6fb8000 r-xp 00000000 08:01 5046543    /usr/thunderbird/components/libmyspell.so
b6fb8000-b6fb9000 rwxp 0000b000 08:01 5046543    /usr/thunderbird/components/libmyspell.so
b6fb9000-b6fc2000 r-xp 00000000 08:01 12959756   /lib/tls/i686/cmov/libnss_files-2.6.1.so
b6fc2000-b6fc4000 rwxp 00008000 08:01 12959756   /lib/tls/i686/cmov/libnss_files-2.6.1.so
b6fc4000-b6fcc000 r-xp 00000000 08:01 12959758   /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b6fcc000-b6fce000 rwxp 00007000 08:01 12959758   /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b6fce000-b6fe2000 r-xp 00000000 08:01 12959753   /lib/tls/i686/cmov/libnsl-2.6.1.so
b6fe2000-b6fe4000 rwxp 00013000 08:01 12959753   /lib/tls/i686/cmov/libnsl-2.6.1.so
b6fe4000-b6fe6000 rwxp b6fe4000 00:00 0 
b6fe6000-b6fed000 r-xp 00000000 08:01 12959754   /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b6fed000-b6fef000 rwxp 00006000 08:01 12959754   /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b6fef000-b6ff1000 r-xp 00000000 08:01 2721632    /usr/lib/libavahi-glib.so.1.0.1
b6ff1000-b6ff2000 rwxp 00001000 08:01 2721632    /usr/lib/libavahi-glib.so.1.0.1
b6ff2000-b6ff7000 r-xp 00000000 08:01 5046603    /usr/thunderbird/extensions/talkback@mozilla.org/components/libqfaservices.so
b6ff7000-b6ff8000 rwxp 00004000 08:01 5046603    /usr/thunderbird/extensions/talkback@mozilla.org/components/libqfaservices.so
b6ff8000-b6ffa000 r-xp 00000000 08:01 2737912    /usr/lib/gconv/UTF-16.so
b6ffa000-b6ffc000 rwxp 00001000 08:01 2737912    /usr/lib/gconv/UTF-16.so
b6ffc000-b6ffd000 r-xp 00000000 08:01 2737858    /usr/lib/gconv/ISO8859-1.so
b6ffd000-b6fff000 rwxp 00000000 08:01 2737858    /usr/lib/gconv/ISO8859-1.so
b6fff000-b703e000 r-xp 00000000 08:01 13385729   /usr/lib/locale/en_US.utf8/LC_CTYPE
b703e000-b703f000 r-xp 00000000 08:01 2770399    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b703f000-b711f000 r-xp 00000000 08:01 13385730   /usr/lib/locale/en_US.utf8/LC_COLLATE
b711f000-b7122000 rwxp b711f000 00:00 0 
b7122000-b7144000 r-xp 00000000 08:01 2719913    /usr/lib/libpng12.so.0.15.0
b7144000-b7145000 rwxp 00021000 08:01 2719913    /usr/lib/libpng12.so.0.15.0
b7145000-b7146000 rwxp b7145000 00:00 0 
b7146000-b7164000 r-xp 00000000 08:01 27607111   /usr/lib/libexpat.so.1.0.0
b7164000-b7166000 rwxp 0001e000 08:01 27607111   /usr/lib/libexpat.so.1.0.0
b7166000-b717a000 r-xp 00000000 08:01 2720074    /usr/lib/libz.so.1.2.3.3
b717a000-b717b000 rwxp 00013000 08:01 2720074    /usr/lib/libz.so.1.2.3.3
b717b000-b7190000 r-xp 00000000 08:01 2720616    /usr/lib/libICE.so.6.3.0
b7190000-b7192000 rwxp 00014000 08:01 2720616    /usr/lib/libICE.so.6.3.0
b7192000-b7193000 rwxp b7192000 00:00 0 
b7193000-b719a000 r-xp 00000000 08:01 2720769    /usr/lib/libSM.so.6.0.0
b719a000-b719b000 rwxp 00006000 08:01 2720769    /usr/lib/libSM.so.6.0.0
b719b000-b719f000 r-xp 00000000 08:01 2720311    /usr/lib/libXdmcp.so.6.0.0
b719f000-b71a0000 rwxp 00003000 08:01 2720311    /usr/lib/libXdmcp.so.6.0.0
b71a0000-b71a1000 rwxp b71a0000 00:00 0 
b71a1000-b71a3000 r-xp 00000000 08:01 2720270    /usr/lib/libXau.so.6.0.0
b71a3000-b71a4000 rwxp 00001000 08:01 2720270    /usr/lib/libXau.so.6.0.0
b71a4000-b71d1000 r-xp 00000000 08:01 2720523    /usr/lib/libpangoft2-1.0.so.0.1800.3
b71d1000-b71d2000 rwxp 0002c000 08:01 2720523    /usr/lib/libpangoft2-1.0.so.0.1800.3
b71d2000-b71da000 r-xp 00000000 08:01 2720268    /usr/lib/libXcursor.so.1.0.2
b71da000-b71db000 rwxp 00007000 08:01 2720268    /usr/lib/libXcursor.so.1.0.2
b71db000-b71e0000 r-xp 00000000 08:01 2721589    /usr/lib/libXrandr.so.2.1.0
b71e0000-b71e1000 rwxp 00005000 08:01 2721589    /usr/lib/libXrandr.so.2.1.0
b71e1000-b71e8000 r-xp 00000000 08:01 2721581    /usr/lib/libXi.so.6.0.0
b71e8000-b71e9000 rwxp 00006000 08:01 2721581    /usr/lib/libXi.so.6.0.0
b71e9000-b71ea000 rwxp b71e9000 00:00 0 
b71ea000-b71ec000 r-xp 00000000 08:01 2720558    /usr/lib/libXinerama.so.1.0.0
b71ec000-b71ed000 rwxp 00001000 08:01 2720558    /usr/lib/libXinerama.so.1.0.0
b71ed000-b71fa000 r-xp 00000000 08:01 2720970    /usr/lib/libXext.so.6.4.0
b71fa000-b71fb000 rwxp 0000d000 08:01 2720970    /usr/lib/libXext.so.6.4.0
b71fb000-b7270000 r-xp 00000000 08:01 2720444    /usr/lib/libcairo.so.2.11.5
b7270000-b7272000 rwxp 00074000 08:01 2720444    /usr/lib/libcairo.so.2.11.5
b7272000-b7276000 r-xp 00000000 08:01 2720724    /usr/lib/libXfixes.so.3.1.0
b7276000-b7277000 rwxp 00003000 08:01 2720724    /usr/lib/libXfixes.so.3.1.0
b7277000-b7279000 r-xp 00000000 08:01 2720674    /usr/lib/libXdamage.so.1.1.0
b7279000-b727a000 rwxp 00001000 08:01 2720674    /usr/lib/libXdamage.so.1.1.0
b727a000-b727b000 rwxp b727a000 00:00 0 
b727b000-b727d000 r-xp 00000000 08:01 2721561    /usr/lib/libXcomposite.so.1.0.0
b727d000-b727e000 rwxp 00001000 08:01 2721561    /usr/lib/libXcomposite.so.1.0.0
b727e000-b7286000 r-xp 00000000 08:01 2720489    /usr/lib/libpangocairo-1.0.so.0.1800.3
b7286000-b7287000 rwxp 00007000 08:01 2720489    /usr/lib/libpangocairo-1.0.so.0.1800.3
b7287000-b73cb000 r-xp 00000000 08:01 12959747   /lib/tls/i686/cmov/libc-2.6.1.so
b73cb000-b73cc000 r-xp 00143000 08:01 12959747   /lib/tls/i686/cmov/libc-2.6.1.so
b73cc000-b73ce000 rwxp 00144000 08:01 12959747   /lib/tls/i686/cmov/libc-2.6.1.so
b73ce000-b73d1000 rwxp b73ce000 00:00 0 
b73d1000-b73db000 r-xp 00000000 08:01 16777223   /lib/libgcc_s.so.1
b73db000-b73dc000 rwxp 0000a000 08:01 16777223   /lib/libgcc_s.so.1
b73dc000-b748c000 r-xp 00000000 08:01 2721965    /usr/lib/libstdc++.so.5.0.7
b748c000-b7491000 rwxp 000af000 08:01 2721965    /usr/lib/libstdc++.so.5.0.7
b7491000-b7496000 rwxp b7491000 00:00 0 
b7496000-b74b0000 r-xp 00000000 08:01 5046634    /usr/thunderbird/libxpcom_compat.so
b74b0000-b74b1000 rwxp 0001a000 08:01 5046634    /usr/thunderbird/libxpcom_compat.so
b74b1000-b74b2000 rwxp b74b1000 00:00 0 
b74b2000-b74d5000 r-xp 00000000 08:01 2719953    /usr/lib/libfontconfig.so.1.2.0
b74d5000-b74dd000 rwxp 00023000 08:01 2719953    /usr/lib/libfontconfig.so.1.2.0
b74dd000-b74e4000 r-xp 00000000 08:01 2720582    /usr/lib/libXrender.so.1.3.0
b74e4000-b74e5000 rwxp 00006000 08:01 2720582    /usr/lib/libXrender.so.1.3.0
b74e5000-b7551000 r-xp 00000000 08:01 2721076    /usr/lib/libfreetype.so.6.3.16
b7551000-b7555000 rwxp 0006b000 08:01 2721076    /usr/lib/libfreetype.so.6.3.16
b7555000-b7566000 r-xp 00000000 08:01 2721197    /usr/lib/libXft.so.2.1.2
b7566000-b7567000 rwxp 00010000 08:01 2721197    /usr/lib/libXft.so.2.1.2
b7567000-b75b4000 r-xp 00000000 08:01 2720984    /usr/lib/libXt.so.6.0.0
b75b4000-b75b8000 rwxp 0004c000 08:01 2720984    /usr/lib/libXt.so.6.0.0
b75b8000-b75bc000 r-xp 00000000 08:01 5046629    /usr/thunderbird/libprldap50.so
b75bc000-b75bd000 rwxp 00003000 08:01 5046629    /usr/thunderbird/libprldap50.so
b75bd000-b75be000 rwxp b75bd000 00:00 0 
b75be000-b75e7000 r-xp 00000000 08:01 5046622    /usr/thunderbird/libldap50.so
b75e7000-b75e8000 rwxp 00029000 08:01 5046622    /usr/thunderbird/libldap50.so
b75e8000-b75e9000 rwxp b75e8000 00:00 0 
b75e9000-b763b000 r-xp 00000000 08:01 5046632    /usr/thunderbird/libsoftokn3.so
b763b000-b763f000 rwxp 00052000 08:01 5046632    /usr/thunderbird/libsoftokn3.so
b763f000-b76ad000 r-xp 00000000 08:01 5046625    /usr/thunderbird/libnss3.so
b76ad000-b76b2000 rwxp 0006e000 08:01 5046625    /usr/thunderbird/libnss3.so
b76b2000-b76d9000 r-xp 00000000 08:01 5046633    /usr/thunderbird/libssl3.so
b76d9000-b76db000 rwxp 00027000 08:01 5046633    /usr/thunderbird/libssl3.so
b76db000-b76fe000 r-xp 00000000 08:01 5046630    /usr/thunderbird/libsmime3.so
b76fe000-b7701000 rwxp 00022000 08:01 5046630    /usr/thunderbird/libsmime3.so
b7701000-b7724000 r-xp 00000000 08:01 12959751   /lib/tls/i686/cmov/libm-2.6.1.so
b7724000-b7726000 rwxp 00023000 08:01 12959751   /lib/tls/i686/cmov/libm-2.6.1.so
b7726000-b7727000 rwxp b7726000 00:00 0 
b7727000-b7814000 r-xp 00000000 08:01 2720559    /usr/lib/libX11.so.6.2.0
b7814000-b7818000 rwxp 000ed000 08:01 2720559    /usr/lib/libX11.so.6.2.0
b7818000-b78d4000 r-xp 00000000 08:01 27607047   /usr/lib/libglib-2.0.so.0.1400.1
b78d4000-b78d5000 rwxp 000bc000 08:01 27607047   /usr/lib/libglib-2.0.so.0.1400.1
b78d5000-b78d8000 r-xp 00000000 08:01 27607048   /usr/lib/libgmodule-2.0.so.0.1400.1
b78d8000-b78d9000 rwxp 00002000 08:01 27607048   /usr/lib/libgmodule-2.0.so.0.1400.1
b78d9000-b7913000 r-xp 00000000 08:01 27607073   /usr/lib/libgobject-2.0.so.0.1400.1
b7913000-b7914000 rwxp 0003a000 08:01 27607073   /usr/lib/libgobject-2.0.so.0.1400.1
b7914000-b794f000 r-xp 00000000 08:01 2720488    /usr/lib/libpango-1.0.so.0.1800.3
b794f000-b7951000 rwxp 0003b000 08:01 2720488    /usr/lib/libpango-1.0.so.0.1800.3
b7951000-b795b000 r-xp 00000000 08:01 2720549    /usr/lib/libpangox-1.0.so.0.1800.3
b795b000-b795c000 rwxp 0000a000 08:01 2720549    /usr/lib/libpangox-1.0.so.0.1800.3
b795c000-b795d000 rwxp b795c000 00:00 0 
b795d000-b7963000 r-xp 00000000 08:01 2721548    /usr/lib/libpangoxft-1.0.so.0.1800.3
b7963000-b7964000 rwxp 00005000 08:01 2721548    /usr/lib/libpangoxft-1.0.so.0.1800.3
b7964000-b797b000 r-xp 00000000 08:01 2721709    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b797b000-b797c000 rwxp 00016000 08:01 2721709    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b797c000-b7995000 r-xp 00000000 08:01 27607097   /usr/lib/libatk-1.0.so.0.2009.1
b7995000-b7997000 rwxp 00018000 08:01 27607097   /usr/lib/libatk-1.0.so.0.2009.1
b7997000-b7a1b000 r-xp 00000000 08:01 2721689    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b7a1b000-b7a1e000 rwxp 00084000 08:01 2721689    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b7a1e000-b7d9b000 r-xp 00000000 08:01 2721726    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7d9b000-b7da2000 rwxp 0037c000 08:01 2721726    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7da2000-b7da4000 rwxp b7da2000 00:00 0 
b7da4000-b7da6000 r-xp 00000000 08:01 12959750   /lib/tls/i686/cmov/libdl-2.6.1.so
b7da6000-b7da8000 rwxp 00001000 08:01 12959750   /lib/tls/i686/cmov/libdl-2.6.1.so
b7da8000-b7dbc000 r-xp 00000000 08:01 12959761   /lib/tls/i686/cmov/libpthread-2.6.1.so
b7dbc000-b7dbe000 rwxp 00013000 08:01 12959761   /lib/tls/i686/cmov/libpthread-2.6.1.so
b7dbe000-b7dc0000 rwxp b7dbe000 00:00 0 
b7dc0000-b7dc1000 r-xp 00000000 08:01 2769344    /usr/lib/locale/en_US.utf8/LC_TIME
b7dc1000-b7dc2000 r-xp 00000000 08:01 2769345    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7dc2000-b7dc3000 r-xp 00000000 08:01 2785370    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7dc3000-b7dc4000 r-xp 00000000 08:01 2770510    /usr/lib/locale/en_US.utf8/LC_PAPER
b7dc4000-b7dc5000 r-xp 00000000 08:01 2769555    /usr/lib/locale/en_US.utf8/LC_NAME
b7dc5000-b7dc6000 r-xp 00000000 08:01 2769348    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7dc6000-b7dc7000 r-xp 00000000 08:01 2769350    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7dc7000-b7dc8000 r-xp 00000000 08:01 2769351    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7dc8000-b7dcf000 r-xs 00000000 08:01 2736475    /usr/lib/gconv/gconv-modules.cache
b7dcf000-b7dd0000 r-xp 00000000 08:01 2769370    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7dd0000-b7e02000 r-xp 00000000 08:01 5046624    /usr/thunderbird/libnspr4.so
b7e02000-b7e04000 rwxp 00031000 08:01 5046624    /usr/thunderbird/libnspr4.so
b7e04000-b7e06000 rwxp b7e04000 00:00 0 
b7e06000-b7e0a000 r-xp 00000000 08:01 5046627    /usr/thunderbird/libplc4.so
b7e0a000-b7e0b000 rwxp 00003000 08:01 5046627    /usr/thunderbird/libplc4.so
b7e0b000-b7e0d000 r-xp 00000000 08:01 5046628    /usr/thunderbird/libplds4.so
b7e0d000-b7e0e000 rwxp 00002000 08:01 5046628    /usr/thunderbird/libplds4.so
b7e0e000-b7ec8000 r-xp 00000000 08:01 5046635    /usr/thunderbird/libxpcom_core.so
b7ec8000-b7ecf000 rwxp 000b9000 08:01 5046635    /usr/thunderbird/libxpcom_core.so
b7ecf000-b7ed0000 rwxp b7ecf000 00:00 0 
b7ed0000-b7ed3000 r-xp 00000000 08:01 5046636    /usr/thunderbird/libxpcom.so
b7ed3000-b7ed4000 rwxp 00002000 08:01 5046636    /usr/thunderbird/libxpcom.so
b7ed4000-b7f85000 r-xp 00000000 08:01 5046623    /usr/thunderbird/libmozjs.so
b7f85000-b7f8b000 rwxp 000b0000 08:01 5046623    /usr/thunderbird/libmozjs.so
b7f8b000-b7f8d000 rwxp b7f8b000 00:00 0 
b7f8d000-b7fa7000 r-xp 00000000 08:01 16777255   /lib/ld-2.6.1.so
b7fa7000-b7fa9000 rwxp 00019000 08:01 16777255   /lib/ld-2.6.1.so
bfd4d000-bfd63000 rwxp bfd4d000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
[{WIFEXITED(s) && WEXITSTATUS(s) == 134}], 0, NULL) = 1948
--- SIGCHLD (Child exited) @ 0 (0) ---
open("/home/daniel/.thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = -1 ENOENT (No such file or directory)
open("/usr/thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
getdents(3, /* 3 entries */, 4096)      = 52
getdents(3, /* 0 entries */, 4096)      = 0
close(3)                                = 0
stat64("/home/daniel/.thunderbird/init.d/K*", 0xbfb8e44c) = -1 ENOENT (No such file or directory)
stat64("/usr/thunderbird/init.d/K*", 0xbfb8e44c) = -1 ENOENT (No such file or directory)
exit_group(134)                         = ?
Process 1945 detached

---

### Post by NT4usB on 2008-01-21
Edit your post(s) and put the word:
"[code]"
Enclosed in brackets but without the quotes, before the output.
Do the same at the end but put a front slash '/' in front of code but inside the brackets.
Then it'll all fit in one post and we'll be able to read it...

---

### Post by anthropop on 2008-01-21
> **NT4usB said:**
> Edit your post(s) and put the word:
"[code]"
Enclosed in brackets but without the quotes, before the output.
Do the same at the end but put a front slash '/' in front of code but inside the brackets.
Then it'll all fit in one post and we'll be able to read it...

Will do, but I also have some more information.  This bug is because of compiz and it is in the "Crux" theme.  I don't know if it is in other themes, but I know it is not in the "Human" theme.  I reenabled VisualEffects and used the Human theme and thunderbird (and other broken apps) work fine.

---

### Post by anthropop on 2008-01-21
strace output with special keywords as requested:

```

execve("/usr/thunderbird/thunderbird", ["/usr/thunderbird/thunderbird"], [/* 37 vars */]) = 0
brk(0)                                  = 0x805f000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f17000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=65326, ...}) = 0
mmap2(NULL, 65326, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f07000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260a\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1339816, ...}) = 0
mmap2(NULL, 1349136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7dbd000
mmap2(0xb7f01000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x143) = 0xb7f01000
mmap2(0xb7f04000, 9744, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f04000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7dbc000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7dbc6b0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7f01000, 4096, PROT_READ)   = 0
munmap(0xb7f07000, 65326)               = 0
getpid()                                = 2652
rt_sigaction(SIGCHLD, {SIG_DFL}, {SIG_DFL}, 8) = 0
geteuid32()                             = 1000
brk(0)                                  = 0x805f000
brk(0x8080000)                          = 0x8080000
getppid()                               = 2651
stat64("/home/daniel", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/thunderbird/thunderbird", O_RDONLY) = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {0x80551b0, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL}, NULL, 8) = 0
read(10, "#!/bin/sh\n#\n# ***** BEGIN LICENS"..., 8192) = 5205
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7dbc6f8) = 2653
close(4)                                = 0
read(3, "/usr/thunderbird\n", 128)      = 17
--- SIGCHLD (Child exited) @ 0 (0) ---
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 2653
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7dbc6f8) = 2654
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 2654
stat64("/usr/thunderbird/run-mozilla.sh", {st_mode=S_IFREG|0755, st_size=10492, ...}) = 0
geteuid32()                             = 1000
getgid32()                              = 1004
getegid32()                             = 1004
getgroups32(0, NULL)                    = 18
getgroups32(18, [4, 20, 21, 24, 25, 29, 30, 44, 46, 109, 111, 114, 119, 124, 125, 1004, 1006, 1007]) = 18
open("/usr/thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
getdents(3, /* 3 entries */, 4096)      = 52
getdents(3, /* 0 entries */, 4096)      = 0
close(3)                                = 0
open("/home/daniel/.thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = -1 ENOENT (No such file or directory)
stat64("/usr/thunderbird/init.d/S*", 0xbfc0ecbc) = -1 ENOENT (No such file or directory)
stat64("/home/daniel/.thunderbird/init.d/S*", 0xbfc0ecbc) = -1 ENOENT (No such file or directory)
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7dbc6f8) = 2655
wait4(-1, *** glibc detected *** /usr/thunderbird/thunderbird-bin: double free or corruption (out): 0x08f2eb90 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb72b7d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb72bb800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7815961]
/usr/thunderbird/thunderbird-bin[0x826be52]
/usr/thunderbird/thunderbird-bin[0x826c98d]
/usr/thunderbird/thunderbird-bin[0x826aaa2]
/usr/thunderbird/thunderbird-bin[0x82be98c]
/usr/thunderbird/thunderbird-bin[0x82bdd0c]
/usr/thunderbird/thunderbird-bin[0x82fb444]
/usr/thunderbird/thunderbird-bin[0x83e1110]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x83e120a]
/usr/thunderbird/thunderbird-bin[0x83e130b]
/usr/thunderbird/thunderbird-bin[0x83e1031]
/usr/thunderbird/thunderbird-bin[0x82f8454]
/usr/thunderbird/thunderbird-bin[0x82f836f]
/usr/thunderbird/thunderbird-bin[0x82f8317]
/usr/thunderbird/thunderbird-bin[0x82de573]
/usr/thunderbird/thunderbird-bin[0x84e5782]
/usr/thunderbird/thunderbird-bin[0x84e981c]
/usr/thunderbird/thunderbird-bin[0x84e9218]
/usr/thunderbird/thunderbird-bin[0x84e7fbb]
/usr/thunderbird/thunderbird-bin[0x84ead94]
/usr/thunderbird/thunderbird-bin[0x84e50e6]
/usr/thunderbird/thunderbird-bin[0x829bf89]
/usr/thunderbird/thunderbird-bin[0x8293f6b]
/usr/thunderbird/thunderbird-bin[0x8298e80]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7b3f1de]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb78aa772]
/usr/lib/libgobject-2.0.so.0[0xb78bb323]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb78bc60f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb78bca09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c5d498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x475)[0xb7b396f5]
/usr/lib/libgdk-x11-2.0.so.0[0xb798f06f]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0xba)[0xb798f73a]
/usr/lib/libgdk-x11-2.0.so.0[0xb798f79b]
/usr/lib/libgdk-x11-2.0.so.0[0xb79755e8]
/usr/lib/libglib-2.0.so.0[0xb780c551]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb780e11c]
======= Memory map: ========
08048000-08d00000 r-xp 00000000 08:01 5046689    /usr/thunderbird/thunderbird-bin
08d00000-08d19000 rwxp 00cb7000 08:01 5046689    /usr/thunderbird/thunderbird-bin
08d19000-09d5c000 rwxp 08d19000 00:00 0          [heap]
b2300000-b23f3000 rwxp b2300000 00:00 0 
b23f3000-b23f4000 ---p b23f3000 00:00 0 
b23f4000-b2bf4000 rwxp b23f4000 00:00 0 
b2bf4000-b2bf5000 ---p b2bf4000 00:00 0 
b2bf5000-b33f5000 rwxp b2bf5000 00:00 0 
b33f5000-b33f9000 r-xp 00000000 08:01 12959755   /lib/tls/i686/cmov/libnss_dns-2.6.1.so
b33f9000-b33fb000 rwxp 00003000 08:01 12959755   /lib/tls/i686/cmov/libnss_dns-2.6.1.so
b33fb000-b33fd000 r-xp 00000000 08:01 16777311   /lib/libnss_mdns4_minimal.so.2
b33fd000-b33fe000 rwxp 00001000 08:01 16777311   /lib/libnss_mdns4_minimal.so.2
b340e000-b340f000 ---p b340e000 00:00 0 
b340f000-b3c10000 rwxp b340f000 00:00 0 
b3c10000-b3c14000 r-xp 00000000 08:01 5046516    /usr/thunderbird/compKilled
[{WIFEXITED(s) && WEXITSTATUS(s) == 137}], 0, NULL) = 2655
--- SIGCHLD (Child exited) @ 0 (0) ---
open("/home/daniel/.thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = -1 ENOENT (No such file or directory)
open("/usr/thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
getdents(3, /* 3 entries */, 4096)      = 52
getdents(3, /* 0 entries */, 4096)      = 0
close(3)                                = 0
stat64("/home/daniel/.thunderbird/init.d/K*", 0xbfc0ecbc) = -1 ENOENT (No such file or directory)
stat64("/usr/thunderbird/init.d/K*", 0xbfc0ecbc) = -1 ENOENT (No such file or directory)
exit_group(137)                         = ?
Process 2652 detached

```

---

### Post by jay4e on 2008-02-27
are you running lightning with thunderbird? (calendar add on)  If so thats your problem there is something wrong with lightning and gutsy.  i had the same problem when i first install then got it work for a week and it came back.  just removed lightning as per another thread and it works fine.  Im guessing its a problem with lightning parsing emails for calendar information or just some totaly random bug.

ps if you use lightning removing then reinstalling seems to have worked for some at least for the short term.

---

