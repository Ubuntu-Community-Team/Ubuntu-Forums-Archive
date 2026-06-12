---
title: "GRUB2 booting with labels (no UUID) (10 years later)"
date: 2020-06-27
forum: General Help
---

### Post by p.elsie on 2020-06-27
"10 years later" -French Narrator of Sponge Bob (speak it slowly in a French accent)

I came across an old thread with the same title. It's old, and closed. But I think I've improved on what was summarized in conclusion by MountainX (thank you!)

First, we need to label our drive partitions. Here are some examples:

sudo e2label /dev/mapper/vg02-boot boot
sudo e2label /dev/mapper/vg02-root19 mint19-root
sudo e2label /dev/mapper/vg02-root20 mint20-root
sudo e2label /dev/mapper/vg02-home home
sudo e2label /dev/sda1 non-lvm-root
sudo e2label /dev/sda4 non-lvm-home

Before labeling a partition, you might want to see if it already has a label (same command, no label name). It will print the current label. Usage for [e2label]("http://manpages.ubuntu.com/manpages/focal/en/man8/e2label.8.html") is ***e2label device [ new-label ]***

Before continuing, backup /etc/grub.d/10_linux and /usr/lib/grub/grub-mkconfig_lib files. 

Now open /etc/grub.d/10_linux in a text editor. Look for the line that has "/sys/firmware/efi" and comment out some lines and add some lines until it looks like this:

```

#  COMMENTED OUT FOR CUSTOM CODE
#  if test -d /sys/firmware/efi && test -e "${linux}.efi.signed"; then
#    sed "s/^/$submenu_indentation/" << EOF
#	linux	${rel_dirname}/${basename}.efi.signed root=${linux_root_device_thisversion} ro ${args}
#EOF
#  else
#    if [ x"$GRUB_FORCE_PARTUUID" = x ]; then
#        sed "s/^/$submenu_indentation/" << EOF
#        linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
#EOF
#    else
#        sed "s/^/$submenu_indentation/" << EOF
#        linux	${rel_dirname}/${basename} root=PARTUUID=${GRUB_FORCE_PARTUUID} ro ${args}
#EOF
#    fi
#  fi
  #CUSTOM_CODE
  auto_label="`e2label ${LINUX_ROOT_DEVICE} 2>/dev/null`"
  linux_root_device_thisversion="LABEL=${auto_label}"
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  #END CUSTOM CODE

```

Save that and then open /usr/lib/grub/grub-mkconfig_lib in a text editor. Look for the line that has "filesystem UUID" and comment out some lines and add some lines until it looks like this:


```

  # If there's a filesystem UUID that GRUB is capable of identifying, use it;
  # otherwise set root as per value in device.map.
#  COMMENTED OUT FOR CUSTOM CODE
#  fs_hint="`"${grub_probe}" --device $@ --target=compatibility_hint`"
#  if [ "x$fs_hint" != x ]; then
#    echo "set root='$fs_hint'"
#  fi
#  if fs_uuid="`"${grub_probe}" --device $@ --target=fs_uuid 2> /dev/null`" ; then
#    hints="`"${grub_probe}" --device $@ --target=hints_string 2> /dev/null`" || hints=
#    echo "if [ x\$feature_platform_search_hint = xy ]; then"
#    echo "  search --no-floppy --fs-uuid --set=root ${hints} ${fs_uuid}"
#    echo "else"
#    echo "  search --no-floppy --fs-uuid --set=root ${fs_uuid}"
#    echo "fi"
#  fi
#CUSTOM CODE 
  # If there's a filesystem fs_label that GRUB is capable of identifying, use it;
  # otherwise print a warning. 
  fs_label="`"${grub_probe}" --device $@ --target=fs_label`"
  if [ "x$fs_label" != x ]; then
    echo "search --no-floppy --set=root --label $fs_label"
  else
    echo "### YOU REALLY SHOULD LABEL YOUR PARTITIONS!!! ###"
    echo "# ... because... device $@ was considered by ${grub_probe} and no label was found"
    fs_hint="`"${grub_probe}" --device $@ --target=compatibility_hint`"
    if [ "x$fs_hint" != x ]; then
      echo "set root='$fs_hint'"
    fi
    if fs_uuid="`"${grub_probe}" --device $@ --target=fs_uuid 2> /dev/null`" ; then
      hints="`"${grub_probe}" --device $@ --target=hints_string 2> /dev/null`" || hints=
      echo "if [ x\$feature_platform_search_hint = xy ]; then"
      echo "  search --no-floppy --fs-uuid --set=root ${hints} ${fs_uuid}"
      echo "else"
      echo "  search --no-floppy --fs-uuid --set=root ${fs_uuid}"
      echo "fi"
    fi
  fi
#END CUSTOM CODE

```

Now use grub-mkconfig like you normally would. But enjoy grub.cfg files that are much easier to read. 

And if you ever get stuck in a grub menu on an LVM system, here's how to boot... 

Use the ls command to find out how grub sees your partitions.

Use the ls command to find out what files exist, their names, their path. For example, *ls (lvm/vg01-boot)/* will list the files on vg01/boot and *ls (lvm/vg01-boot)/grub* will list the files in the grub folder on vg01/boot. 

Assuming that you might not have labels, I'll skip the search command. But to get usage help, enter "search --help". 

If you have separate boot and root partitions, named vg01/boot and vg/01/root, then you'll enter these commands:

set prefix=(lvm/vg01-boot)/grub
set root=(lvm/vg01-boot)
insmod gzio
insmod part_gpt
insmod lvm
insmod ext2
linux /vmlinuz-4.15.0-20-generic root=/dev/mapper/vg01-root ro 
initrd /initrd-4.15.0-20-generic
boot

The more common scenario is that the boot files are on the root partition, and in that case, you'll enter commands like this:

set prefix=(lvm/vg01-root)/grub
set root=(lvm/vg01-root)
insmod gzio
insmod part_gpt
insmod lvm
insmod ext2
linux /boot/vmlinuz-4.15.0-20-generic root=/dev/mapper/vg01-root ro 
initrd /boot/initrd-4.15.0-20-generic
boot

That's what I know today. I'll probably forget it tomorrow.

---

### Post by p.elsie on 2020-06-28
Actually, I now admit that I can't get this to work when the OS root and boot partitions are different partitions (which I really want, so that I only have ***one*** instance of grub.cfg). This syntax doesn't seem to work like I think it should:

```

	search --no-floppy --label my_Boot_label --set root
	linux	/boot/vmlinuz-4.15.0-20-generic root=LABEL=my_Root_label ro 

```

This doesn't work either:
```

	search --no-floppy --label my_Boot_label --set rootlinux
	search --no-floppy --label my_Root_label --set osroot
	linux	/boot/vmlinuz-4.15.0-20-generic root=$osroot ro 

```

To clarify, my use case is LVM. Therefore, $osroot has a value like *lvm/vgmint-root*. And I'm guessing that:

1) In both cases, it resolves to *linux /boot/vmlinuz-4.15.0-20-generic root=lvm/vgmint-root ro*, and that's never going to work. 
2) If you use a regular partition, it will resolve to something that does work. 
3) I may just have to live with using a label for the boot partition, and *root=/dev/mapper/vgmint-root*. I can live with that - it's still human readable, and I control the names of logical volumes and volume groups. 

I hope this thread is still useful to someone. I'm still pretty sure that there was a bug in the [Mountain X_ solution]("https://ubuntuforums.org/showthread.php?t=1530532&page=2"), in that it used *e2label ${GRUB_DEVICE_BOOT}* where it should have used *e2label ${LINUX_ROOT_DEVICE}*. However, it is of no consequence if those two are the same partition.

---

### Post by p.elsie on 2020-06-29
Today, I found some new pages:

[https://www.dedoimedo.com/computers/grub-2.html](https://www.dedoimedo.com/computers/grub-2.html)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

For me, these provide the solution. I want custom, human readable menus, not automatically generated menus. 

I've disabled /etc/grub.d/10_linux and /etc/grub.d/30_os-prober and I've customized /etc/grub.d/40_custom

I've even added a section to boot from Live CD as described here:

[https://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/](https://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/)

---

### Post by p.elsie on 2020-07-02
My final lesson for this thread - GRUB2 will boot from a linear logical volume. It may even boot from a mirrored logical volume. But it won't do it from more than one disk (in my experience). So for me, that limitation (and the frustration I experienced learning this lesson) negates the reason I wanted to use a logical volume for the boot partition. I now have one regular ext2 boot partition on each disk, and I'll just manually synchronize the files on them.

---

### Post by VMC on 2020-07-02
I use labels for all my boots, with the exception of windows. I'm guessing you haven't had a lot of input because of slightly confusing context. I don't use grub scripts. 
I will show using labels in a more readable fashion. Partial output of lsblk & grub:
```
&#9500;&#9472;nvme0n1p4 ext4   1.0   [COLOR=#008000]**manjaro**[/COLOR] f9136941-2d90-4ad6-8878-f17ffabb6349
&#9500;&#9472;nvme0n1p5 ext4   1.0   [COLOR=#008000]**kubuntu**[/COLOR] 8729f784-918f-4005-a5c9-d3e8c9882585
&#9492;&#9472;nvme0n1p6 ext4   1.0   [COLOR=#008000]**ubuntu**[/COLOR]  517b1205-d3fb-4b84-b130-982cf970f389
```

```
menuentry 'Windows' --class windows --class os{
    insmod part_gpt
    insmod fat
    search --no-floppy --fs-uuid --set=root 06F2-A932
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
menuentry 'manjaro' --class gnu-linux --class gnu --class os{
    insmod all_video
    insmod gzio
    insmod ext2
    search --no-floppy --set=root --label "[COLOR=#008000]**manjaro**[/COLOR]"
    linux /boot/vmlinuz-5.6-x86_64 root=LABEL=[COLOR=#008000]**manjaro**[/COLOR] rw quiet splash pci=noaer
    initrd /boot/initramfs-5.6-x86_64.img
}
menuentry 'kubuntu' --class ubuntu --class gnu-linux --class gnu --class os{
    insmod all_video
    insmod gzio
    insmod ext2
    search --no-floppy --set=root --label "[COLOR=#008000]**kubuntu**[/COLOR]"
    linux /boot/vmlinuz root=LABEL=[COLOR=#008000]**kubuntu**[/COLOR] ro quiet splash pci=noaer
    initrd /boot/initrd.img
}
menuentry 'ubuntu' --class ubuntu --class gnu-linux --class gnu --class os{
       insmod all_video
    insmod gzio
    insmod ext2
    search --no-floppy --set=root --label "[COLOR=#008000]**ubuntu**[/COLOR]"
    linux /boot/vmlinuz root=LABEL=[COLOR=#008000]**ubuntu**[/COLOR] ro quiet splash pci=noaer
    initrd /boot/initrd.img
}
```

---

