---
title: "NTFS directory coloring in terminal"
date: 2008-04-24
forum: General Help
---

### Post by josteinaj on 2008-04-24
I'm annoyed by the default coloring of NTFS directories in Ubuntu. Just watch:
[IMG]http://josteinaj.no/images/2011/ntfs_coloring.png[/IMG]
(I believe the NTFS partition may have encryption enabled and the green background color symbolizes that the folder is encrypted?)

The screenshot is taken from a gnome-terminal running on my Ubuntu 7.10 laptop, ssh'ed into my desktop PC which has both a ntfs and a fat32/vfat partition on it. However the same colors appear when sshing in using PuTTY, or using gnome-terminal without sshing directly from the desktop computer.

So I guess it must be the "terminal-server" (if there is such a thing) on the Ubuntu 7.10 x64 desktop PC that defines the coloring scheme.

I want to remove the green background-color from the NTFS directories so it becomes readable. How do I do that?

---

### Post by warp99 on 2008-04-24
> **josteinaj said:**
> I'm annoyed by the default coloring of NTFS directories in Ubuntu. Just watch:
[IMG]http://folk.ntnu.no/josteija/webshare/ntfs_coloring.png[/IMG]
(I believe the NTFS partition may have encryption enabled and the green background color symbolizes that the folder is encrypted?)

The screenshot is taken from a gnome-terminal running on my Ubuntu 7.10 laptop, ssh'ed into my desktop PC which has both a ntfs and a fat32/vfat partition on it. However the same colors appear when sshing in using PuTTY, or using gnome-terminal without sshing directly from the desktop computer.

So I guess it must be the "terminal-server" (if there is such a thing) on the Ubuntu 7.10 x64 desktop PC that defines the coloring scheme.

I want to remove the green background-color from the NTFS directories so it becomes readable. How do I do that?

You need to make changes to the dircolors command in your .bashrc script, but first you need to export the dircolors database to a file like this:
```
dircolors --print-database > ~/.mydircolors
```
then edit the file:
```
nano ~/.mydircolors
```
and change the colors to your preferences. Save the file then make changes to your .bashrc script. So you would:
```
nano ~/.bashrc
```
then locate the following portion:
```
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

```
and change the string:
```
"`dircolors -b`"
``` 
to 
```
"`dircolors ~/.mydircolors`"
```
so when you login your bash script will change the defaults to your colors.

---

### Post by josteinaj on 2008-04-24
It worked. Thanks! :)

[IMG]http://folk.ntnu.no/josteija/webshare/ntfs_coloring_fixed.png[/IMG]
(It seems NTFS doesn't discriminate between "readable" and "executable", but that's another issue.)

---

### Post by aodhan on 2008-09-13
Thanks for that tip.  It worked for me as well. :)

---

### Post by andylinux on 2008-10-21
If you got this to work, can you share your .mydircolors file?  I can't seem to get the directory background highlighting turned off.

Thanks.

---

### Post by andylinux on 2008-10-23
I figured it out.  Change the line in .mydircolors to this,

STICKY_OTHER_WRITABLE 01;34 # dir that is sticky and other-writable (+t,o+w)
OTHER_WRITABLE 01;34 # dir that is other-writable (o+w) and not sticky

Problem solved.

---

### Post by jt_04 on 2009-05-11
> **andylinux said:**
> I figured it out.  Change the line in .mydircolors to this,

STICKY_OTHER_WRITABLE 01;34 # dir that is sticky and other-writable (+t,o+w)
OTHER_WRITABLE 01;34 # dir that is other-writable (o+w) and not sticky

Problem solved.

thanks for that extra detail, that solved it.  the details are rather important.

---

### Post by atomics on 2009-05-20
What does it mean when a directory is listed with a green background?

When I text copied from the terminal window into Gmail I don't get the colors. How do you copy the directory listing with colors? 

Thanks in advance.

---

### Post by rocuan on 2010-05-31
Cool tip! Thanx

---

