---
title: "Yubikey on multiple LUKS drives"
date: 2019-02-16
forum: General Help
---

### Post by takeawaydave on 2019-02-16
I have the following LUKS partitions:

```
    root@precision:~# blkid | grep crypto_LUKS
    /dev/nvme0n1p3: UUID="e1ac241d-a91c-4386-9b08-752dc5d0e9b8" TYPE="crypto_LUKS" PARTUUID="91fc5b71-7c22-4e3e-821d-7116a5a46f7e"
    /dev/nvme0n1p4: UUID="23c3618e-be44-42f0-812b-bee1b0ac8dfe" TYPE="crypto_LUKS" PARTUUID="a6caf1e1-6ceb-4287-a2e2-45e4bbf1cec1"
    /dev/sda1: UUID="396463ed-16f8-4f77-808d-743f35eaa4cb" TYPE="crypto_LUKS" PARTUUID="1cec189b-c43b-4094-a9f2-47d8f589c6d8"
```

Trying to setup Yubikey 2FA as per:

[https://askubuntu.com/questions/599825/yubikey-two-factor-authentication-full-disk-encryption-via-luks](https://askubuntu.com/questions/599825/yubikey-two-factor-authentication-full-disk-encryption-via-luks)

[https://www.howtoforge.com/ubuntu-two-factor-authentication-with-yubikey-for-harddisk-encryption-with-luks](https://www.howtoforge.com/ubuntu-two-factor-authentication-with-yubikey-for-harddisk-encryption-with-luks)

I run the following script three times, each time changing the target disk within the script before doing so. Each time I sent the same passphrase "123456"

I then check the slots on each of the crypto LUKS disks and see that SLot 7 is ENABLED:
```

    root@precision:~# cryptsetup luksDump /dev/nvme0n1p3 | grep Slot
    Key Slot 0: ENABLED
    Key Slot 1: DISABLED
    Key Slot 2: DISABLED
    Key Slot 3: DISABLED
    Key Slot 4: DISABLED
    Key Slot 5: DISABLED
    Key Slot 6: DISABLED
    Key Slot 7: ENABLED
    root@precision:~# cryptsetup luksDump /dev/nvme0n1p4 | grep Slot
    Key Slot 0: ENABLED
    Key Slot 1: DISABLED
    Key Slot 2: DISABLED
    Key Slot 3: DISABLED
    Key Slot 4: DISABLED
    Key Slot 5: DISABLED
    Key Slot 6: DISABLED
    Key Slot 7: ENABLED
    root@precision:~# cryptsetup luksDump /dev/sda1 | grep Slot
    Key Slot 0: ENABLED
    Key Slot 1: DISABLED
    Key Slot 2: DISABLED
    Key Slot 3: DISABLED
    Key Slot 4: DISABLED
    Key Slot 5: DISABLED
    Key Slot 6: DISABLED
    Key Slot 7: ENABLED
    root@precision:~# 
```

Problem: 

When I reboot the Yubikey 2FA appears to unlock nvme0n1p3 however /dev/nvme0n1p4 and /dev/sda1 drives don't get unlocked and I need to enter the LUKS passphrase.

When not using the Yubikey I can enter the LUKS passphrase just the once and all drives are unlocked.

---

