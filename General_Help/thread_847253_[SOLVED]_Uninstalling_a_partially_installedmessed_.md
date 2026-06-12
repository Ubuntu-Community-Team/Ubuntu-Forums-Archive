---
title: "[SOLVED] Uninstalling a partially installed/messed up ubuntu"
date: 2008-07-02
forum: General Help
---

### Post by lotrkev on 2008-07-02
OK. Here is my story. I have 2 computers, and both have Windows XP. On one, I successfully installed and am happily running and using Ubuntu Hardy. On the other, I tried to install Ubuntu, but it is messed up. At the setup screen, it failed the partition set-up with an "exit error 10". So I clicked continue anyway (after clicking retry, but then it just did nothing). And it went to the login screen. When I tried to login, it acted as if it was logging in, but then it just went back to the login screen.
Any help would be GREATLY Appreciated. Thanks!

---

### Post by Elfy on 2008-07-02
I would boot the livecd - from there you can either reinstall or use the partition editor to remove the partitions it made.

Does it have any other os on it as when you delete the partition if it did remove the original boot ti would be gone after deletion.

---

### Post by lotrkev on 2008-07-02
How do I get to the partition editor from the livecd?

---

### Post by Elfy on 2008-07-02
It's in the system admin menu - if when you open it there are padlocks on swap partitions, which is unlikely if the partition failed originally, run

```
sudo swapoff -a
```

That assumes it's hardy - can't remember if it's available in gutsy or feisty - if not install it

```
sudo apt-get install gparted
```

---

### Post by lotrkev on 2008-07-02
Well, I would do that, but in order to do so, I need to solve the problem of logging in, so I can use  it. (remember I can't login, thats why I want to uninstall it and try installing it again)

---

### Post by Elfy on 2008-07-02
If you are having to login to the livecd then there is likely a problem with that or you misunderstand - you can install gparted inside the livecd if necessary.

This shouldn't be going anywhere near your damaged installation.

---

### Post by lotrkev on 2008-07-02
Well, I think I misunderstand. I'm burning a new, perfect, checked livecd; so can you guide me from there?

---

### Post by Elfy on 2008-07-02
Boot with the cd and then you should be able to get a t the partition editor - if you are burning version8.04 it is in the menu I said earlier.

When it boots use the check cd for defects first to make sure it's ok.

I assume you have checked the md5sum then as you say it's perfect.

---

### Post by lotrkev on 2008-07-02
Yes, I used the md5sum check. So, I put the disc in the tray, then restart the computer?
By the way-- I'm burning the cd at 8x speed, is that low enough?

---

### Post by avtolle on 2008-07-02
Once the CD boots and you are into the desktop, hit Alt+F2; in the box input "gksudo gparted" and <Enter>, which will put you into the graphical disk partitioning program. From there, you can deal with your partitions.

Warning: for some reason, from time to time, gparted as run from the live CD mounts the drive (even though it shouldn't, IMO). Should this happen, select the partition and click unmount. If this doesn't work, minimize the gparted window and look on your desktop for an icon indicating there is a volume mounted. If there is, right click on the icon, select unmount volume, and when the icon "disappears", and maximize the gparted window, and try again.

---

### Post by lotrkev on 2008-07-02
k. restarting computer with disc

---

### Post by lotrkev on 2008-07-02
ok, I booted from cd and am at the login screen
when i try to login, it plays the login sound, then goes right back to the login screen. what do i do?

---

### Post by lotrkev on 2008-07-02
It keeps logging in every 10 seconds, and keeps going back to the screen to login again <ugh!>

---

### Post by Elfy on 2008-07-02
I would say that there was something with it in some way then. Is it a diy pc or is it a manufactured one - if it's manufactured what is it maybe there is a record of it needing something added to the boot line.

---

### Post by lotrkev on 2008-07-02
It is a manufactured compaq-presario pc. Ubuntu is booted, it's just that I cant get past the login screen.

---

### Post by Elfy on 2008-07-02
You could try ubuntu as a user name but there shouldn't be one, no password.

Post pc spec if it doesn't boot. But I assume it does let you install as you're trying to deal with half a previous installation.

---

### Post by avtolle on 2008-07-02
Is your BIOS set to boot first from the CD drive? It appears from reading that the computer is booting from the failed installation on your hard drive.

---

### Post by Elfy on 2008-07-02
good catch - I'm still thinking of one the other day that had similar problem:)

---

### Post by lotrkev on 2008-07-02
How do I load the bios first

---

### Post by Elfy on 2008-07-02
could be F2, esc, delete - check as it boots - it usually will say press blah to enter setup 

then find where the boot order is and ensure it is set to cdrom first

---

### Post by avtolle on 2008-07-02
When you restart the computer, or first power it up, there should be an introductory screen which, among other things, gives you options. The screen or the message goes away quickly, so you need to read fast. On the screen/in the message will be a list of F# keys to press to take certain actions; one of these will be to alter boot order, or words to that effect. The precise key varies among vendors, so there isn't to my knowledge a uniform way to do it; you'll just have to read fast and press the correct key before anything boots.

---

### Post by lotrkev on 2008-07-02
now it ejected the disc from the tray before restart, so then i restarted, made cd-rom first, then boothed "ubuntu" operating system.
now it ran a setup where it asks timezone, then it said, "partman crashed- exit code 10" so i clicked continue, then it asked for info, then said "summary crashed- exit code 141", now it is stuck on "prepare disk space" doing nothing. what now?

---

### Post by lotrkev on 2008-07-02
maybe i should just give up. and deal with only one computer with ubuntu. how can i remove ubuntu from (through/ while using) windows? (i know its there because it took up 15 gigs of hdd.

---

### Post by lotrkev on 2008-07-02
ok, well, i found an uninstall file in c:/ubuntu, so i used it and now i have the 15 gigs back. thanks guys very much for the help!:guitar:

---

### Post by Elfy on 2008-07-02
Ha - you were talking about wubi were you :)

---

### Post by lotrkev on 2008-07-02
yep i guess:lolflag:

---

### Post by Elfy on 2008-07-02
would probably speeded things up, I certainly thought you were talking about a real installation and I expect avtolle did too :lol:

As it's all done now could you mark thread solved please.

---

