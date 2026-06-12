---
title: "Boot process disables the monitor on Ubuntu 12.04"
date: 2014-12-02
forum: General Help
---

### Post by ineuw on 2014-12-02
At a community center for seniors, I installed Ubuntu 12.04 on an older IBM computer and it worked fine for the past year. Recently the monitor began to blank out intermittently after boot and now it blanks out regularly. But the not monitor nor the video card is the problem.

I managed to log in as the admin and I initiated the Grub customizer to change the kernel, hoping that the older kernel .69 is better than the new update .72. I also generated and placed all the relevant reports to pastebin and the URL's are listed below.

Grub could not save the file and it reported the following:
> 
Please take a look at the command line output below. If you think this is a bug of Grub Customizer, please create one at [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)! Generally Grub Customizer should prevent errors like this.

failed running 'grub-mkconfig -o "/boot/grub/grub.cfg"' output:
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-72-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-72-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-69-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-69-generic-pae
erreur : syntax error.
erreur : Incorrect command.
erreur : syntax error.
erreur : Incorrect command.
erreur : syntax error.
error: line no: 98
Syntax errors are detected in generated GRUB config file. Ensure that there are no errors in /etc/default/grub and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached. done


These are all the documents I generated:
grub.cfg.new: [http://paste.ubuntu.com/9340329/](http://paste.ubuntu.com/9340329/)
boot log: [http://paste.ubuntu.com/9340239/](http://paste.ubuntu.com/9340239/)
Xorg.0.log here: [http://paste.ubuntu.com/9340258/](http://paste.ubuntu.com/9340258/)

and these two successive boot-repair reports.
boot-repair: [http://paste.ubuntu.com/9335221/](http://paste.ubuntu.com/9335221/)
boot-repair: [http://paste.ubuntu.com/9335042/](http://paste.ubuntu.com/9335042/)

---

### Post by oldfred on 2014-12-02
Did you manually change grub or grub scripts or just use grub-customizer?

Grub customizer changes settings and will install its own scripts. If you now have errors I would totally uninstlal grub and reinstall it, But that will clear any changes you may have made with grub customizer.

In Advanced mode of Boot-Repair is a total uninstall reinstall of grub. I would run that. Make sure internet is working as it has to download grub all over again.

Or you can chroot into your system and run the full uninstall & reinstall of grub.

       drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

After chroot, you at least want to run these:

 apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

 # uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

 apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

---

### Post by ineuw on 2014-12-02
> **oldfred said:**
> Did you manually change grub or grub scripts or just use grub-customizer?

Grub customizer changes settings and will install its own scripts. If you now have errors I would totally uninstlal grub and reinstall it, But that will clear any changes you may have made with grub customizer.

In Advanced mode of Boot-Repair is a total uninstall reinstall of grub. I would run that. Make sure internet is working as it has to download grub all over again.



oldfred, thanks for your help. I have the boot-repair on disk as well as installed on the machine. Earlier today, I used the boot-repair disk in advanced mode, just as you recommended above and reinstalled the kernel as well, because I was sure it was damaged. But, it doesn't always boot. Currently I am suspect that the hard drive is the culprit, that it might be wobbling because of its age.

Nevertheless, I will run all your recommended maintenance. Just to mention, after searching, there is a multitude of posts about a very similar problem with Ubuntu relating to blanked out monitors, and I tested the possible recommended solutions, (with and without the grub parameters of nomodeset, acpi=off, in combination and separately, and without any parameters, but it didn't help. One successful boot in five attempts is the best I can get and only if I keep tapping the Enter key. Thanks again

P.S: This is the last report generated by boot repair. [http://paste.ubuntu.com/9344067/](http://paste.ubuntu.com/9344067/)

---

### Post by oldfred on 2014-12-02
Any of the scripts with proxy in the name are from grub customizer.
If you do not purge sda1/etc/grub.d/, you may have new grub files & the old customizer files. 

Normally the blank screen is a video issue. But that is typically with a new install until you install the proprietary drivers.

If concerned about hard drive use Disks(14.04) or Disk Utility(12.04) and the Smart Data. With Disks it now is hidden under the gear icon in upper right corner for more actions. While it can run tests on drive, all I really know is passed or green is good, anything else is time for a new drive. A few bad blocks is not a major concern, but if bad blocks starts growing then it is an issue.

Also sometimes a fsck helps. 

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by ineuw on 2014-12-02
Many thanks for you invaluable info. Your first post's instructions worked like a charm - for about an hour and then it died again. As I suspected, the hard disk "wobbles" and it must be replaced, hopefully someone donates another old PC. I am embarrassed to post the PC's age and CPU. So, I'll mark this solved again, thanks.

---

