---
title: "Wubi &amp; Alpha 5"
date: 2008-02-23
forum: General Help
---

### Post by acowboydave on 2008-02-23
Downloaded Alpha 5 last night, put the current Wubi And Alpha in the same file would not pick up the download of Alpha 5.. Made a CD of Alpha 5 put that in and installed Alpha from the Wubi in the CD..worked like a charm..Thanks you guys have done a great job...:)

---

### Post by ago on 2008-02-23
Pls, type %temp% in the windows file manager and look into the wubi log in there why the ISO was not recognized. Thanks.

---

### Post by acowboydave on 2008-02-23
I don't know if this is what you need, new to Vista and do not use Win. much..```
## LOCALE
# Locale sets language and country.
d-i debian-installer/locale string ${locale}

## KEYBOARD
# Keyboard selection.
d-i console-setup/modelcode string ${modelcode}
d-i console-setup/layoutcode string ${layoutcode}
# To select a variant of the selected layout (if you leave this out, the
# basic form of the layout will be used):
#d-i console-setup/variantcode string dvorak

#d-i console-tools/archs select at
#d-i console-keymaps-at/keymap select us

## HW-DETECT
# Work around i82365 oops (https://launchpad.net/bugs/74122).
d-i	hw-detect/start_pcmcia	boolean false
d-i	hw-detect/start_pcmcia	seen false

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
d-i netcfg/dhcp_options select Configure network manually
# Static network configuration.
d-i netcfg/get_nameservers string 192.168.1.1
d-i netcfg/get_ipaddress string 192.168.1.42
d-i netcfg/get_netmask string 255.255.255.0
d-i netcfg/get_gateway string 192.168.1.1
d-i netcfg/confirm_static boolean true
# Any hostname and domain names assigned from dhcp take precedence over
# values set here. However, setting the values still prevents the questions
# from being shown, even if values come from dhcp.
d-i netcfg/get_hostname string ${hostname}
d-i netcfg/get_domain string ${domain}
# Disable that annoying WEP key dialog.
d-i netcfg/wireless_essid string essid
d-i netcfg/wireless_wep string
# The wacky dhcp hostname that some ISPs use as a password of sorts.
#d-i netcfg/dhcp_hostname string radish

## MIRRORS
#~ d-i mirror/country string enter information manually
#~ d-i mirror/http/hostname string archive.ubuntu.com
#~ d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

## SUITE
# Suite to install.
d-i mirror/suite string feisty
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
#d-i partman-auto/disk string /dev/loop7
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
#d-i partman/confirm_write_new_label boolean true
##
#d-i partman/choose_partition \
#       select Finish partitioning and write changes to disk
#d-i partman/confirm boolean true

## CLOCK AND TIME ZONE
# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean false
# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string ${timezone}

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
#       deb http://local.server/ubuntu edgy main
#d-i apt-setup/local0/comment string local server
# Enable deb-src lines
#d-i apt-setup/local0/source boolean true
# URL to the public key of the local repository
#d-i apt-setup/local0/key string http://local.server/key

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
d-i passwd/user-fullname string ${user-fullname}
d-i passwd/username string ${username}
# Normal user's password, either in clear text
# d-i passwd/user-password password ubuntu
# d-i passwd/user-password-again password ubuntu
# or encrypted using an MD5 hash.
#d-i passwd/user-password-crypted password [MD5 ${md5-password}]
#An MD5 hash for a password can be generated using the following command.
#$ echo "r00tme" | mkpasswd -s -H MD5

## BASE SYSTEM INSTALLATION
# Select the initramfs generator used to generate the initrd for 2.6 kernels.
#d-i base-installer/kernel/linux/initramfs-generators string yaird

## BOOT LOADER
# Grub is the default boot loader (for x86). If you want lilo installed
# instead, uncomment this:
d-i grub-installer/skip boolean true
d-i lilo-installer/skip boolean true
# This is fairly safe to set, it makes grub install automatically to the MBR
# if no other operating system is detected on the machine.
#d-i grub-installer/only_debian boolean true
# This one makes grub-installer install to the MBR if if finds some other OS
# too, which is less safe as it might not be able to boot that other OS.
#d-i grub-installer/with_other_os boolean true
# Alternatively, if you want to install to a location other than the mbr,
# uncomment and edit these lines:
#d-i grub-installer/bootdev  string (hd0,0)
#d-i grub-installer/only_debian boolean false
#d-i grub-installer/with_other_os boolean false

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

## SHELL COMMANDS.
# d-i preseeding is inherently not secure. Nothing in the installer checks
# for attempts at buffer overflows or other exploits of the values of a
# preseed file like this one. Only use preseed files from trusted
# locations! To drive that home, and because it's generally useful, here's
# a way to run any shell command you'd like inside the installer,
# automatically.

# This first command is run as early as possible, just after
# preseeding is read.
#d-i preseed/early_command string anna-install some-udeb

# This command is run just before the install finishes, but when there is
# still a usable /target directory.
#d-i preseed/late_command string echo foo > /target/etc/bar
# d-i preseed/late_command string rm /target/usr/lib/base-config/menu/apt-setup; rm /target/usr/lib/base-config/menu/apt-setup.mnu
d-i preseed/late_command string /sbin/late_command

# This command is run just as base-config is starting up.
# base-config base-config/early_command string wget -O /etc/apt/sources.list debian/sources.list; apt-get update;

# This command is run after base-config is done, just before the login:
# prompt. This is a good way to install a set of packages you want, or to
# tweak the configuration of the system.
# base-config base-config/late_command string aptitude install fai; cd /etc/fai; wget debian/fai.conf; fai softupdate

```

---

### Post by Derek Chai on 2008-02-23
Where is the wubi on the 7.10 disc? also can you tell me this procedure

---

### Post by acowboydave on 2008-02-23
I don't know about the 7.10 Gutsy, using 8.4 Hardy, "Alpha 5" version, which just came out yesterday I believe..it is not the final release which is due in April. Any ways downloaded the desktop live ISO, and in my case the AMD 64 version. Burn the download, after checking the md5sum,burn to a CD..verify your burn. Place the CD or keep it in the tray..push it in windows will read what is on the disk..you will see Wubi near the bottom of the files, double click Wubi and you are on your way...

PS I might add this am a fan of Wubi..it got me to a full install of Ubuntu after using it in Win....good luck!:)

---

### Post by ago on 2008-02-24
Derek, (full) wubi is only in Ubuntu 8.04 alpha5+ ISO/CD

acowboydave, I'd need the wubi log, not the preseed file. The wubi log is in the user temp folder. You can go to that folder by typing %temp% in the location bar of windows explorer

---

### Post by acowboydave on 2008-02-24
Hello..OK did that, could not any Wubi logs..a few empty and a few DF files none that I could read. I did however uninstalled everything before using the CD for installation..could that have erased the log? Wubi just didn't pick up my download of Alpha and started searching to download via net. I know without the log it is hard to say why?

---

