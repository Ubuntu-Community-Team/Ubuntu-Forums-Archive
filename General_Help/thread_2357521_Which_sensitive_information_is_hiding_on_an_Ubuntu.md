---
title: "Which sensitive information is hiding on an Ubuntu system?"
date: 2017-04-03
forum: General Help
---

### Post by knahrvorn on 2017-04-03
For a private project of mine, I'm downloading the Ubuntu Mate image for Raspberry Pi 3, writing it to my SD card, booting it, installing and configuring some extra software and then I plan to do a new disk image file and make it available for download. All this is no problem, which is why I didn't post this to somewhere Raspberry Pi specific or Mate specific. My question is the following:

What do I need to consider, security wise? Is any sensitive information automatically saved in files around the system that I need to remove before making a disk image file?

What I already do is:
- sudo apt update && sudo apt upgrade && sudo apt autoremove --purge && sudo apt clean && sudo apt autoclean # mostly in order to make compressed image file as small as possible
- use a generic password, and also "sudo chage -d 0 pinode" to force new password
- sudo rm /etc/ssh/ssh_host_* && sudo dpkg-reconfigure openssh-server
- rm -rf ~/.ssh
- rm /home/pi/.bash_history
- sudo sfill -llvz / && sudo sfill -llvz /boot # fill empty space with zeros using sfill from secure-delete package

I have not connected to anything using wifi (only Ethernet), but maybe the system still saves info on wifi networks it has detected?

Anything else I need to consider?

---

### Post by Paddy Landau on 2017-04-03
May I suggest that you create an OEM-style installation disk? In other words, you create a Live ISO just like (say) Ubuntu Mate, but with your customisations.

To do this:

[LIST=1]
[*]Boot your installation disk. Press Shift to get to the boot menu.
[*]Choose F4 and select OEM Install.
[*]Install. It will ask for a temporary user name and password.
[*]Boot into the system. Tailor to your heart's content.
[*]Once working, open "Prepare for shipping to end user".
[*]Don't boot into the system again!
[/LIST]
Create a disk image as your ISO.

I haven't done this for quite a while, so one or two details might be a little out of date; please test it before doing it properly.

---

### Post by knahrvorn on 2017-04-03
> **Paddy Landau said:**
> May I suggest that you create an OEM-style installation disk? In other words, you create a Live ISO just like (say) Ubuntu Mate, but with your customisations.

Oh, I didn't know about this; it looks very promising! I'm not sure it will work with the Raspberry Pi where you don't install off a Live ISO/cdrom/usbdisk but instead transfer a .img directly to the SD card using e.g. dd. Anyway, I'll definitely look into this, if not anything else it is very nice to know in the future. Thanks!

---

### Post by Paddy Landau on 2017-04-03
I don't know how to create an .img from an ISO, but I'm sure that it's possible.

I am curious to know if it works on the Raspberry Pi &#8212; please let us know (and if it does, [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so others can find it). Thanks!

---

### Post by knahrvorn on 2017-04-03
> **Paddy Landau said:**
> I don't know how to create an .img from an ISO, but I'm sure that it's possible.

Converting an ISO to a .img wouldn't be a problem. Off the top of my head, just mount the ISO and then use dd (or ddrescue) to read the contents of the mounted ISO byte-by-byte and spit out the contents to a .img file.

BUT, I don't think it is relevant here, since installing Ubuntu on a Raspberry Pi does not involve an ISO or an installation process in the normal way. You simply download the .img (which is a mirror of an already installed system) and write it to your SD card. Then you insert the SD card into your Raspberry Pi and boot off it, and except for setting up username and password, you have a fully functioning system by then.

So, the first point in your list "Boot your installation disk. Press Shift to get to the boot menu" does not seem to work, since there is no installation disk. I tried activating a boot menu when booting the system normally to see whether that included an option to make an OEM-like system, but that sadly doesn't seem to be possible.

So, I'm afraid we're back to my original question:

> What do I need to consider, security wise? Is any sensitive information automatically saved in files around the system that I need to remove before making a disk image file?

What I already do is:
- sudo apt update && sudo apt upgrade && sudo apt autoremove --purge && sudo apt clean && sudo apt autoclean # mostly in order to make compressed image file as small as possible
- use a generic password, and also "sudo chage -d 0 pinode" to force new password
- sudo rm /etc/ssh/ssh_host_* && sudo dpkg-reconfigure openssh-server
- rm -rf ~/.ssh
- rm /home/pi/.bash_history
- sudo sfill -llvz / && sudo sfill -llvz /boot # fill empty space with zeros using sfill from secure-delete package

I have not connected to anything using wifi (only Ethernet), but maybe the system still saves info on wifi networks it has detected?

Anything else I need to consider? 

---

### Post by Paddy Landau on 2017-04-04
> **knahrvorn said:**
> So, the first point in your list "Boot your installation disk. Press Shift to get to the boot menu" does not seem to work, since there is no installation disk.
I think that I have misunderstood, because I thought that you were installing the system elsewhere and then copying the image to the Raspberry Pi. Sorry, that is the best way that I know how to do this.

Regarding your original question:

The only places where I am aware of non-system information being stored are:

[LIST]
[*]The home folder, in your case [FONT=lucida console]/home/pi[/FONT]. There will be several possible folders, including [FONT=lucida console].cache[/FONT] and [FONT=lucida console].config[/FONT]. If you can remove the entire folder rather than just single items, that surely will be better. When the new user boots, Ubuntu will recreate the home folder afresh.
[*]Folder [FONT=lucida console]/tmp[/FONT].
[*]Unused areas on the disk, which is why you are using zero-fill. However, from what I understand about SSDs and their internal (hidden) mechanism, doing this might not achieve quite what you want. But, I could be wrong on this; I'm not an expert.
[/LIST]
The ideal way would be to install, using the method that I suggested, onto another machine (a virtual machine with [Virtual Box]("https://www.virtualbox.org/") would do the job perfectly, but don't install Guest Additions into the machine); once complete, create an ISO or IMG from the installation; and transfer that image to your Raspberry Pi.

By the way, [FONT=lucida console]autoclean[/FONT] is a subset of [FONT=lucida console]clean[/FONT], so you don't need both; just the latter one will do.

---

### Post by knahrvorn on 2017-04-06
> **Paddy Landau said:**
> I think that I have misunderstood, because I thought that you were installing the system elsewhere and then copying the image to the Raspberry Pi. Sorry, that is the best way that I know how to do this.

No problem. I see why that suggestion came to your mind; it would have been an obvious and preferred solution, hadn't it been for the Pi's rather special ways of installing the system.

> Regarding your original question:

The only places where I am aware of non-system information being stored are:

[LIST]
[*]The home folder, in your case [FONT=lucida console]/home/pi[/FONT]. There will be several possible folders, including [FONT=lucida console].cache[/FONT] and [FONT=lucida console].config[/FONT]. If you can remove the entire folder rather than just single items, that surely will be better. When the new user boots, Ubuntu will recreate the home folder afresh.
[*]Folder [FONT=lucida console]/tmp[/FONT].[/list]

Thanks for your suggestions. There might indeed be something in some of these, so I'd better remove those as well.

> [list][*]Unused areas on the disk, which is why you are using zero-fill. However, from what I understand about SSDs and their internal (hidden) mechanism, doing this might not achieve quite what you want. But, I could be wrong on this; I'm not an expert.
[/LIST]

The Pi in fact boots from an SD card, not an SSD, but as I understand it might have the same functionality where at any given time you can't be 100% sure whether some data has been physically written to disk or is still residing in cache, so thank you for mentioning this. Anyway, without being absolutely certain (please, correct me if I'm mistaken), I think I am safe here because:
1. I am arranging all data, then shutting the system down, whereby any data in cache should be written to disk, and only then (now with the SD card in another physical computer) will I make a mirror image of the SD card.
2. I am not letting the physical SD card in the hands of others, only a mirror image of it (.img file). When creating the mirror image, the *dd* tool will only read the apparent data, whether it has been physically written or not, just like any other regular program. It does not also read and store the old data that might still be left physically on the card; that would require the file to contain more data than its size, which is obviously not possible.

> The ideal way would be to install, using the method that I suggested, onto another machine (a virtual machine with [Virtual Box]("https://www.virtualbox.org/") would do the job perfectly, but don't install Guest Additions into the machine); once complete, create an ISO or IMG from the installation; and transfer that image to your Raspberry Pi.

Yes, I agree. The Pi uses the ARM architecture instead of i386 or amd64, though, and there's also something different with the boot procedure as far as I'm being told, so that wouldn't work, unless that other machine was also a Raspberry Pi. Maybe VirtualBox run from a Pi, though, but that wouldn't make any difference than from a physical Pi, if it's even possible. I'll stick to my current method -- thanks for the tips!

> By the way, [FONT=lucida console]autoclean[/FONT] is a subset of [FONT=lucida console]clean[/FONT], so you don't need both; just the latter one will do.

Oh, thanks! I was worried I would need more steps; now I'm getting less :-)

---

### Post by Paddy Landau on 2017-04-06
> **knahrvorn said:**
> The Pi in fact boots from an SD card, not an SSD…
I think that the internal workings of an SD and SSD are the same, aren't they, at least for this context? Anyway, the way you describe your method, I feel confident that you are safe.
> **knahrvorn said:**
> The Pi uses the ARM architecture instead of i386 or amd64…
Ah. I know next-to-nothing about this. I wonder if a virtual machine would allow you to emulate ARM, in which case you can do that to create your image?

Good luck; I hope that it all works out well.

---

