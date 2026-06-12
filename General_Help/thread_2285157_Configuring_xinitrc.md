---
title: "Configuring xinitrc"
date: 2015-07-03
forum: General Help
---

### Post by DanielWEWO on 2015-07-03
Hey guys, I done funked. So I was typing fast and was attempting to delete another file, and did a sudo rm xinitrc lol :roll: . Well I'm starting to rebuild it and I'm having trouble figuring out what needs to be done.

When I log in now I get only "dummy output" as my only audio output. I can solve this with a 
```
sudo setfacl -m u:daniel:rw /dev/snd/*
``` but I have to enter that every time. I tried adding that line to xinitrc but no dice. I'm clearly not understanding something here. I was wondering if you guys could help me out getting ubuntu to configure my sound on startx.

Also, I have another "issue" that's not really an issue, just something a little annoying. Gnome now asks me for permission to do almost anything: shutdown, reboot, mount disks; kind of how Xfce4 does. I'm assuming this is some line I can add to xinitrc.

The only thing in my xinitrc right now is ```
exec gnome-session
```

I'm using 14.04 with Gnome 3, and I currently boot into tty1 with no gui started on F7 as configured in grub.

You guys rule :D pls help ily


Edit: so apparently I've run into a more difficult issue. I am having trouble launching steam and games involved since accidentally deleting my xinitrc file. Every time I launch steam I get "OpenGL GLX context is not using direct rendering, which may cause performance problems." I am indeed using direct rendering. I've attempted the solution where you remove the libraries that steam provides that depend on that, and still have the issue. I've completely reinstalled steam, and reinstalled fglrx-updates. I still get the issue. I'm assuming this is related to me deleting xinitrc because this problem never occured before. I've just spent the last two hours googling and trying every possible solution out there and I just can't figure it out. ](*,)

---

