---
title: "can't reboot my headless pc after grub-efi update (beta2-9ubuntu1.3)"
date: 2015-07-08
forum: General Help
---

### Post by hefty2 on 2015-07-08
Hallo community,

today I installed the following packets:
grub-common (2.02~beta2-9ubuntu1.2) to 2.02~beta2-9ubuntu1.3
grub-efi-amd64 (2.02~beta2-9ubuntu1.2) to 2.02~beta2-9ubuntu1.3
grub-efi-amd64-bin (2.02~beta2-9ubuntu1.2) to 2.02~beta2-9ubuntu1.3
grub-efi-amd64-signed (1.34.3+2.02~beta2-9ubuntu1.2) to 1.34.4+2.02~beta2-9ubuntu1.3
grub2-common (2.02~beta2-9ubuntu1.2) to 2.02~beta2-9ubuntu1.3

After that I rebooted my headless pc with no success. I can't exactly say what's going wrong but I can't connect to ssh.
Then I plugged-in a monitor and reboot again. With a monitor everything works as expected. The OS and all services are starting on boot.

Btw: In the [changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/g/grub2/grub2_2.02~beta2-9ubuntu1.3/changelog") they say:
> grub2 (2.02~beta2-9ubuntu1.3) trusty; urgency=medium
* Do not hang headless servers indefinitely on boot after edge case power     failure timing (LP: #1443735). Instead, time out after 30 seconds and boot     anyway, including on non-headless systems.

My question is:
How can I downgrade to Version 2.02~beta2-9ubuntu1.2, so that I can boot my pc in headless mode again? 
Or maybe somebody knows how to boot with version 1.3 (in headless mode of course)?

To downgrade I tried:
```
sudo apt-get install grub-efi-amd64=2.02~beta2-9ubuntu1.2
```
but with no success:
```
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
E: Version »2.02~beta2-9ubuntu1.2« für »grub-efi-amd64« konnte nicht gefunden werden.
```

Thanks for your help!

PC: Intel x64 with UEFI (secureboot is disabled)
OS: Linux Mint 17.1 Xfce (Ubuntu 14.04 LTS)

---

### Post by oldfred on 2015-07-08
Supposedly the update was to fix your exact issue?

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1443735](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1443735)

---

### Post by hefty2 on 2015-07-08
I think the update apply exactly to fix a problem caused by rebooting after a power     failure.
Maybe the update fixed a bug and caused another?

Although I played around with the grub option GRUB_RECORDFAIL_TIMEOUT mentioned in the bug report. But without success.

So far I couldn't find a point in your "UEFI tips" that describes my problem.
Do you think it is an option to run Boot-Repair? Maybe I give it a try.

Because there is[ no investigation by the Technical Board]("https://answers.launchpad.net/ubuntu/+source/grub2/+question/269021"), I think to downgrade is the only proper solution.
But I don't know how to downgrade. Nor where to download the grub package in version 2.02~beta2-9ubuntu1.2?
Can somebody provide a link?

Right now my only idea is to reinstall the hole OS and holding the grub version 2.02~beta2-9ubuntu1.2. But I don't like the idea.

---

### Post by oldfred on 2015-07-08
The UEFI tips are just in my signature for those with UEFI. And is really only for desktops as I do not know servers.

I know Boot-Repair often does a full purge & reinstall of grub to fix some errors or convert from BIOS to UEFI.
You may be able to fully uninstall grub and be specific about reinstalling a version? Never tried that.

       # kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)
# HOWTO: Purge and Reinstall Grub 2 from the live-CD/DVD/USB - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

   # purge old and reinstall new to sda for BIOS
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common

If UEFI
 sudo apt-get purge -y --force-yes grub*-common shim-signed linux-signed*
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
[http://askubuntu.com/questions/440024/boot-repair-grub-is-still-present-please-try-again-message-is-displayed-whi](http://askubuntu.com/questions/440024/boot-repair-grub-is-still-present-please-try-again-message-is-displayed-whi)
Not sure if then on install command above you can specify version, not most current in repository which would be default.

---

### Post by hefty2 on 2015-07-09
Hallo oldfred, thanks for your reply.

By now I run Boot-Repair (2 times with different options) but without the desired result.

Afterwards I deinstalled the 5 packages I listed in my first post and reinstalled the version 2.02~beta2-9ubuntu1.2 of these packages (found [here]("https://launchpad.net/ubuntu/+source/grub2/2.02~beta2-9ubuntu1.2")).
Furthermore I replaced the /etc/default/grub by a backup-file from yesterday. So I'm sure I use a configuration that worked for me in the past.
Then I run ```
update-grub
``` and booted without a display pluged-in, to test the downgrade. But it ends up with the same problem and the same result. 

But I'm not sure if this is enough to reinstall/reconfigure grub. Maybe I have to do some more configuration?
For example run ```
grub-install --recheck
```? But I don't think so, because grub boots the correct partition, when a display is pluged-in.

So when the downgrade was successful, maybe the update to grub 2.02~beta2-9ubuntu1.3 didn't cause the problem!? 
But I promise: Only ten minutes before I updated to version 2.02~beta2-9ubuntu1.3 I did a reboot by ssh and everything worked like a charm.

Do you (or anybody else) have an idea what I could test next?

---

### Post by hefty2 on 2015-07-09
Ok, now I'm able to boot my pc in headless mode again.
The solution for me was to deinstall grub/grub2 and install [rEFInd]("http://www.rodsbooks.com/refind/"), a alternative Boot Manager.

---

### Post by oldfred on 2015-07-09
I thought rEFInd was just a boot manager or menu, & you normally still used grub as boot loader.

But with UEFI, there are other ways to boot.

I understand one other way was to use gummiboot, but that was just discontinued and spun into systemd. 
So is rEFInd directly booting using systemd as 15.04 now uses that?

---

### Post by hefty2 on 2015-07-09
I think so. The web page say that it is a graphical menu for booting EFISTUB kernels. But I'm not familiar with EFISTUB.
I know it is possible to configure to load a EFISTUB kernel without using a boot manager. But the articles I found were too complicated.
With rEFInd you only have to install the deg file. That's it.
I only used grub2, because it came along with Linux Mint / Ubuntu setup.

Btw: I think the main problem is my UEFI-Firmware by American Megatrends. When I set some advanced boot options in the rEFInd-config, my system also doesn't boot in headless mode. But with the default rEFInd options it works. (I only increase the menu-timeout to 2sec.)

---

### Post by oldfred on 2015-07-09
Good to know, thanks.

I have been planning on trying rEFInd in one of my installs.

---

