---
title: "rEFInd and Grub"
date: 2019-01-10
forum: General Help
---

### Post by lksjfnvljnfdv on 2019-01-10
I have just reinstalled everything to my laptop from scratch. Got Windows 10 installed (vercrypt coming soon) and Kubuntu LUKS encrypted.

I have installed rEFInd and its working ok, it see's the Windows and Kubuntu OS's. But when you click on the Kubuntu it then loads grub and shows the grub menu. is there a way i can get it to ignore that bit and go straight from rEFInd to the LUKS encryption page.

Any advice?

---

### Post by rbmorse on 2019-01-10
When the rEFInd menu page appears, press the <F2> key and see if lists additional options.

---

### Post by &amp;KyT$0P# on 2019-01-10
You could just configure GRUB to not display the menu.

edit [FONT=Courier New]/etc/default/grub[/FONT]
Assuming you're running Kubuntu 18.04, change these lines... (yours may not be set quite identically to mine)
```
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10

```
... like this -
```
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=1

```

Save, and exit the editor.

To apply this change, run -
```
sudo update-grub
```

---

