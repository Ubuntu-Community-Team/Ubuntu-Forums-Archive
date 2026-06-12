---
title: "Package System Broken after 22.10 Upgrade from 22.04 (libparted2 / libparted)"
date: 2022-12-05
forum: General Help
---

### Post by johnsweeney85 on 2022-12-05
[INDENT]After upgrade to 22.10, the upgrade completed with errors.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291375&stc=1[/IMG]

MESSAGE FROM SOFTWARE UPDATER

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
The following packages have unmet dependencies:

parted: Depends: libparted2 (= 3.4-2build1) but 3.5-2 is installed
Depends: libreadline8 (>= 6.0) but 8.2-1 is installed
Depends: libtinfo6 (>= 6) but 6.3+20220423-2 is installed


I have tried all the standard, clean, autoclean, autoremove, force install via APT and Aptitude.
I have rebooted in safemode, used dpkg to configure all and get the same error again.


TAIL END OF main.log.partial from /var/log/dist-upgrade


2022-12-05 11:57:59,686 DEBUG Upgradable, but held- back: grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed
2022-12-05 11:57:59,686 DEBUG Remove:
2022-12-05 11:57:59,686 DEBUG Install:
2022-12-05 11:57:59,686 DEBUG Upgrade: parted
2022-12-05 11:57:59,688 DEBUG apt btrfs snapshots supported: False
2022-12-05 11:57:59,711 DEBUG dir '/var' needs '0' of '<DistUpgrade.DistUpgradeCache.MyCache.checkFreeSp ace.<locals>.FreeSpace object at 0x7fca568ce590>' (375152692144.000000)
2022-12-05 11:57:59,711 DEBUG dir '/usr' needs '52428800' of '<DistUpgrade.DistUpgradeCache.MyCache.checkFreeSp ace.<locals>.FreeSpace object at 0x7fca568ce590>' (375152692144.000000)
2022-12-05 11:57:59,711 DEBUG dir '/boot' needs '178507501.2' of '<DistUpgrade.DistUpgradeCache.MyCache.checkFreeSp ace.<locals>.FreeSpace object at 0x7fca568ce590>' (375100263344.000000)
2022-12-05 11:57:59,711 DEBUG dir '/tmp' needs '5242880' of '<DistUpgrade.DistUpgradeCache.MyCache.checkFreeSp ace.<locals>.FreeSpace object at 0x7fca568ce590>' (374921755842.799988)
2022-12-05 11:57:59,711 DEBUG dir '/' needs '10485760' of '<DistUpgrade.DistUpgradeCache.MyCache.checkFreeSp ace.<locals>.FreeSpace object at 0x7fca568ce590>' (374916512962.799988)
2022-12-05 11:57:59,711 DEBUG dir '/tmp' needs '0.0' of '<DistUpgrade.DistUpgradeCache.MyCache.checkFreeSp ace.<locals>.FreeSpace object at 0x7fca568ce590>' (374906027202.799988)
2022-12-05 11:57:59,711 DEBUG dir '/usr' needs '0.0' of '<DistUpgrade.DistUpgradeCache.MyCache.checkFreeSp ace.<locals>.FreeSpace object at 0x7fca568ce590>' (374906027202.799988)
2022-12-05 11:57:59,711 DEBUG Found writable ESP /dev/nvme0n1p1 /boot/efi vfat rw,relatime,fmask=0077,dmask=0077,codepage=437,ioc harset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
2022-12-05 11:58:17,304 INFO cache.commit()
2022-12-05 11:58:26,443 ERROR got an error from dpkg for pkg: '/var/cache/apt/archives/parted_3.5-2_amd64.deb': 'new parted package pre-installation script subprocess returned error exit status 1'
2022-12-05 11:58:26,444 DEBUG running apport_pkgfailure() parted: new parted package pre-installation script subprocess returned error exit status 1
2022-12-05 11:58:26,779 ERROR Exception during pm.DoInstall()
Traceback (most recent call last):
File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeView.py", line 220, in run
res = pm.do_install(self.writefd)
apt_pkg.Error: E:Sub-process /usr/bin/dpkg returned an error code (1)
2022-12-05 11:58:26,845 ERROR SystemError from cache.commit(): installArchives() failed
2022-12-05 11:58:26,845 ERROR found exception: 'E:Sub-process /usr/bin/dpkg returned an error code (1)'

TAIL END OFCode:
sudo apt --fix broken install
dpkg: warning: files list file for package 'node-has-unicode' missing; assuming package has no files currently installed
(Reading database ... 289588 files and directories currently installed.)
Preparing to unpack .../parted_3.5-2_amd64.deb ...
dpkg-query: warning: files list file for package 'parted' missing; assuming package has no files currently installed
dpkg-maintscript-helper: error: file '/usr/share/doc/parted' not owned by package 'parted:amd64'
dpkg-query: warning: files list file for package 'parted' missing; assuming package has no files currently installed
dpkg-maintscript-helper: error: file '/usr/share/doc/parted/changelog.Debian.gz' not owned by package 'parted:amd64'
dpkg-query: warning: files list file for package 'parted' missing; assuming package has no files currently installed
dpkg-maintscript-helper: error: file '/usr/share/doc/parted/copyright' not owned by package 'parted:amd64'
dpkg-maintscript-helper: error: directory '/usr/share/doc/parted' contains files not owned by package parted:amd64, cannot switch to symlink
dpkg: error processing archive /var/cache/apt/archives/parted_3.5-2_amd64.deb (--unpack):
new parted package pre-installation script subprocess returned error exit status 1
Errors were encountered while processing:
/var/cache/apt/archives/parted_3.5-2_amd64.deb
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)




Thanks in advance for your help[/INDENT]

---

### Post by Bashing-om on 2022-12-05
johnsweeney85; Hey -

As an alternate thought. remove-purge gparted from that install ! 

Having gparted installed is a hazard; might lead to a stupid move, There is a reason why the utility is removed during the install process.

gparted remains as available on the live environment - that prevents attempting to work on a running file system.

[INDENT]just my 2 cents worth
[/INDENT]

---

