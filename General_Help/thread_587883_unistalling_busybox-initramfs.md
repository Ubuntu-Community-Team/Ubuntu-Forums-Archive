---
title: "unistalling busybox-initramfs"
date: 2007-10-23
forum: General Help
---

### Post by nikef on 2007-10-23
Hi
can any1 help

i have upgraded to gutsy 7.10,but the pc will not boot up

this is the error i get 

busybox v1.1.3/debian 1.1.1.3-5ubuntu7 built in shell (ash)

now while searching in synaptic  package manager i found this installed

Busybox -initramfs

now,what i want to know,can i safely remove this,or will it cause problems,because i think if this was unistalled my pc would boot up normally

thanks for any help

trish

---

### Post by Kaptain Chaos on 2007-10-23
Hello,

Sorry for the delay in answering your post.

I wouldn't recommend uninstalling it because (from my limited understanding) the dependencies will mean that your system won't boot.

I've been having problems with the busybox-initramfs issue too. I don't pretend to understand why or how it's happened, but it seems to be related to the new kernel upgrade - my upgrade boots fine from the previous kernel but not the newer one. I thought I'd try a fresh install in case there were problems related to the upgrade, but no change! Searching on other posts confirms (to me) that the problem stems from having more than one hard drive installed on the system.

As a work around, I've found that once the busybox initramfs error is displayed, typing the word return (or exit) allows the boot up process to complete in text mode until you reach the login screen. Gutsy runs BUT (and it's a problematic BUT) it only recognises one hard drive; I'm unable to access the other drive (which holds my linux swap partition amongst other shared folders).

Not sure how to correct this at the moment

---

### Post by nikef on 2007-10-23
Thank you for your post
i made an error above ,i can not edit my post,i meant to say i can not boot the pc
i have read your post,i only have 1 hard drive, i will try out what you said and leave busybox alone

---

