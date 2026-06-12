---
title: "how to mount usb drive with sync option using hal?"
date: 2007-11-03
forum: General Help
---

### Post by sles on 2007-11-03
Hello!

I have mp3 player which doesn't works correctly if it is mounted async.
Certanly, I can mount it as I need every time manually ;-) , but I want to do this automatically.
And I want mount point be named different than volume name (it is hardcoded in player)

So I readed article here 
[http://www.mythic-beasts.com/~mark/random/hal/](http://www.mythic-beasts.com/~mark/random/hal/)

&#1072;nd added this to /etc/hal/fdi/policy/preferences.fd :

   <match key="storage.vendor" string="EM732X">                                                                                                    
                  <merge key="volume.policy.desired_mount_point" type="string">player</merge>                                                       
                  <merge key="volume.policy.mount_option.sync" type="bool">true</merge>                                                             
                                                                                                                                                    
    </match>             

I restarted hal, but looks like it is ignoring my changes- player is still mounted with volume name and without sync.

This is device info:

lshal |grep EM732
  scsi.vendor = 'EM732X'  (string)
udi = '/org/freedesktop/Hal/devices/storage_serial_EM732X_MP3_Player_0_0'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_EM732X_MP3_Player_0_0'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_EM732X_MP3_Player_0_0'  (string)
  info.vendor = 'EM732X'  (string)
  storage.serial = 'EM732X_MP3_Player-0:0'  (string)
  storage.vendor = 'EM732X'  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_EM732X_MP3_Player_0_0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_EM732X_MP3_Player_0_0'  (string)


Could you tell me how can do what I want ? ;-)

I use 7.10 amd64.

---

