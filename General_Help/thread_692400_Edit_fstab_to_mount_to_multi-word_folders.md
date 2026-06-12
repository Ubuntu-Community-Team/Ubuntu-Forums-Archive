---
title: "Edit fstab to mount to multi-word folders?"
date: 2008-02-09
forum: General Help
---

### Post by jorwex on 2008-02-09
Hey all,

I'd like to mount my sda5 to a folder called "My Docs" in the /media/ folder. I had it there at one point or another, but I've messed with my partitions a lot since then -- plus that was back when I was too scared to edit the fstab file, so I wouldn'tv known what to look for. 

I tried editting it so the mount point in the fstab file said

/media/My Docs/

but that didn't work. I just left home but before I left, I changed it to

"/media/My Docs" with the quotes and without the forward slash after 'Docs'

I'm skeptical that I got it right, so I was wondering if anyone knew what the correct thing is so I can try it when I get home tonight. 

Thanks!

Jordan

---

### Post by HermanAB on 2008-02-09
Unix file systems accept any character except a NUL and a slash.

A POSIX portable filename uses only the portable character set
[a-zA-Z0-9.-_], and does not begin with a hyphen.

You would avoid lots of head-aches by restricting the characters to the above subset.

---

### Post by jorwex on 2008-02-09
I had it working at one point though! To be fair, those mount points were automatically created based on the volume labels I had set in Windows before I made the switch. Still tho, it seems as though I should be able to accomplish what I want. 

Respectfully, I would like to still go for the multiword label.

Thanks!

---

