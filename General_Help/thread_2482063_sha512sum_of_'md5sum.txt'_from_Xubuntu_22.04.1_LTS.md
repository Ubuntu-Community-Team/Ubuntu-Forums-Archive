---
title: "sha512sum of 'md5sum.txt' from Xubuntu 22.04.1 LTS amd64 iso?"
date: 2022-12-18
forum: General Help
---

### Post by matthewrkarlsen on 2022-12-18
Hello,

Would it be possible for someone to post an sha512sum of the 'md5sum.txt' file contained within the Xubuntu 22.04.1 LTS amd64 iso?

To be specific, I mean the iso available via: [https://torrent.ubuntu.com/xubuntu/releases/jammy/release/desktop/xubuntu-22.04.1-desktop-amd64.iso.torrent](https://torrent.ubuntu.com/xubuntu/releases/jammy/release/desktop/xubuntu-22.04.1-desktop-amd64.iso.torrent)  

I have two different USB sticks for Xubuntu 22.04.1 and they do not appear to be identical...

I am worried a system may be infected with malware and need a reliable live USB to use to carry out scans for malware (but there is clearly no point if the USB stick is also infected).

Thank you for any assistance,
--Matthew

---

### Post by matthewrkarlsen on 2022-12-18
I solved this problem via
```

cmp /dev/cdrom /path/cdrom.iso

```
 as described on [https://unix.stackexchange.com/questions/39467/how-to-verify-a-cd-against-an-iso-image](https://unix.stackexchange.com/questions/39467/how-to-verify-a-cd-against-an-iso-image) followed by 
```

sha256sum --ignore-missing -c SHA256SUMS

```
followed by manually checking the SHA256SUMS file against the file at [https://cdimages.ubuntu.com/xubuntu/releases/22.04/release/SHA256SUMS](https://cdimages.ubuntu.com/xubuntu/releases/22.04/release/SHA256SUMS).

It's not perfect, but provides some reassurance. I can proceed with my malware scan now.

Regards,
Matthew

---

