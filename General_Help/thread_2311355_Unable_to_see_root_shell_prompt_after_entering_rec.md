---
title: "Unable to see root shell prompt after entering recovery mode due to screen corruption"
date: 2016-01-26
forum: General Help
---

### Post by jerome21 on 2016-01-26
Hi

I am trying to change my root password as Ubuntu no longer lets me install anything via the terminal or make any changes. It continually says 'no such user in sudoer file' after asking for the user password. So I thought to try changing the root password via a similar means to this:

[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

There is also a similar thread in this forum which follows the initial process of entering the menu at start up, and selecting the second option (recovery mode). This text I can see. But as soon as I select this option, the entire screen corrupts. The system is processing something, as I can see the menu shape and what is almost certainly the prompt behind the corrputed lines of text and image - like dashes and dots on the black screen. 

Enough is visible to see that I can scroll down 8 options to get to 'Drop to root shell prompt', but nothing is legible. I am unwilling to start guessing at typing something and wonder if anybody else has ever encountered this. I am using an Acer Aspire laptop with a second larger monitor since the brightness on the laptop has been stuck on full bore for a while - something that apparently can also be fixed in the sudoer area, but because I cannot access the root, I cannot fix it. Perhaps these two screen issues are linked?

Has anybody had something like this before? The monitor is fine otherwise, displaying images correctly once on the desktop. Only on the second menu after selecting recovery mode does it suddenly corrupt every time.

---

### Post by Dreamer Fithp Apprentice on 2016-01-26
> **jerome21 said:**
> I am trying to change my root passwordThis is a forbidden topic here. People advising you on enabling a root password will be chastised by the powers. And anyway, it would be easier to do after fixing the sudo problem first. Of course, after fixing the sudo problem you won't need to enable a root password, and may change your mind about wanting to.> **jerome21 said:**
> 'no such user in sudoer file'Probably better to address that directly anyway. I'd try this:
boot from something else, another partition or a live disk
edit /etc/group
    Look for a line beginning "sudo:" . Your user name should appear on that line, probably following the last colon ( ":"}, If not, be guided by the format of other lines and edit it in, and save and reboot.

If there is nothing to fix there, look in /etc/sudoers
There should be a line like```
%sudo    ALL=(ALL:ALL) ALL
```If not, make a line like that, save the file, and reboot. You don't really need to worry about the warning "This file MUST be edited with the 'visudo' command as root." That's a lie. You can edit it with anything. Be careful. But it is already broken, so you can't make it any worse really. It wouldn't hurt to make a copy before you edit it.

---

