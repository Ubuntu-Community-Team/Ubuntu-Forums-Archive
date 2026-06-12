---
title: "Can't upload anything via any webbrowser in Ubuntu 22.04"
date: 2022-09-19
forum: General Help
---

### Post by Semn on 2022-09-19
Hi, I try to upload some attachments on my email account, and also on a canvas account for university , but all the buttons for upload are non-responsive. This happens in all browsers, Firefox, Chrome and Opera. There is a minor difference on which of the three freezes completely, while the others just do not respond to the upload button. 

I have no idea what to do, I tried updating the system, so I am obliged to use Windows at this stage.

Any ideas?

---

### Post by ajgreeny on 2022-09-19
Are all those browsers snap versions?

I have not used Opera since about 2003 so have no idea how it can be installed now. However both chromium and Firefox are snaps by default which could be behind your problem as they can access only certain folders in the filesystem. I do not use any snaps so can't give more details of this.

---

### Post by Semn on 2022-09-19
No, they are installed via DEB files, and its worse, I can't close the windows when it doesn't respond to upload button.  They remain open and the close (X) button does not do anything. So this seems to be systemic problem. I have to reboot to close those windows.

---

### Post by The Cog on 2022-09-19
> No, they are installed via DEB files.
That doesn't mean they are not snaps. I know that the Ubuntu .deb file for Firefox is just a bait-and-switch installer that actually installs the snap. I would not be surprised if the others do the same. 
Mozilla themselves offer a tar.bz file: [https://www.mozilla.org/en-US/firefox/new/](https://www.mozilla.org/en-US/firefox/new/)

Before you give up on Linux altogether, try installing Mint. It's based on Ubuntu, but without the snaps silliness. The desktop interface is rather different, but having tried it, I prefer it. Try a live installer first, to get a flavour.

---

### Post by Semn on 2022-09-19
Will do! Thanks for the tip.

---

### Post by Semn on 2022-09-19
> **The Cog said:**
> That doesn't mean they are not snaps. I know that the Ubuntu .deb file for Firefox is just a bait-and-switch installer that actually installs the snap. I would not be surprised if the others do the same. 
Mozilla themselves offer a tar.bz file: [https://www.mozilla.org/en-US/firefox/new/](https://www.mozilla.org/en-US/firefox/new/)

Before you give up on Linux altogether, try installing Mint. It's based on Ubuntu, but without the snaps silliness. The desktop interface is rather different, but having tried it, I prefer it. Try a live installer first, to get a flavour.


Hi,I am running Linux MINT now on the same machine. Everything works smoothly compared to Ubuntu 22.04. Also, I  noticed copying from USB stick to computer is faster with MINT than Ubuntu (weird?). Thanks for the tip, it solved the whole problem (which was related to the machine type - DELL E6430 which has chronic problems with Ubuntu 22.04)

---

### Post by The Cog on 2022-09-19
Thanks for the feedback. I'm glad you like mint.
I don't understand why copying from USB should be faster though - mint is mostly Ubuntu, especially underneath the visible UI.

---

### Post by Semn on 2022-09-19
But Mint had no problems with the hardware of DELL E6450 which Ubuntu 22.04 has had. Mint appears to be more stable, plain and simply. And USB transfer was faster indeed, from USB to computer (Mint) than computer to USB (Ubuntu 22)

---

### Post by ajgreeny on 2022-09-19
> **Semn said:**
> But Mint had no problems with the hardware of DELL E6450 which Ubuntu 22.04 has had. Mint appears to be more stable, plain and simply. And USB transfer was faster indeed, from USB to computer (Mint) than computer to USB (Ubuntu 22)
That is probably to be expected as writing to a USB disk will always be slower than reading from that same disk.

---

### Post by Semn on 2022-09-20
Okey, thanks

---

