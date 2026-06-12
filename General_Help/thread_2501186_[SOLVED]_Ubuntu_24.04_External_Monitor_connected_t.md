---
title: "[SOLVED] Ubuntu 24.04 External Monitor connected to DELL WD19TB Not Receiving Signals"
date: 2024-09-26
forum: General Help
---

### Post by hbingham on 2024-09-26
Prior to upgrading to Ubuntu 24 my external monitor was receiving signals from my laptop which was connected to the external monitor via USBC via a DELL WD19TB docking station.

Once I upgraded, the monitor stopped receiving signals. I spent a lot of time debugging nvidia drivers, nvidia-xconfig (when I run this command, my laptop freezes at startup) and jumping down a lot of rabbit holes.

Eventually I backed up my laptop and did fresh install of Ubuntu 24 and even this did not work. After the fresh install, I checked the Firmware Updater app and updated the firmware of the dock. After a reboot, my external monitor started to receive signal.

And then I restored from the backup and the issue reappeared - no connection received by external monitor. The firmware was still updated per the Firmware Updater app.

After the restore, I updated the "/etc/default/grub" file and changed the GRUB_CMDLINE_LINUX_DEFAULT to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"

(This disabled the power-saving feature that can "autosuspend" idle USB devices)

Then I ran 'sudo update-grub', rebooted, and the external monitor worked again! Hope this helps some people.

[EDIT FOLLOWS] My laptop then was suspended and I had disconnected it from the dell dock. Upon logging in again and reconnecting the dock, I was not sending signals to the external monitor again.

I proceeded to run 

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo ubuntu-drivers autoinstall
reboot

This had caused a new nvidia driver to get downloaded and installed, upgrading me from 550 to 560. However, still no signal sent to external monitor.

I proceeded to force all usb connections to be powered ON by default:

for i in /sys/bus/usb/devices/*/power/control; do echo on | sudo tee $i; done

Still no success.

Since I had added that new PPA repository and got new drivers, I decided to:

sudo apt update
sudo apt upgrade
sudo apt autoremove

This installed some more updates and removed the old 550 driver. The external monitor connection immediately worked after this. I may have rebooted as well but don't think I needed to.

---

