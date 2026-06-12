---
title: "What HAS Grub been up to?"
date: 2014-10-08
forum: General Help
---

### Post by Mike_Walsh on 2014-10-08
Morning, all.

Sorry if this is in the wrong place, admins; please relocate if it is!

I'm doing a bit of 'head-scratching' here, I must admit. I've got a dual-boot setup with Ubuntu and Zorin's OS Core 9, plus a separate /home partition, on my main HDD (sda):-

[ATTACH=CONFIG]257037[/ATTACH]

Sda1 is Ubuntu; sda5 is Zorin. Sda3 is /home.

I also have Lubuntu in a separate partition on my external HDD (sdb6):-

[ATTACH=CONFIG]257038[/ATTACH]

It shares dev/sda3 with Ubuntu.

Now, then; last night, I decided to do a full install of Kubuntu, on a 64 GB Sandisk 'CruzerBlade' flashdrive I've got. I'd been running Puppy 'Slacko' on it; it's a nice little OS, but it's not the easiest thing in the world to work with.....so I decided to return to the 'buntu flavours with which I'm familiar (following advice in a post by QIII, in this thread.....thanks, QIII!):-

[http://ubuntuforums.org/showthread.php?t=2247065](http://ubuntuforums.org/showthread.php?t=2247065)

> [COLOR=#000000]For $20US you can find a 32GB USB thumb drive. Rather than a live image or a live image with persistence, you can install a full-on Linux installation. Provided you do not install proprietary hardware drivers (or you uninstall them when done) this will allow you to move from machine to machine provided you can boot from USB. [/COLOR]

[COLOR=#000000]I find this much more satisfactory than a live image or live with persistence.[/COLOR]

[COLOR=#000000]USB is much faster than optical, but not as fast as a hard drive.[/COLOR]

[COLOR=#000000]You can have what is effectively a dual boot for $20.[/COLOR]

[COLOR=#000000]If you disconnect your hard drives during installation you eliminate the potential for the disaster of overwriting Windows.[/COLOR]

[COLOR=#000000]My personal recommendation is a full installation on a USB thumb drive. As I said, this will allow you to fully test proprietary drivers for your hardware.[/COLOR]

[ATTACH=CONFIG]257042[/ATTACH]

That's Kubuntu installed on the Sandisk (sdg1).

    ---o---     ---o---     ---o---     ---o---     ---o---     ---o---

THIS is where the 'head-scratching' begins! 

The install itself went as smooth as silk, and I have a fully functional, self-contained system that I can take anywhere with me, since I installed the boot-loader to sdg, as well as the OS to sdg1. This being the case, it's like a computer with a single OS; I never expected to see Grub appear. Imagine my surprise, then, when after install, on the initial re-start, up pops Grub, with not ONLY Kubuntu at the top (as you'd expect, being the last one installed), but also the full contents of my Grub menu from the main HDD (sda)..!

It doesn't make any difference to the operation of Kubuntu, as a self-contained OS on the flashdrive, and it also hasn't prevented normal operation of the main system (it doesn't appear to have MOVED the grub config. files, merely copied them).....but I'm real curious as to WHY it's copied the Grub information from the main system.

Can anybody enlighten me, please?  :confused:

Regards,

Mike.

---

### Post by kurt18947 on 2014-10-08
I haven't a clue as to the mechanism. To avoid it, I unplug all hard drives  prior to creating the full install flash drive. Then I'm SURE nothing untoward is going to happen to the hard drive contents and it also avoids 'contamination' of the flash drive install.  I've never tried disabling the hard drives in BIOS prior to booting the live DVD/USB, that might work as well.

---

### Post by Mike_Walsh on 2014-10-08
Hallo, kurt.

Yes, I daresay it would work that way. When I originally installed Zorin a few months ago, it kept on trying to install itself to my external Seagate (that's a saga in itself! If you're interested, you can read about THAT one in this thread I created on the Zorin Forums:-

[http://zoringroup.com/forum/viewtopic.php?f=4&t=7595](http://zoringroup.com/forum/viewtopic.php?f=4&t=7595))

You need to read it ALL the way through; it's quite a long thread! :D

Anyway, I'm not THAT fussed. Like I said, it's all working exactly as it should; I just have superfluous information in Grub on sdg that I don't need. I guess the easiest way round that is to install 'Grub-customizer', and just delete the entries I don't want; what do you think? Or is it even WORTH the bother?

Regards,

Mike.

---

### Post by kurt18947 on 2014-10-08
Hi Mike

I guess it depends on if it bothers you or not. The axiom about "if it ain't broke ........." comes to mind. I'm having another issue with Grub probably unrelated but it reminds me that Grub is imperfect.  Grub Customizer might be worth a go, thanks for reminding me about that.

---

### Post by grahammechanical on 2014-10-08
Stop and think.

If you install Ubuntu onto the hard disk you would expect Grub to detect all the other OS on that hard disk and on any other hard disk. Did this not happen when you installed Lubuntu on that external hard disk (sdb6)? So, why should it be any different when we install onto a USB memory stick? It is after all just another kind of external drive.

When Kubuntu was installed on that Scandisk (sdg1) the installation of Grub ran a Grub utility called os-prober and that utility searched all connected disks (storage) for operating systems. So, it naturally detected every other OS.

What can you do about it? Load Kubuntu from the Scandisk and,

Go to /etc/grub.d and you will see a file called 30_os-prober. Look at its properties. You will see under Permissions that there is a box called Execute Allow executing file as a program. Untick that box. You need Administrator privileges to do this

Then run

```
sudo update-grub
```

That should update the Grub configuration file without os-prober being run. So, none of the other OS will be detected.

Regards.

---

### Post by oldfred on 2014-10-08
+1 on grahammechanical's suggestion on os-prober

But I do like to have a backup way to boot from flash drive, so I add my own boot stanza to 40_custom to boot the most current kernel in my install. And I like to copy ISO to flash drive and then I can directly boot ISO (several repair type)  from grub. I then have one flash drive for emergency boot, repairs and testing or working with a full install.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

[http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484](http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484)

 This will boot an ISO from a hard drive or any second drive with full install or grub installed.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by Mike_Walsh on 2014-10-08
Thanks, guys.

@Graham; I do feel an absolute prat. You pointed out almost this exact same thing to me only a few weeks back:-

[http://ubuntuforums.org/showthread.php?t=2238681&p=13094006#post13094006](http://ubuntuforums.org/showthread.php?t=2238681&p=13094006#post13094006)

Mind you, I appreciate that Grub and Grub-related stuff IS a tad on the complex side; I'm gradually putting all the pieces of the jigsaw puzzle together, but it's a slow business. Shows how rubbish my memory's getting..! :p


@oldfred; Thanks **once **again for your advice. As I've just said to Graham, I'm slowly putting all the pieces together.....but then, Rome wasn't built in a day; I'd be daft to think I can master all this stuff overnight. After all, I've been using these things for well over 30 years; and I'm still learning.

I keep giving Cavsfan's 'Maintenance-free customized Grub 2 screen' a look, and thinking how nice it would be to replace that magenta screen with something a wee bit more pleasant to look at. One of these days, I WILL get around to it!


I'll give Graham's tip a try out, and let you know if it works.

Regards,

Mike.

---

### Post by Mike_Walsh on 2014-10-08
@grahammechanical:-

Well, that worked a treat; the extraneous information has disappeared from Grub, just as you said it would.....thank you for that. ;)

Now; let me test my admittedly meagre store of knowledge here. From reading back over some of the advice you've given **me**, and also reading some of your advice to other people, let me ask you this:-

Am I correct in thinking that on a single OS set-up, although Grub is still there, you don't normally see it, since there's no need...yes?

That being the case, is there a way to 'hide' Grub on this Kubuntu flashdrive of mine? I agree, Kurt's absolutely right about the hoary old axiom, "If it ain't broke...", and to be fair, it's behaving itself just fine.....but if you **don't** ask, you don't learn! I **will** eventually get myself into the position of understanding how all the various parts of the system interact.....and, just sometimes, you have to learn from your mistakes; that's knowledge that usually sticks with you!! :) 

Regards,

Mike.

---

### Post by oldfred on 2014-10-08
If you have only one install, it should just hide itself. And you may want to reduce the timeout, but I do not suggest changing to 0 as some then can never hit shift key to get into grub menu if desired for recovery.

 gksudo gedit /etc/default/grub

Change this from 10 to 3:
GRUB_TIMEOUT=3

Then run 
sudo update-grub

And you get this warning:
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.

I have not followed all the details on which of the settings work. More discussion:
       Discussion of timeouts issue & recordfail:
[http://ubuntuforums.org/showthread.php?t=1717700](http://ubuntuforums.org/showthread.php?t=1717700)
Stop 30_custom from resetting timeout & style
[https://gist.github.com/LeahCim/9332432](https://gist.github.com/LeahCim/9332432)
Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported. 
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)
Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'
Pageflip error and 0 timeout - /etc/default/grub to equal to 0
[http://ubuntuforums.org/showthread.php?t=2050807](http://ubuntuforums.org/showthread.php?t=2050807)

---

### Post by Bashing-om on 2014-10-08
Mike_Walsh; Hey ;

Not a thing I can add to what the guru - oldfred - advises, really.

I too am intrigued by grub, the basis of all the learning about grub's display behavior :
[https://help.ubuntu.com/community/Grub2#Boot_Display_Behavior](https://help.ubuntu.com/community/Grub2#Boot_Display_Behavior)

At this time your attention is directed to section 6.

[INDENT][INDENT]I stay in tune
[INDENT][INDENT][INDENT]for what I can further learn
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2014-10-08
@oldfred:-

Thanks for that. That essentially gives me a single OS Grub, that only shows itself for a moment; that'll do.....I can live with that!

Another coupla tricks to add to my arsenal. I'll mark this as 'Solved'. Much appreciated.

Regards,

Mike.

---

### Post by Cavsfan on 2014-10-08
Thanks for the kind words about my wiki. I always disconnected my USB drive prior to installing because 99% of the time it hung and would not proceed period or it would try to install grub on the USB drive.
But when I installed Utopic Mate I accidentally left the USB drive plugged in and it didn't hang or try to install grub there so maybe it's improving.
You can setup these colors. I just chose magenta on the bottom and top because I've always had cyan there and I thought the combinations look fantastic. That picture doesn't do the actual screen justice.

[ATTACH=CONFIG]257053[/ATTACH]

Here are a few possibilities:

 [[IMG]http://www.zimagez.com/miniature/20141001122252.jpg[/IMG]]("http://www.zimagez.com/zimage/20141001122252.php") [[IMG]http://www.zimagez.com/miniature/20140930171821.jpg[/IMG]]("http://www.zimagez.com/zimage/20140930171821.php")

[[IMG]http://www.zimagez.com/miniature/20140930113614.jpg[/IMG]]("http://www.zimagez.com/zimage/20140930113614.php") [[IMG]http://www.zimagez.com/miniature/20140924125302.jpg[/IMG]]("http://www.zimagez.com/zimage/20140924125302.php")

[[IMG]http://www.zimagez.com/miniature/20140924143821.jpg[/IMG]]("http://www.zimagez.com/zimage/20140924143821.php") [[IMG]http://www.zimagez.com/miniature/customgrub.jpg[/IMG]]("http://www.zimagez.com/zimage/customgrub.php")

Here is the default which doesn't actually work. If I select Utopic for example it shows Utopic boot screen but the dots never go past moving across the screen.
Then when I press Alt+Cntl+F1 to boot tty it tells me I'm in Precise. So I have to install grub there and then boot into where I want my grub and install it there.
But the default will only boot into the very top option and not any of the others displayed. 

[[IMG]http://www.zimagez.com/miniature/defaultgrub.jpg[/IMG]]("http://www.zimagez.com/zimage/defaultgrub.php")

But, what is so great about customizing it this way is that it never fails to boot into the right system and you can add the Upstart boot line and the Systemd boot line for Utopic which makes it easier to boot with either.
Here is my /etc/grub.d/06_custom file currently:
[PHP]
#!/bin/sh
echo 1>&2 "Adding Precise Pangolin 12.04, Trusty Tahr 14.04, Utopic Unicorn 14.10, Utopic Unicorn 14.10 Mate, Mint 13 Nadia, Mint 17 Quina and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Precise Pangolin 12.04 LTS" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 LTS (Recovery Mode)" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04 LTS" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04 LTS (Recovery Mode)" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 (devel branch)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 systemd (Devel Branch)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash init=/lib/systemd/systemd
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 (devel branch) (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 Mate (devel branch)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 Mate systemd (Devel Branch)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash init=/lib/systemd/systemd
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 Mate (devel branch) (Recovery Mode)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Mint 13 Nadia" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry "Mint 13 Nadia (Recovery Mode)" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Mint 17 Qiana LTS" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro quiet splash
        initrd /initrd.img
}
menuentry "Mint 17 Qiana LTS (Recovery Mode)" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}[/PHP]

---

### Post by Dennis N on 2014-10-08
Another option --- Hide menu with countdown. 
Setting GRUB_TIMEOUT=0 along with GRUB_HIDDEN_TIMEOUT=5
[http://ubuntuforums.org/showthread.php?t=2246349&p=13132687#post13132687](http://ubuntuforums.org/showthread.php?t=2246349&p=13132687#post13132687)

---

### Post by Mike_Walsh on 2014-10-08
Hi, guys. 

@Cavsfan; I've been following your postings in the VinDiesel conky thread, too. My goodness, that's been running for a few years! I found your thread about customizing Grub 2 a couple of months ago, and forgot where I saw it. I found the Conky thread about a fortnight back, and that reminded me, from the link in your signature, all over again; one of these days, I WILL get around to trying it.

I had a go at changing the background picture in Grub Customizer, but it doesn't appear to do anything, so.....I may have a shot at doing it yr way.


@Dennis; Thanks for the suggestion, mate. I'll have a look at it tomorrow, 'cos I'm off to bed soon. Looooong old day... Will let you know how it works; sounds a bit like display adjustment on a cell phone, as you call them over there. Difference between display timeout, as opposed to backlight timeout....that kind of thing!


Regards,

Mike.

---

### Post by Cavsfan on 2014-10-08
> **Mike_Walsh said:**
> Hi, guys. 

@Cavsfan; I've been following your postings in the VinDiesel conky thread, too. My goodness, that's been running for a few years! I found your thread about customizing Grub 2 a couple of months ago, and forgot where I saw it. I found the Conky thread about a fortnight back, and that reminded me, from the link in your signature, all over again; one of these days, I WILL get around to trying it.

I had a go at changing the background picture in Grub Customizer, but it doesn't appear to do anything, so.....I may have a shot at doing it yr way.


@Dennis; Thanks for the suggestion, mate. I'll have a look at it tomorrow, 'cos I'm off to bed soon. Looooong old day... Will let you know how it works; sounds a bit like display adjustment on a cell phone, as you call them over there. Difference between display timeout, as opposed to backlight timeout....that kind of thing!


Regards,

Mike.

Glad to hear Mike! If you want or need any help just post in that thread in my signature. 
It used to lead you straight to the Wiki but now it goes to the thread and the first post has the link to the wiki in it.
It is not nearly as difficult as it at first appears. 
You just drop a picture into **/boot/grub/** make a couple of changes to **/etc/default/grub** and add your boot partitions to **/etc/grub.d/40_custom** 
but then you save that as **/etc/grub.d/06_custom** and leave **/etc/grub.d/40_custom** asis.
That way your custom entries appear on top while all the default entries show below that. So, you've really done nothing to affect your system at that point.

Then when your comfortable with the way the custom entries work, you make the other files unexecutable so they don't show up and just the menu as I posted above shows.
Like I say it is not nearly as complicated as it first appears. It's simple once you've done it a couple of times. I can practically do it with my eyes closed. :p

Cheers

---

### Post by Mike_Walsh on 2014-10-08
> **Cavsfan said:**
> it is not nearly as difficult as it at first appears. 

It's simple once you've done it a couple of times. I can practically do it with my eyes closed. :p

Cheers

Hmm! O-kaaay; I'll take your word for that. 

It is, of course, the mark of the craftsman; making the difficult appear simple. Still, I'm finding Linux a LOT easier than I at first feared I would, 5 months ago; I guess 30-odd years of faffing about with these things has got to count for SOMETHING!! :p

I'm the same, really; very cautious when I first try something out, then finding that it wasn't SO bad, after all. So you try it again (and again), and before you know it, something you were in two minds about quickly becomes second nature, and you're doing it almost without thinking about it...

You may well find me dropping you a line in that thread before very much longer..! ;)

Regards,

Mike.

---

### Post by Mike_Walsh on 2014-10-09
@Dennis N;

Hiya, mate. I've just tried your 'fix'; works nicely, too. I've still had to re-arrange my Grub stuff, 'cos I've just had 3.13-0.37 come down the tubes for all my distros this morning..! It ALWAYS re-arranges things in the main sda Grub entry when that happens.....as I'm sure you're no doubt aware!

Cheers for that, though; much appreciated, as always.

Regards,

Mike.

---

### Post by Dennis N on 2014-10-09
> **Mike_Walsh said:**
> @Dennis N;

Hiya, mate. I've just tried your 'fix'; works nicely, too. I've still had to re-arrange my Grub stuff, 'cos I've just had 3.13-0.37 come down the tubes for all my distros this morning..! It ALWAYS re-arranges things in the main sda Grub entry when that happens.....as I'm sure you're no doubt aware!

Cheers for that, though; much appreciated, as always.

Regards,

Mike.

Hi Mike,

Yes, with more than one OS you would need to update-grub in the "main" OS to have it reflect any new kernels installed in any other systems. You can avoid that with a custom menu, which I use. I wrote a concise description of how I make a custom menu in that same thread, post #8, under "What I did" part way through that post.

[http://ubuntuforums.org/showthread.php?t=2246349&p=13133445#post13133445](http://ubuntuforums.org/showthread.php?t=2246349&p=13133445#post13133445)

It's a real time saver (no upkeep needed) and also allows you to make a more appropriate title for each grub entry besides "ubuntu".

---

### Post by Cavsfan on 2014-10-10
I also wanted to mention a very valuable tool, in my opinion, to label your partitions. 
It was first shown to me by an admin here drs305 who retired. He wrote the main grub wikis.

[ATTACH=CONFIG]257108[/ATTACH]

I am not sure what these partitions look like without labeling them but I find this very convenient. 
[B]
sudo tune2fs -L "Utopic" /dev/sda5[/B] 

The labels also show here:
```
cavsfan@cavsfan-MS-7529:~$ sudo blkid
[sudo] password for cavsfan: 
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" PARTUUID="a55f55ec-01" 
/dev/sda2: LABEL="Precise" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" PTTYPE="dos" PARTUUID="a55f55ec-02" 
/dev/sda3: UUID="e14dc02e-6ea8-4c95-b4d0-9dc04d32294d" TYPE="swap" PARTUUID="a55f55ec-03" 
/dev/sda5: LABEL="Utopic" UUID="7c76d1de-7439-4b55-b587-898f104235da" TYPE="ext4" PARTUUID="a55f55ec-05" 
/dev/sda6: LABEL="Trusty" UUID="d3281f82-3582-4081-b4d7-4769a2f427c5" TYPE="ext4" PARTUUID="a55f55ec-06" 
/dev/sda7: LABEL="Mint-Maya" UUID="77cf61db-2e8b-4531-9594-80f35ad4dc69" TYPE="ext4" PARTUUID="a55f55ec-07" 
/dev/sda8: LABEL="Mint-Quina" UUID="673f25f0-6149-4da7-98f8-4ebfe08a2188" TYPE="ext4" PARTUUID="a55f55ec-08" 
/dev/sda9: LABEL="Utopic-Mate" UUID="9c1694e3-0a35-4cf2-9c74-4103abce882f" TYPE="ext4" PARTUUID="a55f55ec-09" 
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs" PARTUUID="f87b4c9a-01" 

```

It is mentioned in section 1.5 of my wiki.

[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Labelling_the_partitions](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Labelling_the_partitions)

---

### Post by Mike_Walsh on 2014-10-11
Hi, Cavsfan.

Thanks for that..! That makes IDing my partitions a hell of a lot simpler.

I'll ask you this, since I'm still only scratching the surface of what I can do with Ubuntu; once you've performed this, and labelled the partitions.....do you need to perform this every time you boot up, or is this permanent now?

Don't I need to edit a .config file somewhere, or something? :-k

Regards,

Mike.

---

### Post by Cavsfan on 2014-10-11
> **Mike_Walsh said:**
> Hi, Cavsfan.

Thanks for that..! That makes IDing my partitions a hell of a lot simpler.

I'll ask you this, since I'm still only scratching the surface of what I can do with Ubuntu; once you've performed this, and labelled the partitions.....do you need to perform this every time you boot up, or is this permanent now?

Don't I need to edit a .config file somewhere, or something? :-k

Regards,

Mike.

It should stay that way until you label it differently. I've had the occasion to perform that command twice but that is about it. 
It should be good until you change it.
[COLOR=#ff0000]You can also label the partitions with Gparted[/COLOR] but the command is easier IMO.

If you label something with 2 words I suggest you place a dash inbetween the words like "Utopic-Mate". That way you can access that partition from another partition easier.

---

### Post by Dennis N on 2014-10-11
Hello there Mike -  you can also just use gparted to label partitions: **Partition > Label**
No live cd needed. Unmounting not needed.

---

### Post by Mike_Walsh on 2014-10-11
Hi, guys; thanks for both replies.

MORE info for my single brain cell to process; ouch, that HURTS! ;)

@Dennis; You're right, I'd forgotten that.....information overload, I think is the problem...

Regards,

Mike.

---

### Post by Cavsfan on 2014-10-11
> **Dennis N said:**
> Hello there Mike -  you can also just use gparted to label partitions: **Partition > Label**
No live cd needed. Unmounting not needed.

I mentioned that already. There are 2 ways to do it. See the red in my previous post. But, it's all good.

The CLI way requires nothing but the terminal.

---

### Post by Dennis N on 2014-10-11
> **Cavsfan said:**
> I mentioned that already. There are 2 ways to do it. See the red in my previous post. But, it's all good.

The CLI way requires nothing but the terminal.

What happens is when I started composing the post you quote, yours was not there. During the time I was thinking and writing, you posted yours.  Happens a lot on the forums.

---

### Post by Cavsfan on 2014-10-11
> **Dennis N said:**
> What happens is when I started composing the post you quote, yours was not there. During the time I was thinking and writing, you posted yours.  Happens a lot on the forums.

Yes, I understand quite well. I'm pretty slow at times and sometimes by the time I've looked at what has been posted and then post my response I see there are 5 or so other posts. :lol:

It's all good. We're all just trying to help. 

Cheers

---

