---
title: "Problems running a Program (Diogenes) in Perl - help, please!"
date: 2014-05-02
forum: General Help
---

### Post by Jamie_Dow on 2014-05-02
Hi,
I have been suddenly having trouble running a program that I've used successfully for years, called Diogenes (it's a program for accessing ancient Greek and Latin texts from files on my hard drive). It's written in Perl. It's possible that somehow part of my Perl installation has gone awry, or some files that it depends on are missing, or something. But I'm beyond my technical ability.

Can anyone help, please?
When I run the program from the command line, the output I get is pasted below.
Many thanks in advance.
Jamie


> (diogenes:7769): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised


(diogenes:7769): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised


(diogenes:7769): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised


(diogenes:7769): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised
Lockfile exists.
Lockfile present
Shutting down server.
Waiting for /home/<username>/.diogenes/.diogenes.run to disappear.Diogenes: waiting for server to exit
Diogenes: waiting for server to exit
Diogenes: waiting for server to exit
Diogenes: waiting for server to exit
Diogenes: waiting for server to exit
Diogenes: waiting for server to exit
Diogenes: waiting for server to exit
Diogenes: waiting for server to exit
Diogenes: waiting for server to exit
Use of qw(...) as parentheses is deprecated at /usr/local/diogenes/perl/Diogenes/UnicodeInput.pm line 109.
Diogenes: waiting for server to exit
Running diogenes-server-kill.pl
Lock file exists, pid: 7655
Diogenes: waiting for server to exit
Killed 7655.
diogenes-server-kill.pl exiting.
Diogenes: waiting for server to exit
Starting up server.
Looking for /home/<username>/.diogenes/.diogenes.run


Starting Diogenes...
Diogenes: attempting to contact server
Diogenes: attempting to contact server
Diogenes: attempting to contact server
Diogenes: attempting to contact server
Diogenes: attempting to contact server
Diogenes: attempting to contact server
[Thu Apr 24 10:10:29 2014] UnicodeInput.pm: Use of qw(...) as parentheses is deprecated at /usr/local/diogenes/perl/Diogenes/UnicodeInput.pm line 109.
Diogenes: attempting to contact server
Diogenes: attempting to contact server
Diogenes: attempting to contact server
Diogenes: attempting to contact server
Diogenes: attempting to contact server
[Thu Apr 24 10:10:29 2014] diogenes-server.pl: Use of qw(...) as parentheses is deprecated at (eval 172) line 645, <SCRIPT> line 1.


Startup complete. You may now point your browser at this address:
[http://127.0.0.1:8888](http://127.0.0.1:8888)
Diogenes: attempting to contact server
[Thu Apr 24 10:10:30 2014] diogenes-server.pl: Use of uninitialized value $method in lc at (eval 124) line 7.
[Thu Apr 24 10:10:30 2014] diogenes-server.pl: Use of uninitialized value $method in lc at (eval 124) line 7.
*** Error in `diogenes': free(): invalid pointer: 0x092028d0 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x767c2)[0xb749b7c2]
/lib/i386-linux-gnu/libc.so.6(+0x77510)[0xb749c510]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_free+0x20)[0xb61a65d0]
/usr/local/diogenes/xulrunner/libxul.so(+0x97041a)[0xb6c9b41a]
/usr/local/diogenes/xulrunner/libxul.so(+0x97178c)[0xb6c9c78c]
/usr/local/diogenes/xulrunner/libxul.so(+0x98fc24)[0xb6cbac24]
/usr/local/diogenes/xulrunner/libxul.so(+0x3633c1)[0xb668e3c1]
/usr/local/diogenes/xulrunner/libxul.so(+0x3376a6)[0xb66626a6]
/usr/local/diogenes/xulrunner/libxul.so(+0x362098)[0xb668d098]
/usr/local/diogenes/xulrunner/libxul.so(+0x34fa6a)[0xb667aa6a]
/usr/local/diogenes/xulrunner/libxul.so(+0x337732)[0xb6662732]
/usr/local/diogenes/xulrunner/libxul.so(+0x42b785)[0xb6756785]
/usr/local/diogenes/xulrunner/libxul.so(+0x423528)[0xb674e528]
/usr/local/diogenes/xulrunner/libxul.so(+0x423c04)[0xb674ec04]
/usr/local/diogenes/xulrunner/libxul.so(+0x4243f8)[0xb674f3f8]
/usr/local/diogenes/xulrunner/libxul.so(+0x424cbe)[0xb674fcbe]
/usr/local/diogenes/xulrunner/libxul.so(+0x43a356)[0xb6765356]
/usr/local/diogenes/xulrunner/libxul.so(+0x431b16)[0xb675cb16]
/usr/local/diogenes/xulrunner/libxul.so(+0x431b88)[0xb675cb88]
/usr/local/diogenes/xulrunner/libxul.so(+0x36826a)[0xb669326a]
/usr/local/diogenes/xulrunner/libxul.so(+0x431685)[0xb675c685]
/usr/local/diogenes/xulrunner/libxul.so(+0x37900a)[0xb66a400a]
/usr/local/diogenes/xulrunner/libxul.so(+0x3791c8)[0xb66a41c8]
/usr/local/diogenes/xulrunner/libxul.so(+0x43d02b)[0xb676802b]
/usr/local/diogenes/xulrunner/libxul.so(+0x43dfa2)[0xb6768fa2]
/usr/local/diogenes/xulrunner/libxul.so(+0x43ee19)[0xb6769e19]
/usr/local/diogenes/xulrunner/libxul.so(+0x3570fe)[0xb66820fe]
/usr/local/diogenes/xulrunner/libxul.so(+0x35387b)[0xb667e87b]
/usr/local/diogenes/xulrunner/libxul.so(+0x3553be)[0xb66803be]
/usr/local/diogenes/xulrunner/libxul.so(+0x355951)[0xb6680951]
/usr/local/diogenes/xulrunner/libxul.so(+0x3560af)[0xb66810af]
/usr/local/diogenes/xulrunner/libxul.so(+0x3570fe)[0xb66820fe]
/usr/local/diogenes/xulrunner/libxul.so(+0x35387b)[0xb667e87b]
/usr/local/diogenes/xulrunner/libxul.so(+0x3553be)[0xb66803be]
/usr/local/diogenes/xulrunner/libxul.so(+0x355951)[0xb6680951]
/usr/local/diogenes/xulrunner/libxul.so(+0x3560af)[0xb66810af]
/usr/local/diogenes/xulrunner/libxul.so(+0x3570fe)[0xb66820fe]
/usr/local/diogenes/xulrunner/libxul.so(+0x35387b)[0xb667e87b]
/usr/local/diogenes/xulrunner/libxul.so(+0x3553be)[0xb66803be]
/usr/local/diogenes/xulrunner/libxul.so(+0x355951)[0xb6680951]
/usr/local/diogenes/xulrunner/libxul.so(+0x3560af)[0xb66810af]
/usr/local/diogenes/xulrunner/libxul.so(+0x3570fe)[0xb66820fe]
/usr/local/diogenes/xulrunner/libxul.so(+0x35387b)[0xb667e87b]
/usr/local/diogenes/xulrunner/libxul.so(+0x3553be)[0xb66803be]
/usr/local/diogenes/xulrunner/libxul.so(+0x355951)[0xb6680951]
/usr/local/diogenes/xulrunner/libxul.so(+0x3560af)[0xb66810af]
/usr/local/diogenes/xulrunner/libxul.so(+0x3570fe)[0xb66820fe]
/usr/local/diogenes/xulrunner/libxul.so(+0x35387b)[0xb667e87b]
/usr/local/diogenes/xulrunner/libxul.so(+0x3553be)[0xb66803be]
/usr/local/diogenes/xulrunner/libxul.so(+0x355951)[0xb6680951]
/usr/local/diogenes/xulrunner/libxul.so(+0x3560af)[0xb66810af]
/usr/local/diogenes/xulrunner/libxul.so(+0x35dd6b)[0xb6688d6b]
/usr/local/diogenes/xulrunner/libxul.so(+0x375e40)[0xb66a0e40]
/usr/local/diogenes/xulrunner/libxul.so(+0x35dd6b)[0xb6688d6b]
/usr/local/diogenes/xulrunner/libxul.so(+0x370867)[0xb669b867]
/usr/local/diogenes/xulrunner/libxul.so(+0x372409)[0xb669d409]
/usr/local/diogenes/xulrunner/libxul.so(+0x372924)[0xb669d924]
/usr/local/diogenes/xulrunner/libxul.so(+0x35dd6b)[0xb6688d6b]
/usr/local/diogenes/xulrunner/libxul.so(+0x3ad68c)[0xb66d868c]
/usr/local/diogenes/xulrunner/libxul.so(+0x33c1fb)[0xb66671fb]
/usr/local/diogenes/xulrunner/libxul.so(+0x3428b5)[0xb666d8b5]
/usr/local/diogenes/xulrunner/libxul.so(+0x3429e4)[0xb666d9e4]
/usr/local/diogenes/xulrunner/libxul.so(+0x342a70)[0xb666da70]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:01 2228998    /usr/local/diogenes/diogenes
0804f000-08050000 rw-p 00006000 08:01 2228998    /usr/local/diogenes/diogenes
08df2000-09522000 rw-p 00000000 00:00 0          [heap]
ad9d3000-ada2d000 r--p 00000000 08:01 269278     /usr/share/fonts/truetype/dejavu/DejaVuSerif.ttf
ada2d000-ada2e000 ---p 00000000 00:00 0 
ada2e000-ae22e000 rw-p 00000000 00:00 0          [stack:7784]
aea2f000-aea30000 ---p 00000000 00:00 0 
aea30000-af230000 rw-p 00000000 00:00 0          [stack:7781]
afa31000-afa32000 ---p 00000000 00:00 0 
afa32000-b0232000 rw-p 00000000 00:00 0          [stack:7785]
b0232000-b0248000 r--p 00000000 08:01 669697     /usr/share/locale/en_GB/LC_MESSAGES/gedit.mo
b0248000-b0268000 r--s 00000000 08:01 2753779    /usr/share/mime/mime.cache
b0268000-b0269000 ---p 00000000 00:00 0 
b0269000-b0a69000 rw-p 00000000 00:00 0 
b0a69000-b0a6a000 ---p 00000000 00:00 0 
b0a6a000-b126a000 rw-p 00000000 00:00 0          [stack:7793]
b1674000-b1801000 r--p 00000000 08:03 3670918    /home/<username>/.fonts/ttf-fonts/GentiumPlus-R.ttf
b1801000-b18b6000 r--p 00000000 08:01 269270     /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
b18b6000-b19b6000 rw-s 00000000 00:04 9535539    /SYSV00000000 (deleted)
b19b6000-b1a6b000 r--p 00000000 08:01 269270     /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
b1a6b000-b1aaa000 r-xp 00000000 08:01 2365551    /usr/local/diogenes/xulrunner/libnssckbi.so
b1aaa000-b1ab4000 rw-p 0003f000 08:01 2365551    /usr/local/diogenes/xulrunner/libnssckbi.so
b1ab4000-b1afc000 r-xp 00000000 08:01 2365549    /usr/local/diogenes/xulrunner/libfreebl3.so
b1afc000-b1afd000 rw-p 00047000 08:01 2365549    /usr/local/diogenes/xulrunner/libfreebl3.so
b1afd000-b1afe000 ---p 00000000 00:00 0 
b1afe000-b22fe000 rw-p 00000000 00:00 0          [stack:7774]
b22fe000-b22ff000 ---p 00000000 00:00 0 
b22ff000-b2aff000 rw-p 00000000 00:00 0          [stack:7773]
b2aff000-b2b00000 ---p 00000000 00:00 0 
b2b00000-b3300000 rw-p 00000000 00:00 0 
b3300000-b3321000 rw-p 00000000 00:00 0 
b3321000-b3400000 ---p 00000000 00:00 0 
b3407000-b340e000 r-xp 00000000 08:01 417951     /lib/i386-linux-gnu/libacl.so.1.1.0
b340e000-b340f000 r--p 00006000 08:01 417951     /lib/i386-linux-gnu/libacl.so.1.1.0
b340f000-b3410000 rw-p 00007000 08:01 417951     /lib/i386-linux-gnu/libacl.so.1.1.0
b3410000-b3430000 r--s 00000000 08:01 2753779    /usr/share/mime/mime.cache
b3430000-b345c000 r-xp 00000000 08:01 2365539    /usr/local/diogenes/xulrunner/libnssdbm3.so
b345c000-b345f000 rw-p 0002c000 08:01 2365539    /usr/local/diogenes/xulrunner/libnssdbm3.so
b345f000-b34bf000 rw-s 00000000 00:04 9437230    /SYSV00000000 (deleted)
b34bf000-b34df000 r--s 00000000 08:01 2753779    /usr/share/mime/mime.cache
b34df000-b34ff000 r--s 00000000 08:01 2753779    /usr/share/mime/mime.cache
b34ff000-b3500000 ---p 00000000 00:00 0 
b3500000-b3d00000 rw-p 00000000 00:00 0          [stack:7771]
b3d00000-b3db5000 r--p 00000000 08:01 269270     /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
b3db5000-b3e92000 r--s 00000000 08:01 2363469    /var/cache/fontconfig/f8bc6966b549555332024bc9fa41f081-le32d4.cache-4
b3e92000-b3f70000 r--s 00000000 08:01 2364902    /var/cache/fontconfig/a744f5ed0109b8ebe6eb11a33cb02a01-le32d4.cache-4
b3f70000-b4034000 r--s 00000000 08:01 2362508    /var/cache/fontconfig/1b093df283eb9046237f3196b8621797-le32d4.cache-4
b4034000-b4100000 r--s 00000000 08:01 2362957    /var/cache/fontconfig/7c2268956d8a152e5eab12bdf59dc3c7-le32d4.cache-4
b4100000-b4121000 rw-p 00000000 00:00 0 
b4121000-b4200000 ---p 00000000 00:00 0 
b4201000-b4202000 rw-p 00000000 00:00 0 
b4202000-b4206000 r-xp 00000000 08:01 394151     /lib/i386-linux-gnu/libattr.so.1.1.0
b4206000-b4207000 r--p 00003000 08:01 394151     /lib/i386-linux-gnu/libattr.so.1.1.0
b4207000-b4208000 rw-p 00004000 08:01 394151     /lib/i386-linux-gnu/libattr.so.1.1.0
b4208000-b4214000 r-xp 00000000 08:01 2371281    /usr/lib/i386-linux-gnu/gnome-vfs-2.0/modules/libfile.so
b4214000-b4215000 r--p 0000b000 08:01 2371281    /usr/lib/i386-linux-gnu/gnome-vfs-2.0/modules/libfile.so
b4215000-b4216000 rw-p 0000c000 08:01 2371281    /usr/lib/i386-linux-gnu/gnome-vfs-2.0/modules/libfile.so
b4216000-b421c000 r-xp 00000000 08:01 2371213    /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b421c000-b421d000 r--p 00005000 08:01 2371213    /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b421d000-b421e000 rw-p 00006000 08:01 2371213    /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b421e000-b421f000 r--s 00000000 08:03 3672609    /home/<username>/.local/share/mime/mime.cache
b421f000-b4220000 r--s 00000000 08:03 3672609    /home/<username>/.local/share/mime/mime.cache
b4220000-b4221000 r--s 00000000 08:01 2363085    /var/cache/fontconfig/556b8bf2d5667b76b1153c2e1a657f39-le32d4.cache-4
b4221000-b4222000 r--s 00000000 08:01 2362848    /var/cache/fontconfig/0679aa654d1145c6b43ba94bcd425fc7-le32d4.cache-4
b4222000-b4224000 r--s 00000000 08:01 2362959    /var/cache/fontconfig/6de4d616398067bfdcc8e46496f80fe2-le32d4.cache-4
b4224000-b4225000 r--s 00000000 08:01 2362075    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-4
b4225000-b422d000 r--s 00000000 08:01 2368764    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-4
b422d000-b422f000 r--s 00000000 08:01 2365458    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-4
b422f000-b4233000 r--s 00000000 08:01 2365284    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-4
b4233000-b4234000 r--s 00000000 08:01 2365272    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-4
b4234000-b4235000 r--s 00000000 08:01 2364917    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-4
b4235000-b423a000 r--s 00000000 08:01 2365070    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-4
b423a000-b4243000 r--s 00000000 08:01 2365071    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-4
b4243000-b4252000 r--s 00000000 08:01 2364939    /var/cache/fontconfig/04aabc0a78ac019cf9454389977116d2-le32d4.cache-4
b4252000-b4253000 r--s 00000000 08:01 2364929    /var/cache/fontconfig/1ac9eb803944fde146138c791f5cc56a-le32d4.cache-4
b4253000-b4256000 r--s 00000000 08:01 2364925    /var/cache/fontconfig/385c0604a188198f04d133e54aba7fe7-le32d4.cache-4
b4256000-b4257000 r--s 00000000 08:01 2364915    /var/cache/fontconfig/dc05db6664285cc2f12bf69c139ae4c3-le32d4.cache-4
b4257000-b4259000 r--s 00000000 08:01 2364927    /var/cache/fontconfig/767a8244fc0220cfb567a839d0392e0b-le32d4.cache-4
b4259000-b425a000 r--s 00000000 08:01 2364921    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-4
b425a000-b425d000 r--s 00000000 08:01 2364924    /var/cache/fontconfig/8801497958630a81b71ace7c5f9b32a8-le32d4.cache-4Aborted (core dumped)

---

### Post by Jamie_Dow on 2014-05-07
Bump!

I'm still having problems. I've now done a reinstall of the OS, in case somehow any software tinkering of mine had caused the problem. Nope.
Here's the console output I get when I try to run the program.
Cheers for any help!

> Starting Diogenes...
Diogenes: attempting to contact server
Diogenes: attempting to contact server
Diogenes: attempting to contact server
[Wed May  7 22:00:27 2014] UnicodeInput.pm: Use of qw(...) as parentheses is deprecated at /usr/local/diogenes/perl/Diogenes/UnicodeInput.pm line 109.
Diogenes: attempting to contact server
Diogenes: attempting to contact server
[Wed May  7 22:00:27 2014] diogenes-server.pl: Use of qw(...) as parentheses is deprecated at (eval 172) line 645, <SCRIPT> line 1.


Diogenes: attempting to contact server
Startup complete. You may now point your browser at this address:
[http://127.0.0.1:8888](http://127.0.0.1:8888)
Diogenes: attempting to contact server
[Wed May  7 22:00:27 2014] diogenes-server.pl: Use of uninitialized value $method in lc at (eval 124) line 7.
[Wed May  7 22:00:27 2014] diogenes-server.pl: Use of uninitialized value $method in lc at (eval 124) line 7.




---

### Post by Jamie_Dow on 2014-05-07
Ah, now I have something different again (it seems that 'uninitiated value' is just a warning, and probably not what causes it to abort).
Here's the terminal output.
Any help .... ideas ..... anyone? Please?!!

> *** Error in `/usr/local/bin/diogenes': double free or corruption (out): 0x08622a40 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x767c2)[0xb74697c2]
/lib/i386-linux-gnu/libc.so.6(+0x77510)[0xb746a510]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_free+0x20)[0xb61755d0]
/usr/local/diogenes/xulrunner/libxul.so(+0x97041a)[0xb6c6941a]
/usr/local/diogenes/xulrunner/libxul.so(+0x97178c)[0xb6c6a78c]
/usr/local/diogenes/xulrunner/libxul.so(+0x98fc24)[0xb6c88c24]
/usr/local/diogenes/xulrunner/libxul.so(+0x3633c1)[0xb665c3c1]
/usr/local/diogenes/xulrunner/libxul.so(+0x3376a6)[0xb66306a6]
/usr/local/diogenes/xulrunner/libxul.so(+0x362098)[0xb665b098]
/usr/local/diogenes/xulrunner/libxul.so(+0x34fa6a)[0xb6648a6a]
/usr/local/diogenes/xulrunner/libxul.so(+0x337732)[0xb6630732]
/usr/local/diogenes/xulrunner/libxul.so(+0x42b785)[0xb6724785]
/usr/local/diogenes/xulrunner/libxul.so(+0x423528)[0xb671c528]
/usr/local/diogenes/xulrunner/libxul.so(+0x423c04)[0xb671cc04]
/usr/local/diogenes/xulrunner/libxul.so(+0x4243f8)[0xb671d3f8]
/usr/local/diogenes/xulrunner/libxul.so(+0x424cbe)[0xb671dcbe]
/usr/local/diogenes/xulrunner/libxul.so(+0x43a356)[0xb6733356]
/usr/local/diogenes/xulrunner/libxul.so(+0x431b16)[0xb672ab16]
/usr/local/diogenes/xulrunner/libxul.so(+0x431b88)[0xb672ab88]
/usr/local/diogenes/xulrunner/libxul.so(+0x36826a)[0xb666126a]
/usr/local/diogenes/xulrunner/libxul.so(+0x431685)[0xb672a685]
/usr/local/diogenes/xulrunner/libxul.so(+0x37900a)[0xb667200a]
/usr/local/diogenes/xulrunner/libxul.so(+0x3791c8)[0xb66721c8]
/usr/local/diogenes/xulrunner/libxul.so(+0x43d02b)[0xb673602b]
/usr/local/diogenes/xulrunner/libxul.so(+0x43dfa2)[0xb6736fa2]
/usr/local/diogenes/xulrunner/libxul.so(+0x43ee19)[0xb6737e19]
/usr/local/diogenes/xulrunner/libxul.so(+0x3570fe)[0xb66500fe]
/usr/local/diogenes/xulrunner/libxul.so(+0x35387b)[0xb664c87b]
/usr/local/diogenes/xulrunner/libxul.so(+0x3553be)[0xb664e3be]
/usr/local/diogenes/xulrunner/libxul.so(+0x355951)[0xb664e951]
/usr/local/diogenes/xulrunner/libxul.so(+0x3560af)[0xb664f0af]
/usr/local/diogenes/xulrunner/libxul.so(+0x3570fe)[0xb66500fe]
/usr/local/diogenes/xulrunner/libxul.so(+0x35387b)[0xb664c87b]
/usr/local/diogenes/xulrunner/libxul.so(+0x3553be)[0xb664e3be]
/usr/local/diogenes/xulrunner/libxul.so(+0x355951)[0xb664e951]
/usr/local/diogenes/xulrunner/libxul.so(+0x3560af)[0xb664f0af]
/usr/local/diogenes/xulrunner/libxul.so(+0x3570fe)[0xb66500fe]
/usr/local/diogenes/xulrunner/libxul.so(+0x35387b)[0xb664c87b]
/usr/local/diogenes/xulrunner/libxul.so(+0x3553be)[0xb664e3be]
/usr/local/diogenes/xulrunner/libxul.so(+0x355951)[0xb664e951]
/usr/local/diogenes/xulrunner/libxul.so(+0x3560af)[0xb664f0af]
/usr/local/diogenes/xulrunner/libxul.so(+0x3570fe)[0xb66500fe]
/usr/local/diogenes/xulrunner/libxul.so(+0x35387b)[0xb664c87b]
/usr/local/diogenes/xulrunner/libxul.so(+0x3553be)[0xb664e3be]
/usr/local/diogenes/xulrunner/libxul.so(+0x355951)[0xb664e951]
/usr/local/diogenes/xulrunner/libxul.so(+0x3560af)[0xb664f0af]
/usr/local/diogenes/xulrunner/libxul.so(+0x3570fe)[0xb66500fe]
/usr/local/diogenes/xulrunner/libxul.so(+0x35387b)[0xb664c87b]
/usr/local/diogenes/xulrunner/libxul.so(+0x3553be)[0xb664e3be]
/usr/local/diogenes/xulrunner/libxul.so(+0x355951)[0xb664e951]
/usr/local/diogenes/xulrunner/libxul.so(+0x3560af)[0xb664f0af]
/usr/local/diogenes/xulrunner/libxul.so(+0x35dd6b)[0xb6656d6b]
/usr/local/diogenes/xulrunner/libxul.so(+0x375e40)[0xb666ee40]
/usr/local/diogenes/xulrunner/libxul.so(+0x35dd6b)[0xb6656d6b]
/usr/local/diogenes/xulrunner/libxul.so(+0x370867)[0xb6669867]
/usr/local/diogenes/xulrunner/libxul.so(+0x372409)[0xb666b409]
/usr/local/diogenes/xulrunner/libxul.so(+0x372924)[0xb666b924]
/usr/local/diogenes/xulrunner/libxul.so(+0x35dd6b)[0xb6656d6b]
/usr/local/diogenes/xulrunner/libxul.so(+0x3ad68c)[0xb66a668c]
/usr/local/diogenes/xulrunner/libxul.so(+0x33c1fb)[0xb66351fb]
/usr/local/diogenes/xulrunner/libxul.so(+0x3428b5)[0xb663b8b5]
/usr/local/diogenes/xulrunner/libxul.so(+0x3429e4)[0xb663b9e4]
/usr/local/diogenes/xulrunner/libxul.so(+0x342a70)[0xb663ba70]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:01 412399     /usr/local/diogenes/diogenes
0804f000-08050000 rw-p 00006000 08:01 412399     /usr/local/diogenes/diogenes
082da000-089f0000 rw-p 00000000 00:00 0          [heap]
aef91000-af11e000 r--p 00000000 08:03 3670918    /home/jamie/.fonts/ttf-fonts/GentiumPlus-R.ttf
af11e000-af1d3000 r--p 00000000 08:01 1180497    /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
af1d3000-af288000 r--p 00000000 08:01 1180497    /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
af288000-af2e2000 r--p 00000000 08:01 1180509    /usr/share/fonts/truetype/dejavu/DejaVuSerif.ttf
af2e2000-af2e3000 ---p 00000000 00:00 0 
af2e3000-afae3000 rw-p 00000000 00:00 0 
afae3000-afae4000 ---p 00000000 00:00 0 
afae4000-b02e4000 rw-p 00000000 00:00 0 
b02e4000-b02e5000 ---p 00000000 00:00 0 
b02e5000-b0ae5000 rw-p 00000000 00:00 0          [stack:12687]
b0ae5000-b0ae6000 ---p 00000000 00:00 0 
b0ae6000-b12e6000 rw-p 00000000 00:00 0          [stack:12690]
b12e6000-b12e7000 ---p 00000000 00:00 0 
b12e7000-b1ae7000 rw-p 00000000 00:00 0          [stack:12685]
b1ae7000-b1aeb000 r-xp 00000000 08:01 918442     /lib/i386-linux-gnu/libattr.so.1.1.0
b1aeb000-b1aec000 r--p 00003000 08:01 918442     /lib/i386-linux-gnu/libattr.so.1.1.0
b1aec000-b1aed000 rw-p 00004000 08:01 918442     /lib/i386-linux-gnu/libattr.so.1.1.0
b1aed000-b1af4000 r-xp 00000000 08:01 918436     /lib/i386-linux-gnu/libacl.so.1.1.0
b1af4000-b1af5000 r--p 00006000 08:01 918436     /lib/i386-linux-gnu/libacl.so.1.1.0
b1af5000-b1af6000 rw-p 00007000 08:01 918436     /lib/i386-linux-gnu/libacl.so.1.1.0
b1af8000-b1b0e000 r--p 00000000 08:01 1191435    /usr/share/locale/en_GB/LC_MESSAGES/gedit.mo
b1b0e000-b1b1a000 r-xp 00000000 08:01 262481     /usr/lib/i386-linux-gnu/gnome-vfs-2.0/modules/libfile.so
b1b1a000-b1b1b000 r--p 0000b000 08:01 262481     /usr/lib/i386-linux-gnu/gnome-vfs-2.0/modules/libfile.so
b1b1b000-b1b1c000 rw-p 0000c000 08:01 262481     /usr/lib/i386-linux-gnu/gnome-vfs-2.0/modules/libfile.so
b1b1c000-b1b3c000 r--s 00000000 08:01 533495     /usr/share/mime/mime.cache
b1b3c000-b1b7b000 r-xp 00000000 08:01 412280     /usr/local/diogenes/xulrunner/libnssckbi.so
b1b7b000-b1b85000 rw-p 0003f000 08:01 412280     /usr/local/diogenes/xulrunner/libnssckbi.so
b1b85000-b1bcd000 r-xp 00000000 08:01 412276     /usr/local/diogenes/xulrunner/libfreebl3.so
b1bcd000-b1bce000 rw-p 00047000 08:01 412276     /usr/local/diogenes/xulrunner/libfreebl3.so
b1bce000-b1bfa000 r-xp 00000000 08:01 412273     /usr/local/diogenes/xulrunner/libnssdbm3.so
b1bfa000-b1bfd000 rw-p 0002c000 08:01 412273     /usr/local/diogenes/xulrunner/libnssdbm3.so
b1bfd000-b1bfe000 ---p 00000000 00:00 0 
b1bfe000-b23fe000 rw-p 00000000 00:00 0          [stack:12683]
b23fe000-b23ff000 ---p 00000000 00:00 0 
b23ff000-b2bff000 rw-p 00000000 00:00 0          [stack:12682]
b2bff000-b2c00000 ---p 00000000 00:00 0 
b2c00000-b3400000 rw-p 00000000 00:00 0 
b3400000-b3421000 rw-p 00000000 00:00 0 
b3421000-b3500000 ---p 00000000 00:00 0 
b3500000-b3501000 rw-p 00000000 00:00 0 
b3501000-b3521000 r--s 00000000 08:01 533495     /usr/share/mime/mime.cache
b3521000-b3581000 rw-s 00000000 00:04 13008932   /SYSV00000000 (deleted)
b3581000-b3587000 r-xp 00000000 08:01 262466     /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b3587000-b3588000 r--p 00005000 08:01 262466     /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b3588000-b3589000 rw-p 00006000 08:01 262466     /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b3589000-b35a9000 r--s 00000000 08:01 533495     /usr/share/mime/mime.cache
b35a9000-b35c9000 r--s 00000000 08:01 533495     /usr/share/mime/mime.cache
b35c9000-b35ca000 r--s 00000000 08:03 3672609    /home/jamie/.local/share/mime/mime.cache
b35ca000-b35cb000 r--s 00000000 08:03 3672609    /home/jamie/.local/share/mime/mime.cache
b35cb000-b35cc000 ---p 00000000 00:00 0 
b35cc000-b3dcc000 rw-p 00000000 00:00 0          [stack:12680]
b3dcc000-b3e81000 r--p 00000000 08:01 1180497    /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
b3e81000-b3e82000 r--s 00000000 08:03 3435594    /home/jamie/.cache/fontconfig/556b8bf2d5667b76b1153c2e1a657f39-le32d4.cache-4
b3e82000-b3f5f000 r--s 00000000 08:03 3439585    /home/jamie/.cache/fontconfig/f8bc6966b549555332024bc9fa41f081-le32d4.cache-4
b3f5f000-b3f61000 r--s 00000000 08:03 3435358    /home/jamie/.cache/fontconfig/6de4d616398067bfdcc8e46496f80fe2-le32d4.cache-4
b3f61000-b3f62000 r--s 00000000 08:01 270814     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-4
b3f62000-b3f6a000 r--s 00000000 08:01 270807     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-4
b3f6a000-b3f6c000 r--s 00000000 08:01 270809     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-4
b3f6c000-b3f70000 r--s 00000000 08:01 270792     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-4
b3f70000-b4034000 r--s 00000000 08:03 3435297    /home/jamie/.cache/fontconfig/1b093df283eb9046237f3196b8621797-le32d4.cache-4
b4034000-b4100000 r--s 00000000 08:03 3435270    /home/jamie/.cache/fontconfig/7c2268956d8a152e5eab12bdf59dc3c7-le32d4.cache-4
b4100000-b4121000 rw-p 00000000 00:00 0 
b4121000-b4200000 ---p 00000000 00:00 0 
b4200000-b4201000 r--s 00000000 08:01 270824     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-4
b4201000-b4202000 r--s 00000000 08:01 270789     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-4
b4202000-b4207000 r--s 00000000 08:01 270811     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-4
b4207000-b4210000 r--s 00000000 08:01 270802     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-4
b4210000-b421f000 r--s 00000000 08:01 270787     /var/cache/fontconfig/04aabc0a78ac019cf9454389977116d2-le32d4.cache-4
b421f000-b4220000 r--s 00000000 08:01 270791     /var/cache/fontconfig/1ac9eb803944fde146138c791f5cc56a-le32d4.cache-4
b4220000-b4223000 r--s 00000000 08:01 270795     /var/cache/fontconfig/385c0604a188198f04d133e54aba7fe7-le32d4.cache-4
b4223000-b4224000 r--s 00000000 08:01 270821     /var/cache/fontconfig/dc05db6664285cc2f12bf69c139ae4c3-le32d4.cache-4
b4224000-b4226000 r--s 00000000 08:01 270804     /var/cache/fontconfig/767a8244fc0220cfb567a839d0392e0b-le32d4.cache-4
b4226000-b4227000 r--s 00000000 08:01 263719     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-4
b4227000-b422a000 r--s 00000000 08:01 270806     /var/cache/fontconfig/8801497958630a81b71ace7c5f9b32a8-le32d4.cache-4
b422a000-b422f000 r--s 00000000 08:01 270793     /var/cache/fontconfig/3047814df9a2f067bd2d96a2b9c36e5a-le32d4.cache-4
b422f000-b4233000 r--s 00000000 08:01 270812     /var/cache/fontconfig/b47c4e1ecd0709278f4910c18777a504-le32d4.cache-4
b4233000-b4243000 r--s 00000000 08:01 270818     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-4
b4243000-b424a000 r--s 00000000 08:01 270796     /var/cache/fontconfig/3f7329c5293ffd510edef78f73874cfd-le32d4.cache-4
b424a000-b4253000 r--s 00000000 08:01 270819     /var/cache/fontconfig/d589a48862398ed80a3d6066f4f56f4c-le32d4.cache-4
b4253000-b4262000 r-xp 00000000 08:01 262958     /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libredmond95.so
b4262000-b4263000 r--p 0000e000 08:01 262958     /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libredmond95.so
b4263000-b4264000 rw-p 0000f000 08:01 262958     /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libredmond95.so
b4264000-b4265000 ---p 00000000 00:00 0 
b4265000-b4a65000 rw-p 00000000 00:00 0          [stack:12679]
b4a65000-b4a70000 r-xp 00000000 08:01 918530     /lib/i386-linux-gnu/libnss_files-2.17.so
b4a70000-b4a71000 r--p 0000a000 08:01 918530     /lib/i386-linux-gnu/libnss_files-2.17.so
b4a71000-b4a72000 rw-p 0000b000 08:01 918530     /lib/i386-linux-gnu/libnss_files-2.17.so
b4a72000-b4a7c000 r-xp 00000000 08:01 918534     /lib/i386-linux-gnu/libnss_nis-2.17.so
b4a7c000-b4a7d000 r--p 00009000 08:01 918534     /lib/i386-linux-gnu/libnss_nis-2.17.so
b4a7d000-b4a7e000 rw-p 0000a000 08:01 918534     /lib/i386-linux-gnu/libnss_nis-2.17.so
b4a7e000-b4a93000 r-xp 00000000 08:01 918524     /lib/i386-linux-gnu/libnsl-2.17.so
b4a93000-b4a94000 r--p 00014000 08:01 918524     /lib/i386-linux-gnu/libnsl-2.17.so
b4a94000-b4a95000 rw-p 00015000 08:01 918524     /lib/i386-linux-gnu/libnsl-2.17.so
b4a95000-b4a97000 rw-p 00000000 00:00 0 
b4a97000-b4a9e000 r-xp 00000000 08:01 918526     /lib/i386-linux-gnu/libnss_compat-2.17.so
b4a9e000-b4a9f000 r--p 00006000 08:01 918526     /lib/i386-linux-gnu/libnss_compat-2.17.so
b4a9f000-b4aa0000 rw-p 00007000 08:01 918526     /lib/i386-linux-gnu/libnss_compat-2.17.so
b4aa0000-b4aa7000 r-xp 00000000 08:01 138680     /usr/lib/i386-linux-gnu/libogg.so.0.8.1
b4aa7000-b4aa8000 r--p 00006000 08:01 138680     /usr/lib/i386-linux-gnu/libogg.so.0.8.1
b4aa8000-b4aa9000 rw-p 00007000 08:01 138680     /usr/lib/i386-linux-gnu/libogg.so.0.8.1
b4aa9000-b4ad2000 r-xp 00000000 08:01 138925     /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b4ad2000-b4ad3000 ---p 00029000 08:01 138925     /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b4ad3000-b4ad4000 r--p 00029000 08:01 138925     /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b4ad4000-b4ad5000 rw-p 0002a000 08:01 138925     /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b4ad5000-b4ad8000 r-xp 00000000 08:01 918485     /lib/i386-linux-gnu/libgpg-error.so.0.10.0
b4ad8000-b4ad9000 r--p 00002000 08:01 918485     /lib/i386-linux-gnu/libgpg-error.so.0.10.0
b4ad9000-b4ada000 rw-p 00003000 08:01 918485     /lib/i386-linux-gnu/libgpg-error.so.0.10.0
b4ada000-b4af6000 r-xp 00000000 08:01 138696     /usr/lib/i386-linux-gnu/libp11-kit.so.0.0.0
b4af6000-b4af7000 ---p 0001c000 08:01 138696     /usr/lib/i386-linux-gnu/libp11-kit.so.0.0.0
b4af7000-b4af8000 r--p 0001c000 08:01 138696     /usr/lib/i386-linux-gnu/libp11-kit.so.0.0.0
b4af8000-b4af9000 rw-p 0001d000 08:01 138696     /usr/lib/i386-linux-gnu/libp11-kit.so.0.0.0
b4af9000-b4b09000 r-xp 00000000 08:01 138854     /usr/lib/i386-linux-gnu/libtasn1.so.3.2.0
b4b09000-b4b0a000 r--p 0000f000 08:01 138854     /usr/lib/i386-linux-gnu/libtasn1.so.3.2.0
b4b0a000-b4b0b000 rw-p 00010000 08:01 138854     /usr/lib/i386-linux-gnu/libtasn1.so.3.2.0
b4b0b000-b4b14000 r-xp 00000000 08:01 138592     /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
b4b14000-b4b15000 r--p 00008000 08:01 138592     /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
b4b15000-b4b16000 rw-p 00009000 08:01 138592     /usr/lib/i386-linux-gnu/libltdl.so.7.3.0Aborted




---

### Post by Auricomans on 2014-05-15
Hello:

Diogenes loses functionality with the latest versions of Perl and xulrunner.  Specifically (from Heslin's website):

> [**Note on Linux**. At the moment, Diogenes is not compatible with the latest version of Perl which is supplied with some very recent Linux distributions).  Right now, Diogenes does not work if you upgrade your operating system. I will make the necessary changes to make Diogenes work with the newer version of Perl and release a new version very soon.]("https://community.dur.ac.uk/p.j.heslin/Software/Diogenes/")

Additional discussion [here]("https://aur.archlinux.org/packages/diogenes/?comments=all").

In the meantime, you could use Perseus or implement multiple versions of perl (and/or xulrunner).

---

### Post by Jamie_Dow on 2014-05-15
Ach. Thanks.
I should have found that sooner (Peter's page, at least). Doh.
Not sure about how to implement multiple versions of perl and/or xulrunner, and a bit anxious about what else I might mess up by doing so, so I'm trying the person who offered a reworked version of diogenes, in the archlinux thread. We'll see how we go with that. It's quite annoying to be without it, I confess.
Thanks again.

---

### Post by Auricomans on 2014-05-16
No problem.  I have used multiple versions of xulrunner in the past (I just had more than one installed and didn't notice any issues with them), but I cannot claim that I went about it in a particularly well-educated manner.  The different versions of Perl is also [a thing]("http://stackoverflow.com/questions/398221/how-do-you-manage-perl-modules-when-using-a-package-manager"), but I have yet to try it personally.

Did you come by Diogenes through means other than through Heslin's site?  There are also a number of other programs (which may be pertinent, depending on your needs for Diogenes), but many are not appropriate to Linux and/or not free.  A list of those compatible with the TLG databases and available for Windows or Mac can be found [here]("http://www.tlg.uci.edu/about/cd_soft.php"). I am afraid that I do not have experience with them, personally, so you'd have to investigate whether any are worthwhile and have Linux distros.

Another possibility, of course, is that you could try (until Heslin releases a new version) to use a Windows distrobution of Diogenes in conjunction with WINE (or another virtual box).

Hope this helps!

---

