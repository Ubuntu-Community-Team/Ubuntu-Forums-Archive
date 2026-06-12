---
title: "Changing the resolution of the greeter and the plymouth screen"
date: 2015-06-06
forum: General Help
---

### Post by amhndu on 2015-06-06
I have Lubuntu 15.04 and I want to change the resolution of the greeter and the plymouth loading screen.
By going to Applications Menu > Preferences > Monitor Settings, I was able to change the resolution to my liking but this setting only applies after I login.

Actually, I would have been fine with any legible resolution, after all, it's just a greeter but it is set as an odd 1024x768**i**. I have no idea what that i suffix means but the screen is rather blurry and the text poorly rendered this way. Thus, I would like to set this to 1024x768, my preffered resolution.

---

### Post by amhndu on 2015-06-07
Bump.

---

### Post by Bashing-om on 2015-06-07
amhndu; Hello ;

Try to effect grub's resolution by editing one of grub's config files.
The file to be edited is " /etc/default/grub " we edit the file :
```

sudo cp /etc/default/grub /etc/default/grub-07jun2015
gksudo /etc/default/grub

```
Of interest here is the line " [color=red]#[/color]GRUB_GFXMODE=640x480 "
change the line to read:
```

GRUB_GFXMODE=1024x768

```
note that the comment character '#' at the start of the line is removed.

Save the file and exit back to terminal, and to propagate the change to the operating system, run terminal command:
```

sudo update-grub

```

Reboot to see the effect.

[INDENT][INDENT]ain't grub wonderful
[/INDENT][/INDENT]

---

### Post by amhndu on 2015-06-08
@Bashing-Om, first, thank you for helping me.
The problem is not with grub's resolution, it's resolution is fine but the problem is with the resolution in which the **login screen** and the **tty**'s appear. It's odd resolution i.e. 1024x768 suffixed with "**i"** makes the screen render improperly on my monitor, the grub screen is fine.
To ask the question in another way, how can I change the resolution of **ALL users**&#8203;

---

### Post by Bashing-om on 2015-06-08
amhndu; Well;

I can relate that enabling a resolution in grub does effect the initial text terminal and splash image.
My edit to this effect:
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1600x900

```

Grub controls the resolution until the GUI is loaded and the graphics driver for the GUI is loaded. Until someone logs onto the system and activates the GUI The kernel (nobody ?) and root are the only users, and in this TTY, grub I do expect to have control and pass to the kernel the screen settings .

Try it;
[INDENT][INDENT][INDENT]you may be pleasantly surprised
[/INDENT][/INDENT][/INDENT]

---

### Post by amhndu on 2015-06-09
It didn't work :(
Just to be sure, here's the grub file:
```

~ $ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1024x768


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by amhndu on 2015-06-09
Also tried this [http://askubuntu.com/a/18463](http://askubuntu.com/a/18463) but it didn't work either, not only that with those settings, I got a "ACPI PCC probe failed" message during the bootup. (which I found out to be harmless and useless)

---

### Post by Dennis N on 2015-06-09
I think you would want to change the lightdm display resolution to affect the greeter. lightdm is the display manager that starts the xserver, greeter, and user sessions:

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

A quick search found an article on forcing a particular resolution:

[http://www.mattfischer.com/blog/?p=154](http://www.mattfischer.com/blog/?p=154)

It is a bit old (2013), so you may find something more recent.  I have no idea how well these ideas would work today. You should search the web and research this further.

The 'i' in 1024x768i probably means interlaced, and applies to television displays and the way they paint the screen with the scan lines - in two passes with every other line painted on each pass.

---

### Post by Bashing-om on 2015-06-09
@Dennis N ;

Wow, An elegant solution .

Noted. As always, the tutelage is appreciated .

[INDENT]'buntu
[INDENT][INDENT][INDENT]1 for all and all for one
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by amhndu on 2015-06-11
There was no `/etc/lightdm/lightdm.conf` file as required by that blogpost, but there were these files in that directory:
* lightdm-gtk-greeter.conf
* lightdm-gtk-greeter-ubuntu.conf 
* users.conf
By looking at the files, I realized that lightdm-gtk-greeter.conf is probably the one I should edit (I knew by seeing the `background` images specified in both) and followed that blogpost with this file
Unfortunately, this didn't work either :(
(And I'm sorry for the delay in replying, some stuff came up)

---

### Post by amhndu on 2015-06-11
Also, I tried switching to a different terminal now (C-A-F<n>), they are now in the 1024x768 resolution (my preferred resolution).
I'm guessing, this is due to the edited grub file, so, now it looks like I'll have to look lightdm configurations for the greeter.

---

### Post by cariboo on 2015-06-11
It might help if you told us what type of display you are using. I have an older Samsung 32" LCD that would only do 720p when I used it for a TV. I can force the resolution to 1920X1080, but the display is all but unusable until I set the font size to 32px+, which defeats the purpose of having a high resolution display. It's native resolution using the vga port is 1360X720, and that's what I leave it set at.

---

### Post by amhndu on 2015-06-11
It's an old CRT monitor, xrandr output :
```

Screen 0: minimum 8 x 8, current 1024 x 768, maximum 32767 x 32767
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 270mm x 200mm
   1024x768       60.0* 
   1024x768i      87.1  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        85.0     75.0     72.8     66.7     60.0     59.9  
   720x405        70.0  
   720x400        70.1  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

Please tell me if there's anything else I can provide

---

### Post by Bashing-om on 2015-06-11
amhndu; et all ; Humm ....

Presently donning my "learning cap"/ let us hope it does not become a "dunce cap" .
I do have an lubuntu install on this box, and later I will reboot into it and see what I can learn to add to this thread.
It do look like - to me - that what is set for the resolution should be what is being used . Let's find out at what point lightdm starts it's greeter. Grub is set to "1024x768", xrandr says the display is set to same, so where could the disparity be ?
> 
Also, I tried switching to a different terminal now (C-A-F<n>), they are now in the 1024x768 resolution (my preferred resolution).
I'm guessing, this is due to the edited grub file, so, now it looks like I'll have to look lightdm configurations for the greeter.


[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by amhndu on 2015-06-11
> [COLOR=#000000]xrandr says the display is set to same[/COLOR]
Note that this is what I get **after** I log in, that is, this is set up by lxsession/lxrandr much later than when lightdm has started

This just got even more confusing, now the terminals are in 1024x768*i* resolution :confused:. So, I think I did something which caused the change in resolution, but since it didn't effect the greeter, I probably reverted it back 
Now, I'll try and isolate whatever configuration causes the change in terminals' resolution.

EDIT: I made lightdm.conf file in /etc/lightdm/ with the following contents
```

[SeatDefaults]
display-setup-script=/etc/lightdm/lightdmxrandr

```
Where lightdmxrandr is a shell script which changes the resolution to 1024x768 with xrandr.
After saving it and rebooting .. lightdm didn't like it and didn't load the login screen ...
It loaded up properly when I removed the file

EDIT2 : Tried adding the display-setup-script line to 60-lightdm-gtk-greeter.conf and 20-lubuntu.conf in /usr/share/lightdm/lightdm.conf.d/, both failed with some "drm checksum error message"

(on a different note, I see that the "fonts" in the forum text insert box are all "Mircosoft" fonts ?? It doesn't even have the "Ubuntu" family [but of course the forum is in that font])

---

### Post by Bashing-om on 2015-06-12
amhndu; HoKay ;

I am back, booting from a 14.04 lubuntu install with a bit more ammo .

A list of the files in the target directory:
```

sysop2@lubie1404:~$ ls -al /etc/lightdm
total 32
drwxr-xr-x   3 root root  4096 Jun 12 16:01 .
drwxr-xr-x 129 root root 12288 Jun 12 16:02 ..
-rw-r--r--   1 root root    73 Dec  1  2013 lightdm.conf
drwxr-xr-x   2 root root  4096 Jun  9  2014 lightdm.conf.d
lrwxrwxrwx   1 root root    55 Sep 23  2012 lightdm-gtk-greeter.conf -> /etc/alternatives/lightdm-gtk-greeter-config-derivative
-rw-r--r--   1 root root  1317 Mar 13  2014 lightdm-gtk-greeter-ubuntu.conf
-rw-r--r--   1 root root   452 Mar 11 17:32 users.conf
sysop2@lubie1404:~$

```

And what a default /etc/lightdm/lightdm.conf file looks like:
```

sysop2@lubie1404:~$ cat /etc/lightdm/lightdm.conf

[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=Lubuntu
sysop2@lubie1404:~$

```

Let's go back to as close to default as possible and take off again.

[INDENT][INDENT]I too think there should be a simple solution
[/INDENT][/INDENT]

---

### Post by amhndu on 2015-06-12
Hey all,
I have something embarrassing to confess, the reason lightdm didn't start when I edited the .conf files the last was that ...
My display setup script contained invalid arguments for xrandr :oops:
When I made a lighdm.conf file as exactly as Bahing-Om's WITH the display-setup-script line, lightdm didn't start, but when I removed that line with just the defaults, it started, prompting me to test the command in display-setup-script. (I really thought that I had tested it previously)
Then, I corrected it and added the display-setup-script line to lightdm.conf, the greeter was in the correct resolution.
Now, I have the display-setup-script line at the end of 20-lubuntu.conf in /usr/share/lightdm/lightdm.conf.d/ and everything is good.

Thanks to all who have helped and special thanks to Bashing-Om for sticking up even after a week of the original post.
Marked as [SOLVED]

---

### Post by Bashing-om on 2015-06-13
amhndu; Outstanding !

It is you who do good work and spread the knowledge.

[INDENT][INDENT]look forward to our next
[INDENT][INDENT][INDENT][INDENT]adventure
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

