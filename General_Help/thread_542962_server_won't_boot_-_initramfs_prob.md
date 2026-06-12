---
title: "server won't boot - initramfs prob?"
date: 2007-09-04
forum: General Help
---

### Post by malder on 2007-09-04
My feisty server did not come back up after rebooting. Nothing changed on the reboot. I just wanted network settings to reconnect after I had a router go down... didn't want to login as my server is sort of hard to get to.

Here is what I get on boot:

```
Failed to execute /init
Kernel panic - not syncing: No init found. Try passing init= option to kernel.
```

I found a  [page on a gentoo related site]("http://gentoo-wiki.com/SECURITY_System_Encryption_DM-Crypt_with_LUKS#FAQ") (down towards the bottom - or search for  "failed to execute") that appears to address the problem, but I'm lost with the solution presented.


Can anyone tell me if this [page ]("http://gentoo-wiki.com/SECURITY_System_Encryption_DM-Crypt_with_LUKS#FAQ")I found is going to be applicable to my situation?

I've searched hard for a more detailed article about this issue, but have only come up with that page. I was hoping someone had an article that was a little more detailed on how to accomplish the fix... anyone?

Thanks

---

### Post by malder on 2007-09-04
Is there any way I can just overwrite the kernel... recompile... something? I'm open to options....

:confused:

---

### Post by malder on 2007-09-05
bump - anyone?

---

### Post by Midahed on 2007-09-05
In the absence of any other suggestions....

I'm not familiar with the server installation CD, but maybe it has a 'rescue' option like the workstation version.  Alternatively, can you boot the installation CD as a live system and take a look round your hard drive to try to see why it isn't booting.

Mike

---

### Post by Midahed on 2007-09-05
By the way, did your problem arise after the recent kernel update?  I haven't applied it yet because I want to do a full backup before running it, but I have seen a few posts recently from users saying their systems wouldn't boot afterwards.  It may be worth doing a search for 'kernel update' to see what falls out of the woodwork...

Mike

---

### Post by malder on 2007-09-06
The server distro does not come with a livecd install, just straight text. I think I'll grab my desktop edition from home and poke around that way. We'll see what happens.

I know the problem didn't arise from any update because this was the second reboot in as many days and no upgrades in between. At least not that I remember - was a pretty short time span, so ....

Kernel update didn't bring anything of interest up on search...

Thanks for the input. I'll post when I figure it out. Hopefully it isn't a reinstall. What a pain that would be...

---

### Post by bogolisk on 2007-09-06
> **malder said:**
> The server distro does not come with a livecd install, just straight text. I think I'll grab my desktop edition from home and poke around that way. We'll see what happens.

I know the problem didn't arise from any update because this was the second reboot in as many days and no upgrades in between. At least not that I remember - was a pretty short time span, so ....

Kernel update didn't bring anything of interest up on search...

Thanks for the input. I'll post when I figure it out. Hopefully it isn't a reinstall. What a pain that would be...


It might be just:
[list]
[*] boot with any liveCD or usb-key linux (I have mini-grml on a usb-key, very convenient).
[*] mount the disk.
[*] check if the appropriate /my_harddisk_mount_point/boot/initrd.img-2.6.xxxx (it's just a gzipped cpio archive) a non-corrupted /init file
[*] replace that initrd.img-xxx with the original one from the server CD.
[/list]

It might help!

---

### Post by malder on 2007-09-06
I threw my Feisty desktop cd in and tried to boot up the livecd. Stragely enough I got a similar error. Popped in my Knoppix - similar error (something about init not loading and kernel panic). Figured it must be a hardware issue. 

Memtest ran for a while and came up with tens of thousands of errors ( I think I stopped it at 30,000+)

I pulled the 2 older sticks of ram out and like magic, it booted up as it should.

SOLUTION: new ram. 2 gigs on it's way!

Thanks everyone for the help

---

