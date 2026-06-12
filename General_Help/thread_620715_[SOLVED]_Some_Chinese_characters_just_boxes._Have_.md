---
title: "[SOLVED] Some Chinese characters just boxes. Have Language packs installed."
date: 2007-11-22
forum: General Help
---

### Post by cookies on 2007-11-22
Even though I can't read a letter of Chinese, I still like to be able to display as many languages as I can. I followed the Tutorial for Sharp Fonts:
[http://ubuntuforums.org/showthread.php?t=208396&highlight=sharp+fonts](http://ubuntuforums.org/showthread.php?t=208396&highlight=sharp+fonts)

But I decided I like my Anti-Aliasing, so I removed the lines that stop anti-aliasing. Now, my Chinese font has gone wonky, and instead of letters, I get boxes in some places. I know this is a font issue, but I don't know how to solve it, because the letters display if I use another font that is tailored to Chinese.

See attachments for fontconfig files and screenshots.

---

### Post by cookies on 2007-11-23
Okay I fixed it. Turns out I had added SimSun to the local.conf file for all aliases, and that had gotten removed. And, Arial seems to to think I has the characters when it does not.

---

