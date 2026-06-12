---
title: "partman help"
date: 2021-02-09
forum: General Help
---

### Post by rakansen77 on 2021-02-09
could someone help me with this? preseeding works with ubuntu 20.04.2, but the partitioning doesnt work correctly. i have been using this to get the partitioning to work, as the expert_recipe just gets ignored by partman. so i modified the default multi scheme:
```
partman-auto/text/multi_scheme ::

1 1 1 free
    $iflabel{ gpt }
    $reusemethod{ }
    method{ biosgrub } .

538 538 1075 fat32
    $reusemethod{ }
    $primary{ }
    method{ efi }
    format{ } .

512 1024 768 ext4
    $defaultignore{ }
    $lvmignore{ }
    method{ format }
    format{ }
    use_filesystem{ }
    filesystem{ ext4 }
    mountpoint{ /boot } .

2000 3500 25000 $default_filesystem
    $lvmok{ }
    method{ format }
    format{ }
    use_filesystem{ }
    $default_filesystem{ }
    mountpoint{ / } .

1000 1500 10000 $default_filesystem
    $lvmok{ }
    method{ format }
    format{ }
    use_filesystem{ }
    $default_filesystem{ }
    mountpoint{ /var } .

96 512 200% linux-swap
    $defaultignore{ }
    $lvmok{ }
    $reusemethod{ }
    method{ swap }
    format{ } .

256 400 2000 $default_filesystem
    $lvmok{ }
    method{ format }
    format{ }
    use_filesystem{ }
    $default_filesystem{ }
    mountoptions{ noexec } 
    mountoptions{ nosuid }
    mountoptions{ nodev }
    mountpoint{ /tmp } .

4000 10000 -1 $default_filesystem
    $lvmok{ }
    method{ format }
    format{ }
    use_filesystem{ }
    $default_filesystem{ }
    mountpoint{ /home } .

```

this however doesnt mount the selected /tmp partition with any options specified. in case your wondering why i have mountoptions there, its cause options/nodev{ nodev } didnt work. i am completly stumped here as nothing i have been doing has worked. 

here is my preseed file:

```
#auto install ubuntu
d-i auto-install/enable boolean true
# only prompt for critical stuff
d-i debconf/priority select critical
d-i live-installer/enable boolean false
#set langauge to english_us
d-i debian-installer/locale string en_US.UTF-8
d-i debian-installer/country string US
d-i localechooser/supported-locales multiselect en_US.UTF-8
#disable interactive keyboard setup
d-i console-setup/ask_detect boolean false
#auto configure the network
d-i netcfg/choose_interface select auto
d-i hw-detect/load_firmware boolean true
#setup mirrors for updates etc
d-i mirror/country string manual
d-i mirror/http/hostname string archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string
#create base user
d-i passwd/user-fullname string raka
d-i passwd/username string raka
d-i passwd/user-password-crypted password XXX
d-i passwd/root-password-crypted password XXX
#dont encrypt the home dir
d-i user-setup/encrypt-home boolean false
#setup timezone
d-i clock-setup/utc boolean true
d-i time/zone string US/Eastern
#partition the drive
d-i partman-auto/method lvm
d-i partman-auto/method string regular
d-i partman-auto-lvm/guided_size string max
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true
d-i partman-auto/choose_recipe select multi
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
d-i debian-installer/quiet boolean false
d-i debian-installer/splash boolean false
d-i cdrom-detect/eject boolean true
d-i ubiquity/reboot boolean true
```

i am not going to use ubuntu server with the new format and install desktop, my workplace doesnt like seeing a server version installed on desktops. any help would be greatly appreciated. 

Thanks.

PS if this is the wrong section, sorry, didnt know where else to post it.

---

