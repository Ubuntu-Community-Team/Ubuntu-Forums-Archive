---
title: "How able to mark partition from system partition"
date: 2023-06-09
forum: General Help
---

### Post by sandy11in on 2023-06-09
In my system, ubuntu system file in having single partition. I want form a other partition.. How?

---

### Post by TheFu on 2023-06-09
> **sandy11in said:**
> In my system, ubuntu system file in having single partition. I want form a other partition.. How?

The answer depends on many things.  Provide more data, like the current layout and what you'd like, and someone can help.
First, there needs to be room for another partition on the storage.  It is also possible that selections during installation (or prior failed attempts) did some things that are unusual to the storage. We need a nice summary of the current state.

The output from these commands is needed:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
```

Please show the command an all output wrapped in _forum code tags_. Without the _code tags_ (adv reply/editor,  (#) button), the columns won't line up correctly, which makes reading the output from very difficult to impossible.  Copy/pasting terminal output then using the code-tag button is pretty easy.  Bold, Underline, Quote forum tags all work similar to code-tags.

BTW, many people post their OS disk layouts in these forums. Sometimes they explain "why" they make specific choices.
The tools to be used differ based on what you have currently, which *file systems* are setup and if there are any *volume managers* involved.  For simple partitions, you'll probably need to boot from a flash drive with an Ubuntu install ISO setup.  **No tools allow changing partitions that have mounted file systems.**  Boot that ISO, choose the "Try Ubuntu" option, then install **gparted**.  

If you checked the _Use LVM_ during install and there is free space inside the VG, we'll need to run some other commands. We aren't there yet. Need to see the output from the 2 commands above first.

---

### Post by MAFoElffen on 2023-06-09
That information would be a snapshot of what is now... Additional would be what you have planned (the goal) of what you want to split out and why.

---

