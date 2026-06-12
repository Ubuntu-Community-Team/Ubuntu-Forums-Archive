---
title: "dual Boot Problem"
date: 2007-09-12
forum: General Help
---

### Post by backstrap on 2007-09-12
Here's my problem. I wanted to dual boot my desktop ubuntu/xp. I had xp working and popped in my ubuntu live dvd... followed the instructions, used the live dvd installers partition resizer (which is my problem i think) to resize my xp partition for ubuntu. now what i have is an ubuntu system that boots perfectly... in fact its hella fast. but my xp install splashes then loses video and hangs. i get no video signal, no errors that i can see... but all my files are intact, i can access them via ubuntu. 
normally i would just toast windows but my pc has 1 problem... a soundblaster x-fi soundcard... ie i have a great ubuntu system with 0 sound... sad times. so my question is this... i know my windows filesystem is in place, how can i fix it to boot properly. my grub menu.lst is all in order, xp appears in grub's bootloader. xp splashes then dies in the dark. 

i have been looking around for similar problems via the forums and didnt find anything. if someone can point me in the correct direction i would greatly appreciate it. oh and if there has been a driver release for the xfi cards, let me know :D

baxter

---

### Post by mirzmaster on 2007-09-13
Have you tried running the Windows recovery?  If you boot from your Windows XP CD, you'll encounter an option to recover your installation of Windows.

It's not a pleasant process as it takes nearly as long as installing a fresh Windows XP copy, but it's helped me in the past (I experienced a similar symptoms, but in my case the root cause was invalid video drivers).

---

### Post by backstrap on 2007-09-13
i havent tried a whole recovery. i did use the win recovery cd and ran fixboot, to see if ubuntu had just changed the entry a little...  i was going to try fixmbr but then i think i will have windows working and ubuntu will be gone... anyway i will give that a try. i have no important stuff on my ubuntu partition so if it ends up going away, i will just reinstall it again... using a different method from before.

---

### Post by backstrap on 2007-09-13
ok so running fixmbr fixed my windows installation.. now how do i add an entry for ubuntu?
both operating systems work... i just need the bootloader to not be retarded. 

any ideas? actually heres what i want... since grub didnt like doing both for some reason, is there a way to add my current ubuntu installation to the XP bootloader? or is there a really simple fix to this whole thing?


sorry for being such a noob but i am trying to convert completely. my laptop is 100% ubuntu right nwo, unfortunately due to my soundcard my desktop will be at most 50% until creative launches linux support. then im all over the pure linux.

thanks for the help so far and thanks in advance to anyone else who can help :D

---

### Post by logos34 on 2007-09-13
you can try **WinGrub**
[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

if it doesn't work uninstall it and post back. i have another way

---

