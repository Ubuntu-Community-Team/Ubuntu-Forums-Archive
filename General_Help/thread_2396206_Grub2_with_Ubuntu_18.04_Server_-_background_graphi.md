---
title: "Grub2 with Ubuntu 18.04 Server - background graphics"
date: 2018-07-12
forum: General Help
---

### Post by nsmith.maculogix on 2018-07-12
I've been experiencing some issues with Grub 2.02 that is setup with  Ubuntu 18.04 Server.  I have been attempting to get a graphic splash to  display but have had no luck.  At the grub console:
  ```
grub> vbeinfo
List of supported video modes:
Legend: mask/position=red/green/blue/reserved
 Adapter 'VESA BIOS Extension Video Driver':
    VBE info: version: 3.0 OEM software rev: 1.0
              total memory: 63424 KiB
    EDID version: 1.3
 Preferred mode: 800x600

```  I have a 800x600 LCD connected to the SBC running this system so that  seems to be ok.  When running with a higher resolution monitor, this  max resolution value is displayed accordingly. I found an article indicating that with Grub2 the image must be 256  colors only so I've verified this and tried both a .jpg and .png file  format.  I could not find reference to this in the GRUB help (grub.pdf)  from the GNU site.

  The /etc/default/grub file:
  ```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="2"
#GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND="/boot/grub/Splash.png"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that   obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="800x600x8"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```  Running sudo update-grub generated a message that a non-zero  GRUB_HIDDEN_TIMEOUT isn't supported with  GRUB_HIDDEN_TIMEOUT_QUIET="true".  I commented this out as if I didn't I  would never see the Grub menu and it would immediately boot the first  option.
  I have tried with and without specifying the background path variable.
  Since I have X and GTK installed I installed 'grub-customizer'.  This  is where the "800x600x8" came from in the above configuration.  I've  tried multiple configurations with this as well as trying to simply  change the test colors but none of the text color changes seem to be  applied.  The time out and option setting changes seem to be ok and  propagate through to update process.
  It appears that Grub is actually in console / text mode and not  really in graphical mode.  However I'm not sure how to confirm this.
  At the grub console I noticed the vbetest command (from help).  This indicated:
  error: no suitable video mode found
  So maybe this indicates it isn't in a graphics mode?  Is there maybe a way to resolve this?
  I'm able to change the timeout in the config and perform an update  with no error messages being generated.  I just can't seem to get the  graphics mode splash to display.
  I tried working with Grub in my VMWare player but it looks like grub  is being bypassed with VMWare player or something is configured  differently by default differently with 18.04 Server on VMWare as the  grub config looks like the installer debian version.  Update-grub in the  VM generates an error indicating the default isn't found.
  Has anyone tried displaying a graphic splash with Grub2.02 / Ubuntu  18.04 LTS?  Or a suggestion to further diagnose this with my SBC  (Advantech MIO-5251)?

---

### Post by nsmith.maculogix on 2018-07-12
A little more information:
I have tried setting:

    GRUB_TERMINAL="gfxterm" 

as it looks like this is the only way the 00_header script will enable gfxmode in the generated grub.cfg.
I also tried setting each individually:

    GRUB_TERMINAL_INPUT="gfxterm"
    GRUB_TERMINAL_OUTPUT="gfxterm"

I tried instrumenting the 00_header script so I could check these variables.  It appears that GRUB_TERMINAL_INPUT and _OUTPUT is always set to console regardless of what I specify in the grub input file. Evidently grub-mkconfig is doing something with these variables?  Anyone know how these variables should be set? Is there another way to debug this?   Maybe some rule that overrides what is specified in the grub file?

I tried manually editing the grub.cfg file using a Ubuntu desktop grub.cfg as a model but was unable to get a graphic terminal to appear with a graphic splash.  Seems I'm missing something fundamental.

---

### Post by nsmith.maculogix on 2018-07-12
I installed Ubuntu 18.04 LTS desktop on the same hardware and have no problems setting the background image.  It seems to default to gfxmode by default with even the simple grub parameter file.  Simply copying the .png file into /boot/grub and running update-grub finds the .png, updates the grug.cfg accordingly and it is displayed.  So I'm assuming there is something quite different about how grub is installed / setup with 18.04 Server.

---

### Post by gfreshman on 2018-08-08
Hello, I have exactly the same issue as you are describing. I can easily have background image in GRUB with single line added to /etc/default/grub in Ubuntu 18.04 **Desktop**, but no luck in **Server** edition. Have you, by any chance, found some solution for this? I have read many guides and articles about gfx in GRUB, but this forum topic and your StackOverflow question are the only mentions of this issue I have found. I have been comparing GRUB config files from both editions and they are the same, but then grub.cfg generated by update-grub is different, server is adamant about *terminal_input console* & *terminal_output console *and I have no idea why. :confused:

---

