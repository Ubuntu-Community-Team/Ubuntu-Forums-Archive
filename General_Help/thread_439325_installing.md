---
title: "installing"
date: 2007-05-10
forum: General Help
---

### Post by atticboy30 on 2007-05-10
hi there, i'm completely new to this, and wondered what i would loose if i installed ubuntu from my present windows xp - would i have to remove my present software that is xp based, as you may be able to tell i am completely fresh faced when it comes to this as a subject, i've had very little problems with my windows xp, i've got macafee protecting my computer and will have untill it runs out next year, my main reason for wanting to change is the fact that i know the reputation that linux has for being a much more solid base for almost everything on the pc - it seems to make it more mac like from what i've heard, and to me that's a fantastic attchievement. i just want to use a lot of the features i already have.

i just wonder if i'll be able to leave music or picture files on the computer and then install ubuntu over the top like you can with xp and then find your old files and open them as before.

i wonder if other programmes i have installed on my computer will still work, or if i'll have to get linux based programmes - i have skype, sonic music and dvd copying software, napster, oprea web browser, microsoft office 2003, would i have to buy these new programmes, would i have to download new printer software, would my broadband still work. and could i have xp and ubuntu on the same comptuer in case i would still need microsoft xp based programmes on it

---

### Post by threegremlins on 2007-05-10
You'll have to partition your hard drive if you want to install Ubuntu or Install it on virtual partition. There may be other ways to install inside a Windows Xp partition but someone will have to answer with that knowledge. There are ways, if you only have Xp installed over the whole drive to shrink the Windows partition down to make room for a Linux swap and Linux file partition. There are a lot of great programs to replace your Windows based programs and the best part is they are free. I'm grateful to the many coders out there who believe in the Linux community who have made this all possible. I still use some Windows programs even though I've pretty much switched to Ubuntu, so I keep a  windows a partition active. The more you use Ubuntu, you'll find it has benefits Windows can't ever hope to compete with because they are commercially based.

---

### Post by finer recliner on 2007-05-10
disregarding the idea of "virtual partitions", no you cannot install linux *over the top of xp* and keep all your music/pics. there are 2 ways to install ubuntu...either dual boot (recommended) or reformat your entire computer for only linux (your will lose your files/programs). either way you choose *back up your data!*. dual boot means installing ubuntu on your hard drive while leaving windows intact. of course you will have to devote some of your hard drive space to linux, and you will have to shrink down the size that windows uses. there are alternatives to nearly every application you may use in windows:
media player = VLC, mplayer, xmms
instant messenger = gaim
internet browser = firefox
MS office = open office
skype even has an alpha version available for linux (alpha means still in testing)

i recommend burning the ubuntu installation disk and booting from it. this will make it act as a live cd. booting a live cd will allow you to interact with ubuntu without actually installing anything to your hard drive. this will give you a chance to try things out and see how it looks.

if you choose to dual boot, your linux partition will be able to read and write from the windows one, so you can leave all your music/pics right where they are. if you wipe out windows, then burn everything to cds and copy them back onto the linux system once installed.

---

### Post by jbro on 2007-05-10
> **atticboy30 said:**
> hi there, i'm completely new to this, and wondered what i would loose if i installed ubuntu from my present windows xp - would i have to remove my present software that is xp based, as you may be able to tell i am completely fresh faced when it comes to this as a subject
You wouldn't necessarily have to lose anything, and you may find that you've gained a lot. You would not have to remove XP or any software installed under XP. It is quite possible to have a machine that boots both Windows and Linux. I would bet that a large proportion of Linux users either have a dual-boot machine or can run Windows in a virtual machines for those rare moments when something must be in Windows.


> **atticboy30 said:**
> i've had very little problems with my windows xp, i've got macafee protecting my computer and will have untill it runs out next year, my main reason for wanting to change is the fact that i know the reputation that linux has for being a much more solid base for almost everything on the pc - it seems to make it more mac like from what i've heard, and to me that's a fantastic attchievement.
I don't know if I would necessarily call Linux more "Mac-like". Visually, Linux can look like whatever you would like - Mac and Vista lookalikes seem to be popular right now. OS X does had a BSD base (similar to Linux), but this is usually hidden behind the GUI. I would have to say the interaction (at least with GNOME/KDE/XFCE) are more Windows-like than Mac-like, since the Mac paradigm (Finder, a single toolbar) is very different than Windows or the default Linux setups in the mentioned environments. This is not to discourage you, but to prevent any misconceptions.

> **atticboy30 said:**
> i just wonder if i'll be able to leave music or picture files on the computer and then install ubuntu over the top like you can with xp and then find your old files and open them as before.
If you do set up a double boot machine, you can have Linux read and even write NTFS file systems, so you would not have to do anything special to migrate files. (Note that NTFS writing is experimental, meaning you could nuke your NTFS file system - be sure to have regular backups.)

> **atticboy30 said:**
> i wonder if other programmes i have installed on my computer will still work, or if i'll have to get linux based programmes - i have skype, sonic music and dvd copying software, napster, oprea web browser, microsoft office 2003, would i have to buy these new programmes, would i have to download new printer software, would my broadband still work. and could i have xp and ubuntu on the same comptuer in case i would still need microsoft xp based programmes on it
You will most likely have to get new programs for Linux. Except for (possibly) Java programs, you can't just run Windows executables on Linux unless you use an emulator like Wine, which would let you run Windows programs under Linux. If you do this, you might as well just use Windows since you already have it set up.

As far as replacing your Windows software with Linux equivalents, you probably won't have to buy anything. The Ubuntu software repositories have nearly everything you might need. If you don' t find what you are looiking for, there may be third party repositories with what you need. Nearly every piece of Windows software has a Linux equivalent. For example, we have Office -> OpenOffice, Skype -> Skype (no video), Sonic -> GnomeBaker/K3b, Opera -> Opera, Napster -> ?. That said, the mapping is not exact, and if you have to interoperate with people who work with Windows, you may have some glitches you have to work out. Your broadband (wired and wireless) should work and you will have to install or download CUPS drivers for your printer.

 Double booting is a widely used solution to your problem. I do it because I need Windows to run video conferencing (I'm trying to find a Linux alternative to say, Skype's video phone,) and some development tools. (If I can get a Linux video phone package I'll just run Windows in a virtual machine under Linux. A google for "dual boot Windows Linux" will bring you a load of information on how to set this up.

Well, enough rambling. I hope this gives you a little bit better idea about Linux. I would recommend perhaps trying a LiveCD for a week to do some of your basic tasks. If you like Linux, install it. Then, slowly pick the tasks you want to start doing on Linux and see how it works for you. I think you'll find that after a time you'll do more and more in Linux and only what you have to in Windows.

Regards,
jbro

---

