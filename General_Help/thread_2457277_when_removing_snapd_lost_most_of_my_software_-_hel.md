---
title: "when removing snapd lost most of my software - help!"
date: 2021-01-29
forum: General Help
---

### Post by brownie3 on 2021-01-29
[I don't know much about ubuntu, sorry about that but I will explain as good as I can.]

I have the version 20.04.1 and often have memory shortage problems. For that reason, I already have an executable file to remove old snaps. However this time I need to clear some space on the snapd as I had nearly 3Gb there which I had no clue what it was. 
After searching and finding [HTML]https://ubuntuforums.org/showthread.php?t=2328152[/HTML] a thread about it, the solution seemed to be ```
sudo apt purge snapd
``` as there seemed to be no big consequences - and so I did it.
Now I have lost most of my software - Kyle/TeXMaker, Sublime text editor, Spotify, Telegram,... I did not lose everything (web browsers + other programming languages software) but I would like to understand why this happened and if there is any way to reverse it (especially for Sublime as there were important not saved info there).
Any help?

Thank you for any piece of information!

---

### Post by howefield on 2021-01-29
> **brownie3 said:**
> ...but I would like to understand why this happened and if there is any way to reverse it..

To reinstall your applications (which appear to be snap packaged applications) you will need to reinstall snapd. Uninstalling the snapd package as you have done, also removes the snap packaged applications. The output of the terminal would have stated exactly what was being carried out after you entered the remove command.

```
sudo apt install snapd
```

Then reinstall your above mentioned applications the ame way as you did originally.

Your main problem appears to be a lack of disk space rather than a lack of memory ? That being the case you will still have that issue unless you can increase the disk space given to your Ubuntu installation.

---

### Post by brownie3 on 2021-01-29
Thank you for the explanation! I installed it again now but I guess I can't recover the lost data.
I understand the logic of it but I have not installed anything new (except updates), I move big files to my hard drive when I receive them and it was the first time I got the shortage of disk space notice since I updated to Ubuntu 20.04 in these 2 months.
Could the snapd have keep also old versions like snap?

---

### Post by Impavidus on 2021-01-29
I don't think old versions of snaps are removed automatically and the snaps are quite large, so it quickly piles up. Removing snapd removed all snaps. I haven't checked this, but I think that at least all user files belonging to those snaps (like configuration of the software) are still in your home directory and should be used again when you reinstall the snaps. User files you edited using the snaps aren't affected – files aren't tied to applications in any way – but unsaved changes when the application wa killed may be gone. Maybe the application saves files automatically. I can't be sure of all that, as I don't use snaps. All software I want is available as .deb packages (or, very rarely, source code).

---

### Post by brownie3 on 2021-01-29
Thank you so much! 
I will put this as solved

---

### Post by TheFu on 2021-01-29
By default, snapd kepes 3 versions of the snap packages.
The lowest setting allowed is 2. There is a snap command to change that documented some where.

There are many discussions about the pros/cons of snap packages already in these forums and elsewhere online. Go read those. But for someone new to linux, some of the terms will require research to understand.

---

