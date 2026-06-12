---
title: "how to copy file through live cd"
date: 2014-09-23
forum: General Help
---

### Post by arun-3 on 2014-09-23
Since system cannot able to login through os. I tried to get my files through live CD. It shows the files in live Cd.But when i tried copy the file to pen drive it shows the permission denied.Please suggest a command to recover files.

---

### Post by slickymaster on 2014-09-23
*Moved to the ***General Help*** sub-forum*

Start your file manager in the Ubuntu live system with the following commands in a terminal window```
sudo -i nautilus
```and you should now have read/write access to any drive thus being able to copy the files to your USB drive.

---

### Post by arun-3 on 2014-09-24
hi,
I try this code in live cd by typing sudo -i i can access as root . But when i type nautilus its showing error message .

---

### Post by westie457 on 2014-09-24
What error message is shown when you run the command posted by 'slickymaster'?

---

### Post by slickymaster on 2014-09-24
> **arun-3 said:**
> hi,
I try this code in live cd by typing sudo -i i can access as root . But when i type nautilus its showing error message .

Which flavor are you running from the LiveCD?

---

### Post by arun-3 on 2014-09-24
I am using 14.04 LTS ubuntu

---

### Post by slickymaster on 2014-09-24
Can you please post back in the thread the error message you're getting when you run```
sudo -i nautilus
```

---

### Post by arun-3 on 2014-09-24
```
ubuntu@ubuntu:~$ sudo -i nautilus

(nautilus:5658): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(nautilus:5658): GLib-GObject-WARNING **: invalid cast from 'GtkMessageDialog' to 'NautilusWindow'
**
ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))
ubuntu@ubuntu:~$
```

---

### Post by slickymaster on 2014-09-24
Bummer, that's a a confirmed bug in Nautilus: [Bug #1309254]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1309254")

The workaround for that one would be to update the nautilus package version to 1:3.10.1-0ubuntu9.

The easiest thing for you to do would is to get a LiveCD of Xubuntu 14.04, since the default Xubuntu file manager is Thunar instead of Nautilus, and boot from it and once in the live environment open a terminal window and run```
sudo -i thunar
```and you'll have read/write access to any drive thus being able to copy the files to your USB drive.

---

### Post by matt_symes on 2014-09-24
Hi

> **slickymaster said:**
> Bummer, that's a a confirmed bug in Nautilus: [Bug #1309254]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1309254")

The workaround for that one would be to update the nautilus package version to 1:3.10.1-0ubuntu9.

The easiest thing for you to do would is to get a LiveCD of Xubuntu 14.04, since the default Xubuntu file manager is Thunar instead of Nautilus, and boot from it and once in the live environment open a terminal window and run```
sudo -i thunar
```and you'll have read/write access to any drive thus being able to copy the files to your USB drive.

I am interested to see if Thunar will work here as i have very recently had the same issue of copying a file to an internal hard drive from a live environment.

In my case it was copying a xorg.conf file - yes one of my machines has an onboard sis video card :| - into /etc/X11 after a fresh installation of the machine from a PXE environment.

In the end i just rebooted into the new install on the machine and copied it manually from an external hard drive.

So i'm interested to see if this is indicative of a deeper problem or not as i did not bother investigating the reason why i could not copy the file.

Kind regards

---

### Post by slickymaster on 2014-09-24
> **matt_symes said:**
> Hi



I am interested to see if Thunar will work here as i have very recently had the same issue of copying a file to an internal hard drive from a live environment.

In my case it was copying a xorg.conf file - yes one of my machines has an onboard sis video card :| - into /etc/X11 after a fresh installation of the machine from a PXE environment.

In the end i just rebooted into the new install on the machine and copied it manually from an external hard drive.

So i'm interested to see if this is indicative of a deeper problem or not as i did not bother investigating the reason why i could not copy the file.

Kind regards

I've just tried it with Xubuntu 14.10 Beta2 and it worked Matt.

---

### Post by matt_symes on 2014-09-24
Hi slickymaster

> **slickymaster said:**
> I've just tried it with Xubuntu 14.10 Beta2 and it worked Matt.

Thanks for testing that. I did suspect it was something on my end. It does give me something to look into when i can snatch a couple of hours over the weekend.

Anyway, not wishing to derail this thread any further, i'll pass my apologies to the OP and slink away quietly :)

Kindregards

---

### Post by arun-3 on 2014-09-24
ok thanks slickymaster. As there was a urgent i tried the following steps just created root password by set passwd root and logout from  the current session in live cd .Again login as root and copied the file.It works in live cd .

Thanks,
Best Regards
Arun

---

### Post by arun-3 on 2014-09-24
Anyway thanks i love ubuntu os. Since its having all resources.

Thanks,
Arun

---

