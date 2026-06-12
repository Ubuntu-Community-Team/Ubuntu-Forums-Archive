---
title: "Wacky Chaotic Mess of Graphic Drivers, Desktop Environments, Grub, Kernel, and More."
date: 2013-11-27
forum: General Help
---

### Post by RocketPenguin on 2013-11-27
First off, I am not exactly sure if this is the correct category to post this, considering it could fit under Desktop Environments, Video, and/or Installation/Upgrades. Second, i consider myself medicore in the knowledge of Ubuntu. Since i have not been using it for a while (Laptop couldn't handle the heat) i have forgotten a great deal. Now, to the long story of why i am asking for help, and more specifically, why.

I had just purchase a laptop, a Lenovo G555, from my brother after he had purchased a better computer. Since my old computer couldn't handle Ubuntu 12.04 for more than 15 minutes without over heating, i had stuck to the other os (Windows) i had on my SSD. After i placed my SSD into my new computer, and booted up Ubuntu, the graphics where very strange. Like windows 98, when i would move the tasks i had open, they would leave a trail of copies, spamming my desktop. The background was messed up, as if a still image was chugging, blobs of color all over it, chaotic. Having no clue what was causing this bassar issue, i thought, "If i upgrade to the latest Ubuntu (13.04) it would resolve the issue. So, i began to upgrade to 12.10, an then to 13.04 directly afterwards. When i booted, i received the error
 > Error: File not found
Error: File not found
Error: File not found
Press Any key to continue
I pressed the key, and Ubuntu 13.04 finished booting. Everything was low resolution, the desktop background was solid black, unity/the side taskbar was nowhere in sight, the top bar with shutdown, switch users, etc was gone, and i couldn't open any programs. Until now, i hadn't changed anything that dealt with graphics. After spending hours on google, other forums, IRC Xchat, simultaneously looking for my black screen missing unity issue, and in the corner of my room from the overload of why life isn't fair, i had finally (With the help of a few IRC Xchatters) had the correct drivers installed, without any errors. My graphics card being compatible with ubuntu, AMD ATI Radeon HD 4xxx, it could have been as easy as selecting it in the additional drivers menu. Only problem, it left me with an error telling me to look into my jockey.log. I then rebooted, and BAM! Right after the multi boot screen, right after i hit "Any other key" from the error i previously talked about, it froze, a few seconds later, the screen goes black. And it stays black. xchatters told me it is probably a grub issue, i tried looking into that. With my live disk i burned, (13.04) i remembered. For some odd reason, my laptop cannot recognize live disk. Whenever i try to boot on it, it ignores it. If i take out the SSD, it acts as if the disk doesn't exist, and has nothing to boot off of. I may try burning it again, but again, my computer is too lazy to wipe a re writable disk, meaning i have to use a new one each time. Tinkering around with the multi boot, i found i can go to advanced options, which is right under the "Ubuntu" option, i can choose another (Please correct me if i am wrong, i am not a hundred percent sure.) previous kernel, and boot off of that. I still have the black screen no unity issue, but it boots. Tinkering more, and i found out i can select another environment from the list of environments, i can boot into gnome rollback. FOr some strange reason, Cinnamon doesn't work, crashing each time i try to log in using it, redirecting me to gnome fallback.

Now, my question. How do i solve my (What i think is) grub issue, how do i resolve my black desktop and broken unity, and how do i make sure i have correct graphcs drivers?

P.S. Happy Thanksgiving to all you Ubuntu'ers!

---

### Post by oldfred on 2013-11-27
It does not sound like a grub issue. Grub is just a boot loader and once kernel starts to load grub is not involved. At most you might need boot options in the grub menu like nomodeset. 
I have nVidia so I do not know details on AMD, other than they the main line proprietary driver is not used with legacy cards. I think legacy for AMD means anything before HD5000.

So if your upgrades also updated to the newest proprietary driver you may have a AMD mismatch.

Do not know if something newer available?
 This repository provides AMD Catalyst drivers for legacy graphics Radeon HD 2xxx - 4xxx for several versions of Ubuntu.
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

---

### Post by RocketPenguin on 2013-11-27
This is the tutorial i used for installing drivers: [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

---

### Post by RocketPenguin on 2013-12-03
Yup, you where right! I just re-installed stock drivers, problem solved! Thankies!

---

