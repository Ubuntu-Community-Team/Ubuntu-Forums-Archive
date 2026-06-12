---
title: "OpenOffice Writer hangs often. :("
date: 2007-11-08
forum: General Help
---

### Post by ldesilva on 2007-11-08
Hi,
I am using Gutsy 7.10 for a while and just started using OpenOffice Writer to write some documents. I noticed that the applications hangs so often. Does anyone encounter the same problem as I do?

Thank you.

---

### Post by p_quarles on 2007-11-08
By "hangs" do you mean that it pauses for a while, and then works again, or that it crashes? I've had the former happen to me a few times, but I've never had it crash completely. 

Anyway, OpenOffice.org is a great software suite, but it's also kind of slow and resource-heavy. If you're experiencing slowness with that, you might want to look into alternatives. AbiWord (Gnome) and KWord (KDE) are both very powerful word processors, available in the repositories, and are considerably faster.

I would keep OOo Writer around, though, because it has much better support for reading MS Word .doc files than the alternatives. That's the main reason for it being the default word processor in Ubuntu, even though the others are less resource-intensive.

---

### Post by ldesilva on 2007-11-08
It just stop responding completely. I actually ended up closing the application and start the recovery process. I need OO Writer so that I can save my doco in the word format as most of my colleagues are on Windows.

---

### Post by p_quarles on 2007-11-08
> **ldesilva said:**
> It just stop responding completely. I actually ended up closing the application and start the recovery process. I need OO Writer so that I can save my doco in the word format as most of my colleagues are on Windows.
I understand. Sounds like you have a couple options:
1) Use one of the word processors I mentioned, and save your docs in .rtf -- this is a very standard format that is supported by every word processor. 

2) Attempt to debug OpenOffice Writer. The first step would be to run it from the terminal:
```
ooffice -writer
```
Generally speaking, the terminal will give you some extra information about *why *it's crashing when it does. It's possible that I or someone else here could help you fix the problem if you post the crash feedback here.

---

### Post by LobbyDizzle on 2007-11-09
I can open openoffice but when I try to open a powerpoint file it freezes and I have to force quit.... Here is my terminal output.

jared@jared-laptop:~$ ooffice -presentation
jared@jared-laptop:~$ *** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x00000000013b12c0 ***
======= Backtrace: =========
/lib/libc.so.6[0x2baa27613b0a]
/lib/libc.so.6(cfree+0x8c)[0x2baa276176fc]
/usr/lib/openoffice/program/libvclplug_gtk680lx.so[0x2baa2d67a378]
/usr/lib/openoffice/program/libvcl680lx.so(_ZN11SalGraphics22GetNativeControlRegionEjjRK6RegionjRK16ImplControlValueR16SalControlHandleRKN3rtl8OUStringERS0_SC_PK12OutputDevice+0x168)[0x2baa2337c3a8]
/usr/lib/openoffice/program/libvcl680lx.so(_ZN6Window22GetNativeControlRegionEjjRK6RegionjRK16ImplControlValueN3rtl8OUStringERS0_S8_+0x112)[0x2baa23433212]
/usr/lib/openoffice/program/libvcl680lx.so(_ZN7ListBox6ResizeEv+0x19f)[0x2baa234748ef]
/usr/lib/openoffice/program/libvcl680lx.so[0x2baa2341b519]
/usr/lib/openoffice/program/libvcl680lx.so(_ZN6Window4ShowEht+0xd6)[0x2baa2341d886]
/usr/lib/openoffice/program/libsvx680lx.so[0x2aaab190a0aa]
/usr/lib/openoffice/program/libsvx680lx.so(_ZN26SvxLineStyleToolBoxControl16CreateItemWindowEP6Window+0x3a)[0x2aaab191360a]
/usr/lib/openoffice/program/libsfx680lx.so(_ZN17SfxToolBoxControl16createItemWindowERKN3com3sun4star3uno9ReferenceINS2_3awt7XWindowEEE+0x52)[0x2aaaadb2e742]
/usr/lib/openoffice/program/libfwk680lx.so[0x2aaaaeb8dd6a]
/usr/lib/openoffice/program/libfwk680lx.so[0x2aaaaeb94fa0]
/usr/lib/openoffice/program/libfwk680lx.so[0x2aaaaeb86713]
/usr/lib/openoffice/program/libfwk680lx.so[0x2aaaaeb82474]
/usr/lib/openoffice/program/libfwk680lx.so[0x2aaaaeaed2f9]
/usr/lib/openoffice/program/libfwk680lx.so[0x2aaaaea96f7b]
/usr/lib/openoffice/program/libfwk680lx.so[0x2aaaaeab1f75]
/usr/lib/openoffice/program/libfwk680lx.so[0x2aaaaeab0c3f]
/usr/lib/openoffice/program/libsd680lx.so[0x2aaabfc0f2e4]
/usr/lib/openoffice/program/libsd680lx.so[0x2aaabfc10e6c]
/usr/lib/openoffice/program/libvcl680lx.so[0x2baa2342e1c1]
/usr/lib/openoffice/program/libvclplug_gen680lx.so(_ZN10SalDisplay21DispatchInternalEventEv+0xb6)[0x2baa2e518826]
/usr/lib/openoffice/program/libvclplug_gtk680lx.so[0x2baa2d65b969]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1c3)[0x2baa2bbe4fd3]
/usr/lib/libglib-2.0.so.0[0x2baa2bbe82dd]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x6e)[0x2baa2bbe880e]
/usr/lib/openoffice/program/libvclplug_gtk680lx.so[0x2baa2d65d389]
/usr/lib/openoffice/program/libvcl680lx.so(_ZN11Application5YieldEb+0x3e)[0x2baa2324d84e]
/usr/lib/openoffice/program/libvcl680lx.so(_ZN11Application7ExecuteEv+0x27)[0x2baa2324d927]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0x1303)[0x42a553]
/usr/lib/openoffice/program/libvcl680lx.so[0x2baa23253244]
/usr/lib/openoffice/program/libvcl680lx.so(_Z6SVMainv+0x25)[0x2baa23253335]
/usr/lib/openoffice/program/soffice.bin(main+0xa8)[0x41d5c8]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2baa275bfb44]
/usr/lib/openoffice/program/soffice.bin(_ZN6Window15SetPosSizePixelEllllt+0x369)[0x41d489]
======= Memory map: ========
00400000-00459000 r-xp 00000000 08:03 11437111                           /usr/lib/openoffice/program/soffice.bin
00659000-0065b000 rw-p 00059000 08:03 11437111                           /usr/lib/openoffice/program/soffice.bin
0065b000-026da000 rw-p 0065b000 00:00 0                                  [heap]
40000000-40001000 ---p 40000000 00:00 0 
40001000-40801000 rw-p 40001000 00:00 0 
40801000-40802000 ---p 40801000 00:00 0 
40802000-41002000 rw-p 40802000 00:00 0 
41002000-41003000 ---p 41002000 00:00 0 
41003000-41803000 rw-p 41003000 00:00 0 
41803000-41804000 ---p 41803000 00:00 0 
41804000-42004000 rw-p 41804000 00:00 0 
42004000-42005000 ---p 42004000 00:00 0 
42005000-42805000 rw-p 42005000 00:00 0 
42805000-42806000 ---p 42805000 00:00 0 
42806000-43006000 rw-p 42806000 00:00 0 
43807000-43808000 ---p 43807000 00:00 0 
43808000-44008000 rw-p 43808000 00:00 0 
44008000-44009000 ---p 44008000 00:00 0 
44009000-44809000 rw-p 44009000 00:00 0 
44809000-4480a000 ---p 44809000 00:00 0 
4480a000-4500a000 rw-p 4480a000 00:00 0 
2aaaaaaab000-2aaaaaabb000 rw-p 2aaaaaaab000 00:00 0 
2aaaaaabc000-2aaaaaad4000 r-xp 0

---

### Post by eino on 2007-11-10
I had a same problem and I solve it so that I change my theme back to "Human"

It sems that Ubuntu 7.10 do not co-operate OK with open-office when changing theme to some other.

I don't know if the problem is same,tell me.

---

### Post by Jiawen on 2007-11-17
I'm having the same problem: when I do a few minutes' work in OpenOffice Writer, the whole program locks up and the only way to get the window closed is to kill it. CPU usage goes up to 75% or so. If I let it go too long, it locks up my whole computer and I have to restart, 

Uninstalling openoffice.org-gtk does *not* help. This is a terrible state of affairs. :(

Please tell me what to do. I need to have OO.o operational; there are various reasons why I can't use Abiword or other lighter word processors.

---

### Post by LobbyDizzle on 2007-11-20
Changing the Theme back to 'Human' worked for me too.

---

### Post by Jiawen on 2007-11-20
If uninstalling openoffice.org-gtk didn't help, would going back to Human help? For what it's worth, I'm using Xfce, so it seems like that might actually not be root of the problem. And: OO.o Writer was actually working pretty well for the past few days, but then it just hung again. :(

To be honest, I really don't want to have to change my theme. I find it pretty indefensible that OpenOffice can crash based on what theme I'm using.

---

### Post by carstanje on 2007-11-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This bug only happends when you are using incomplete themes. There are tons of themes that do work with openoffice correctly. For example, the highest rated themes on gnome-look.org won't give you these problems.

---

### Post by mike555 on 2007-11-21
If you have lots of RAM , you can set OpenOffice to use more ....... in preferences , the memory tab, set it to use 128 , and 20 per object ..... that should help it start faster also........
    don't know if that will help you much, but it's a good thing to do anyway .

---

### Post by mike555 on 2007-11-21
Also set the "undo "from 100 down to 20  or 30 .......

---

### Post by stchman on 2007-11-21
I have a script that will install the Openoffice.org 2.3 from Openoffice.org website.  I run OO 2.3 on one of my Feisty machines with no trouble.  Some folks on the forum have reported better performance with OO2.3 from OO rather than the default OO2.3 install in Gutsy.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

Look in the Scripts section.

---

### Post by carstanje on 2007-11-21
> **Jiawen said:**
> For what it's worth, I'm using Xfce, so it seems like that might actually not be root of the problem. 
XFCE is also using the GTK engine, that's why you encounter the same problem.

---

### Post by Jiawen on 2007-12-16
> **carstanje said:**
> This bug only happends when you are using incomplete themes. There are tons of themes that do work with openoffice correctly. For example, the highest rated themes on gnome-look.org won't give you these problems.Fine. But a theme should not ever crash an entire application like OOo. And in fact, it has actually crashed my *entire computer* twice now. We should be able to use themes! I don't think that's asking too much.

There are supposed to be fixes out there (such as in the Launchpad bug threads you posted), but I have no idea how to apply them, and no one seems to explain how to do it, either.

---

### Post by carstanje on 2007-12-16
You can't. :( I agree with you this should be already fixed, but it's simply not.

Your only option is to use valid themes, file a new bug or update one or wait for an update...

On the other hand, themes could also be better checked before installation to make sure they won't screw up your system.

---

