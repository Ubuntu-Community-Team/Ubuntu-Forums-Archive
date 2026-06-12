---
title: "Update menu entry list with custom menu entries"
date: 2013-02-05
forum: General Help
---

### Post by viktorjano on 2013-02-05
Hi,
I am trying to edit my start up menu list, and I use this code

```
#!/bin/sh 
set -e
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Ubuntu 12.04 custom">&2
cat<<EOF 
menuentry "Ubuntu Server 12.04" {
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 951ba983-0dc6-46fa-ad6d-58494b3610ff
linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=951ba983-0dc6-46fa-ad6d-58494b3610ff ro
initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
EOF
```

I then chmod +x this script in the grub.d folder and run update-grub.
But when I run sudo update-grub I get this error:

viktor@ubuntuServerSSKT:/etc/grub.d$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found Windows NT/2000/XP on /dev/sdc1
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 146
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
viktor@ubuntuServerSSKT:/etc/grub.d$ 

Can someone give some useful hint... I can not find line 146... It is probably the part of the script with the set command...

---

### Post by mcduck on 2013-02-05
As far as I know you shouldn't need (or use) any of the echo & cat stuff in the file. Just take a look at the existing 04_custom file in the same directory. OR simply add your entries there if you want.

[https://help.ubuntu.com/community/Grub2/CustomMenus]("https://help.ubuntu.com/community/Grub2/CustomMenus")

```

#!/bin/sh 
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Ubuntu Server 12.04" {
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 951ba983-0dc6-46fa-ad6d-58494b3610ff
linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=951ba983-0dc6-46fa-ad6d-58494b3610ff ro
initrd    /boot/initrd.img-3.2.0-29-generic-pae
}

```

---

### Post by viktorjano on 2013-02-27
Same again... The same error appears, and the grub.cfg file does not get updated. Instead a new file is generated which contains syntax error, but that happened and before.

---

