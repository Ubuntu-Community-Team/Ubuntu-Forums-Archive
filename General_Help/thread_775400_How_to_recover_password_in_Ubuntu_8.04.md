---
title: "How to recover password in Ubuntu 8.04"
date: 2008-04-30
forum: General Help
---

### Post by mzbeg on 2008-04-30
Hi all

I forgot my password, and I have been trying to recover it by using different methods, have not been successful.  I have already tried following methods.

Booted into recover mode and typing "# pass root; I got this reply "Authentication service cannot retrieve authentication info"

Also booted with original CD, but could not open /etc/shadow file, permission denied.

Need help, but please bear in mind that I am totally new to this environment. Would appreciate clear and detailed instruction as much as possible.  Thanks.

---

### Post by Nunu on 2008-04-30
> **mzbeg said:**
> Hi all

I forgot my password, and I have been trying to recover it by using different methods, have not been successful.  I have already tried following methods.

Booted into recover mode and typing "# pass root; I got this reply "Authentication service cannot retrieve authentication info"

Also booted with original CD, but could not open /etc/shadow file, permission denied.

Need help, but please bear in mind that I am totally new to this environment. Would appreciate clear and detailed instruction as much as possible.  Thanks.

And if you booted from the live CD and tried

```
sudo -s /etc/shadow
``` as root?

---

### Post by angry_johnnie on 2008-04-30
How about logging in in recovery mode, and then typing:

**passwd yourusername**

and then just entering a new password?

I think that should do it.

---

### Post by Nunu on 2008-04-30
> **angry_johnnie said:**
> How about logging in in recovery mode, and then typing:

**passwd yourusername**

and then just entering a new password?

I think that should do it.

That does seem a bit easier  LOL

---

### Post by mzbeg on 2008-04-30
> **Nunu said:**
> And if you booted from the live CD and tried

```
sudo -s /etc/shadow
``` as root?

Thanks for your reply, but where and how should I enter this command. Thanks

---

### Post by _aXXe_ on 2008-04-30
I'm trying to install the seti@home program listed in the synaptic package manager. I can find the two folders for the manager and client but I can't start them using my normal login. I don't remember setting a root password so how do I login as root to change permissions so I can use the programs?

Any help will be greatly appreciated as I am falling behind on my PC's computations and will lose several credits for my team if I don't get this working.

Thanks

---

### Post by Nunu on 2008-04-30
> **mzbeg said:**
> Thanks for your reply, but where and how should I enter this command. Thanks

You can run this from terminal

---

### Post by MaindotC on 2008-04-30
C'mon Nunu - a newb asking for "clear and detailed instructions"?  You gotta be nicer than that :)

I think what he means is when you boot up Ubuntu and obviously cannot log into the desktop, press ctrl + alt + f2 to open a terminal - sometimes this is referred to as a "backscreen" or a tty.  You can do this for f1 - f7 (which I believe is referred to as tty1 - tty7), and f7 is the graphical environment.  You'll understand this more as you try it yourself.  

When you do that, if you can login as root, then you have a command prompt and you can enter the commands listed above.  If it is the root password that you don't have, then we may have to take deeper measures.

---

### Post by mzbeg on 2008-04-30
> **Nunu said:**
> You can run this from terminal

Hi, I am logged on to ubuntu@buntu this is I think is Ubuntu CD. How do I log on to the directory where Ubuntu reside on my computer. C:\ is populated by XP. So it must be D:\. How do I navigate to D:\ in Ubuntu terminal.  Thanks

---

### Post by ryanhaigh on 2008-04-30
> **Nunu said:**
> 
```
sudo -s /etc/shadow
``` as root?

sudo as root would be a little pointless considering that if you are root you don't need to use sudo

As pointed out here [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword) using the recovery mode is the way to go.

---

### Post by MaindotC on 2008-04-30
ryan that is absolutely INCORRECT - you do NOT have root permissions by default and must precede root-permission commands with 'sudo' in the LiveCD.

---

### Post by MaindotC on 2008-04-30
> **mzbeg said:**
> Hi, I am logged on to ubuntu@buntu this is I think is Ubuntu CD. How do I log on to the directory where Ubuntu reside on my computer. C:\ is populated by XP. So it must be D:\. How do I navigate to D:\ in Ubuntu terminal.  Thanks

Your ubuntu partition is usually located in the /media folder.  For example, the cdrom is located in /media/cdrom or /media/cdrom0.  Your windoze partition may show as /media/sda1.  The Ubuntu partition will be different - maybe sda2 depending on the naming convention of your installation.  Hope this helps!

---

### Post by mzbeg on 2008-04-30
> **ryanhaigh said:**
> sudo as root would be a little pointless considering that if you are root you don't need to use sudo

As pointed out here [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword) using the recovery mode is the way to go.

I tried that and got this message
"Authentication service can not retrieve Authentication info"

cheers

---

### Post by ryanhaigh on 2008-04-30
> **strAlan said:**
> ryan that is absolutely INCORRECT - you do NOT have root permissions by default and must precede root-permission commands with 'sudo' in the LiveCD.

If you look at the quote the poster says to run the sudo command as root, I am well aware of the need to use sudo when running as an unprivilleged user on the livecd or installed system.

---

### Post by Nunu on 2008-04-30
> **strAlan said:**
> C'mon Nunu - a newb asking for "clear and detailed instructions"?  You gotta be nicer than that :)

I think what he means is when you boot up Ubuntu and obviously cannot log into the desktop, press ctrl + alt + f2 to open a terminal - sometimes this is referred to as a "backscreen" or a tty.  You can do this for f1 - f7 (which I believe is referred to as tty1 - tty7), and f7 is the graphical environment.  You'll understand this more as you try it yourself.  

When you do that, if you can login as root, then you have a command prompt and you can enter the commands listed above.  If it is the root password that you don't have, then we may have to take deeper measures.

Sorry i get carried away sometimes :)

You can do this as described above would be the easiest why. 

What i meant buy as root? was actually, to go to the tty and in the tty to sudo to become root and then try the command. Sorry for the confusion. #-o

---

### Post by dannylweston on 2009-06-11
I bought a new dell mini for my sons birthday. i did the initial setup awhile back so when he got it he could use it right away. now he need to install updates but doesn't have the administrator password which i forgot. i tried the method of using 'esc' at startup but nothing happens. any thoughts?

---

### Post by michy99 on 2009-06-11
Found on another thread:

[http://ubuntuforums.org/showthread.php?t=1182992](http://ubuntuforums.org/showthread.php?t=1182992)

If you have an original Dell Mini 9 with Ubuntu pre-installed, you may have a hard time entering the GRUB menu as the default delay is zero. This is particularly problematic if you're trying to reset your password using the passwd command.

You can enter the recovery mode following these steps:

1. Boot the mini 9 while pressing ESC every second
2. When you see the "MBR 2FA:" prompt or similar, the boot process is stopped.
3. Press ENTER and ESC very fast one after the other.
4. You should then see the GRUB menu. Using the up and down arrows, highlight the second option and press ENTER to boot into recovery mode.

---

### Post by bodhi.zazen on 2009-06-11
> **dannylweston said:**
> I bought a new dell mini for my sons birthday. i did the initial setup awhile back so when he got it he could use it right away. now he need to install updates but doesn't have the administrator password which i forgot. i tried the method of using 'esc' at startup but nothing happens. any thoughts?

Step-by-step directions are posted here :

[uwiki]LostPassword[/uwiki]

---

### Post by Slim Odds on 2009-06-11
> **strAlan said:**
> ryan that is absolutely INCORRECT - you do NOT have root permissions by default and must precede root-permission commands with 'sudo' in the LiveCD.

Maybe there is a misunderstanding here, but there is never a need to run 'sudo' as root.

The original question he responded to was about running a 'sudo' command and the question was "as root?".

---

### Post by dannylweston on 2009-06-11
ok i can get the MBR 2FA:, but after esc, enter, esc, enter, etc., it still loads right into ubuntu

---

### Post by dannylweston on 2009-06-11
did not help:(> **bodhi.zazen said:**
> Step-by-step directions are posted here :
 
[uwiki]LostPassword[/uwiki]

---

### Post by michy99 on 2009-06-11
> **dannylweston said:**
> ok i can get the MBR 2FA:, but after esc, enter, esc, enter, etc., it still loads right into ubuntu

If you are able to get into Ubuntu anyway, we can change the grub menu delay so you can get to it.```
gksudo gedit /boot/grub/menu.lst
```
Look for the line that says 'timeout 0' and change it to 15 or 30 or whatever. Then when you boot you should get the menu long enough to press esc and choose recovery mode.

---

### Post by bodhi.zazen on 2009-06-11
> **dannylweston said:**
> did not help:(

Not Esc-Enter-Esc-Enter ...

Just Esc

It sounds as if you or someone changed the defaults on grub to 0 , thus you have not much time as it boots.

Boot the computer and mash on the Esc key as fast as you can.

If that fails you will need to boot a live CD, mount your ubuntu partition, and set a password manually.

Assuming Ubuntu is on /dev/sda1 ... , on a live CD

```
# become root
sudo -i

#mount ubuntu partition 
mount /dev/sda1 /mnt

#Chroot
chroot /mnt /bin/bash

#Set password
passwd <user>
```

You will need to know your Ubuntu partition (fdisk -l) and change "/dev/sda" to your Ubuntu root and "<user>" to the log in name.

Reboot and all should be good in the world again.

---

### Post by michy99 on 2009-06-11
> **bodhi.zazen said:**
> Not Esc-Enter-Esc-Enter ...

Just Esc

It sounds as if you or someone changed the defaults on grub to 0 , thus you have not much time as it boots.

That is the way the Mini 9 comes from the dealer.

> **bodhi.zazen said:**
> Boot the computer and mash on the Esc key as fast as you can.

If that fails you will need to boot a live CD, mount your ubuntu partition, and set a password manually.

I don't think the Mini 9 has a cd drive.

---

### Post by dannylweston on 2009-06-11
> **michy99 said:**
> If you are able to get into Ubuntu anyway, we can change the grub menu delay so you can get to it.```
gksudo gedit /boot/grub/menu.lst
```
Look for the line that says 'timeout 0' and change it to 15 or 30 or whatever. Then when you boot you should get the menu long enough to press esc and choose recovery mode.
 where do i find or enter code from desktop?

---

### Post by michy99 on 2009-06-11
> **dannylweston said:**
> where do i find or enter code from desktop?

Applications->Accessories->Terminal

---

### Post by dannylweston on 2009-06-11
> **michy99 said:**
> Applications->Accessories->Terminal
 "enter your password for administrative tasks"?

---

### Post by michy99 on 2009-06-11
> **dannylweston said:**
> "enter your password for administrative tasks"?

Oops, I forgot about that. Kind of going in circles, aren't we. Ok, you say you can get to the MBR 2FA screen. The way I understand it, you then press Enter and then Esc very quickly. Give this a try once or twice and see if it works.

Whoever set these Mini 9s up like this needs a good spanking.

---

### Post by dannylweston on 2009-06-11
> **michy99 said:**
> Oops, I forgot about that. Kind of going in circles, aren't we. Ok, you say you can get to the MBR 2FA screen. The way I understand it, you then press Enter and then Esc very quickly. Give this a try once or twice and see if it works.
 
Whoever set these Mini 9s up like this needs a good spanking.
 ok finally got there! says [EMAIL="root@joshua"]root@joshua:~#[/EMAIL]. Now what?

---

### Post by bodhi.zazen on 2009-06-11
What is your son's user name ?

```
passwd user_name
```then reboot

While you are there, b4 you reboot, you might want to :

```
nano /boot/grub/menu.lst
```

And change the time out to something more reasonable such a 1 or 2.

---

### Post by threemoons on 2009-06-11
Excuse me for asking this question if it is stupid. But isn't Linux supposed to be a vaunted system that's superior to Windows BECAUSE it is secure?!?! This appears to be a horrible horrible security flaw if you can do this really. I have an encrypted ubuntu linux server and I don't want this to happen, ever. Also I am considering installing ubuntu desktop on a laptop computer. What the heck is this about?!

---

### Post by bodhi.zazen on 2009-06-11
> **michy99 said:**
> That is the way the Mini 9 comes from the dealer.

I don't think the Mini 9 has a cd drive.

That could be a problem ...

>_<

---

### Post by michy99 on 2009-06-11
First, if you don't know the username, enter ```
ls /home
```This will list all the users on the system. Now enter```
passwd username
```But use the actual username instead of 'username'. When you enter the new password, you won't see anything on the screen. just type it in and press enter. Then type```
exit
``` and resume normal boot.

---

### Post by bodhi.zazen on 2009-06-11
> **threemoons said:**
> Excuse me for asking this question if it is stupid. But isn't Linux supposed to be a vaunted system that's superior to Windows BECAUSE it is secure?!?! This appears to be a horrible horrible security flaw if you can do this really. I have an encrypted ubuntu linux server and I don't want this to happen, ever. Also I am considering installing ubuntu desktop on a laptop computer. What the heck is this about?!

LOL

yep , physical access is a problem with every OS.

your best protection is encryption, so use the alternate  CD and encrypt your installation.

More important, if you do not want this happening to you, restrict physical access.

---

### Post by michy99 on 2009-06-11
> **threemoons said:**
> Excuse me for asking this question if it is stupid. But isn't Linux supposed to be a vaunted system that's superior to Windows BECAUSE it is secure?!?! This appears to be a horrible horrible security flaw if you can do this really. I have an encrypted ubuntu linux server and I don't want this to happen, ever. Also I am considering installing ubuntu desktop on a laptop computer. What the heck is this about?!

The only way to secure a system from someone who has physical access to the computer is to encrypt all data.

---

### Post by threemoons on 2009-06-11
> **bodhi.zazen said:**
> LOL

yep , physical access is a problem with every OS.

your best protection is encryption, so use the alternate  CD and encrypt your installation.

More important, if you do not want this happening to you, restrict physical access.

  what if someone steals my laptop? or I leave it at home with a friend or family which I believed that I could trust but I was wrong? :( This is very bad if this is true. People at Slashdot.org claim always that Linux is so great because of stuff like this. Am I missing something? Is this another user rather than an Administrator?

---

### Post by threemoons on 2009-06-11
> **michy99 said:**
> The only way to secure a system from someone who has physical access to the computer is to encrypt all data.

  Yes, my server is fully encrypted LVM. But I intend to install ubuntu desktop on a regular notebook computer and encrypt it using ubuntu's encryption software. I use Truecrypt for my Windows computers.

---

### Post by mcduck on 2009-06-11
> **threemoons said:**
> Excuse me for asking this question if it is stupid. But isn't Linux supposed to be a vaunted system that's superior to Windows BECAUSE it is secure?!?! This appears to be a horrible horrible security flaw if you can do this really. I have an encrypted ubuntu linux server and I don't want this to happen, ever. Also I am considering installing ubuntu desktop on a laptop computer. What the heck is this about?!

Giving any untrusted person physical access to your system is a security flaw.

Software can't give hardware-level security. When there's physical access to the computer only thing you can do to protect the system is to encrypt your data. It makes no difference what operating system you use.

The machine can always be booted from a CD or thumbdrive, passwords can be cracked and BIOS settings cleared, and in the end anybody could just take the hard disks out of the machine and plug them in to another computer to access the data.

Linux is very secure operating systems, but there's simply things that operating systems can't change. With physical access to the machine the security is already broken outside of the limits where operating systems work.

---

### Post by michy99 on 2009-06-11
> **threemoons said:**
> what if someone steals my laptop? or I leave it at home with a friend or family which I believed that I could trust but I was wrong? :( This is very bad if this is true. People at Slashdot.org claim always that Linux is so great because of stuff like this. Am I missing something? Is this another user rather than an Administrator?

If someone steals your laptop, they can access anything on your drive, even if they have to go as far as removing it and hooking it up to another system.

---

### Post by bodhi.zazen on 2009-06-11
> **mcduck said:**
> Software can't give hardware-level security. When there's physical access to the computer only thing you can do to protect the system is to encrypt your data. It makes no difference what operating system you use.

The machine can always be booted from a CD or thumbdrive, passwords can be cracked and BIOS settings cleared, and in the end anybody could just take the hard disks out of the machine and plug them in to another computer to access the data.

+10

Physical access has nothing to do with the underlying security (or lack of it) of the OS. There is no known OS that can protect you from physical access, encryption can only protect your data.

Encryption does not stop somebody from physically damaging your equipment or reformatting the hard drive and installing whatever s/he pleases.

---

### Post by dannylweston on 2009-06-11
Yay:DI finally got it! Thanx everyone for your support. Sorry for being so computer illiterate. I'm still learning the lingo:confused:

---

### Post by michy99 on 2009-06-11
> **dannylweston said:**
> Yay:DI finally got it! Thanx everyone for your support. Sorry for being so computer illiterate. I'm still learning the lingo:confused:

No need to apologize, Your situation was made needlessly more complicated by a stupid decision on Dell's part to set the boot menu time to zero. By the way, if you haven't already, you might want to change that as show above.

---

### Post by dannylweston on 2009-06-11
Got it done, Thanks.

---

### Post by bodhi.zazen on 2009-06-11
wOOt !!!

I am going to close this thread now as your question has been asked and answered.

If anyone wishes to discuss the issue of physical access, please use [Recurring discussions](  http://ubuntuforums.org/forumdisplay.php?f=302)   
  recurring discussions as the topic has been discussed many many times.

---

