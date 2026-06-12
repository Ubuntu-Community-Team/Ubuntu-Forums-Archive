---
title: "What command to defragment BTRFS partition using maximum compression ?"
date: 2021-01-03
forum: General Help
---

### Post by aug7744 on 2021-01-03
Hello.
Using the command below
sudo btrfs filesystem defragment -v -r -czlib -f /
defragment an BTRFS partition root using compression zlib.

in fstab is possible select zlib compression 1 to 9.
strange detail is that defrag command allow to select zlib, but not has  any information if is possible select low or high compression.
trying to use czlib:9 or c zlib:9 result in error and not will run the command.

If using defrag command will use zlib compression settings from fstab ?  will use maximum compression ? If not how is possible configure to use  maximum compression ?
Thanks for reply.

---

