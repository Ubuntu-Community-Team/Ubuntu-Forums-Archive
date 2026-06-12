---
title: "[SOLVED] Here's a weird one!"
date: 2007-02-24
forum: General Help
---

### Post by anyoneseenmypenguin on 2007-02-24
Ok first let me say I am fairly new to Linux but have many years of computer experience. I installed Edgy on my daughters computer and have been playing on it for a few days now and  lovin it. The computer has a small hard drive only 6.4 Gig but still has 3.0 Gigs free after some customizing. The other night I was downloading 2 new apps from the add remove programs gbaker and  VLC player. I left the pc running overnight as I only have a dialup connection and in the morning I had a message not able to complete the download. So I tried to connect again and could not I figured some kind of server problem so I re-booted and when I went to log in I could not and received a familiar error message GDM could not write your authorization file.... you know the rest. So I've learned alot about using the terminal to check my hard drive. I thought it can't be full could it? when I df -h it showed 100% used?? Huh?? can't be so I ran some other commands to free up space apt-get autoclean and others but to no avail. I finally decided to upgrade the hard drive to a 80 Gig drive I had here and now I'm learning how to add it to the system. Now here's the best part,I was not successful at adding the drive I partioned it and formatted it but was looking for some kind of cloning program when I went back to the pc I rebooted and used the grub recovery console I checked the drive again and now it showed correctly 48% used. Then I proceeded to log into the gnome desktop almost as usual. The system is not as stable sometimes logs in and sometimes does not,when it does not the df -h shows usage at 100% again. Some weird stuff going on? Almost virus like. Any idea's? The system uses a AMD Duron processor with 384 megs of ram.:confused:

---

### Post by cronholio on 2007-02-25
That's really strange. Do you notice a lot of HD activity while using the system?

---

### Post by haricharan on 2007-02-25
try ```
du -sh
``` for each directory in / to find disk usage and see which one is occupying the most

---

### Post by Tomosaur on 2007-02-25
I too have had this problem. The cause (for me, at least) was that I had run out of space in my home directory. Try switching to the terminal when you hit the 'could not write to xauthority file' (by hitting ctrl+alt+f1), logging in that way, then deleting any unwanted files using ```

rm <filename>

```

Worked for me.

---

### Post by anyoneseenmypenguin on 2007-02-25
Hi there thanks for the replies my system is back up now (I'm not sure why) my disk usage is where I remember it to be @ 47% approximately 3 gigs free. I did notice on startup with in the nautilius window the little icons that load when the system loads correctly there is a window icon a gnome icon and a show desktop icon but when the system does not boot up correctly instead of the last icon (show desktop) I have the Update manager icon showing. I think if updates were to continue my drive may have been filled up ( although seems unlikely) Also when I was back into my system all my settings for my modem where wiped out ( I use Gnome PPP) and the system did not detect my modem until I switched it off and back on again. I did use the du -sh command but I could not remember how to display one screen at a time and I did not know which files were safe to delete? rm command or even which directories (if any) are safe to delete? :confused:

---

### Post by haricharan on 2007-02-25
well..its good to hear that ur problem is solved :)

---

### Post by anyoneseenmypenguin on 2007-02-25
Anyone know when you need to free up space and use the du -sh command  how to display one screen at a time and which files are safe to delete? (rm command )or even which directories (if any) are safe to delete?  :-k

---

### Post by haricharan on 2007-02-25
u can use ```
du -sh | more
``` to show page by page...but as far as i know u should not delete any directory except the files in ur home directory that u can delete...

---

### Post by anyoneseenmypenguin on 2007-02-25
Thanks all!:)

---

