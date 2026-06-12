---
title: "Recovery mode woes"
date: 2014-04-04
forum: General Help
---

### Post by John_Brooks on 2014-04-04
So I have an elderly Dell optiplex 320 running 13.04 that I've been using as a jukebox at my bar. It's not connected to the internet so it hasn't been updating for the last few months and I decided to give it an update today.

Unfortunately It asked for my user account password, which I've since forgotten.

No big deal, I thought. I'll just boot to recovery mode and change it that way.

So I restart the system, Hold down shift and wait for GRUB to load then select advanced ubuntu options to get into recovery mode.

It flashes up with the two boot options (the boot normally and the boot to recovery mode options) for about half a second and then decides to boot normally.

So I tried again

and again

and again.

I've been checking all over the forums and can't find anyone else who has had this issue.

I thought maybe I could get through to recovery mode through terminal but it doesn't seem like thats possible.

Anybody have some ideas

---

### Post by Impavidus on 2014-04-04
Not so easily. You could change the configuration of grub so that it shows the menu by default, but that would require the use of sudo. You can use a live disk and then chroot into your install to change the password or, very simple, run [boot-repair]("https://help.ubuntu.com/community/Boot-Repair"), which will install a grub menu with default settings, which will show automatically for 10 seconds. It can do much more, but you only need it to make the grub menu visible.

But I think you'll encounter a different error whilst updating. 13.04 is end of live since 3 months and the repositories have been taken offline. As you keep the computer offline there isn't much risk in running it as an end of life system. It may be best to just continue using it for one or two months and then do a fresh install of 14.04, which will be supported for 5 years.

---

### Post by grahammechanical on 2014-04-04
The Grub count down is supposed to stop once we press any key. It is possible to bring up the Recovery menu in a terminal. It is just a shell script that uses a tool called Whiptail to put up the text mode menu. The command is

```
/lib/recovery-mode/recovery-menu
```

I have experimented modifying some of the recovery scripts and then running them from both a terminal and a tty but I have never tried running Root script from a terminal. Anyway , that command will bring up the recovery menu in a terminal. You could wait until the end of April and download and install 14.04

Regards.

---

### Post by John_Brooks on 2014-04-04
So it seems that the keyboard I was using wasn't cooperating with recovery mode. I got it sorted out now. 

Thanks guys

---

