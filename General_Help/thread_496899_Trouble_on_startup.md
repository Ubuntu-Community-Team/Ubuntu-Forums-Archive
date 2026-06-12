---
title: "Trouble on startup"
date: 2007-07-09
forum: General Help
---

### Post by NuNn DaDdY on 2007-07-09
When I startup on my computer and as it gets ready to head to grub I am at a screen with the  following happening:
[I]
"Client Mac Addres: VA 04 E2 ..etc"
"DHCP..."[/I]

Then some time goes by and I recieve the following messages.
[I]
"PXE-E53:    NO BOOT FILENAME RECIEVED"
"PXE-M0F     EXITING BROADCAM PXE ROM"[/I]

After this the computer runs fine and goes to grub with the dual load and loads up without any issues.  This is just time consuming to have to wait on and I believe that there is a quick fix for it but I'm unsure as to what it is.

---

### Post by NuNn DaDdY on 2007-07-09
Is there anyone with a solution please?  :guitar:

---

### Post by AlexThomson_NZ on 2007-07-09
What line exactly does it get stuck on?  Fetching a DHCP IP address? 

I am surprised it is doing this before loading grub- is this being done by the bios firmware?  can it be disabled?

---

### Post by lakris61 on 2007-07-09
You most likely have PXE (a network boot functionality) enabled. When You start Your pc, enter the BIOS and check boot order. Move Network boot (PXE) down in the list.

---

