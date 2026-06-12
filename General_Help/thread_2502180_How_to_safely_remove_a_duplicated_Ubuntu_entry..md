---
title: "How to safely remove a duplicated Ubuntu entry."
date: 2024-11-04
forum: General Help
---

### Post by vw16v on 2024-11-04
Hello, I recently upgraded the NVME drive on my laptop. During the cloning process detailed in my thread [here]("https://ubuntuforums.org/showthread.php?t=2501622") I was unable to boot into Ubuntu and couldn't see GRUB. 
A member named oldfred had me run this command.
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

This fixed the issue and allows me to see GRUB with Ubuntu and Windows to boot into. However, I see two entries in the BIOS boot order for Ubuntu. What's odd is I only see one Ubuntu entry in GRUB now. I had Easy UEFI installed in Windows that would of allowed me to delete the duplicate entry but the 15 day trail period ended. So, I'm going to attempt to remove the duplicate entry via efibootmgr.

This is the information teaforone provided my stating which one is the "Active" partition it's booting from.

> [COLOR=#000000]Somehow, you seem to have different UUIDs for Windows and Ubuntu[/COLOR]

[COLOR=#000000]Line 106 - Boot0000* Windows Boot Manager HD(1,GPT,[/COLOR][COLOR=#0000FF]303a4c17-90b2-4258-a536-590849804b1d[/COLOR][COLOR=#000000],0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)[/COLOR]
[COLOR=#000000]Line 107 - Boot0001* Ubuntu HD(1,GPT,[/COLOR][COLOR=#FF0000]4c29f2dc-736f-4b76-a238-b3224e258df2[/COLOR][COLOR=#000000],0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)[/COLOR]

[COLOR=#000000]Windows boots OK because the UUID is present[/COLOR]
[COLOR=#000000]Line 206 - &#9500;&#9472;nvme0n1p1 vfat D0E8-205E [/COLOR][COLOR=#0000FF]303a4c17-90b2-4258-a536-590849804b1d[/COLOR]

**So, I'd like to try and remove 4c29f2dc-736f-4b76-a238-b3224e258df2 from the boot menu.**

Here's my efibootmgr output. I'm reviewing this post regarding efibootmgr usage. I believe I can delete this entry using this tool.
Boot0001* Ubuntu    HD(1,GPT,4c29f2dc-736f-4b76-a238-b3224e258df2,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)

However, it does show an * indicating it's active. It's listed as 2nd in my boot order.

```
efibootmgr
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0002,0001,0000,0019,0015,0014,0016,0017,0018,001A
Boot0000* Windows Boot Manager    HD(1,GPT,303a4c17-90b2-4258-a536-590849804b1d,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000061000100000010000000040000007fff0400
Boot0001* Ubuntu    HD(1,GPT,4c29f2dc-736f-4b76-a238-b3224e258df2,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* Ubuntu    HD(1,GPT,303a4c17-90b2-4258-a536-590849804b1d,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)
Boot0010  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011  Boot Menu    FvFile(86488440-41bb-42c7-93ac-450fbf7766bf)
Boot0012  Diagnostic Splash    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0013  UEFI Diagnostics    FvFile(f8397897-e203-4a62-b977-9e7e5d94d91b)
Boot0014* USB CD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0015* USB FDD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0016* NVMe: Samsung SSD 990 EVO 1TB                    PciRoot(0x0)/Pci(0x6,0x0)/Pci(0x0,0x0)/NVMe(0x1,00-25-38-28-41-A0-D9-8D){99191c00-d932-4e4c-ae9a-a0b6e98eb8a4}
Boot0017* ATA HDD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot0018* ATA HDD1:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot0019* USB HDD: SAMSUNG MZVLB512HBJQ    PciRoot(0x0)/Pci(0xd,0x0)/USB(2,0){aa21e833-33af-47bc-89bd-419f88c50803}
Boot001A* PCI LAN:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)



```

Has anyone used this utility and do you think it's safe to remove Boot0001* Ubuntu    HD(1,GPT,4c29f2dc-736f-4b76-a238-b3224e258df2,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)?

The main reason I'm asking is ever since my upgrade to the new NVME my laptop is not properly suspending and drains power pretty fast. It didn't do this prior to upgrading the NVME.

Thanks for any input!

---

### Post by vw16v on 2024-11-04
Just to confirm. This is the syntax I'm planning on running to remove entry Boot001 
```
sudo efibootmgr -b 0001 -B
```
This should remove this duplicate entry.
Boot0001* Ubuntu    HD(1,GPT,4c29f2dc-736f-4b76-a238-b3224e258df2,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)

Any ideas if this might potentially cause any issues? I noticed both these entries point to the same file.
\EFI\ubuntu\shimx64.efi

---

### Post by vw16v on 2024-11-04
FYI, I did enough research to commit to this. I was pretty nervous rebooting but it did not affect GRUB that oldfred helped me with before. I have removed the other entry. Whether this will help with my suspend issue is another question. More testing.

sudo efibootmgr -b 0001 -B
[sudo] password for styles:
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0002,0000,0019,0015,0014,0016,0017,0018,001A
Boot0000* Windows Boot Manager HD(1,GPT,303a4c17-90b2-4258-a536-590849804b1d,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000061000100000010000000040000007fff0400
Boot0002* Ubuntu HD(1,GPT,303a4c17-90b2-4258-a536-590849804b1d,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)
Boot0010 Setup FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011 Boot Menu FvFile(86488440-41bb-42c7-93ac-450fbf7766bf)
Boot0012 Diagnostic Splash FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0013 UEFI Diagnostics FvFile(f8397897-e203-4a62-b977-9e7e5d94d91b)
Boot0014* USB CD: VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0015* USB FDD: VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0016* NVMe: Samsung SSD 990 EVO 1TB PciRoot(0x0)/Pci(0x6,0x0)/Pci(0x0,0x0)/NVMe(0x1,00-25-38-28-41-A0-D9-8D){99191c00-d932-4e4c-ae9a-a0b6e98eb8a4}
Boot0017* ATA HDD: VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot0018* ATA HDD1: VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot0019* USB HDD: SAMSUNG MZVLB512HBJQ PciRoot(0x0)/Pci(0xd,0x0)/USB(2,0){aa21e833-33af-47bc-89bd-419f88c50803}
Boot001A* PCI LAN: VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)

---

### Post by oldfred on 2024-11-04
I have many times deleted entries without issue.
But some with HP and maybe others have to use UEFI system settings as efibootmgr does not always work.

We used to get two settings by default one with shim that works with both UEFI Secure boot on or off.
And one with grub that only works with Secure boot off.
My system has never had Secure boot on, but has the shim entry?

---

### Post by dragonfly41 on 2024-11-04
You could also try installing rEFInd GUI which offers a parallel grub manager. Does not impact on your current Grub.

---

### Post by vw16v on 2024-11-04
Thanks for the responses oldfred and dragonfly41. As I mentioned previously I seriously appreciated your expertise in recovering my Ubuntu / GRUB from the reference thread. efibootmgr is an excellent utility! It saved me two times now and is free! I might check out rEFInd as well but I'm currently working as intended. Just need to try to figure out why my system is draining a lot of battery power while suspended after swapping out my NVME. I don't know if removing one of these entries will help but I'm going to test more before trying to change my suspend mode I mentioned in another thread that I haven't got any responses on. I supposed it's possible, but not likely, the suspend issue was related to having a duplicate entry?

---

