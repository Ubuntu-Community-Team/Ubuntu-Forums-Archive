---
title: "win7 won't boot from grub"
date: 2013-02-06
forum: General Help
---

### Post by Strojar on 2013-02-06
yesterday dual booting worked just fine, this morning after the update for ubuntu 12.04 64bit I can't boot into win anymore. tried boot repair from live distro withouth any result.

dual boot OS: ubuntu 12.04 64 bit & win 7 64 bit
notebook: compaq presario cq61

boot repair worked for everything until this prbolem showed. the only thing i can think of is to reinstall win, don't have anything of value on them so the only problem is the hustle of reinstalling. any other solution?

---

### Post by schragge on 2013-02-06
What does the output of
```
sudo grub-mkconfig 2>/dev/null | grep -w -B2 -A5 ntfs
```
look like?

---

### Post by Strojar on 2013-02-06
```
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 6AD61AABD61A7811
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```
tried with win bootloader automated repair, didn't fix it and then i found how to repair it from command line ow the win bootloader repair with:
```
bootrec /fixboot
```[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

it is working now, not sure anymore if the update caused the problem.

---

