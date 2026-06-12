---
title: "Could not create MokListRT: volume full etc when trying to boot almost any distro/liv"
date: 2024-08-12
forum: General Help
---

### Post by sultan78611 on 2024-08-12
I'm having this issue for a two weeks now.
I can't install or run a live environment of almost any ddistro/liveUSB.
I get the same error at bootup and the PC turns off. 
I've tried other distros but no luck. I'm stuck on windows for the time being.


The error(s):


Could not create MokListRT: Volume Full
Could not create MokListXRT: Volume Full
Could not create SbatLevelRT: Volume Full
Could not create MokListTrustedRT: Volume Full
Something has gone seriously wrong: import_mok_state() failed: Volume Full


I would really appreciate any help with this issue


My Laptop is Asus Rog Gl502VM.

---

### Post by currentshaft on 2024-08-12
.

---

### Post by coffeecat on 2024-08-12
Not a chat thread. *Moved to **General Help**.*

---

### Post by yancek on 2024-08-12
Did you check your EFI entries.  Use sudo efibootmgr to see what you have and if necessary, delete old or unused entries.  Explained at the link below.

[https://askubuntu.com/questions/1401737/couldnt-create-moklist-volume-full-grub-doesnt-start-at-all](https://askubuntu.com/questions/1401737/couldnt-create-moklist-volume-full-grub-doesnt-start-at-all)

---

