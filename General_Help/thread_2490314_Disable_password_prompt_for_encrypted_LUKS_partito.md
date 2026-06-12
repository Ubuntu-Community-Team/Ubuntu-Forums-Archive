---
title: "Disable password prompt for encrypted LUKS partiton after setting up automatic decryp"
date: 2023-08-29
forum: General Help
---

### Post by ubunnewbie21 on 2023-08-29
Hello,
I am running Ubuntu 22.04.3, I encrypted the hard drive during installation and bind it to TPM2 to decrypt the hard drive automatically.
Right now every time boot up the system the TPM2 could decrypt the hard drive automatically and directly go to login screen, but before TPM2 auto decrypt the hard drive, there is a password prompt for encrypted LUKS partition. But after all I don't need to input password, the TPM2 will decrypt it and go to Login screen. It is annoying that every time this password prompt every time.

Is there any way to disable this password prompt?

Thank you!

---

### Post by MAFoElffen on 2023-08-29
Yes... Posting right now from work, on a break... On my phone. So will be limited.

Please post your /etc/crypttab... What I'm looking for is that instead of prompt for the key, that it points to where to find it ...

---

### Post by ubunnewbie21 on 2023-08-30
Hello [COLOR=#000000]MAFoElffen,

Thank you for your quick reply during your break time.
Here is my /etc/crypttab file:

[/COLOR]nvme0n1p3_crypt UUID=f3137811-b82a-4353-818b-7640013a97f9 none luks,discard

Thank you!

---

### Post by MAFoElffen on 2023-08-30
> **ubunnewbie21 said:**
> Hello [COLOR=#000000]MAFoElffen,

Thank you for your quick reply during your break time.
Here is my /etc/crypttab file:
[/COLOR]```

nvme0n1p3_crypt UUID=f3137811-b82a-4353-818b-7640013a97f9 none luks,discard

```
Thank you!
Where yours says "none luks,discard" will prompt for the passphrase...

Here is what a cryptab enty will look like if you are storing it on a TPM:
```

nvme0n1p3_crypt UUID=f3137811-b82a-4353-818b-7640013a97f9 /dev/shm/tpm_temp.key luks,keyscript=/root/key_script.sh

```
RE: [https://glentomkowiak.medium.com/luks-with-tpm-in-ubuntu-df867cad9a1](https://glentomkowiak.medium.com/luks-with-tpm-in-ubuntu-df867cad9a1)

I use a similar line to store keyfiles on USB Flash Drives as a physical security token.

---

### Post by ubunnewbie21 on 2023-09-20
Hello [COLOR=#000000]MAFoElffen,

I am sorry I was in another project and just came back to work this tpm stuff
Wow, it works! I followed the link you posted and applied tpm encryption and auto decrypt, system boots up bypass passphrase prompt!

Thank you again. You are really my life saver!

Harry[/COLOR]

---

### Post by MAFoElffen on 2023-09-21
Glad to hear this is "solved" and working for you. Please go to the "Thread Tools" link in the upper right of the page to mark your thread as "Solved" so others may find what worked for you to solve their similar issues.

Remeber that you ca set up multiple keys, (tpm, prompt, keyfile), so that if one fails or get's cleared for some reason, that there is another way in...

---

