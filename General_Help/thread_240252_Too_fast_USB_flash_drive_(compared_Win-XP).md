---
title: "Too fast USB flash drive (compared Win-XP)"
date: 2006-08-20
forum: General Help
---

### Post by Meelis on 2006-08-20
Hello

Why SanDisk Cruzer Crossfire 1GB USB flash drive is so fast under Kubuntu 6.06?
My motherboard is SIS M830LR (with USB 1.1).
Under WinXP it writes 60mb 35-40s.
Under Kubuntu it writes 60mb 3-4s.
Why, is this safe to flash drive, to I need some driver for winxp to write faster on the flash drive?
:confused: ](*,)

---

### Post by engla on 2006-08-20
Linux does not behave at all in the same way as windows with regard to hardware.

The drivers and the OS try to optimize what you do and schedule it if other tasks are pending.. if the files have recently been used for example, they are still in cache and the read (before write) goes lighening fast. 

Windows always copies in sync, so when it said it's done, it's done. You can pull out the disk from windows and nothing will happen.

On Linux, you have to unmount it.. deterred writes and such might still be hanging and it takes the signal and finishes that.. so try to do the 4s copy and then eject it, it should take a while for it until it allows you.

So the answer is, the behind the scenes thing is completely different. Hopefully it gives a better outward result to the users, too.

---

### Post by jdong on 2006-08-20
> **engla said:**
> 

Windows always copies in sync, so when it said it's done, it's done. You can pull out the disk from windows and nothing will happen.



Everything you said except that statement is accurate. Even under Windows with "optimize for quick removal" set, it's **still not 100% safe to rip out the drive without unmounting it first**. I've personally seen people corrupt the filesystem on their thumb drives before, and while working at my school's IT help desk I've had to resort to Norton Disk Doctor on several occasions to repair badly corrupted thumb drives.

You ALWAYS should properly unmount your removable media before yanking it out. It's just that under XP's default settings, the unmounting process is much faster.

---

### Post by yopnono on 2006-08-20
Question. Is there a way to make (linux) to write to the usbstick directly? Like in windows, and not cache it until you use umount.

---

### Post by jdong on 2006-08-20
> **yopnono said:**
> Question. Is there a way to make (linux) to write to the usbstick directly? Like in windows, and not cache it until you use umount.
Yes, there is. It involves editing some hal config file in /etc... I can't tell you off the top of my head where it is, but it's definitely possible!

---

### Post by yopnono on 2006-08-21
> **jdong said:**
> Yes, there is. It involves editing some hal config file in /etc... I can't tell you off the top of my head where it is, but it's definitely possible!

Ok. thanks, I will search some more on the webb about this.

I don't see why it's not could be done, and also in a safe way. If the CRC is checked before and after it sholud be safe.

---

### Post by yopnono on 2006-08-21
fixed. I did find some info on the webb.

I just put this in a new file that I called "usb.fdi" in the "/etc/hal/fdi/policy"
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <!-- Default policies merged onto computer root object  -->
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/computer">
      <merge key="storage.policy.default.mount_root" type="string">/mnt</merge>
      <merge key="storage.policy.default.use_managed_keyword" type="bool">true</merge>
      <merge key="storage.policy.default.managed_keyword.primary" type="string">managed</merge>
      <merge key="storage.policy.default.managed_keyword.secondary" type="string">kudzu</merge>
      <merge key="storage.policy.default.mount_option.noauto" type="bool">true</merge>
      <merge key="storage.policy.default.mount_option.pamconsole" type="bool">true</merge>
      <merge key="storage.policy.default.mount_option.exec" type="bool">true</merge>
    </match>
  </device>

  <device>
    <!-- Whitelist bus types of storage devices we care about  -->
    <match key="info.category" string="storage">
      <match key="storage.bus" string="usb">
	<merge key="storage.policy.should_mount" type="bool">true</merge>      
      </match>
      <match key="storage.bus" string="ide">
	<merge key="storage.policy.should_mount" type="bool">true</merge>
      </match>
      <match key="storage.bus" string="ieee1394">
	<merge key="storage.policy.should_mount" type="bool">true</merge>
      </match>
      <match key="storage.bus" string="sata">
	<merge key="storage.policy.should_mount" type="bool">true</merge>
      </match>
      <match key="storage.bus" string="platform">
	<merge key="storage.policy.should_mount" type="bool">true</merge>
      </match>
    </match>

    <!-- Normal volumes; use volume label, uuid or drive_type -->
    <match key="block.is_volume" bool="true">
      <match key="volume.fsusage" string="filesystem">
	<!-- skip for drives with the no partitions hint (they are handled above) -->
	<match key="@block.storage_device:storage.no_partitions_hint" bool="false">

	  <merge key="volume.policy.should_mount" type="bool">true</merge>
	  <merge key="volume.policy.mount_filesystem" type="copy_property">volume.fstype</merge>
	  
	  <!-- Fallback is '<storage.bus>', appended with 'disk', e.g. usbdisk,
		  idedisk, scsidisk etc. -->
	<!--
	  <merge key="volume.policy.desired_mount_point" type="copy_property">@block.storage_device:storage.bus</merge>
	  <append key="volume.policy.desired_mount_point" type="string">disk</append>
	  -->
	  <merge key="volume.policy.desired_mount_point" type="string">removable</merge>

  
          <!-- Best: If available use filesystem label -->
          <match key="volume.label" empty="false">
            <!-- unless it's a path (e.g. /boot, /, /home etc) -->
            <match key="volume.label" is_absolute_path="false">
	      <!-- and only if the label is ascii -->
              <match key="volume.label" is_ascii="true">
		<merge key="volume.policy.desired_mount_point" type="copy_property">volume.label</merge>
              </match>
            </match>
          </match>
	  

	  <!-- Use noatime and sync options for all hotpluggable or removable
	       volumes smaller than 2GB -->
	  <match key="volume.size" compare_lt="2147483648">
	    <match key="@block.storage_device:storage.hotpluggable" bool="true">
	      <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
	      <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
	    </match>
	    <match key="@block.storage_device:storage.removable" bool="true">
	      <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
	      <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
	    </match>
	  </match>

	  <!-- Use UTF-8 charset for vfat -->
	  <!--
	  <match key="volume.fstype" string="vfat">
	    <merge key="volume.policy.mount_option.iocharset=utf8" type="bool">true</merge>
    </match>-->
	  
	  </match>	  
	</match>
      </match>
    </device>


</deviceinfo>
```

EDIT: wrong path

---

### Post by jdong on 2006-08-21
Yes, there it is :)

Thanks!

---

