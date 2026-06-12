---
title: "Solution?: Nautilus not able to move files to trash via NFS"
date: 2007-06-28
forum: General Help
---

### Post by ImpelGD on 2007-06-28
I came across this bug the other day. When accessing an NFS share Nautilus wasn't able to "move" files into the trash, but could permanently delete them. There were also issues with things like moving. It gave an error message regarding a different file system if I remember correctly.

However, I've since changed the exports file on the providing machine to be 'sync' instead of 'async' (and also got rid of the root squash option), in order to avoid potential corruptions and I don't get the error anymore...

Now I know I've seen a [bug report]("https://launchpad.net/ubuntu/+bugs") on this, but can't find it now. So I wanted to post it here on the off chance that I've actually managed to stumble upon something useful instead of asking others as per usual. If someone can establish where the info on this bug is, please let me know or see if the above is relevant if you can test. Thanks.

:)

---

