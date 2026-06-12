---
title: "No thumbnails with Panasonic Lumix camera in Ubuntu 18.4"
date: 2020-06-07
forum: General Help
---

### Post by HC48 on 2020-06-07
Hello, I have searched in English and French but have not found a solution or I have not understood what I have read so far. I need an answer in simple language if possible.( I have noticed that other people have similar problems however in Ubuntu 18.4 in that the thumbnails have disappeared in photo and video files.) When I connect my camera I just get black squares with jpg in them.When I open the files in image viewer I see the picture.I have checked the preferences in Files- preferences- search and preview but it seems ok.'Thumbnails' is checked for 'all files'. I have the same problem when I want to download files from my cellphone. Thank you for any help.

Here are a few more details. My camera is a Panasonic Lumix, DMC TZ55 and the size of my photos is around 5.5MB. I tried to set the preferences in <Files-preferences- search and preview-thumbnails> to 'all files' and 'only files smaller than  6000MB', but the size goes back to smaller than 4096MB automatically even when I reboot my PC.

When I open with Shotwell I get the message ' unable to fetch previews from the camera/ could not claim the USB device (-53)'. I'm wondering if it's a problem with permissions. The digital card works in the slot of my laptop ok. I get thumbnails and photos. The problem is on my PC only.
Hoping someone can help. The problem isn't stopping me from exploiting my digital photos but it would be easier if I had previews/thumbnails. Thank you in advance for any advice. :)

---

### Post by HC48 on 2020-06-20
I had a break from this and then found this: [https://askubuntu.com/questions/1140576/nautilus-doesn-allow-thumbnail-for-image-size-above-4096-kib](https://askubuntu.com/questions/1140576/nautilus-doesn-allow-thumbnail-for-image-size-above-4096-kib)
"No workaround found, upgrading to Ubuntu 19.04 solved the issue. I successfully tested 8MiB and 10MiB thumbnail size limit using Nautilus preference pane." was the solution.
Also suggested here: 
"a workaround is: installing gthumb, **($sudo apt install gthumb)** a more professional image viewer, and very useful. I tested it can preview at least +5M JPG. HIH"
Could anyone tell me if this last idea is a good solution? I hesitate to install things I don't know. There seem to have been some problems with gthumb and I already have shotwell. I hesitate to upgrade as I've just got used to ubuntu 18.04.
Thank you for any advice. :)

---

### Post by CelticWarrior on 2020-06-20
Installing software from the official repositories is safe.

---

### Post by HC48 on 2020-06-20
Thank you Celtic Warrior.

---

### Post by HC48 on 2020-06-24
Installed gthumb and it gives access to the home folder so I can see my camera DCM file thumbnails. Problem solved! :)

---

