---
title: "Will moving my HD from 2nd to 1st SATA connector cause errors?"
date: 2022-09-13
forum: General Help
---

### Post by sofasurfer on 2022-09-13
My drive is connected to SATA connector #2 (the second one on the cable). So it is sdb. Secondary drive is sda. But if I disconnect the secondary drive it becomes sda instead of sdb. Now if I move the drive to the first connector it will ALWAYS be sda even when a secondary drive is connected to the cable. Question...I bet this will cause errors because of drive            misidentification, right? I am thinking my backup software will have trouble.

---

### Post by Dennis N on 2022-09-13
> Question...I bet this will cause errors because of drive misidentification, right? I am thinking my backup software will have trouble. 
Trouble only if your computer is uses BIOS.
A UEFI system is not affected, because UEFI firmware finds partitions by their PARTUUID (in red below) for booting which won't change if you switch SATA port. UUIDs and Labels don't change either.

```
Boot0000* ubuntu	HD(1,GPT,**[COLOR="#FF0000"]65e53d74-b000-4f9e-9d58-c45398bf1083[/COLOR]**,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)
```

---

### Post by oldfred on 2022-09-13
When I plug a flash drive in, it is the last drive, sdc for example. 
But on reboot my flash drive is sda and every other drive changes one letter.
You always need to check device. 
And use labels, UUIDS or GUIDs to uniquely identify drives, not device like /dev/sda.

---

