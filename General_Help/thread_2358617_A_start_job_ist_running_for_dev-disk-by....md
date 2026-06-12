---
title: "A start job ist running for dev-disk-by..."
date: 2017-04-15
forum: General Help
---

### Post by Canaryguy on 2017-04-15
If you are having a slow booting due to this message "A start job ist running for dev-disk-by..." (one must wait 1 minute 30 seconds till the system goes on loading) you can fix it easily:

From the terminal: [B]sudo gedit /etc/crypttab
[/B]
There's a line that starts by: **cryptswap1**....

Write the symbol **#** at the beginning of the line. So the line should be like this: **# cryptswapt...**

Save the file.

Next time you don't have to wait the 90 seconds.

---

