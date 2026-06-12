---
title: "Ubuntu does not handls dvi monitor inputs"
date: 2006-10-11
forum: General Help
---

### Post by Lithp on 2006-10-11
Hi.,

When I use live cd. Ubuntu will not display on my monitor with DVI inputs. I have to use a VGA input for any success in getting a display.

Is this normal? Is there a way to resolve this issue?  By the way, the same happens with Mepis Linux distro. Isw this a Linux based fault?

---

### Post by meng on 2006-10-11
I have no problems with DVI output to monitor (I assume this is what you're talking about). What sort of graphics card do you have?

---

### Post by Lithp on 2006-10-11
I have a Radeon x1600 card with a Hanns-g monitor.
And yes that is what I am talking about. Did you have to configure your card or Ubuntu in any special way? 
By the way my display is wide screen 1440x900. Does that matter perhaps?

---

### Post by meng on 2006-10-11
I did not have to change anything to get DVI input. It may be that the widescreen display is relevant, but I'm not sure. Are you using the generic radeon driver, or the proprietary ATI drivers? You may wish to search the forums for how to install ATI drivers "properly" if you haven't already, but in my experience the best tutorial is here:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by fragos on 2006-10-11
I have an FX5200 with both DVI and VGA connectors.  I had been using a VGA CRT and upgraded to a wide screen LCD, 1440x900.  I removed the VGA cable and plugged in the DVI cable with the system powered down of course.  the DVI works flawlwessly.  I edited xorg.conf to get the 1440x900 on my Viewsonic VA1912wb.  Very nice monitor and the DVI has a much sharper display.  Its not clear what my video card would do if I hooked up two monitors, one DVI and the other VGA.  The Viewsonic has both DVI and VGA with a button to switch betwwen them.

---

### Post by Lithp on 2006-10-12
Hmm.... for some reason the only way I can get any display is if I use a VGA hookup. I am confused. Windows XP can function without any special configuration. yet not Linux.

I'm a newbie to Linux. Can anyone suggest exactly how to get my OS and monitor to play nicely.? Whether it be editing a config or something to that effect?

I am aware the simplest answer is merely to switch cables to VGA from DVI. I would rather not do that.I quite enjoy the crisp display the DVI has to offer.

TIA

---

### Post by meng on 2006-10-12
In my earlier post I discussed the proprietary ATI drivers rather than the default radeon drivers. You didn't indicate whether you'd tried that. That's a suggestion, although I can't be certain it would work.

---

### Post by fragos on 2006-10-12
If you used the Driver CD that came with your card with Windows that is equivalent to installing the ATI drivers on Linux.  The fact that Linux frquently works without a driver install is hardly a negative for Linux.  The live CD may be similar to running Windows without installing the driver CDs that are are always part of using Windows.  So the question is, did you install a driver CD for your ATI video card with Windows?

---

### Post by Narzuhl on 2006-10-12
i tried it on a Dell 20 Widescreen DVI and a ATI X1800 XT and a Nvidia 7900GS with out a problem. I could not get the fuill resolution in wide screen untill i edited the xorg.cfg file. but it works. With the live CD and the full install. Also tried it at work on my Compaq with a X1600 and a 20" Planar LCD and max resolution it would boot up with was 1280 x 1024. i could not leave it at work but it did boot up. Maybe a bad CD or an older one?

---

### Post by epennings on 2006-10-12
I used to have similar problems with my HP 1825 (dvi) + ATI Radeon 9600

I had to install Ubuntu using safe graphics mode. After installing I could just install an updated driver with this guide :

[http://ubuntuforums.org/showthread.php?t=204910&highlight=xpress+series]("http://ubuntuforums.org/showthread.php?t=204910&highlight=xpress+series") 
The latest version is 8.29.6 btw, the guide is a little old, but works great for me.

---

### Post by Pacey on 2006-10-12
Hey im having the same problem too. My rig is also running SLI graphics cards. Is it the DVI that doesnt work or bad support for SLI?

---

### Post by Lithp on 2006-10-13
Epennings:

When you linked to the "Guide" it brought up 34 pages of guides, codes, problems, and solutions.

Sorry, I am just too new at Linux and not all that smart ](*,) 

Is There a relatively simple answer for this problem?

I realize Linux takes work to learn. And I am willing to put in the time. It would be nice however, if I could lean Linux and Ubuntu by actually seeing what I am doing and learning in a graphical environment. Pages of code before I even get a display on my screen is discouraging.

TIA

---

### Post by epennings on 2006-10-13
I'll give a short summary :
(you can copy/paste the commands in a terminal)

Download driver :
```
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.29.6.run
```

Install prerequisites :
```
sudo apt-get update 
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```

Create *.deb packages :
```
chmod +x ati-driver-installer-8.29.6.run
./ati-driver-installer-8.29.86.run --buildpkg Ubuntu/dapper
```

Install the *.deb packages you created :
```
sudo dpkg -i xorg-driver-fglrx_8.29.6-1_i386.deb 
sudo dpkg -i fglrx-kernel-source_8.29.6-1_i386.deb 
sudo dpkg -i fglrx-control_8.29.6-1_i386.deb
```

Remove any old fglrx deb's from /usr/src/ :
```
sudo rm /usr/src/fglrx-kernel*.deb
```

Compile the kernel module :
```
sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod
```

**Note: You have to recompile the kernel module after each kernel update!**

Update the xorg.conf file :
```
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
```

**Reboot**

Confirm that it worked :
```
epennings@epennings-desktop:~$ **fglrxinfo**
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6065 (8.29.6)
```

---

### Post by Lithp on 2006-10-13
hi,
I tried the commands you suggested. but ran into the following problem.

"sudo module-assistant prepare,update " --- command not found
"sudo module-assistant build,install fglrx "  -- command not found

Any ideas?

---

### Post by epennings on 2006-10-14
I'm sorry, I kinda assumed you had the universe/multiverse repositories enabled. It looks like you don't ( module-assistant isn't installed )

You can enable it by editing your sources.list :
```
sudo gedit /etc/apt/sources.list
```

Replace the content of your sources.list with this (you can change nl with your countries 2-letter code): 

```
deb http://nl.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

## Major bug fix updates 
deb http://nl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

## Backports
deb http://nl.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

## Security
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
 
```

Save the file

Update your system :

```
sudo aptitude update
sudo aptitude dist-upgrade
```

Now you can try again from the start of my summary.

Let me know if you have any questions.

---

### Post by fvgm on 2006-11-03
hi, i have Radeon 9250 (rv280)... and i have installed fglrx driver, but with no signal in DVI output.. how i fix it??? can anyone help me?
I have installed by using xorg-driver-fglrx

sorry for mi english, i'm from Brazil.

---

### Post by epennings on 2006-11-04
You can use my guide above to install drivers for your card.
Unfortunately ATI doesn't support your card anymore in their latest drivers.
You have to install version 8.28.8.

From ATI site:
```
ATI Proprietary Linux x86 Display Driver

As of driver version 8.29.6 support for the following products is no longer included:

    * Radeon® 8500/9000/9100/9200/9250
    * Mobility™ Radeon® 9000/9100/9200
    * Radeon® IGP 9000/9100/9200

Users with these products should use driver version 8.28.8
```

Just replace all commands containing **8.29.6** with **8.28.8**

---

