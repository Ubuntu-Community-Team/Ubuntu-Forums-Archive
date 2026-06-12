---
title: "Major differences between 12.04/12.10/13.04?"
date: 2013-03-02
forum: General Help
---

### Post by Juniorr on 2013-03-02
I'm having problems with 12.10 and 13.04 regarding Steam (specifically Team Fortress 2 game) which at some random point I will experience a fps drop, something like from 200 to 10. I'm not sure but this could be a memory leak because the whole system gets slow afterwards, only a reboot to fix (sometimes a lightdm restart).

I even created a thread on Steam Linux Discussions reporting how to fix it on 12.04.1 by manually upgrading the kernel to 3.5.0-25 (**[[COLOR=#0000ff]Link HERE[/COLOR]]("http://steamcommunity.com/app/221410/discussions/0/864960986991466725/")**), but somehow if the kernel comes with the system (like on 12.04.2/12.10/13.04) the problem still persists.

I love 13.04 and 12.10, but I can't see any major differences in performance or anything else, just in their repositories (12.04 has "older" versions of the majority of programs out there). So, what makes 12.10/13.04 better than 12.04?

---

### Post by Mr. Shannon on 2013-03-02
13.04 has not been released yet so it does not have this, but [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes) will tell you some of what is new with 12.10 for a bunch of different flavors of ubuntu.

---

### Post by sudodus on 2013-03-02
[COLOR=#a9a9a9][I could not post here before, maybe it works now][/COLOR]

12.04 LTS has long time support and is now debugged for a year (counting  the beta testing period). So it is quite reliable. And it is the last  Ubuntu version supporting CPUs without PAE. I like 12.04 and run it most  of the time.

There are newer versions of some programs and also newer kernel features  in 12.10 and 13.04. This can be very important in some cases and for  some users, for example drivers for new hardware and ability to dual  boot with Windows 8 booted in UEFI.

I'm sure there is a lot to add to this, and maybe some people will disagree with me.

---

### Post by Juniorr on 2013-03-02
> **sudodus said:**
> [COLOR=#a9a9a9][I could not post here before, maybe it works now][/COLOR]

12.04 LTS has long time support and is now debugged for a year (counting  the beta testing period). So it is quite reliable. And it is the last  Ubuntu version supporting CPUs without PAE. I like 12.04 and run it most  of the time.

There are newer versions of some programs and also newer kernel features  in 12.10 and 13.04. This can be very important in some cases and for  some users, for example drivers for new hardware and ability to dual  boot with Windows 8 booted in UEFI.

I'm sure there is a lot to add to this, and maybe some people will disagree with me.
[COLOR=#000000]Thanks for your reply. Feel free to add your points, I'm here to learn =)[/COLOR]

[COLOR=#000000]So basically there's no way of using Quantal repos for Precise? For example, on Precise: Gimp version is 2.6, on 12.10 is 2.8. I guess I can't do so on Precise?[/COLOR]

---

### Post by Mr. Shannon on 2013-03-02
> **Juniorr said:**
> [COLOR=#000000]So basically there's no way of using Quantal repos for Precise? For example, on Precise: Gimp version is 2.6, on 12.10 is 2.8. I guess I can't do so on Precise?[/COLOR]
Not a good idea, but some software does have PPA's that give you more up to date packages.  For instance [http://www.webupd8.org/2012/08/install-gimp-282-in-ubuntu-1204-precise.html](http://www.webupd8.org/2012/08/install-gimp-282-in-ubuntu-1204-precise.html) has instructions on how to enable a PPA that will give you GIMP 2.8 on ubuntu 12.04.  I use this on Linux Mint 13 (which is based on Ubuntu 12.04) and have thus far not had any problems.

---

### Post by grahammechanical on 2013-03-02
You are now asking different questions. If you suspect a memory leak you can run this command

```
top
```

That will run a utility in the terminal that will show you what process is using what amounts of memory and CPU. Some install, through the Software Centre, htop which is more comprehensive than top.

It is possible to change the precise repositories to Quantal repositories but that will lead to 12.04 being upgraded to 12.10. Do you want to do that? I do not think it advisable to mix repositories as you are thinking of doing. You will hit all kinds of issues with libraries being replaced with newer versions and applications and utilities not functioning because they depend on older versions of the libraries that are not present any more. But hey, if you want to experiment, it is your machine.

You could of course check out the web sites of programs to see if you can find an option to download the latest version and a tutorial on how to do it, But the latest version of an application is not always the most stable version. And this is why even in 13.04 we do not get the very latest as soon as it comes out. Ubuntu developers want even the development release to be stable. And I have found it to be so.

Regards.

---

### Post by Juniorr on 2013-03-02
[**[COLOR=#000000]Mr. Shannon[/COLOR]**]("http://ubuntuforums.org/member.php?u=1303499"), I've tried PPA's in the past but some of them cause the system to break, so I tend to let the system be as original as possible regarding that.
[B][COLOR=#000000][URL="http://ubuntuforums.org/member.php?u=1087323"]
grahammechanical[/URL],[/COLOR][/B]I wouldn't bother upgrading IF the problems get fixed. Basically I have a 12.04.1 DVD and after all updates it still has 3.2 kernel, so after upgrading the kernel all problems get fixed, but I kind of have to make a decision : To have a sort of outdated system but no fps drops (and now that I know I can probably only use other repos via PPA's I won't change the system a bit) or to have a fully new system but with this kind of bug, that is related to Steam and not Ubuntu itself.  It's really hard to decide since Steam seems to be doing nothing about it.

---

### Post by Mr. Shannon on 2013-03-02
> **Juniorr said:**
> [**[COLOR=#000000]Mr. Shannon[/COLOR]**]("http://ubuntuforums.org/member.php?u=1303499"), I've tried PPA's in the past but some of them cause the system to break, so I tend to let the system be as original as possible regarding that.

True, that's why I use them sparingly.

---

