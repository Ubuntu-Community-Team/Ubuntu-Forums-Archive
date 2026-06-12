---
title: "Linux(Mono) Mpeg4Toolkit 0.6.4.0-GUI"
date: 2007-08-31
forum: General Help
---

### Post by god2003 on 2007-08-31
Hi, i am the programmer of Mpeg4Toolkit, which was until a few days for Windows (.NET), so i decided to port to Linux ussing Mono. You can view what it does [here]("http://dark-g.sourceforge.net/").

The program has(for now) less options than the windows version. (i am working in the adaptation to Linux on those). below are the changenotes and the things that are not doing now.

I fixed the "delete Originals" option (next release, not yet  avaliable), but in linux i don't know how to send a file to the trash(Recycle bin) i have to lines, in windows dends the files to Recycle bin, and in linux deletes it (shellLib functions are windows only).
I am developing the project from windows and testing it with vmware, so i can try in both O.S. at the same time.

I posted this info at doom9 forum, but i considered opportune to do it here too. I hope, is helpfull to anyone.

[download]("http://downloads.sourceforge.net/dark-g/linux_mpeg4toolkit_0.6.4.0_bin.tar.gz")
Release notes:
Mpeg4Toolkit ported to Linux using Mono.

Due to the limitations in mono, the linux versión have not the opction "delete Originals", "Fix interleave with VirtualDubMod" (but it warns you), and does not have the "Check updates" Option.
of course it needs Mono in order to work. (Check if in your distribution are installed the Mono packges).
Also works in Windows because is a Windows binary.

Included a launcher "M4T Launcher"(You may have to establish the execute properties). You can launch it by typing "mono m4t.exe" in the directorie where you extracted it(console), or you can create your own launcher, in your distribution.

MFE (Multiple Filename Editor) has been removed(for now), because it was using windows functions.

Integration it's gone, because it is useless in Linux, but the program accepts one parameter(argument), which can be a dirtectorie or one file.

[IMG]http://dark-g.sourceforge.net/images/m4t_linux_en.png[/IMG]

It is my first aproach to linux. Iwill try to merge into one, both versions.
Tested on Ubuntu 7.04 x86, with mono packages from synaptic.

---

