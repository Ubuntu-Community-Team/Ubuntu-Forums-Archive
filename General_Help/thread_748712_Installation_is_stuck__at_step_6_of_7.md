---
title: "Installation is stuck  at step 6 of 7"
date: 2008-04-07
forum: General Help
---

### Post by Fatal Equinox on 2008-04-07
Hello,

I am using wubi beta which in turn is installing the 8.04 beta. I got to the point where I needed to restart to apply changes and it loaded up properly and i could choose from windows and Unbuntu. When i get back into unbuntu I get step 6 of 7 in the installation which is 'Migrate Documents and Settings' It gives me the option to select my windows account but the option to go forward is greyed out and can't be clicked. Even after waiting for about 45 minutes the option remains grey. I don't want to hit cancel(again), I know for a fact that if I do ubuntuu will work perfectly fine, i just wont beable to save my changes while using ubuntuu and will have to do this again every time i start up ubuntuu... any insight would be great. Thank you :popcorn:

---

### Post by ago on 2008-04-07
can you post c:\ubuntu\install\custom-installation\preseed.cfg (remove the password)

---

### Post by Fatal Equinox on 2008-04-07
> **ago said:**
> can you post c:\ubuntu\install\custom-installation\preseed.cfg (remove the password)

Ok sorry for the wait.... here is the required literature 


## LOCALE

# Locale sets language and country.

d-i debian-installer/locale string en_US.UTF-8



## KEYBOARD

# Keyboard selection.

# d-i console-setup/modelcode string pc104

d-i console-setup/layoutcode string us

# To select a variant of the selected layout (if you leave this out, the

# basic form of the layout will be used):

#d-i console-setup/variantcode string dvorak



#d-i console-tools/archs select at

#d-i console-keymaps-at/keymap select us



## NETWORKING

# netcfg will choose an interface that has link if possible. This makes it

# skip displaying a list if there is more than one interface.

d-i netcfg/choose_interface select auto

# To pick a particular interface instead:

#d-i netcfg/choose_interface select eth1

# If you have a slow dhcp server and the installer times out waiting for

# it, this might be useful.

#d-i netcfg/dhcp_timeout string 60

# If you prefer to configure the network manually, uncomment this line and

# the static network configuration below.

#d-i netcfg/disable_dhcp boolean true

# If you want the preconfiguration file to work on systems both with and

# without a dhcp server, uncomment these lines and the static network

# configuration below.

d-i netcfg/dhcp_failed note

d-i netcfg/dhcp_options select Do not configure the network at this time

# Static network configuration.

# d-i netcfg/get_nameservers string 192.168.1.1

# d-i netcfg/get_ipaddress string 192.168.1.42

# d-i netcfg/get_netmask string 255.255.255.0

# d-i netcfg/get_gateway string 192.168.1.1

# d-i netcfg/confirm_static boolean true

# Any hostname and domain names assigned from dhcp take precedence over

# values set here. However, setting the values still prevents the questions

# from being shown, even if values come from dhcp.

d-i netcfg/get_hostname string ubuntu

d-i netcfg/get_domain string ubuntu-domain

# Disable that annoying WEP key dialog.

d-i netcfg/wireless_essid string essid

d-i netcfg/wireless_wep string

# The wacky dhcp hostname that some ISPs use as a password of sorts.

#d-i netcfg/dhcp_hostname string radish



## UBIQUITY

ubiquity	ubiquity/summary	note

ubiquity	ubiquity/reboot boolean true

ubiquity    ubiquity/success_command string [ -x /custom-installation/hooks/success-command.sh ] && /custom-installation/hooks/success-command.sh 

ubiquity    ubiquity/failure_command string [ -x /custom-installation/hooks/failure-command.sh ] && /custom-installation/hooks/failure-command.sh 


## SKIP Security-Update-Error

d-i apt-setup/security-updates-failed note



## MIRRORS

#~ d-i mirror/country string enter information manually

#~ d-i mirror/http/hostname string archive.ubuntu.com

#~ d-i mirror/http/directory string /ubuntu

d-i mirror/http/proxy string



## SUITE

# Suite to install.

d-i mirror/suite string hardy

# Suite to use for loading installer components (optional).

#d-i mirror/udeb/suite string edgy



## PARTITIONING

# If the system has free space you can choose to only partition that space.

# Note: this must be preseeded with a localized (translated) value.

#d-i partman-auto/init_automatically_partition \

#      select Use the largest continuous free space

# Alternatively, you can specify a disk to partition. The device name can

# be given in either devfs or traditional non-devfs format.

# For example, to use the first SCSI hard disk:

#d-i partman-auto/disk string /dev/sda

# Or, if you want to use LVM:

#d-i partman-auto-lvm/disk string /dev/sda

# You can choose from any of the predefined partitioning recipes.

# Note: this must be preseeded with a localized (translated) value.

##

#d-i partman-auto/choose_recipe \

#       select All files in one partition (recommended for new users)

#d-i partman-auto/choose_recipe \

#       select Separate /home partition

#d-i partman-auto/choose_recipe \

#       select Separate /home, /usr, /var, and /tmp partitions

# Or provide a recipe of your own...

# The recipe format is documented in the file devel/partman-auto-recipe.txt.

# If you have a way to get a recipe file into the d-i environment, you can

# just point at it.

#d-i partman-auto/expert_recipe_file string /hd-media/recipe

# If not, you can put an entire recipe the preconfiguration file in one

# (logical) line. This example creates a small /boot partition, suitable

# swap, and uses the rest of the space for the root partition:

#LoopInstallFolder=/ubuntu/disks

d-i partman-auto/disk string LIDISK

d-i partman-auto/method string loop

d-i partman-auto-loop/partition string LIPARTITION

d-i partman-auto-loop/recipe string   \

  /ubuntu/disks/root.disk 3000 29000 29000 ext3 method{ format } format{ } use_filesystem{ } filesystem{ ext3 } mountpoint{ / } . \

  /ubuntu/disks/swap.disk 100 1000 1000 linux-swap method{ swap } format{ } . \

  \

  \


#d-i partman-auto/expert_recipe string                         \

#      boot-root ::                                            \

#              40 50 100 ext3                                  \

#                      $primary{ } $bootable{ }                \

#                      method{ format } format{ }              \

#                      use_filesystem{ } filesystem{ ext3 }    \

#                      mountpoint{ /boot }                     \

#              .                                               \

#              500 10000 1000000000 ext3                       \

#                      method{ format } format{ }              \

#                      use_filesystem{ } filesystem{ ext3 }    \

#                      mountpoint{ / }                         \

#              .                                               \

#              64 512 300% linux-swap                          \

#                      method{ swap } format{ }                \

#              .

# This makes partman automatically partition without confirmation.

d-i partman/confirm_write_new_label boolean true

#

d-i partman/choose_partition \

       select Finish partitioning and write changes to disk

d-i partman/confirm boolean true



## CLOCK AND TIME ZONE

# Controls whether or not the hardware clock is set to UTC.

d-i clock-setup/utc boolean false

# You may set this to any valid setting for $TZ; see the contents of

# /usr/share/zoneinfo/ for valid values.

d-i time/zone string America/New_York



## APT

# You can choose to install restricted and universe software, or to install

# software from the backports repository.

#d-i apt-setup/restricted boolean true

#d-i apt-setup/universe boolean true

#d-i apt-setup/backports boolean true

# Uncomment this to avoid adding security sources, or

# add a hostname to use a different server than security.ubuntu.com.

#d-i apt-setup/security_host string

# Additional repositories, local[0-9] available

#d-i apt-setup/local0/repository string \

#       deb [http://local.server/ubuntu](http://local.server/ubuntu) edgy main

#d-i apt-setup/local0/comment string local server

# Enable deb-src lines

#d-i apt-setup/local0/source boolean true

# URL to the public key of the local repository

#d-i apt-setup/local0/key string [http://local.server/key](http://local.server/key)



## USER ACCOUNT

# Skip creation of a root account (normal user account will be able to

# use sudo). The default is false; preseed this to true if you want to set

# a root password.

d-i passwd/root-login boolean false

# Alternatively, to skip creation of a normal user account.

#d-i passwd/make-user boolean false

# Root password, either in clear text

#d-i passwd/root-password password r00tme

#d-i passwd/root-password-again password r00tme

# or encrypted using an MD5 hash.

#d-i passwd/root-password-crypted password [MD5 hash]

# To create a normal user account.

d-i passwd/user-fullname string southstarr User

d-i passwd/username string southstarr

# Normal user's password, either in clear text

#d-i passwd/user-password password

#d-i passwd/user-password-again password

# or encrypted using an MD5 hash.

d-i passwd/user-password-crypted password 

#An MD5 hash for a password can be generated using the following command.

#$ echo "r00tme" | mkpasswd -s -H MD5



## BASE SYSTEM INSTALLATION

# Select the initramfs generator used to generate the initrd for 2.6 kernels.

#d-i base-installer/kernel/linux/initramfs-generators string yaird



## BOOT LOADER

# Grub is the default boot loader (for x86). If you want lilo installed

# instead, uncomment this:

#d-i grub-installer/skip boolean true

d-i lilo-installer/skip boolean true

# This is fairly safe to set, it makes grub install automatically to the MBR

# if no other operating system is detected on the machine.

#d-i grub-installer/only_debian boolean true

# This one makes grub-installer install to the MBR if if finds some other OS

# too, which is less safe as it might not be able to boot that other OS.

#d-i grub-installer/with_other_os boolean true

# Alternatively, if you want to install to a location other than the mbr,

# uncomment and edit these lines:

# d-i grub-installer/bootdev  string (hd0,0)

d-i grub-installer/bootdev_directory string /ubuntu/disks

d-i grub-installer/only_debian boolean true

d-i grub-installer/with_other_os boolean true



## PACKAGE SELECTION

tasksel tasksel/first multiselect ubuntu-desktop

#tasksel tasksel/first multiselect ubuntu-standard

#tasksel tasksel/first multiselect ubuntu-standard, lamp-server

#tasksel tasksel/first multiselect ubuntu-standard, kubuntu-desktop

#d-i pkgsel/include string openssh-server build-essential

# Some versions of the installer can report back on what software you have

# installed, and what software you use. The default is not to report back,

# but sending reports helps the project determine what software is most

# popular and include it on CDs.

#popularity-contest popularity-contest/participate boolean false



## FINISH FIRST STAGE

# Avoid that last message about the install being complete.

d-i finish-install/reboot_in_progress note

# This will prevent the installer from ejecting the CD during the reboot,

# which is useful in some situations.

d-i cdrom-detect/eject boolean false



## X CONFIGURATION

# X can detect the right driver for some cards, but if you're preseeding,

# you override whatever it chooses. Still, vesa will work most places.

#xserver-xorg xserver-xorg/config/device/driver select vesa

# A caveat with mouse autodetection is that if it fails, X will retry it

# over and over. So if it's preseeded to be done, there is a possibility of

# an infinite loop if the mouse is not autodetected.

#xserver-xorg xserver-xorg/autodetect_mouse boolean true

# Monitor autodetection is recommended.

xserver-xorg xserver-xorg/autodetect_monitor boolean true

# Uncomment if you have an LCD display.

#xserver-xorg xserver-xorg/config/monitor/lcd boolean true

# X has three configuration paths for the monitor. Here's how to preseed

# the "medium" path, which is always available. The "simple" path may not

# be available, and the "advanced" path asks too many questions.

##

#xserver-xorg xserver-xorg/config/monitor/selection-method \

#       select medium

##

#xserver-xorg xserver-xorg/config/monitor/mode-list \

#       select 1024x768 @ 60 Hz



## PRESEEDING OTHER PACKAGES

# Depending on what software you choose to install, or if things go wrong

# during the installation process, it's possible that other questions may

# be asked. You can preseed those too, of course. To get a list of every

# possible question that could be asked during an install, do an

# installation, and then run these commands:

#   debconf-get-selections --installer > file

#   debconf-get-selections >> file



## MIGRATION-ASSISTANT

#UserFolder=/Documents and Settings/Fatal Equinox

d-i anna/choose_modules multiselect migration-assistant

d-i migration-assistant/partitions multiselect Windows XP Professional (/dev/MADEVICE)

d-i migration-assistant/MADEVICE/users multiselect Fatal Equinox

d-i migration-assistant/MADEVICE/Fatal+Equinox/items multiselect AIM Triton, Internet Explorer, Yahoo, MSN, Opera, Firefox, Wallpaper, User Picture, Outlook Express, Gaim

# d-i migration-assistant/MADEVICE/hostuser/items multiselect My Documents, Internet Explorer

d-i migration-assistant/MADEVICE/Fatal+Equinox/user string southstarr

# d-i migration-assistant/new-user/linuser/password password xyz

# d-i migration-assistant/new-user/linuser/password-again password xyz

# d-i migration-assistant/new-user/linuser/fullname string fullusername

# d-i migration-assistant/new-user/linuser/administrator boolean true



## SHELL COMMANDS.

# d-i preseeding is inherently not secure. Nothing in the installer checks

# for attempts at buffer overflows or other exploits of the values of a

# preseed file like this one. Only use preseed files from trusted

# locations! To drive that home, and because it's generally useful, here's

# a way to run any shell command you'd like inside the installer,

# automatically.



# This first command is run as early as possible, just after

# preseeding is read.

d-i preseed/early_command string [ -x /custom-installation/hooks/early-command.sh ] && /custom-installation/hooks/early-command.sh



# This command is run just before the install finishes, but when there is

# still a usable /target directory.

#d-i preseed/late_command string echo foo > /target/etc/bar

# d-i preseed/late_command string rm /target/usr/lib/base-config/menu/apt-setup; rm /target/usr/lib/base-config/menu/apt-setup.mnu

#~ d-i preseed/late_command string /sbin/late_command

---

### Post by Fatal Equinox on 2008-04-07
I actually think i found my problem on the wiki... i will try and solve it with  this... 

[https://wiki.ubuntu.com/WubiGuide#head-e4dd73d03cc565bdbdcec46e799f8f73a7b726e0](https://wiki.ubuntu.com/WubiGuide#head-e4dd73d03cc565bdbdcec46e799f8f73a7b726e0)

---

### Post by Fatal Equinox on 2008-04-07
Ok,  I fixed it... the solution works from the wiki so if you have the same problem check it out...


now if anyone has a link to a tutorial on installing and setting up compiz fusion or like program... that would be perfect.... :lolflag: :guitar:

---

### Post by ago on 2008-04-08
Could you please try to reinstall using today's daily ISO?
It should work now without any intervention.

---

### Post by ago on 2008-04-08
New ISO is up!

---

### Post by evan d on 2008-04-08
> **ago said:**
> New ISO is up!

[http://cdimage.ubuntu.com/daily-live/20080408.1/](http://cdimage.ubuntu.com/daily-live/20080408.1/)

---

