---
title: "can't save images from telegram desktop"
date: 2022-05-07
forum: General Help
---

### Post by ronjjjg8885 on 2022-05-07
no matter what i've tried.

i've installed it from the 'shop'

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290408&stc=1[/IMG]

---

### Post by ronjjjg8885 on 2022-05-11
anyone?

---

### Post by #&amp;thj^% on 2022-05-11
maybe this? [https://www.maketecheasier.com/fix-telegram-not-saving-images-to-gallery/](https://www.maketecheasier.com/fix-telegram-not-saving-images-to-gallery/)
It's a long read but beneficial.

---

### Post by ronjjjg8885 on 2022-05-28
at the end i've switched to telegram web because of many annoying bugs

---

### Post by DuckHook on 2022-05-29
I didn't see this until now.

Your problem may have been due to installing the snap version of Telegram. Did you? If so, the default sandboxing settings may prevent you from saving files/photos to your /home directory.

If above is true, then you have two options:

[LIST=1]
[*]Set the sandbox to allow access to "external" drives. This is misleading: it will also allow access to /home
[*]Delete the snap version of Telegram and install from PPA: ```
sudo add-apt-repository ppa:atareao/telegram
```The usual cautions with PPAs (malware, bugs, apt breakage) apply.
[/LIST]
If your version was not the snap, then where did you install from? How did you install it? Give precise details.

---

