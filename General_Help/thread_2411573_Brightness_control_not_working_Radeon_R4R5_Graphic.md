---
title: "Brightness control not working Radeon R4/R5 Graphics on Dell 3541"
date: 2019-01-31
forum: General Help
---

### Post by Jay_Parekh on 2019-01-31
Can someone tell me how I can increase/decrease brightness on my laptop?

Dell 3541 AMD A6 6310 APU with AMD Radeon R4 graphics
Ubuntu 14.04.5 LTS
Using propreitary AMD (Preferences -> Additional Drivers -> Additional drivers (tab) -> Using video drivers for the AMD graphics accelerators from fglrx (propreitary))

Brightness control keys F11 and F12 do not work.

I tried all command line options [https://askubuntu.com/questions/149054/how-to-change-lcd-brightness-from-command-line-or-via-script](https://askubuntu.com/questions/149054/how-to-change-lcd-brightness-from-command-line-or-via-script)
but none seem to work.

xbacklight produces error: No outputs have backlight property

xrandr produces error:
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1366 x 768, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768       76.0* 

echo 20 > /sys/class/backlight/acpi_video0/brightness    returns no error, changes value in file brightness but does not change screen brightness

Ditto for sudo setpci -s 00:02.0 F4.B=80

---

### Post by KBD47 on 2019-02-02
I'm not an expert on this, but since no one else has responded my advice would be to install the newest LTS Ubuntu release 18.04. That will get you a newer kernel and perhaps some updated drivers which might solve your problem.

---

### Post by Jay_Parekh on 2019-02-03
Thanks KBD47, I will look into it.

I was hoping someone could tell me what the error messages mean when I use xrandr and xbacklight because I think that is where the problem lies.

Alternatively, I was hoping that someone using a similar laptop to mine could share what drivers they use.

---

### Post by Autodave on 2019-02-03
+1 with KDB47.  14.04 is nearly 5 years old.  Generally, Dell's don't have a lot of problems due to the fact that Dell actually sells some machines with Linux already installed.  Move up to 18.04 (and I recommend that you backup everything and do a clean install) and see what works and doesn't work.

You can download the 18.04 and make a bootable install medium.  Boot the machine to that and see if the brightness and backlight works then. Chances are that you are not going to have to install and drivers for that graphics card.

---

### Post by Jay_Parekh on 2019-02-03
Thanks for your input Autodave.  I am wary of doing a clean install because I have a dual boot (Win 10) machine and 3+ years ago when I installed 14.04 along side Win 10, I had lots of problems.  Maybe I will try an upgrade first.  If that does not work, I will risk a clean install.  But first, as you say, let me try the 18.04 USB boot to see if brightness control works.

---

### Post by KBD47 on 2019-02-03
You would have to upgrade to Ubuntu 16.04, then Ubuntu 18.04, that's why a clean install would be best. Depending upon your computer, do you have another option/way of installing Ubuntu besides dual-boot? What I'm thinking of is that some laptops with DVD drives are removable and you can put a 2nd hard drive in their place. Some desktop computers also have option for a 2nd drive. That would save you headaches with Windows 10, plus you could use an SSD drive which would be much faster. You could then reclaim space for your Windows 10 install. Just a thought.

---

### Post by Jay_Parekh on 2019-02-16
Here is the solution.

Open /etc/default/grub as root and change line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
Save file and run sudo update-grub from command prompt.  Reboot.

I can now control screen brightness with following command:  echo <n> | sudo tee /sys/class/backlight/dell_backlight/brightness; where n=backlight intensity 0-9.

/sys/class/backlight/dell_backlight helps control backlight, not brightness.  Not exactly what I am looking for, but I can live with this.

What I really need to control brightness is this Radeon driver /sys/class/backlight/radeon_bl0   but I do not know how to install it.

---

### Post by afflospark on 2019-02-16
[COLOR=#000000][FONT=Roboto]Hi ,
You can try this and let me know if it does not work.[/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]Go to control panel and open power options and see if you can increase the brightness through the operating system.[/FONT][/COLOR]

---

