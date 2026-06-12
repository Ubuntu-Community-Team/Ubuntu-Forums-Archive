---
title: "Can not install Ubuntu GNOME on ASUS F3F Laptop"
date: 2014-03-01
forum: General Help
---

### Post by amjjawad on 2014-03-01
Hi,

Since I have joined Ubuntu GNOME Team in July 2013 until few days ago, I had no 'real hardware' to test Ubuntu GNOME on and had to do that on a virtual machines. Now that [my HP Laptop is no longer working]("http://ubuntuforums.org/showthread.php?t=2204750") (maybe dead forever) and I have finally found 2GB RAM stick that I can use on [my ASUS F3F Laptop]("http://phillw.net/hardware/p7x41Lgx") which had only 512MB RAM that is not enough to run Ubuntu GNOME - which was like a great news to me - I was so sad and surprised that I actually couldn't even run the Live Session on that machine :(

It is 32-bit machine so I did try both
[Ubuntu GNOME 13.10]("https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME") i386
and
[Ubuntu GNOME Trusty Tahr Beta 1]("http://ubuntugnome.org/trusty-tahr-beta-1-released/") i386

I got the exact same result when I tried to boot from a LiveUSB created by UNetbootin.

This is what happened:

1- Plug the LiveUSB
2- Turn the machine ON
3- Enter BIOS
4- Make sure the laptop boots from the USB
5- Reboot
6- I do see this:

[IMG]https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME?action=AttachFile&do=get&target=try.png[/IMG]

But not really this, I actually see UNetbootin Menu which has similar optons

7- Select "Check Disk for errors/defects"
8- It gives me 'No' errors so everything is good
9- Select "Try without installation"
10- When I get to the Live Desktop, it is empty and nothing but [the default wallpaper of Ubuntu GNOME]("http://distrowatch.com/table.php?distribution=ubuntugnome")

The same thing happened on both Saucy (stable) and Trusty (development).

If I choose "Install", it got stuck on the first steps and IIRC (If I Remember Correctly), it stopped on the partitions screen as I always choose "Something else".

Hardware Details of my machine:
[http://phillw.net/hardware/p7x41Lgx](http://phillw.net/hardware/p7x41Lgx)
Right from: [https://wiki.ubuntu.com/QATeam/Hardware](https://wiki.ubuntu.com/QATeam/Hardware)

That is actually one of my testing real machines.

Note that other systems like Lubuntu 13.10 is working just fine on that machine.

I had a previous chat with Tim (Ubuntu GNOME main developer) and IIRC, i think he mentioned something about 3D? that the Graphics Card should have 3D capabilities? not 100% sure, to be honest.

Anyone else have the same machine and/or specifications? 
No, I didn't try Ubuntu as I have stopped using it since 11.04 so didn't try it. Same goes for Kubuntu, I never use it (last time I did, it was Kubuntu 10.04).

The systems that I use are:
Ubuntu GNOME, Xubuntu and Lubuntu. Which are the very same systems that [I'm using to convert my neighbours to Linux]("http://amjjawad.blogspot.com/2014/01/2014-report-project-convert-my.html"). 

I got the extra RAM from a neighbour who broke her own laptop because her husband was trying to get the HDD out!

Thoughts?

Thank you so much, in advance :)

---

### Post by amjjawad on 2014-04-24
Hi,

Okay, a side of waiting almost two months, what else can I do? I'm really in need to get this sorted out :(
I don't want to test Ubuntu GNOME UU on a virtual machine.

Thank you!

---

### Post by starnixsa on 2014-04-24
Hi Ali,

I saw you request on the mailing list today and there are two things I can think of.

Firstly, can try make a USB Startup Disk with maybe the latest version of Ubuntu Gnome based on Trusty Tahr using the Startup Disk Creator available in Gnome.
Secondly, you didn't mention skipping the Live environment and going straight to the installation process. Could you maybe try that?

If these two suggestions don't work, please could paste the output from dmesg to pastebin and I'll try and see if I can assist further.

Best of luck :)

---

### Post by amjjawad on 2014-04-25
> **starnixsa said:**
> Hi Ali,

I saw you request on the mailing list today and there are two things I can think of.

Firstly, can try make a USB Startup Disk with maybe the latest version of Ubuntu Gnome based on Trusty Tahr using the Startup Disk Creator available in Gnome.
Secondly, you didn't mention skipping the Live environment and going straight to the installation process. Could you maybe try that?

If these two suggestions don't work, please could paste the output from dmesg to pastebin and I'll try and see if I can assist further.

Best of luck :)

Hi and thanks for posting :)

I finally figured out what is wrong and why this is happening.

The issue [in this thread]("http://ubuntuforums.org/showthread.php?t=2209125") is very much the same as the issue I'm having. 

This is the machine I'm talking about in this thread (ASUS F3F):

[ATTACH=CONFIG]252482[/ATTACH] 

What is happening is, it boots the LiveUSB of Ubuntu GNOME 14.04 LTS and it shows the desktop BUT it does NOT show anything except the Right Click Menu: Change Wallpaper and Settings.

The only way to get around this to display the internal/built-in monitor and switch to the external one, exactly the same what happened with me [with the other thread]("http://ubuntuforums.org/showthread.php?t=2209125") when I had to play/change the settings so that the built-in display is disable and only the external one works.

I will wait for Tim to be back online to ask him against which package should I report this unless someone here knows that.

I'm glad that I figured it out and I'm glad that there is nothing wrong with my machine. Hope it is a matter of time until this bug got fixed and yes, it was with Ubuntu GNOME 13.10 as well.

Thank you!

---

### Post by amjjawad on 2014-04-25
Okay, some good progress here :D

Pressing Fn+F8 on ASUS F3F will switch between the display modes.

I did that until I finally got a full desktop on my Acer External display:

[ATTACH=CONFIG]252483[/ATTACH]

Now, I'm finally installing Ubuntu GNOME 14.04 LTS on ASUS F3F :D

---

### Post by amjjawad on 2014-04-25
YES YES YES :D

Finally, I have a Real Hardware to test Ubuntu GNOME and no more VMs :D

[ATTACH=CONFIG]252484[/ATTACH]

This is the classic mode by the way because GNOME mode didn't work as I expected for some reason.

This thread will be marked as SOLVED!

Thank you!

---

