---
title: "vmlinuz and initrd.img symbolic links in / directory"
date: 2015-01-04
forum: General Help
---

### Post by yoreei.grigorov on 2015-01-04
Hello,
I am running Kubuntu 14.04. Today I found the following files in my root directory:
initrd.img.old (symbolic link)
vmlinuz (symbolic link)
vmlinuz.old (symbolic link)
0 (not a symbolic link), empty file
initrd.img (symbolic link)

I am sure I haven't seen those before. They point to the corresponding files in /boot. Why do I have them there? If, say, something happened to them, what will the consequences be?
I've read that the Lilo bootloader uses those but I've never had Lilo installed on this system. I use Grub 2.
Thank you in advance!

---

### Post by deadflowr on 2015-01-04
If you haven't seen them before, it's because you never looked.

They're always there.

They always point to the latest kernel installed.
You can use them to point to the latest kernel, if using a custom grub entry, easily.

I've never deleted them, but I would think even if you did they'd probably regenerate after any kernel update comes...
Maybe not though, it's a general guess, since I've never even thought of deleting them.

---

### Post by yoreei.grigorov on 2015-01-04
Strange. Does that mean I don't have to mess with Grub if I want to change my kernel?
And what about this 0 file. I couldn't find any information about it either.

Thank you for answering, deadflowr. This question is however still not fully answered. Does anyone know whether these symlinks are actually needed or are they there just for convenience?

---

### Post by ian-weisser on 2015-01-04
Let's look at a grub config entry in /boot/grub/grub.cfg:
```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menu
entry_id_option 'gnulinux-simple-blahblahblah' {
        [...]
        linux   /boot/vmlinuz-3.16.0-28-generic.efi.signed root=UUID=blahblahblah ro  quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.16.0-28-generic
}
```

You don't need those symlinks *if you always boot from this grub.cfg*.
If you are ever manually pointing grub to a boot, 'vmlinuz' is a lot easier to remember and type than '/boot/vmlinuz-3.16.0-28-generic'
The symlinks are a legacy from simpler booting times, but still occasionally very handy.
You can delete the symlinks if you wish, but they will be recreated the next time grub updates it's grub.cfg file.

Lots of stuff gets updated automatically whenever you install a new kernel, including your initrd.img and grub.cfg...and those symlinks.

The '0' file looks like an ancient typo, and has nothing to do with booting. If it's empty, delete it.

---

### Post by yoreei.grigorov on 2015-01-06
[COLOR="#DDA0DD"]Thanks a lot guys!!![/COLOR]

---

### Post by Cavsfan on 2015-01-06
Here is how I boot Ubuntu 14.04, both boot and recovery using those symbolic links. But I use a custom grub menu - the one in my signature.
You never have to touch it when a new kernel gets added as it boots the latest kernel every time and new symbolic links get replaced with the same name.

```
menuentry "[COLOR=#0000ff]Trusty Tahr 14.04 LTS[/COLOR]" {
    set root=(hd[COLOR=#ff0000]0,6[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR=#ff0000]a6[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04 LTS (Recovery Mode)" {
    set root=(hd[COLOR=#ff0000]0,6[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR=#ff0000]a6[/COLOR] ro recovery nomodeset
        initrd /initrd.img
}
```

The blue can be whatever you want to see at boot time and the items in red would have to be changed to match which hard drive/partion your system is on.
If you only have one system Ubuntu this might be too much trouble. It is mainly for dual boot systems or more. I have 4 Linux systems and Windows 7 on my box.

---

