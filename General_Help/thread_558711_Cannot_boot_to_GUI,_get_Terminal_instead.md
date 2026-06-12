---
title: "Cannot boot to GUI, get Terminal instead"
date: 2007-09-24
forum: General Help
---

### Post by D2Hitman on 2007-09-24
Ubuntu been working perfectly for months. One day FSCK forces a check on my main HD. This usually works fine, but this time it gets into a problem and doesn't seem to be able to fix it. I ran a manual FSCK and attempted to fix the problems. The disk now passes the check, but having more problems...

i boot the computer, choose the top kernel from the Grub and get to the Ubuntu loading screen. The bar gets to what appears to be about 99%, but i don't think you see it make it to 100% (not sure if thats normal).

Says starting up, loading please wait, then prints:
> kinit: name_to_dev_t (/dev/disk/by-unid/76bc87bd-ce65-47f2-b4e8-93e217d977c8)=hdb5(3,65)

kinit: No resume image, doing normal boot...

Ubuntu 7.04 name-desktop tty1

name-desktop login:
This allows a login, but in terminal mode. Apt doesn't seem to work in this.

I hit Ctrl-Alt-Del to restart and it prints the list of everything shutting down. I notice that shutting down Avahi mDNS/DNS-SD fails.

I have then gone back into the Grub and tried the recovery startup option. This gets part way through, but then gets:
>    * Mounting local filesystems
NTFS signature is missing
failed to start up volume: Invalid arg
failed to mount '/dev/hdb1': Invalid arg
The device '/dev/hdb1' doesn't have a valid NTFS
failed to access '/dev/hdb1'
No such drive or directory
(the filesystem isn't NTFS btw)

This recovery startup was happening until recently, but through no changes it now just goes straight to the terminal with no error.

I am able to mount this harddisk on another version of ubuntu on a different disk and access all the files, but i really want to be able to get back into the GUI on the main disk. Any help with this wound be excellent.

Thanks.

---

### Post by quixotic-cynic on 2007-09-25
In the long run it might be better to just start X manuall - that way if you get a problem with the graphical stuff you are not as screwed because you are used to it.

3 things you could try:
```
startx
```

```
exec gnome-session
```

```
exec gdm
```

Instead of apt you could try aptitude:

```

sudo aptitude install <package>
sudo aptitude show <package>
sudo aptitude search <package>
sudo aptitude update
sudo aptitude upgrade
etc

```

I'm can't perform a diagnosis based on the fault/crash but those commands *should* boot up graphical environments - so if they don't work it is probably something serious.  : /

---

### Post by D2Hitman on 2007-09-25
Thank you for your response. I've just tried your suggestions for starting the GUI. Here are the results:

startx:
> xauth: creating new authority file /home/jon/.serverauth.5534
/usr/bin/X11/X: error while loading shared libraries: libfontenc.so.1: cannot open shared object file: No such file or directory
xinit: server error

exec gnome-session
> gnome-session: error while loading shared libraries: libesd.so.0: cannot open shared object file: No such file or directory
which then takes you to terminal log in again

exec gdm
> -bash: exec: gdm: not found

does this give you and incite?

thanks.

---

### Post by DeadPiligrim on 2008-03-13
Hi, I have absolutely same problem on Ubuntu 7.10

When I'm trying to boot, i get this kinit error message and terminal login screen. I've tried everything I found in google. After I did

sudo swapoff /dev/hdd4
sudo mkswap /dev/hdd4
sudo update-initramfs -n

the kinit error message gone, but still no gui loading. When I type startx I get this message 

> xauth: creating new authority file /home/username/.serverauth.5090
/usr/bin/X11/X: error while loading shared libraries: libfontenc.so.1: cannot open shared object file: Input/output error
xinit: server error

What can I do with it?

---

### Post by TheTank on 2008-03-16
Same issue as well, but not all the time.
Out of the last 3 initial boots it happend 2 times.

A reboot seems to work.

Sorry to say this is one of the issues that is starting to turn me away from Ubuntu again.

---

### Post by sixpence on 2008-03-16
Alright, let's get your GUI issue out of the way. Is there any way you can make available for us the contents of the following text-based files?

```
/etc/X11/xorg.conf
/var/log/Xorg.0.log
```

That would be great! :D

---

### Post by TheTank on 2008-03-16
Here ya go.

I had to split up the log into two files due to the upload limitation.

I also just checked and my xorg.conf has not changed in the last 2 months.

Thanks in advance!

---

### Post by DeadPiligrim on 2008-03-17
OK. I solved this. Problem was that because of FS failure some libraries were broken. I booted with the Live CD, ran reiserfsck which gave me about 100 files in lost+found. Most of them were from usr/lib folder, so i just copied all the missing files from Live Cd's /usr/lib to my disk and after that the system booted fine. However, some of the libraries were still missing, I couldn't launch amarok, krusader, skype, awn, etc. Some of them I reinstalled, for others I had to search for files containing library's name in lost+found and copied them with new names to /usr/lib. Now the system is more or less stable. There are some glitches that I will try to solve later, i.e. sometimes compiz doesn't redraw desktop after I minimize windows, Thunderbird 3.0a1, which worked fine before, became unstable. To do so I need to find a way that will check all the needed system files and libraries and restore them. Is there anything I can do with apt-get? 

Also, I tried to reinstall compiz with sudo apt-get install compiz --reinstall and it said that the package can not be downloaded etc. Do I have to reinstall it manually?

---

