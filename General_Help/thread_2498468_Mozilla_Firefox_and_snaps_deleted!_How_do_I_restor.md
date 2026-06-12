---
title: "Mozilla Firefox and snaps deleted! How do I restore?"
date: 2024-06-14
forum: General Help
---

### Post by hennmann on 2024-06-14
I have 22.04 and also have VPN installed and lately the app quit working. My subscription was renewed in May and a new version was also installed and during all of this something went wrong. It was defective with App not found and Renew Subscription being displayed so I contacted the VPN provider for assistance and keep in mind Firefox was otherwise working perfectly fine with just the VPN unable to work. On Windows, the app works independently, whereas on Linux it is as an extension on Firefox.
Before I contacted them, I uninstalled VPN,  including browser extension, downloaded the current version, reinstalled the browser extension,  and reinstalled VPN as well, and this VPN opens as a white blank window, the shape of the functioning app and then crashes, again with same nag and the extension has a red X through it as well. I uninstalled VPN and extension twice including downloading the VPN software again. The VPN tech support told me to enter "sudo snap remove firefox" in terminal and my question was WHY? I told him it sounded like a shotgun approach or more like a nuclear bomb!! Anyway like a fool, I entered it and there goes my Firefox. 
After this the commands he gave seemed useless and after several hours or should I say 1:00 am in the morning this so called tech support said he didn't have the right answers. Later on another tech support rep gave commands that went through the motions of installing but Firefox doesn't appear in apps.
Given all of this, what steps do I take to reinstall Firefox and snaps? Should I download the latest Ubuntu and make a bootable USB installation media as well in case it is needed?
Later on another tech support rep told me to enter:

sudo add-apt-repository ppa:mozillateam/ppa

"Next, after the Firefox package priority to insure the PPA/deb/apt version of Firefox is preferred. This can be done using slither of code from FosTips (copy and paste it whole, not line by line)"
 
echo ' Package: * Pin: release o=LP-PPA-mozillateam Pin-Priority: 1001 ' | sudo tee/etc/apt/preferences.d/mozilla-firefox

"For future Firefox upgrades to be installed automatically, run this command on the terminal:"

echo 'Unattended-Upgrade::Allowed-Origins::"LP-PPA-mozillateam:${distro_codename}":' | sudo tee/etc/apt/apt.config.d/51unattended-upgrades-firefox

"Finally, install Firefox via apt by running this command:"

sudo apt install firefox

It now went through the motions of installing and ended at the cursor blinking. This is where we left off and currently I'm creating this thread on my Windows partition on same computer. If need be I can go back into Ubuntu and using a smart phone or my netbook refer to commands OR copy. paste in an email and send it to myself because my email client on Ubuntu is still working. Yes my 22.04 Jelly Fish is fully updated as well.

---

### Post by hennmann on 2024-06-14
After hours of searching on not only how to install Firefox, including snaps I found a command that worked!!
$ sudo snap install firefox
after I hit enter it downloaded and indicated
firefox 127.0-2.1 from Mozilla&#10003; installed

Blip the icon appeared and I'm using Firefox on my Ubuntu to indicate what I had to do.
Of course my VPN is still complaining 
APP Not Found and install desktop app.

---

### Post by TheFu on 2024-06-15
This is an example of why using a volume manager that supports snapshots can make a bad day into a minor issue. Further, once a snapshot is taken, you can get an excellent backup from the snapshot while the system keeps running at full speed.

Nothing replaces good backups, taken just before they are needed, but we never know when that might be, so daily, versioned, backups are the best answer that can be suggested.  With volume manager snapshots, it is possible to take multiple snapshots a day to have even more restore points for next to ZERO overhead, just be certain to delete older snapshots before storage is all marked as used.

Don't confuse a _volume manager snapshot_ with what many backup tools call a _snapshot_.  They are not the same.  LVM, BRTFS, ZFS are the only tools that provide volume manager snapshots to my knowledge.

---

