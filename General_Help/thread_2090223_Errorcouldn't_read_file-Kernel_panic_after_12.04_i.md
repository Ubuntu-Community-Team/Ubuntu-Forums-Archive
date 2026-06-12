---
title: "Error:couldn't read file-Kernel panic after 12.04 installation"
date: 2012-12-01
forum: General Help
---

### Post by AAEIV on 2012-12-01
I have just installed ubuntu 12.04.1. To be honest I had to run installation several times until it was finished fine. When I finally managed to install it properly, I power on the laptop and the grub shoed up! I selected ubuntu generic. It takes some time to load and when it does I get an error message stating that

```
error: couldn't read file
Press any key to continue
```

If I press any button nothing happens. If a leave it there, in a short while there is a black screen loading which gives some weird messages

```
[0.946710] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
[0.946755] Pid: 1, comm: swapper/0 Not tainted 3.2.0-29-generic #46-Ubuntu 
[0.946792] Call Trace:
[0.946831] [<ffffffff81640ec8>] panic+0x91/0x1a4
[0.946869] [<ffffffff81cfc01e>] mount_block_root+0xdc/0x18e
[0.946909] [<ffffffff81002930>] ? populate_rootfs_wait+0x300/0x9d0
[0.946947] [<ffffffff81cfc257>] mount_root+0x54/0x59
[0.946982] [<ffffffff81cfcec9>] prepare_namespace+0x16d/0x1a6
[0.947019] [<ffffffff81cfbd63>] kernel_init+0x153/0x158
[0.947094] [<ffffffff81cfbc10>] ? start_kernel+0x3bd/0x3bd
[0.947129] [<ffffffff81664030>] ? gs_change+0x13/0x13
```

The thing is that the laptop isn't mine. A friend tried to **dual boot** ubuntu alongside windows 7 but he **didn't succeed**. Ubuntu option was in grub, but when you tried to boot it rebooted from the start. So from a **Live CD** I **erased ubuntu**, started windows to check if something went wrong, and fortunately everything was OK. Windows started normally!

So I tried to install ubuntu. Before installation was completed the **installer crashed**! I was afraid that he would **lost windows**, something that was true...

At that point I tried to **install windows** but whichever distro(XP, 7{home, proffessional, ultimate},8) I tried it **could never reach the end**.

So I tried to **reinstall ubuntu** but I was facing those **weird messages**. What can I do to move on?

---

### Post by AAEIV on 2012-12-02
I tried to check and fix(if possible) with GParted it took a lot of hours,although gparted displays only 01:14, I restarted the system and now I get not exactly the same messages.

Numbers in braces [] are different

```
[0.818189] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
[0.818235] Pid: 1, comm: swapper/0 Not tainted 3.2.0-29-generic #46-Ubuntu 
[0.818272] Call Trace:
[0.818312] [<ffffffff81640ec8>] panic+0x91/0x1a4
[0.818351] [<ffffffff81cfc01e>] mount_block_root+0xdc/0x18e
[0.818391] [<ffffffff81002930>] ? populate_rootfs_wait+0x300/0x9d0
[0.818428] [<ffffffff81cfc257>] mount_root+0x54/0x59
[0.818464] [<ffffffff81cfcec9>] prepare_namespace+0x16d/0x1a6
[0.818501] [<ffffffff81cfbd63>] kernel_init+0x153/0x158
[0.818574] [<ffffffff81cfbc10>] ? start_kernel+0x3bd/0x3bd
[0.818610] [<ffffffff81664030>] ? gs_change+0x13/0x13
```

What on earth is going on?

**EDIT:** I forgot to mention that my friend gave a punch to his laptop during a game. After that his cooler became to make a weird noise so I checked and it is a bit tortuous but it is working. What I beleive must be wrong is that his HDD makes a weird noise while trying to load ubuntu, which means he might need a new HDD. Could that be true?

---

