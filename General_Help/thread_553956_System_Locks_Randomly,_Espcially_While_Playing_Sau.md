---
title: "System Locks Randomly, Espcially While Playing Sauerbraten (Cube Engine 2)"
date: 2007-09-18
forum: General Help
---

### Post by GenuineXP on 2007-09-18
I posted about a related (more general) issue I'm having before, but that post got washed away in the torrents of posts in this forum. This problem seems to crop up when I'm playing Sauerbraten now, so I'm suspicious of my graphics card and video drivers.

Anyway, while playing Sauerbraten, the game inevitably locks up after a while (anywhere from two minutes to an hour). Everything just freezes. I play my own music in the background, and that always seems to continue playing, but everything else dies. I can't ssh into my box either, which tells me something bad happened.

This is the output from my messages log.

```
Sep 18 11:58:25 omega kernel: [ 1684.190396] warning: many lost ticks.
Sep 18 11:58:25 omega kernel: [ 1684.190399] Your time source seems to be instable or some driver is hogging interupts
Sep 18 11:58:25 omega kernel: [ 1684.190428] rip 0x2b22dfcaa932
Sep 18 12:11:31 omega -- MARK --
Sep 18 12:30:32 omega syslogd 1.4.1#20ubuntu4: restart.
```

Whenever I've experienced this problem (random locking up), this is the type of output I get. There are many lost ticks, and some driver is hogging interupts. The "rip" message shows up occasionally.

Does anyone know what could cause this? It's getting very, very irritating and sometimes the system locks up when I'm not even playing a game (though rarely). I'm using Compiz Fusion, btw.

I have an nVidia GeForce 6600 GT PCI-Express graphics card and am using the nVidia graphics drivers from the Restricted Drivers manager. Is there a known problem with this configuration?

Any help is greatly appreciated. Thanks!

---

### Post by gmaniac on 2007-09-18
I don't know. Have you tried searching the web.
I found something similar here... 
[https://bugzilla.redhat.com/show_bug.cgi?id=55223](https://bugzilla.redhat.com/show_bug.cgi?id=55223)
check it out. There could be something there for you to try.

BTW if you find the answer don't forget to post it here for others to find ;)

---

### Post by splintercellguy on 2007-09-18
Booting with noapic or disabling SMP may do the trick.

---

### Post by GenuineXP on 2007-09-18
Okay, I've appended "nosmp" and "noapic" to my /boot/grub/menu.lst. I'm not sure about the syntax though, so I'll just have to reboot and see what happens (and if that fixes the problem).

The above link to that system clock bug could be related; I'm playing network games when the lockup occurs.

Thanks for the replies. Any additional ideas are welcome.

---

### Post by GenuineXP on 2007-09-19
No luck. I played Sauerbraten for about thirty or so minutes last night and it locked up again. I also experienced another problem I'm having: I'll suddenly lose keyboard and mouse control. That is, I'll be using my computer (maybe just browsing the Internet and listening to music, etc.) and suddenly nothing responds to my mouse clicks and the keyboard does nothing almost as if it's been disconnected. This has happened too often, and I either have to reboot (Ctrl+Alt+Backspace does nothing; the keyboard stops functioning) or I have to SSH into the machine from my laptop and kill the x-session-manager process.

Does anyone have any (more) ideas about what the problem could be? Should I continue to boot with nosmp and noacpi? Ubuntu is becoming unusable; I can't go a day without having to reboot my computer (sometimes four times or so)!

Thanks!

---

### Post by dude0367 on 2008-05-30
I FOUND OUT HOW TO MAKE IT CONTINUE PLAYING! \\:D/\\:D/ first have two windows open then when it freezes hit the power button once which reactivates the keyboard to some extent then use the arrows to select "cancel" hit enter. then hit "alt-tab" to reopen the page then you can either quit out or continue playing. :guitar:

---

