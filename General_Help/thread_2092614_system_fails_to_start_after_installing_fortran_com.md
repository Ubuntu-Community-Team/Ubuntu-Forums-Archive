---
title: "system fails to start after installing fortran compiler"
date: 2012-12-08
forum: General Help
---

### Post by Jimstehrman on 2012-12-08
Hey all,

I was trying to install the intel Linux fortran compiler and was kind of blindly adding apt-getting packages to meet dependencies when the terminal started saying something like this

Removing brasero ... Removing evolution-plugins ... Removing evolution-indicator ... Removing evolution-exchange ... Removing evolution-couchdb ... Removing evolution ... Removing f-spot ... Removing gbrainy ... Removing ubuntu-desktop ... Removing gdm-guest-session ... Removing gdm ... Removing indicator-me ... Removing indicator-applet-session ... Removing indicator-applet ... Removing gnome-session ... Removing gnome-applets ... Removing gnome-panel ... Removing gnome-about ... Removing gnome-mag ... Removing gnome-orca ... Removing gnome-pilot-conduits ... Removing gnome-pilot ... Removing gnome-power-manager ... Removing gnome-utils ... Removing gvfs-backends ... Removing gvfs-bin ... Removing gvfs-fuse ... Removing nautilus-share ...
I though it might not be the best, and sure enough on restart I get this:

Your screen, graphics card, and input device settings could not be  detected correctly. You will need to configure these yourself.

I click ok and get this:

What would you like to do?
Run in low graphics mode for just one session.
Reconfigure graphics
Troubleshoot the error
Exit to console login

a cancel and OK button. 

Really not sure how to proceed

thanks!

---

### Post by 2F4U on 2012-12-08
Seems as if you removed a large portion of the desktop environment. But there is a meta package called ubuntu-desktop, which should bring the desktop back. I am, however, not sure if you can install it without removing the packages that caused the initial problems.

---

### Post by Jimstehrman on 2012-12-08
Is there any way to re-install these packages from an ubuntu usb start disk?

---

### Post by Jimstehrman on 2012-12-08
After some exploration, I managed to fix my problem.

My entire desktop was removed in adding one of the packages required for the compiler. So I had to re-install that as well as a half dozen other packages to get my desktop back.

At first I tried the root shell in recovery mode, however it wouldn't allow updates or install (maybe because my filesystem in encrypted??).
Then I booted from a livecd and used chroot to access the filesystem

```
sudo mkdir /mnt/temp 
sudo mount /dev/sdXY /mnt/temp
```

Then set up a few things for chroot

```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo chroot /mnt/temp
```

finally reinstalling the packages

```
apt-get update
apt-get upgrade
apt-get install --reinstall ubunutu desktop
apt-get install gnome-shell

```

The last one was required since I had been using gnome 3, and attempting to log-in without gnome installed caused a crash.

I found the above mostly from this guide [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
and the rest through trial and error

---

### Post by NM5TF on 2012-12-08
if your problem is fixed please mark this thread as SOLVED
using the thread tools at top right

---

