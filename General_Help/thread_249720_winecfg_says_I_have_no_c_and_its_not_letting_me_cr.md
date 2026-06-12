---
title: "winecfg says I have no c:\ and its not letting me create one."
date: 2006-09-02
forum: General Help
---

### Post by Tashamon on 2006-09-02
when I winecfg I get a list of messages however winecfg loads but informs me I don't have a c: drive and when I try to create one it does not acknowledge me.   here is the code for the entire process:
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
libGL warning: 3D driver claims to not support visual 0x35
libGL warning: 3D driver claims to not support visual 0x36
libGL warning: 3D driver claims to not support visual 0x39
libGL warning: 3D driver claims to not support visual 0x3a
libGL warning: 3D driver claims to not support visual 0x3d
libGL warning: 3D driver claims to not support visual 0x3e
libGL warning: 3D driver claims to not support visual 0x41
libGL warning: 3D driver claims to not support visual 0x42
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\tashamon\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\tashamon\\Desktop"'.
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

any suggestions?

---

### Post by richardward101 on 2006-09-03
delete the .wine directory in your home directory, then run winecfg again. if than fails, run ```
sudo dpkg-reconfigure wine
```then delete the .wine directory then run winecfg.

---

