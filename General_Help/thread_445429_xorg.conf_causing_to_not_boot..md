---
title: "xorg.conf causing to not boot."
date: 2007-05-15
forum: General Help
---

### Post by mrweektor on 2007-05-15
hey, i've got a problem that needs fixing, and i've done some searching around here for a while but the forums are too vast! so i'm posting now.
ok so i was attempting to configure my [alps touchpad]("http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/"), so i was meesing around in the xorg.conf file.
it wasn't working out the way the article said it would so i changed something where i thought i had gone wrong then rebooted. well, now ubuntu won't boot (im getting some error where it just loops this error message forever, or a very long time).
i made a backup of xorg.conf, i just need a way to log into root and change it back! i tried using the live CD but i had no luck there.

ok, so about this error message, it has a number in []'s then

> [ #] mmcblk0: error 1 sending read/write command

and when i push some buttons it brings up a loggin prompt but only for a second before the loop starts again.
really the error message isn't the important thing, just changing the file back is.
please help, i'd like to get back to experimenting with this geniousness that is linux

---

### Post by heimo on 2007-05-15
Try booting in recovery mode (choose in boot/grub menu).

---

### Post by stonerrob420 on 2007-05-15
I had the same problem recently. All I did is started the computer with the live cd. First I used gparted and enabled the disk from the live cd where I could access it. Then I pulled up the teminal and typed $sudo gedit /etc/X11/xorg.conf . It brought up the xorg.conf where I could replace it with the backed up one. I saved the file and rebooted......it work wonderfully. give it a try......It not a conventional solution but it worked for me. :guitar:

---

### Post by mrweektor on 2007-05-15
> **heimo said:**
> Try booting in recovery mode (choose in boot/grub menu).

i'm noob, but not retrarded. i did try that. i know i didn't mention it, sorry.
thnx tho for your time.

---

### Post by heimo on 2007-05-15
> **mrweektor said:**
> i'm noob, but not retrarded. i did try that. i know i didn't mention it, sorry.
thnx tho for your time.

Well. I wasn't suggesting that you're retarded. That'd be _way_ out of line and definitely not something I'd do.

Do you have several kernels installed? Did you try those? Same thing?

---

### Post by mrweektor on 2007-05-16
sorry that i suggested that you were suggesting that i was retarded, i understand that most of the time you do have to mention all that. i'm not exactly sure what you mean by several kernals, but the only other opperating system i have is windows. i'm about to try stonerrob420's solution.

---

### Post by heimo on 2007-05-16
In grub menu, you might see more than one "Ubuntus", with different version numbers. If you have those, I'd try each one of them. It has helped me couple times when some version of Linux (the kernel of Ubuntu) got mad at me. :)

---

### Post by stonerrob420 on 2007-05-16
oh! by the way dude! be careful! I didnt think about you might be using several  different kernels . Im running ubuntu 6.06 with the kubuntu desktop installed upgraded....it took a super long time to download on this awful dialup connection....... I've tinkered with mine and blown it to pieces several times but it has alway come back together.....I think thats what I like about linux more than anything it is reliable and can be fixed unlike windows where you have to do a repair install to fix things and in most cases it just messes things up worse....may the force be with you!     :guitar:

---

### Post by mrweektor on 2007-05-19
ok, so the problem's been fixed.
i didn't do it, someone helped me, and unfortunately i wasn't able to log in my head everything he did.
The error message had to do with my SD card reader.
mmc is for multi media card, so he turned off some conflicting drivers and that took away the error message.
I think then it booted up and i was able to change it back to the backed up file.
stonerrob, the method u gave me wasn't working for me for some reason, i'd finally get access to change the file, then i'd reboot, the problem would still be there, then i'd go back to the live cd and it would be the old messed up file again. :(

---

### Post by cez801 on 2007-06-05
Hi, I also found that to boot in recovery mode (because of another error) that just removing the SD card from the internal card reader prevented this problem from occurring.
It let me get in an fix the issue.

---

