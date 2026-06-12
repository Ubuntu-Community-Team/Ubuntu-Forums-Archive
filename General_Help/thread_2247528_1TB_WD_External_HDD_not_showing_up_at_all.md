---
title: "1TB WD External HDD not showing up at all"
date: 2014-10-08
forum: General Help
---

### Post by rakrimes on 2014-10-08
Ok so I am fairly new to linux period and I want to move some of my music from my external HDD to the PC my drive is NTFS and when I plug it in it does not show up anywhere.

I did sudo fdisk -l and it only shows my PC hard drive nothing else I used gparted it does not show up there either. I am at a loss as I am quite new to the linux world.

Any help would be great thank you.

---

### Post by rbmorse on 2014-10-08
Tell us about this external hard drive...bare drive?  In some sort of enclosure?  Portable (aka Passport or MyDrive, etc.)?  How are you are connecting it to the PC....USB?  Firewire? eSATA? Wireless?

---

### Post by rakrimes on 2014-10-08
Its a WD passport and connecting via USB it is a 3.0 USB as well and It does not matter if I plug it into my USB 3.0 port or one of my 2.0 Ports it still does not show up. Also it is a portable one.

---

### Post by papibe on 2014-10-08
Hi rakrimes. Welcome to the forum ):P

Is it new?

Some WD drives comes with some protection software that can only be disable on Windows. Once that is done, you can use it anywhere.

Just a thought.
Regards.

---

### Post by rakrimes on 2014-10-08
No I've had it for about two years now its no where near new. I formatted to NTFS on windows a few months ago and other than that its just been a place to keep all music, videos, program exes etc... now it just will not show up under anything here on lubuntu.

---

### Post by matt_symes on 2014-10-08
Hi

Unplug the drive from the computer.

Open a terminal and type

```
tail -f /var/log/syslog
```

It will start tailing your system log for you.

Plug the drive back in and wait 10 seconds or so.

Copy all and any new text displayed in the terminal after you plugged the drive in, into your next post.

You can copy and paste from the terminal by highlighting the text->right click->copy and paste into you next post.

Paste the text between code tags. Look for the **#** button above where you type the text.

Kind regards

---

### Post by yancek on 2014-10-08
What does 'anywhere' mean?  Usually external media will show under the /media directory.  If you are using 14.04 (you don't indicate what you are using?) look under /media/username.  Replace username with whatever your actual user name if.  You should be able to access it in one of the methods.

---

### Post by rakrimes on 2014-10-08
> **matt_symes said:**
> Hi

Unplug the drive from the computer.

Open a terminal and type

```
tail -f /var/log/syslog
```

It will start tailing your system log for you.

Plug the drive back in and wait 10 seconds or so.

Copy all and any new text displayed in the terminal after you plugged the drive in, into your next post.

You can copy and paste from the terminal by highlighting the text->right click->copy and paste into you next post.

Paste the text between code tags. Look for the **#** button above where you type the text.

Kind regards



Ok I did this and I will paste the results below and as for the other post below yours I actually just now installed ubuntu 14.04, didnt really like lubuntu anyway here are the results

Oct  8 19:05:24 Icarion anacron[957]: Job `cron.daily' terminated (mailing output)
Oct  8 19:05:24 Icarion anacron[957]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Oct  8 19:06:44 Icarion wpa_supplicant[787]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct  8 19:06:45 Icarion wpa_supplicant[787]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Oct  8 19:07:31 Icarion kernel: [  502.656048] usb 5-2: new high-speed USB device number 2 using xhci_hcd
Oct  8 19:07:32 Icarion kernel: [  502.850233] usb 5-2: Device not responding to set address.
Oct  8 19:07:32 Icarion kernel: [  503.051719] usb 5-2: Device not responding to set address.
Oct  8 19:07:32 Icarion kernel: [  503.255592] usb 5-2: device not accepting address 2, error -71
Oct  8 19:07:39 Icarion upstart-udev-bridge[284]: Disconnected from Upstart
Oct  8 19:07:39 Icarion upstart-socket-bridge[671]: Disconnected from Upstart
Oct  8 19:07:40 Icarion upstart-socket-bridge[18796]: Disconnected from Upstart
Oct  8 19:07:40 Icarion upstart-udev-bridge[18789]: Disconnected from Upstart
Oct  8 19:07:51 Icarion dbus[541]: [system] Reloaded configuration

---

### Post by rakrimes on 2014-10-08
> **yancek said:**
> What does 'anywhere' mean?  Usually external media will show under the /media directory.  If you are using 14.04 (you don't indicate what you are using?) look under /media/username.  Replace username with whatever your actual user name if.  You should be able to access it in one of the methods.


Yea literally anywhere on the PC my HDD does not show up I checked where you said before making this post and nope not there either, also I was using lubuntu 14.04.1 now I am on Ubuntu 14.04 and still same problem above I posted results of the terminal tail log

---

### Post by leclerc65 on 2014-10-08
If all else fails, plug it into a Windows computer then run a Checkdisk.

---

### Post by rakrimes on 2014-10-08
> **leclerc65 said:**
> If all else fails, plug it into a Windows computer then run a Checkdisk.

Yea that will be the next step right now it is in my windows PC and I'm transferring all my files off it and am going to reformat to NTFS and see what happens. I also suspect it could be the drive as every now and again I have to plug and unplug a few times till windows sees it so maybe its time for a new one.

---

