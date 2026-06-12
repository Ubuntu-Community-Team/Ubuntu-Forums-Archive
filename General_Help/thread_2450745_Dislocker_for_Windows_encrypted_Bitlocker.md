---
title: "Dislocker for Windows encrypted Bitlocker"
date: 2020-09-19
forum: General Help
---

### Post by talkingtree2 on 2020-09-19
Hi,

Wondering what's everyone's experience on this. It seems like you still need to KNOW the encrypted password in order to unlock Bitlocker in Ubuntu. Is this true? Or it can unlock an encrypted HDD without any password?

Reference article to dislocker guide: [https://www.linuxuprising.com/2019/04/how-to-mount-bitlocker-encrypted.html](https://www.linuxuprising.com/2019/04/how-to-mount-bitlocker-encrypted.html)

---

### Post by tapucosmo on 2020-09-20
It is practically impossible to decrypt an encrypted drive without the correct password unless a low entropy password was chosen, some critical weakness is found in the encryption algorithm, or an unexpected breakthrough in mathematics is discovered.

However, depending on how Bitlocker was configured, it may be possible that a recovery password is available on your Microsoft account or elsewhere. [https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan](https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

---

