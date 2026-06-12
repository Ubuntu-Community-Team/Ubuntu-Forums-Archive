---
title: "Making boot image file on LTSP server"
date: 2008-03-03
forum: General Help
---

### Post by jweeks on 2008-03-03
I have edubuntu 7.10 up and working serving a small group of thin clients made from Dell Optiplex GX240s. To all the thin client manager to view the desktops I installed x11vnc. All this works great. However, I tried to PXE boot two Gateway E1400 and the system hangs up after the edubuntu flash screens shows that it has loaded. I created a etherboot floppy to use instead of PXE built into the BIOS. I can now see that x11vnc is causing the problem. I am getting a lot of info that is hard to read, but I can see that is says that I am trying to run x11vnc without a password. Maybe I need to create an image for these machines that does not contain x11vnc to get them to boot then add x11vnc to that image, but I don't know how. Can anyone help with this problem? Maybe you have a better way to approach it?

---

### Post by krunge on 2008-03-03
> **jweeks said:**
> However, I tried to PXE boot two Gateway E1400 and the system hangs up after the edubuntu flash screens shows that it has loaded. I created a etherboot floppy to use instead of PXE built into the BIOS. I can now see that x11vnc is causing the problem. I am getting a lot of info that is hard to read, but I can see that is says that I am trying to run x11vnc without a password. Maybe I need to create an image for these machines that does not contain x11vnc to get them to boot then add x11vnc to that image, but I don't know how. Can anyone help with this problem? Maybe you have a better way to approach it?

The x11vnc no-password message is only a warning, it doesn't change how the application behaves except for adding a couple seconds to its startup.

It not clear how that would make the system boot hang.  Perhaps there is more information after that message?  Feel free to post the full output.  Maybe x11vnc is blocked on reading a ~/.Xauthority file over NFS or something like that (would that block system startup?)

---

### Post by jweeks on 2008-03-10
Thanks for the reply. I have been experimenting and I have discovered that the problem is apparently a difference in video cards. My server has Nvidia card and the units I was trying to connect to it does not.  I found another PC that I would let me a thin client that has an Nvidia card and it connected.  I believe I need to change the image to a generic card so all the thin clients will boot. Can this be done?:KS

---

### Post by krunge on 2008-03-10
> **jweeks said:**
> I believe I need to change the image to a generic card so all the thin clients will boot. Can this be done?

I don't know; I am not well versed in LTSP.  I hope someone else can pick up your question.

---

