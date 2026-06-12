---
title: "Failed to start systemd-journald.service"
date: 2024-06-27
forum: General Help
---

### Post by hlupaku on 2024-06-27
Hello everyone! Right off the bat I'd like to say that I'm sorry if I say something gramatically wrong as I'm not native. Anyways, I love linux but it hates me. A few days ago, I dualbooted ubuntu and everything was great! Everything worked and everything was perfect apart from one thing. As I got it to use for gaming, I wanted to mount the drive that had my windows installation on it and many of my steam games. I mounted it with some tutorial I found online and it kinda worked. You could read the drive but steam still wouldn't recognise it. I thought it might've just needed a restart so I did exactly that. And that was the last time I saw ubuntu. For the past 3 days, I cannot boot into ubuntu. After the restart it was just a blank screen. Since I didn't have anything important on the drive linux was on, I just formatted it and wanted to just do it all over again (install ubuntu). And that's where we currently stand. I boot the live environment and either I get absolutely nothing or it will show the boot screen, but doesn't go any further. When I'm lucky and get to the boot screen and press ESC it is just looping trying to apparently start systemd-journald.service, it fails and it tries again, and that's all it does. I tried different usb drives and it didn't work (they worked on my other computers). I resetted my bios incase I had some settings it didn't like. Heck, I even reflashed my motherboards bios just trying to get it to work, but no dice. I tried a different distro (Nobara) and it's the same issue. And just to top it off my windows is now extremely slow and starts to freeze sometimes. I could not find a single thread having the exact problem as I do, because I cannot even get to the terminal as it has not been installed yet (as far as I can tell). I tried installing it on a drive on a different computer and it just doesn't work. I spent so many hours trying to fix this thing, but I'm literally just a random kid in his teens trying to learn linux. So, I come before you hoping you might know what could be going on. I wonder if I could somehow disable the journal service, but at this point in time I don't even know what I'm talking about. Also, I apologise if this is the wrong forum to post this thread into, but I have never written anything on any forum. Any kind of help is extremely appriciated! Here is an image of all it does: [https://imgur.com/a/i6ZDp39](https://imgur.com/a/i6ZDp39). 

Here are the specs of my pc if that's of any help, but considering ubuntu ran perfectly before, I doubt there is any sort of a compatibility issue:
Intel Core i5-11400f
16GB RAM running at 3200MHz
RTX 3060 
Gigabyte B560 DS3H V2

---

### Post by currentshaft on 2024-06-27
What version of Ubuntu did you dual boot?

How did you create a bootable USB?

What type of storage device are you using?

Have you run any hardware diagnostics from BIOS?

And don't they teach how to write in paragraphs in school anymore? I know you're young, but surely the irony of confusing readers with a wall of text is not lost on you?

---

### Post by hlupaku on 2024-06-28
Alright so after hours of ripping all my hair out, it was a compatibily issue. I have a PCIE GEN4 gpu and I'm using a PCIE GEN3 riser cable and I have a setting in bios to set it what I want it to be and because I resetted the bios the setting went to it's original setting which was auto. Changing it to gen 3 fixed it and everything is working perfectly now. Just puting this here in case someone has the same issue.

---

