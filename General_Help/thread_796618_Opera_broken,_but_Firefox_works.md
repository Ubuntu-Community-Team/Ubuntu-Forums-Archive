---
title: "Opera broken, but Firefox works"
date: 2008-05-16
forum: General Help
---

### Post by georgeclooneylookalike on 2008-05-16
Hi,

I have a problem getting opera to browse the internet in Ubuntu 7.04. Firefox works fine as does pidgin, and all the other software I can think of. I get the standard Opera Network Error page

> You tried to access the address [http://www.opera.com/support/](http://www.opera.com/support/), which is currently unavailable. Please make sure that the Web address (URL) is correctly spelled and punctuated, then try reloading the page.

As my internet connection is fine and my router is working I must have broken something in the OS. Can anyone think of what the problem might be.

Thanks in advance.

Chris

---

### Post by zvacet on 2008-05-16
If you don´t have it allready try with Opera 9.5 beta.it is very strange that Opera doesn´t work properly.If yoi didn´t get answer here try on Opera forums for linux.

---

### Post by 0range0rca on 2008-06-12
Hi,

I have the same problem. Ubuntu 7.10 updated.
Tried Opera 9.27 - Web pages dont open.
Opera 9.5 - No luck either. 

Error!
Could not connect to remote server

You tried to access the address [http://portal.opera.com/](http://portal.opera.com/), which is currently unavailable. Please make sure that the Web address (URL) is correctly spelled and punctuated, then try reloading the page.
Make sure your Internet connection is active and check whether other applications that rely on the same connection are working.

Anyone have a solution? 

Thanks

---

### Post by donkmonk on 2008-09-20
Hardy 8.04.1 fresh installation.

Opera (opera_9.52.2091.gcc4.qt3_i386.deb from the vendor's site) installed OK, started OK, but cannot connect with trivial "You tried to access the address [http://portal.opera.com/](http://portal.opera.com/), which is currently unavailable" bla-bla.

Firefox 3 package installed from repository via Adept installer. Doesn't start at all with no error messages. "dpkg -s firefox" returns "Package `firefox' is not installed and no info is available."

Konqueror and Kmail behave OK, no internet connection problems at all.

UPD: sorry, "dpkg -s firefox-3.0" tells that the package installed OK. Doesn't start either.
firefox 2 runs and browses OK.

But what the hell happened to Opera?..

---

### Post by Mr.Banana on 2008-09-29
I have the same bloody problem.

Tried everything, I could think of, but still, any software needing an internet connection works except opera.

---

### Post by ww711 on 2008-09-29
I upgraded to Opera 9.52. Install went smooth, after installation, loaded up the new Opera, it loads the Opera9.5 'promo page' - black background, huge white text with Opera 9.5. Adjacent to that, the red orange and green swipes/slashes. I can get to other sites with out any problems, gmail, ubuntu forums...

---

### Post by Mr.Banana on 2008-09-29
> **ww711 said:**
> I upgraded to Opera 9.52. Install went smooth, after installation, loaded up the new Opera, it loads the Opera9.5 'promo page' - black background, huge white text with Opera 9.5. Adjacent to that, the red orange and green swipes/slashes. I can get to other sites with out any problems, gmail, ubuntu forums...

Downloaded 9.52.

install went OK.

Still doesnt load any website. Not even the promo.:confused:

---

### Post by Mr.Banana on 2008-10-03
> **Mr.Banana said:**
> Downloaded 9.52.

install went OK.

Still doesnt load any website. Not even the promo.:confused:

Tried to uninstall, remove .opera folder, remove all opera config files, reinstalling again, NOTHING.

:(

---

### Post by Mr.Banana on 2008-10-04
Still having the issue.

did 
```
strace opera
```got this:

```
fstat64(8, {st_mode=S_IFREG|0600, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f3b000
flock(8, LOCK_UN)                       = 0
write(8, "\357\273\277Opera Preferences version 2.1"..., 174) = 174
close(8)                                = 0
munmap(0xb6f3b000, 4096)                = 0
stat64("/home/thunderhead/.opera/fontswitch.ini", {st_mode=S_IFREG|0644, st_size=174, ...}) = 0
access("/home/thunderhead/.opera/", F_OK) = 0
open("/home/thunderhead/.opera/opsrpmULqAv", O_RDWR|O_CREAT|O_EXCL|O_LARGEFILE, 0600) = 8
close(8)                                = 0
open("/home/thunderhead/.opera/oprP4eQTR", O_RDONLY|O_LARGEFILE) = 8
open("/home/thunderhead/.opera/opsrpmULqAv", O_WRONLY|O_CREAT|O_TRUNC|O_LARGEFILE, 0666) = 9
fstat64(8, {st_mode=S_IFREG|0600, st_size=174, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f3b000
read(8, "\357\273\277Opera Preferences version 2.1"..., 32768) = 174
read(8, "", 28672)                      = 0
fstat64(9, {st_mode=S_IFREG|0600, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f3a000
read(8, "", 32768)                      = 0
close(8)                                = 0
munmap(0xb6f3b000, 4096)                = 0
write(9, "\357\273\277Opera Preferences version 2.1"..., 174) = 174
close(9)                                = 0
munmap(0xb6f3a000, 4096)                = 0
rename("/home/thunderhead/.opera/opsrpmULqAv", "/home/thunderhead/.opera/fontswitch.ini") = 0
stat64("/home/thunderhead/.opera/opsrpmULqAv", 0xbfaf906c) = -1 ENOENT (No such file or directory)
unlink("/home/thunderhead/.opera/opsrpmULqAv") = -1 ENOENT (No such file or directory)
chmod("/home/thunderhead/.opera/fontswitch.ini", 0644) = 0
stat64("/home/thunderhead/.opera/oprP4eQTR", {st_mode=S_IFREG|0600, st_size=174, ...}) = 0
unlink("/home/thunderhead/.opera/oprP4eQTR") = 0
stat64("/home/thunderhead/.opera/oprP4eQTR", 0xbfaf90fc) = -1 ENOENT (No such file or directory)
unlink("/home/thunderhead/.opera/oprP4eQTR") = -1 ENOENT (No such file or directory)
close(14)                               = 0
munmap(0xb6678000, 23940)               = 0
close(14)                               = -1 EBADF (Bad file descriptor)
close(15)                               = 0
select(4, [3], [3], NULL, NULL)         = 2 (in [3], out [3])
read(3, "\22\324\345b#\0@\3#\0@\3\0\0\0\0\0\0\0\0\204\257\35\10"..., 4096) = 640
writev(3, [{"\4\0\2\0\"\0@\3\4\0\2\0\10\0@\3\4\0\2\0\t\0@\3\4\0\2\0"..., 2524}], 1) = 2524
select(4, [3], [], NULL, NULL)          = 1 (in [3])
read(3, "\22\324\350b\"\0@\3\"\0@\3\0\0\0\0\0\0\0\0\204\257\35\10"..., 4096) = 2304
read(3, 0x8b2e7d4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
munmap(0xb3d68000, 330412)              = 0
munmap(0xb3d31000, 224692)              = 0
munmap(0xb5dea000, 286620)              = 0
munmap(0xb6f3c000, 275572)              = 0
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"\236\23\2\0\242\3@\3\236\23\2\0\246\3@\3\236\23\2\0P\0"..., 60}], 1) = 60
select(4, [3], [], NULL, NULL)          = 1 (in [3])
read(3, "\1\1*d\0\0\0\0 \0\240\2<c \10\300\325\350\277\330\325\350"..., 4096) = 32
read(3, 0x8b2e7d4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
close(3)                                = 0
brk(0x9221000)                          = 0x9221000
write(4, "\1\v\1\0\1\0\0\0\0\0\0\0\310\344E\267", 16) = 16
close(4)                                = 0
close(5)                                = 0
close(6)                                = 0
munmap(0xb5e67000, 38660)               = 0
munmap(0xb5e30000, 47088)               = 0
munmap(0xb5e62000, 19496)               = 0
munmap(0xb5e3c000, 154236)              = 0
exit_group(0)                           = ?
Process 2996 detached
```


Anyone know what could I try next?

---

### Post by ww711 on 2008-10-04
Have you tried looking in the Error Console for Opera?

Navigate to Tools -> Advanced -> Error Console.

There's a drop down box that includes 'Network'...

Failing that, alternatively...try posting on Opera's Support forums....

---

### Post by TenPlus1 on 2008-10-04
Remove Opera using Synaptic Package Manager, then delete the .opera directory in your home directory and finally click this link to download and install Opera 9.60 RC2:

[http://snapshot.opera.com/unix/snapshot-2444/intel-linux/opera_9.60.2444.gcc4.qt3_i386.deb](http://snapshot.opera.com/unix/snapshot-2444/intel-linux/opera_9.60.2444.gcc4.qt3_i386.deb)

---

### Post by Mr.Banana on 2008-10-04
It doesn't help at all.....

---

### Post by ww711 on 2008-10-04
Any reason why you need Opera in particular? Could you go without?

---

### Post by Mr.Banana on 2008-10-04
> **ww711 said:**
> Any reason why you need Opera in particular? Could you go without?

:rolleyes:  Does it matter?

---

### Post by pcwehle on 2008-10-26
Same problem here, everything except Opera connect fine.

Fresh install of Hardy8.4 and got Opera 9.61 from their website.

Someone found a solution meanwhile?

---

### Post by Elegorod on 2008-11-22
I solved such problem by disabling IPv6
[http://my.opera.com/community/forums/topic.dml?id=256797](http://my.opera.com/community/forums/topic.dml?id=256797)
How to disable IPv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) , I used the second way for Hardy. It works for Intrepid too.

---

