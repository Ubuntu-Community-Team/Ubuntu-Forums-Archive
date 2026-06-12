---
title: "screen resolution problem"
date: 2006-10-28
forum: General Help
---

### Post by waldick on 2006-10-28
i installed edgy and now my screen resolution won't go above 800x600...i edited the xorg.config, restatred x, but the reslution manager still only shows two options, the highest one being 800x600 ...

what am i doing wrong ?

---

### Post by geneticmaterial on 2006-10-28
what type of video card do you have?

---

### Post by ezphilosophy on 2006-10-28
> **waldick said:**
> i installed edgy and now my screen resolution won't go above 800x600...i edited the xorg.config, restatred x, but the reslution manager still only shows two options, the highest one being 800x600 ...



Don't know if you already did a:
sudo dpkg-reconfigure xserver-xorg

but try that and select the resolution you want to use.

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Look here at the "problems section" point 5

---

### Post by peterson23 on 2006-10-28
pls.. tell some details related to this.:-?

---

### Post by waldick on 2006-10-28
the config file has all the resolutions setup properly, but when i go to the gui, it just gives me 640x480 and 800x600...

i'm running an apple g4, but i had much higher resolution when i ran dapper...

very strange

j

---

### Post by stream303 on 2006-10-28
Quickest way I know:

1. In terminal, do
lspci
to find out what card you have

2. sudo dpkg-reconfigure -fgnome -phigh xserver-xorg
This will bring up a gnome dialog that asks you for your card manufacturer and then lets you choose your desired resolution.

---

### Post by waldick on 2006-10-29
that worked...great

thanks alot...

now i can actually see all of the pop-up dialog boxes....

thanks again,

j

---

