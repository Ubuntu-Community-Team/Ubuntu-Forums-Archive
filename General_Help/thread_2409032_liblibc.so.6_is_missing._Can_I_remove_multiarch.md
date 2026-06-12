---
title: "/lib/libc.so.6 is missing. Can I remove multiarch?"
date: 2018-12-26
forum: General Help
---

### Post by 1clue on 2018-12-26
Hi.

I have a SuperMicro motherboard. It's running Gentoo. It's a security appliance. It has IPMI hardware, which is key to console access and remote power control, among other things.

I have an i7 running Ubuntu 18.04. This is my desktop.

SuperMicro has an IPMIView2.0 app linked here: [https://www.supermicro.com/products/nfo/IPMI.cfm](https://www.supermicro.com/products/nfo/IPMI.cfm) , The IPMIView software is linked in the right sidebar, second to last item. To get the software you need to acknowledge their terms of use. That page doesn't seem to link easily so I'm giving you this one.

With older Ubuntu installations, the app works fine. With 18.04 I get "/lib/libc.so.6 is missing.  [https://askubuntu.com/questions/40416/why-is-lib-libc-so-6-missing](https://askubuntu.com/questions/40416/why-is-lib-libc-so-6-missing) shows one guy with the same problem. If I cheat and put in a symbolic link the app gets a different error.

I know what multiarch is. I'm 100% certain that I don't need it, because my Gentoo systems do not have multiarch (they call it multilib) and I have not had any problems related to it, ever since x86_64 became stable years ago.

Is it possible to remove this multiarch junk? In any system where I have a choice I choose a single architecture. AFAICT there is nothing from any other arch (I'm on x86_64) that is of even the slightest use to me. Multiarch is nothing but extra code complexity for an antiquated architecture.

Failing that, is it possible to fix Ubuntu so that closed-source apps compiled for a single architecture can work?

Thank you.

---

### Post by 1clue on 2018-12-28
Bump.

---

### Post by him610 on 2018-12-29
Recommend you prepare Plan B (Contingency) just in case something breaks.

---

### Post by Holger_Gehrke on 2018-12-29
I don't think you can remove the multiarch support. It's not some package, it's a principle for organizing the (library and program) files into various directories.

The IPMIView program you're trying to use is a Java-Application that brings along its own old and outdated JVM (1.7.0_79). You can make it use a modern VM by changing a setting (lax.nl.current.vm) in the launch anywhere configuration file (extension: .lax) for the program(s). The message about libc.so.6 comes from the (launch anywhere, lax) shell-script starter which is trying to grep through the strings in that library to find out whether the library contains native POSIX threads which would make really old Java-VMs (before 1.4 or so) misbehave. You could just edit the shell script (line 1482 in the file IPMIView20) to make it look at the right library. That will make that message go away, but if the program wasn't working before this will probably not fix it.

On my machine IPMIView20 and TrapReceiver started without any problems, even after giving that message, both with the included old JRE and with Java 8. iKVM gives the same message (the shell script contains the same nonsense ...) then gives a graphical error-box about a missing iKVM64 in java.library.path. Setting LD_LIBRARY_PATH=. to make it look for libraries in the current directory makes it give a usage message instead, so it probably works, too. The only one which fails silently after that message is JViewerX9. I don't have the kind of environment in which I could really test these programs but they do seem to run.

Holger

---

### Post by 1clue on 2019-03-13
It turned out to be the PS1 variable that I customized.

[https://zend18.zendesk.com/hc/en-us/articles/203838496-Installation-Fails-Due-to-Malformed-uxxxx-Encoding-](https://zend18.zendesk.com/hc/en-us/articles/203838496-Installation-Fails-Due-to-Malformed-uxxxx-Encoding-)

I ran:

```
PS1=''; IPMIView20
```

and it works.

---

### Post by amelia26 on 2019-04-02
Hi, 

[COLOR=#242729][FONT=Arial]Open a terminal (Ctrl+Alt+T) and run the following commands:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]For 64-bit Ubuntu:[/FONT][/COLOR]
sudo ln -s /lib64/x86_64-linux-gnu/libc.so.6 /lib64/libc.so.6
[COLOR=#242729][FONT=Arial]For 32-bit Ubuntu:[/FONT][/COLOR]
sudo ln -s /lib/i386-linux-gnu/libc.so.6 /lib/libc.so.6





[SIZE=1][COLOR=#000000][FONT=Arial][DigitalOcean]("https://tgw.onl/digitalocean/") [SiteGround]("https://tgw.onl/siteground/") [iPage]("https://tgw.onl/ipage/")[/FONT][/COLOR][/SIZE]

---

### Post by 1clue on 2019-04-04
@amelia26,

I tried some of that awhile back for experimental reasons and it didn't fix the problem. As well there are plenty of warnings about this on the net when you search on this topic. If your system is truly multi-arch, and you have software installed which was compiled for those architectures, then the symbolic links can only cause problems.

As I said in the post above yours, the real cause was that the script which starts the app is not tolerant of my wildly customized PS1 variable. Still not sure why that would be, but it's a simple fix with no edits outside of my $HOME directory.

---

