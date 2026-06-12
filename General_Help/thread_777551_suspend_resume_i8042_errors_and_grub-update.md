---
title: "suspend resume i8042 errors and grub-update"
date: 2008-05-01
forum: General Help
---

### Post by q5bMzm3V2uh6d on 2008-05-01
Some background information:
I am using an acer 5102 wlmi with ubuntu 8.04.  Suspend would work with the ati driver on 7.10 with no errors.

My problem is that while the computer will suspend properly, it will not resume.  It used to resume but would have all kinds of funky weirdness with the screen going black and white for several seconds.  Then there would be some errors displayed for a few seconds.

The errors were:
i8042 kbd activation failed
i8042 aux activation failed

One suggestion I read was to add i8042.reset grubs menu.lst in the defoptions and run sudo update-grub.

So now I have a line that looks like this:
# defoptions=i8042.rest

When I did this and restarted my computer, resume from suspend no longer worked.  So I removed the i8042 part that I had added. Ran sudo update-grub and restarted my computer.  Once again, even with the modification removed, resuming from suspend still does not work.

That is the only change I have made to my computer.  If more information is needed, please let me know.  If you have any suggestions or hints, they would be appreciated.

---

