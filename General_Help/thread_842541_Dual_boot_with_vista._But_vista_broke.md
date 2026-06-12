---
title: "Dual boot with vista. But vista broke?"
date: 2008-06-27
forum: General Help
---

### Post by Akingboy on 2008-06-27
Hi all!

First, im new with ubuntu. I decided to try it since I didn't like vistas slowness.

I really like this ubuntu. It looks good, is fast and has loads of software to play with.

After I had done lots of research and managed to make partition for ubuntu I installed it to this (actually yesterday). When booting I allways saw the window where it asks if you want to boot ubuntu or vista. Today I decided to go to vista to share my music to ubuntu also but when I tried to start vista I got error message something like: "Missing or corrupt file Windows/System32/Winload.exe" and it told me to insert vista dvd and using its fix system to fix things.

I inserted the cd. But my computer didn't react to it anyhow. I told bios to boot first from cd but it still went to the screen ubuntu or vista.

I'ts not end of the world if I lose vista but I'd like to keep it in case that linux doesn't have something it has.
Couldn't anyone tell me what to do?

I need to either fix somehow that the "Winload.exe" doesn't work, or then getting my computer somehow to boot from my vista dvd.
Maybe I installed ubuntu wrong. I read some stuff found from google but they didn't help me. Someone sayd something intresting though that this happens because vista tries to boot from wrong partition or something like that. Hope that helps you analyze my problem.

---

### Post by xdavidx on 2008-06-27
> **Akingboy said:**
> Hi all!

First, im new with ubuntu. I decided to try it since I didn't like vistas slowness.

I really like this ubuntu. It looks good, is fast and has loads of software to play with.

After I had done lots of research and managed to make partition for ubuntu I installed it to this (actually yesterday). When booting I allways saw the window where it asks if you want to boot ubuntu or vista. Today I decided to go to vista to share my music to ubuntu also but when I tried to start vista I got error message something like: "Missing or corrupt file Windows/System32/Winload.exe" and it told me to insert vista dvd and using its fix system to fix things.

I inserted the cd. But my computer didn't react to it anyhow. I told bios to boot first from cd but it still went to the screen ubuntu or vista.

I'ts not end of the world if I lose vista but I'd like to keep it in case that linux doesn't have something it has.
Couldn't anyone tell me what to do?

I need to either fix somehow that the "Winload.exe" doesn't work, or then getting my computer somehow to boot from my vista dvd.
Maybe I installed ubuntu wrong. I read some stuff found from google but they didn't help me. Someone sayd something intresting though that this happens because vista tries to boot from wrong partition or something like that. Hope that helps you analyze my problem.

i have some problems with what ubuntu does to my winxp, and when i was searching for some solution i've found this [http://www.pplware.com/2006/11/27/3-sistemas-operativos-no-boot-menu/](http://www.pplware.com/2006/11/27/3-sistemas-operativos-no-boot-menu/) i think this don't help me, but i think it can help you to understand. but if anyone knows more about it trough that website i think they can help you.

---

### Post by xdavidx on 2008-06-27
i've just realize now that it's in my language, but try to translate it trough google translators page to your language..hope that helps. it tells u the order of the installations. and what to do..

---

### Post by hpdv9500 on 2008-06-27
If it gets to the point where it says .exe not found that means its not a problem with grub. Are you sure you did not format your windows partitions?

what is the output of 

sudo fdisk -l

---

### Post by jimv on 2008-06-27
It won't boot from the VIsta DVD?  Try pressing F10, F11, or F12 during boot...on a lot of motherboards one of these keys will bring up a menu where you can select which drive to boot from (not the bios screen).  If it won't boot from the disk, it may not be a bootable disk...because it will attempt to boot from it, and if it can't, it will move on to the HD.

Is this a Vista DVD, or like a Dell restore CD?

---

### Post by Akingboy on 2008-06-27
Its vista dvd.

I try to spam f9-f12 now after booting.

I think I didn't format my vista because all the games and files I had are still there. I can browse them trough ubuntu.
And there is windows folder and inside system32 is that "winload.exe".

Sudo fdisk -1 is this:
> 
sudo fdisk -1
fdisk: invalid option -- 1
blaablaa...
And if you meant this then sudo fdisk 1 says:
> Device cannot be opened

And I don't know how to use google translator :P

---

### Post by WRDN on 2008-06-27
Akingboy, you entered the command incorrectly.

You need to enter

```
fdisk -l
```

It is the letter 'L', **not** the number 1.

---

### Post by Akingboy on 2008-06-27
Hmm I got something like this:

Device, Running, start, end, sector, id, system
/dev/sda1 * 1913 19317 139805662+ 7 HPFS/NTFS
/dev/sda2   1    1912  15358108+ 83 Linux
/dev/sda3   19318 19457 1124550 82 Linux-sivutus(I think means swap)/Solaris

Someone analyze.

---

### Post by xdavidx on 2008-06-27
> **Akingboy said:**
> Its vista dvd.

I try to spam f9-f12 now after booting.

I think I didn't format my vista because all the games and files I had are still there. I can browse them trough ubuntu.
And there is windows folder and inside system32 is that "winload.exe".

Sudo fdisk -1 is this:

And if you meant this then sudo fdisk 1 says:


And I don't know how to use google translator :P


go here [http://www.google.pt/language_tools?hl=en-EN](http://www.google.pt/language_tools?hl=en-EN) and where it says translate webpage put the link i gave you..translate from Portuguese to English.

---

### Post by Akingboy on 2008-06-28
I read that but if I understood right I would have to completely reinstall vista and ubuntu?

Wouldn't be a big deal but just confirming.

---

### Post by Akingboy on 2008-06-28
Ok I think I'll do fresh install with only ubuntu.
I really like this.

Now I need help. How to do it? How i'm gonna start it?

I wouldn't reinstall but I got this one installed on 15gb big partition and im out of space. I can't resize it because its the system i'm using. > If you run GParted from a running system, you can't work on THIS system.


Please someone =) Do I increase my linux partition's size somehow or complete reinstall without vista and I don't know how to do either.

---

### Post by Diggs808 on 2008-06-28
if you have your Ubuntu Livecd, boot from it and go to system> Administration> Partition Editor.  That will allow you to erase your vista partition.  Once you have done that you can expand out your Ubuntu partition to take over that space.  

Hope this helps!

---

### Post by Akingboy on 2008-06-29
Thanks but I can't boot from my livecd for some reason.

First I could do it because it had the file inside the cd that made computer boot from the cd. In vista I double clicked the file and after rebooting it booted from cd. But that was only for windows. How to boot from CD with ubuntu? I can't find it anywhere. From bios or bootmenu.

Is there similar "Boot from cd" file for linux too?

Oh and also. Today my network connection on my ubuntu machine didn't work... Whats wrong? It worked fine yesterday. Other computers work fine. Also the machine seems bit slow.
Edit. Forget this last part =) Got it working. It didn't correctly recognize the right DNS server and I manually added the right line checking it from other computer.
EDIT2. WOO! I got it started from cd. Its booting now. I just spammed f5-f12 and I got some menu with different possibilities. I was like "damn can't find the cd anywhere" but it was actually there. The third option hidden very well. It was something "BLAABLAA CDDVDBLAA BLAA" so I first didn't recognize it.

But im booting from live CD now thanks for the info m8! I hope it will work.
...ok booted. Scanning devices in gparted... Unmounting vista partition...
**_BTW!! Now that I remove the vista partition do I have to put "boot" flag to the ubuntu partition??_**
More problems. Gparted crashes after I have unmounted vista partition. Why?
Edit. Ok now got things running. Gona take long time. Still asking is that boot flag needed?

---

### Post by Akingboy on 2008-06-29
Ok I got rid of vista and ubuntu has now all the space in my computer. But after this the computer has been slow :confused: and sounds don't work. The sound slider in the upper right doesn't appear there or the speaker picture.

Booting is really slow now. In the desktop it takes ages for the upper and lower panels to show up.
And btw about those sound I try to wait longer if it just loads forever =/
Any ideas why this happened? And what to do.

Also when I start my computer it still goes to the screen ubuntu or vista. After pressing vista it says there is no such partition which is right but I'd like the computer to default boot from ubuntu!

Thanks

Edit: I can open games fast and stuff bu I just tried opening synaptic package manager and it didn't even open. Also device drivers didn't open =/ Somethings seriously wrong. I need help!

---

### Post by Akingboy on 2008-06-29
Bump.
Anyone?

I can open "update management" but when i start searching updates it freezes.
Can't open synaptic package manager at all.

Terminal I CAN open. Also games seem to work normally.
Its not that my computer is slow but looks like some drivers are bad or something I dont know.

*Mounting local filesystems...
then some error message that can't find volume... didn't have time to read what it sayd
ntfs-3g:
/sbin/mount.ntfs

More problems... I try to type my login: aki then the 'k' button doesn't work and 'i' button. Whats wronng? But using shift+k or shift+i works. **I can't login now!**
Also numbers: 1, 7, 8 don't respond and letter 'l'

PLEASE HELP!

Huh I can go with live cd atleast. Gonna try to reinstall the system!
This is scary...

Edit. ok... Reinstalled ubuntu. Thanks anyway.

---

