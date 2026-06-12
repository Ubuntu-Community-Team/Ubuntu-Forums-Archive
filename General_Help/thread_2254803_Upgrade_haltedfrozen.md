---
title: "Upgrade halted/frozen"
date: 2014-11-30
forum: General Help
---

### Post by Kymus on 2014-11-30
Yesterday I started to upgrade to Ubuntu 14.04 from 13.10.

As luck would have it, progress halted in the middle of the upgrade and has remained the same for the past 10 hours. [The last time this happened]("http://ubuntuforums.org/showthread.php?t=2200064"), my system immediately became unusable and was FUBARed. The only difference is that this time, only the progress of the update has halted and my system is otherwise functional at this moment. Considering this, I thought it may be wise to avoid a reboot and instead consult first, as I would of course prefer having to reinstall the OS, again.

Attached is a screenshot of the update window FWIW.

So, essentially: is there some sort of hocus pocus I can do at present to possibly prevent my system from becoming unstable, or do I just reboot and cross my fingers?

---

### Post by ian-weisser on 2014-12-03
An .xcf file isn't the most helpful image format. I don't have anything installed to easily view it (like Gimp), so I have no idea what it says. Personally, I would use a .png or .gif.
...or, better yet, use a Terminal for the upgrade so you can simply copy-and-paste the error messages here.

Precisely how are you upgrading? Are you clicking on something? Using a command? A Live image? Following some instructions?
Please explain in detail. Links are helpful.

---

### Post by Bucky Ball on 2014-12-03
Didn't think it was possible to upgrade via Software Updater from 13.10 anymore, unless you do it like [THIS]("https://help.ubuntu.com/community/EOLUpgrades"). :-k

By the looks of your screen shot (opens in Gimp 'automagically' for me ian) you are doing it, though. So, gets stuck at Libreoffice and that's it for the next ten hours? You are using a cable connection and NOT wireless?

Never a good idea to do an upgrade from one version to another via wireless. If the wireless drops out, it can cause all manner of headaches.

---

### Post by Kymus on 2014-12-03
> **ian-weisser said:**
> An .xcf file isn't the most helpful image format. I don't have anything installed to easily view it (like Gimp), so I have no idea what it says. Personally, I would use a .png or .gif.
...or, better yet, use a Terminal for the upgrade so you can simply copy-and-paste the error messages here.

Precisely how are you upgrading? Are you clicking on something? Using a command? A Live image? Following some instructions?
Please explain in detail. Links are helpful.

My appologies. I edited the screenshot via GIMP and didn't think to change the format. I'll fix that in a moment

---

### Post by Kymus on 2014-12-03
> **Bucky Ball said:**
> Didn't think it was possible to upgrade via Software Updater from 13.10 anymore, unless you do it like [THIS]("https://help.ubuntu.com/community/EOLUpgrades"). :-k

By the looks of your screen shot (opens in Gimp 'automagically' for me ian) you are doing it, though. So, gets stuck at Libreoffice and that's it for the next ten hours? You are using a cable connection and NOT wireless?

Never a good idea to do an upgrade from one version to another via wireless. If the wireless drops out, it can cause all manner of headaches.

That's it for the next 48hrs now :). I am using a wireless connection; not much choice at the moment due to where my computer is situated in the house (an entire floor above the location of the modem and router).

I've been holding off on updating due to paranoia of losing data because last time this happened (the last time I tried to update) not only was the system unstable, but my data was not recoverable. So, I waited for when I had a drive to backup to before updating.

7 years of using Ubuntu as my primary OS and this happens the last two times I try to update >_<;; (edit: though I believe last time the system was a version or more behind as well)

---

### Post by ian-weisser on 2014-12-03
Wireless connections can be fragile; mine have a habit of failing at the worst possible times...as, apparently, have yours.

If you must use wireless, then I might  suggest either 1) Download a Live installer onto a USB stick and upgrade from that, or 2) Add a partition to your hard drive, install to the fresh partition, then copy over your /home data, or 3) Backup your data to external storage before upgrading. Any of these will protect your data, and ensure you have a way to boot in case of another upgrade failure.

Upgrading at night, when fewer people and other interference sources are about, may also be worth a try.

If you have a lot of online accounts, a hard copy of the location/username/password someplace safe may be a good idea...especially if your backups are off in the cloud someplace. Your data is preserved and accessible in case of the need to reinstall.

If upgrading a system that is past end-of-life is becoming a troublesome habit, perhaps the 14.04 LTS release may be appropriate. Supported until 2019.

---

### Post by Kymus on 2014-12-03
> **ian-weisser said:**
> Wireless connections can be fragile; mine have a habit of failing at the worst possible times...as, apparently, have yours.

If you must use wireless, then I might  suggest either 1) Download a Live installer onto a USB stick and upgrade from that, or 2) Add a partition to your hard drive, install to the fresh partition, then copy over your /home data, or 3) Backup your data to external storage before upgrading. Any of these will protect your data, and ensure you have a way to boot in case of another upgrade failure.

Upgrading at night, when fewer people and other interference sources are about, may also be worth a try.

If you have a lot of online accounts, a hard copy of the location/username/password someplace safe may be a good idea...especially if your backups are off in the cloud someplace. Your data is preserved and accessible in case of the need to reinstall.

If upgrading a system that is past end-of-life is becoming a troublesome habit, perhaps the 14.04 LTS release may be appropriate. Supported until 2019.

Thanks for the input. I'll have to stick to USB-based upgrades for now, I suppose.

---

### Post by Kymus on 2014-12-03
Is there a way in which I can possibly prevent system damage at present?

The system is - or seems to be - fully functional at the present. I am very concerned that if I attempt a reboot that what happened last time will re-occur (see the link for more information; it essentially was FUBARed and I had to do a complete drive wipe).

It seems that I can quit the update dialogue. Is it possible to rety the upgrade? Or do I have to reboot the system and see what happens, first?

---

### Post by ian-weisser on 2014-12-03
I would retry the upgrade without rebooting.
It's sticky territory - a failed upgrade is already a situation fraught with risk.
But a retry without rebooting seems unlikely to cause damage.

Er, your data is backed up?

---

### Post by Kymus on 2014-12-07
> **ian-weisser said:**
> I would retry the upgrade without rebooting.
It's sticky territory - a failed upgrade is already a situation fraught with risk.
But a retry without rebooting seems unlikely to cause damage.

Er, your data is backed up?

My data is backed up, thanks for making sure :)

Now.. just to make sure I understand you 100%.... I should exit out of the upgrade, and then re-run an update from the USB, I assume? (suggestions on a source that can walk me through setting up the update on my USB drive?)

---

### Post by ian-weisser on 2014-12-07
Exit out of the upgrade.
Then try re-running the upgrade exactly the way you did before from your normal system (not USB).
If the upgrade fails again, then exit out of the upgrade.

One more try: Open a terminal on your normal system, and run the command 'do-release-upgrade'.
It may fail (it's the same upgrader, just without the pretty bits), but any failure will include important error messages.
Copy-and-paste the complete, exact error messages into here. Stuff before and after, too - context helps a lot.

---

### Post by Kymus on 2014-12-09
I exited the upgrade, ran software updater, and it is not notifying me of any available upgrades (just a flash update). I checked the settings and it was previously set to only notify me of LTS upgrades, so I changed it to all upgrades. Nothing.

Should I try from the terminal now?

---

### Post by ian-weisser on 2014-12-10
Look at the file /etc/update-manager/release-upgrades
The final line of that file should read "Prompt=normal"

If it does, then go ahead and try 'do-release-upgrade' in the terminal.

---

### Post by Kymus on 2014-12-10
***fingers crossed*** I think everything is good.

Ran the update via terminal. Things went smooth. I did notice a few error reports in the process:

> (gtk-update-icon-cache-3.0:10765): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

(gtk-update-icon-cache-3.0:11046): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

(gtk-update-icon-cache-3.0:15517): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

There were strings of text between the errors (this may be a no-brainer, but the terminal is not my strong point). I thought I would copy them down during the update *just incase*.

After the update was finished, I wanted to wait to reboot and just double-check everything locally to make sure everything is backed up. I hit send on a webform and at that point there was a crash. I wasn't able to jot down the error fast enough. I did a REISUB once it seemed like there was no activity and things were stalled. 

After reboot, everything was normal, I got the 14.10 splash screen (a little behind on the update wasn't I?), and then I got a prompt about "an error occured". I wanted to copy and paste the details, but I wasn't able to. It was in regards to X crashing; I assume this is what happened previously.

If everything is still smooth in 48hrs, I'll mark this thread as solved. Much appreciation for the help!

---

