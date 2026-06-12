---
title: "Converting NTFS to FAT32"
date: 2004-12-17
forum: General Help
---

### Post by ibs on 2004-12-17
I just finished installing Ubuntu on a specific partition and WinXP on another NTFS partition.  I want to convert hda1 and hda5 to FAT32 from NTFS but keep the WinXP partition (hda2) as NTFS. (see partition table below)

I'm going to use Partition Magic in Windows to convert NTFS to FAT32 but i remember doing that once and all  filenames on the converted partition were  scrambled. But i think that then i was converting a NTFS partition to FAT32 with WinXP Pro on it. Is it safe to convert NTFS to FAT32 now when no Windows is on them?

My partition table now:
```

Device      Boot    Start         End           Blocks           Id            System
/dev/hda1            1                17799      142970436   7              HPFS/NTFS
/dev/hda2            17800        18728      7462192+     f               W95 Ext'd (LBA)
/dev/hda3   *       18729        19457      5855692+    83             Linux
/dev/hda5            17800        18692      7172991       7              HPFS/NTFS
/dev/hda6            18693        18728      289138+      82             Linux swap

```

---

