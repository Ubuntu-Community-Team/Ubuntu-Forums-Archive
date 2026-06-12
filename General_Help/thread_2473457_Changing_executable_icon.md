---
title: "Changing executable icon"
date: 2022-04-05
forum: General Help
---

### Post by Gordonbp531 on 2022-04-05
Program - ZoHo Notebook
It installed with a generic icon.
I've changed all the executable icons I can find, but the app still appears in the "Show Applications" screen listing with the generic icon.
Can anyone help?

---

### Post by mIk3_08 on 2022-04-05
> **Gordonbp531 said:**
> Program - ZoHo Notebook
It installed with a generic icon.
I've changed all the executable icons I can find, but the app still appears in the "Show Applications" screen listing with the generic icon.
Can anyone help?
Please run this command below in your terminal: to access terminal just  press both ctrl and alt + T or go to your application programs and run the  terminal. Regards and cheers.
```
hostnamectl status
```

---

### Post by Gordonbp531 on 2022-04-05
Static hostname: gordon-ThinkPad-X250
         Icon name: computer-laptop
           Chassis: laptop
        Machine ID: 132b2e9b3675430e99a860e89ce85f27
           Boot ID: 1194efffae8a43c7b6a28fb21d10882b
  Operating System: Ubuntu 20.04.4 LTS
            Kernel: Linux 5.13.0-39-generic
      Architecture: x86-64

---

### Post by ActionParsnip on 2022-04-05
You can edit the files in /usr/share/applications to suit your needs. If they are part of a package then they may be overwritten with package updates

---

### Post by Gordonbp531 on 2022-04-05
I've done that. There's only one notebook file there - notebook.desktop
That has the correct icon.

---

### Post by mIk3_08 on 2022-04-06
> **Gordonbp531 said:**
> I've done that. There's only one notebook file there - notebook.desktop
That has the correct icon.
What is exactly do you want to do? if you want to change the icon you can change it via gedit on your notebook.desktop you should change the address command below:
```
Icon=/homefolder/appfolder/iconfolder/iconname.png
```

---

### Post by Gordonbp531 on 2022-04-06
that did it. Thanks!

---

### Post by mIk3_08 on 2022-04-07
> **Gordonbp531 said:**
> that did it. Thanks! you are always welcome. Regards and cheers.

---

