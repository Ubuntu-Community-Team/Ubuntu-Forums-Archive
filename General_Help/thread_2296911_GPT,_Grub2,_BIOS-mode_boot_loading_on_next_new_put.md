---
title: "GPT, Grub2, BIOS-mode boot loading on next new puter. Only Linux installs."
date: 2015-09-29
forum: General Help
---

### Post by mikodo on 2015-09-29
I've decided to stick with MBR with this aging desktop computer, with only Linux installs.

I like to read and plan ahead for things. I want to use GPT for the next one, (new).

Questions.

1. Is it an acceptable practice to use GPT, the traditional GRUB2 and the BIOS-mode boot loading on new computers?

2. Or, should I start learning about UEFI now, for the future? Even though, I will only install Linux OS's. 

For  hardware support, I plan to buy next, a System76 Desktop. I assume BIOS-mode boot loading, will be well supported on that hardware.

I'm hoping because I only use Linux, I won't have to deal with UEFI and I can "sail off" into the future and never have to worry about it.

Thanks.

[https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_for_Single_Boot_with_a_Random_Boot_Mode](https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_for_Single_Boot_with_a_Random_Boot_Mode)

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by oldfred on 2015-09-30
I wanted UEFI as the "new" thing. I started looking back in 2006 when I then built a system. And the only UEFI was server motherboard for 10x what I was planning for entire system.

But then with 10.10 support for gpt partitioning was added to Ubuntu. I started converting new or reformatted drives to gpt. Ubuntu will boot in BIOS mode from gpt partitioned drives if you add a tiny 1 or 2MB unformatted partition with the bios_grub flag(if using gparted). 

I only built my new UEFI system at the end of last year. But drives had both an ESP - efi system partition (for future use) and the bios_grub for my old system. I then could have used old drives, but ended up with newer drives as the older ones were older.

So far almost all UEFI systems have CSM.
         CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

A few small systems usually 32 bit, had UEFI class 3 systems which had no CSM/BIOS mode, only UEFI. Eventually that will happen to all systems as it costs more to add the extra CSM chip & support it.

But for now you can even stay with BIOS/MBR on almost all new systems. I do prefer gpt and UEFI is more complex  but offers some advantages. Part of complexity is just that it offers both UEFI & CSM/BIOS. And then Windows added secure boot, but so far you can turn that off.

---

### Post by mikodo on 2015-09-30
> **oldfred said:**
>  Ubuntu will boot in BIOS mode from gpt partitioned drives if you add a tiny 1 or 2MB unformatted partition with the bios_grub flag(if using gparted). 

But for now you can even stay with BIOS/MBR on almost all new systems.

Thanks, Fred. I was hoping the title would catch your eye.

Yes, I'm fine actually with MBR. Like you, I was thinking of using GPT, as I see its' use for, more in the future.

It's good to know at least for now, I can use GPT, without fussing with EFI, UEFI and now the secure lock.

We'll see what the future brings, when it is time to upgrade hardware, (my desktop).

Thanks again.

---

