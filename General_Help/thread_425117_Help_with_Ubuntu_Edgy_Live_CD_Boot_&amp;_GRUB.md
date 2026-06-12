---
title: "Help with Ubuntu Edgy Live CD Boot &amp; GRUB"
date: 2007-04-27
forum: General Help
---

### Post by ChubbyBear on 2007-04-27
Ok, well...since this my first post I would first off just like to say hello and thank everyone for their help on my past problems. See...I have been a lurker for quite a while [IMG]http://www.absoluteprelude.com/forums/style_emoticons/default/ninja_hide.gif[/IMG] and decided to finally join the forums.

So anyhow...I hate to start off with a problem in for forums...but alas, I need some help.

******CLIFF NOTES FOR THE PEOPLE THAT HATE TO READ LIKE MYSELF******
[B][COLOR="Red"]
[LIST=1]
[*]Searched Ubuntu forums and Google for "How to reinstall GRUB."
[*]Have Ubuntu Edgy installed already. ([COLOR="DarkOrange"]Section 1[/COLOR])
[*]Deleted GRUB by accident. ([COLOR="Blue"]Section 2[/COLOR])
[*]Trying to reinstall GRUB. ([COLOR="Gray"]Section 3[/COLOR])
[*]Ubuntu Edgy Live CD will boot, when it gets to the pre-load (GNOME Splash?) screen it gets scrambled. ([COLOR="Magenta"]Section 4[/COLOR])
[*]I have a [COLOR="Lime"]Nvidia[/COLOR] 7800GT. ([COLOR="Lime"]Section 5[/COLOR])
[*]Dont know how to fix it. And I am a saaaaaaaad bear. :( 
[/LIST][/COLOR][/B]

[COLOR="DarkOrange"]1.[/COLOR] 
I have previously installed Ubuntu Edgy on my computer and life was awesome. I was chugging along just fine until one day my Windows XP had a problem. :( (Windows...have problems?! Nooo...not windows!.)

[COLOR="Blue"]2.[/COLOR] 
So yeah, I go to reinstall Windows on the 10gb partition I created for it. Well...after all that was done I went to go back to boot Ubuntu, well low and behold...I dont get the GRUB bootloader screen to choose to boot into Ubuntu. So I realized I deleted GRUB by accident from the Windows MBR.

[COLOR="Grey"]3.[/COLOR]
So I search the forums and Google on "How to reinstall GRUB." and find [_**a few places**_]("http://ubuntuforums.org/archive/index.php/t-24113.html") that show how.
Only one problem... you need to boot into Ubuntu and get into the terminal.

[COLOR="Magenta"]4.[/COLOR]
So I stick in my Ubuntu Edgy 6.10? disk and have the same problems I had before when I tried to install Ubuntu. I boot the CD and it runs fine until I get to this screen...
[IMG]http://debianadmin.com/copper/albums/edgy/3.png[/IMG]

[COLOR="Lime"]5.[/COLOR]
When I see this screen the little box (GNOME splash screen?) (see picture above) looks scrambled and it wont go any farther in the boot. So there is basically my problem. I fixed the problem before...but...I am stupid and cant remember exactly how I did it. I remember it had something to do with booting the Live CD and then editing something with the splash window OR changing the boot info or whatever because it was scrambling the video hince the scrambled screen.

Well...Since this post was kinda lengthy I tried to organize this post as much as I could so it would be easy to navigate, hope it helped. 

Any help would be greatly appreciated. 

Thanks, Ryan

---

### Post by Herman on 2007-04-27
Hello Ryan,
I don't know how to fix your display for the Ubuntu LiveCD, but I think I know the world's easiest way to re-install Grub.
You can use a [Super Grub Disk]("http://supergrub.forjamari.linex.org/")
 to do that. Just download a copy, it's free and only a very small download. You can get CD versions, floppy disk or USB versions. If you get the .iso file just make it into a CD and boot it,  the go 'English Super Grub DIsk'-->'Gnu/Linux'-->'[[FONT=Bitstream Vera Sans Mono]**Fix Boot of Gnu/Linux (GRUB)**[/FONT]]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Fix_Boot_of_GnuLinux_GRUB")'
That should fix it.

Regards, Herman :)

---

### Post by ChubbyBear on 2007-04-30
I got the program you said to get and  it brought back grub with no problem what so ever. Only problem is...now I am getting an error.

Error 17: Cannot mount selected partition.

Is there any way I can re-mount these drives?

---

### Post by zvacet on 2007-04-30
[http://ubuntuforums.org/showthread.php?t=426475]("http://ubuntuforums.org/showthread.php?t=426475")

---

### Post by Herman on 2007-04-30
Quote from the Gnu/Grub Manual,> 17 : Cannot mount selected partitionThis error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.The most common cause of this error when trying to boot Ubuntu would be your operating system entry's 'root (hdx,y)' details may be incorrect in your /boot/grub/menu.lst file. 
                                       
                                       You will need Super Grub Disk to boot Ubuntu for you so that you can easily check and repair your operating system's entry in menu.lst. 
                                       Super Grub can boot your operating system by symlinks to the kernel if you use, from the Main Menu,--> Boot Gnu/Linux and  Other OSes --> Boot Gnu/Linux -->...
                                       
I don't know how, but it seems as if either Windows or something else has changed your Ubuntu partition number. You may also need to edit /etc/fstab in Ubuntu with a new UUID number for Windows.
Regards, Herman :)

---

