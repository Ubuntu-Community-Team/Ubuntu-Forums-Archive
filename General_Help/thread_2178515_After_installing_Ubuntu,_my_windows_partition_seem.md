---
title: "After installing Ubuntu, my windows partition seems to have slowed down"
date: 2013-10-03
forum: General Help
---

### Post by Adam_Schoe on 2013-10-03
I installed Ubuntu yesterday using the installer and it worked like a charm. Today, while on my windows operating system, I noticed that the computer was moving much slower than I had ever seen it move. I am currently running Windows 7 Home Premium on a Lenovo IdeaPad Y570 laptop. I'd like a way to fix this problem without having to get rid of Ubuntu, since it is a very nice OS, but if I need to I will.

---

### Post by scbingham on 2013-10-03
Maybe Ubuntu runs much faster & it's your perception that windoze is slow ;-)

Seriously though, have you shrunk your windows partition too much? I seem to remember that it needs at least 10% free disk space to run properly. I may be wrong though.

---

### Post by oldfred on 2013-10-03
How did you install Ubuntu. Wubi inside Windows or in separate partitions? 
But either way Ubuntu would not directly change Windows unless you changed something else also.

Post this from terminal in Ubuntu. You can copy & paste into terminal.
sudo parted -l

---

### Post by Adam_Schoe on 2013-10-03
> **oldfred said:**
> How did you install Ubuntu. Wubi inside Windows or in separate partitions? 
But either way Ubuntu would not directly change Windows unless you changed something else also.

Post this from terminal in Ubuntu. You can copy & paste into terminal.
sudo parted -lI installed Ubunti using Wubi inside Windows. This is what I got in the terminal after that command line: 

[IMG]http://i.imgur.com/JeX0J5J.png[/IMG]

I'm not sure what to make of that information though, so could you please explain it to me?

---

### Post by oldfred on 2013-10-03
I was not sure if you knew if you have wubi or not. Seeing only NTFS partitions confirms it is wubi.

Wubi is just a file inside the Windows NTFS partition.
One of the main reason Windows slows down is that it does not have a lot of room to work with. And a large install of wubi could consume some of that space.
How full is NTFS partition? Windows likes 30% free and at 10% free will take forever to run defrag as you have no working room.
If you cannot tell space used from Ubuntu you can run this, But it will only show mounted partitions, so you have to click on /host which is the drive you installed wubi into.  Since you have several other NTFS partitions you can also mount those.

df -H

---

