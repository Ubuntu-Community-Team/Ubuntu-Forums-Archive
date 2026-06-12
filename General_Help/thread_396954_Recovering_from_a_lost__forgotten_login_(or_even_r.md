---
title: "Recovering from a lost / forgotten login (or even root password) in Edgy Eft"
date: 2007-03-30
forum: General Help
---

### Post by maheshjagadeesan on 2007-03-30
Here's the situation: You have a dual-boot machine at home/work (Ubuntu/Windows), and your main OS is Windows. You use Ubuntu to learn stuff, or maybe just explore, so you don't boot into it all that often. One fine day, after many days of residing in Windows, you want to boot back into the nice GNOME / KDE interface, but find, to your horror, that you've forgotten your password. You still have your Ubuntu Live / install CD with you, but that's about it. You wring your hand, you call friends, you Google, you swear, but all to no avail. You tried booting into Ubuntu's safe mode ([http://aplawrence.com/Linux/lostlinuxpassword.html)](http://aplawrence.com/Linux/lostlinuxpassword.html)), but that didn't help, because you have a new kernel (2.6.17 or above) which doesn't log you in as root if you don't know the root password. Sheesh!!

Here's the solution: Follow the steps outlined in [[COLOR="Magenta"]this page[/COLOR]]("http://news.softpedia.com/news/Resetting-a-Forgotten-Root-Password-40544.shtml"), and voila, you're back home on your favourite OS. If you're unable to, for some reason, access that URL, here's what you have to do:

Method Two - The Hard Way

In case GRUB or LILO are password protected, you will have to boot your system from a live cd Linux distribution such as Knoppix or SLAX and follow these instructions:

- Boot the live cd as normal
- Once logged in, open a terminal and type this as the super-user (to become a super-user aka root, type 
# sudo su - 
):

# mkdir /mnt/hd
# mount /dev/hdaX /mnt/hd
(where /dev/hdaX is your Linux system partition with forgotten root password, it could be /dev/hda1 or /dev/sdaX if you have a S-ATA drive).
# chroot /mnt/hd
# passwd

- If, for whatever reason, the chroot command above fails, try:

# cd /mnt/hd/etc
- Open shadow file in your favorite text editor
- Find the root entry which may look like this:
root:**$1$oPldWBFd$3rQbA.Fz7KtyF4IAFP0kq1**:13472:0:99999:7:::

- Delete the password hash (the bold text)
- After you have edited this entry, it should look like this:
root::13472:0:99999:7:::
- Save the file
- Type:

[NOTE: The number following the two colons are specific to my machine, yours may be different, so **don't **copy them]

# cd /
# umount /dev/hdaX
(Where hdaX is the Linux partition with the forgotten root password mounted earlier)

- Reboot and remove the live cd to boot in your regular Linux system.
- Once the boot process is complete, you will be asked for a username: type root and for a password: press ENTER (NO password because you edited the /etc/shadow file).
- At the moment, your root account is passwordless, which is very bad. To quickly set a root password, type:
# passwd

---

### Post by madcitybrit on 2007-04-07
Oops, my original reply shouldn't have been to here. Now moved to...

[http://ubuntuforums.org/showthread.php?p=2416365&posted=1#post2416365](http://ubuntuforums.org/showthread.php?p=2416365&posted=1#post2416365)

---

### Post by fakie_flip on 2007-04-22
I have a problem with my password. Can you help?

[http://ubuntuforums.org/showthread.php?t=412320](http://ubuntuforums.org/showthread.php?t=412320)

---

