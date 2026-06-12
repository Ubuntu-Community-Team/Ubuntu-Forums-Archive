---
title: "External Monitor Does Not Work (Thinkpad T43)"
date: 2008-02-27
forum: General Help
---

### Post by ncwv44b on 2008-02-27
Folks -

I have a ThinkPad T43 with a ATI Technologies Inc M22 [Mobility Radeon X300].  I know the card and connections work because I've used it when this thing had Windows and Fedora 7.  Also,  the BIOS splash shows up on the external monitor (but not the primary).

I'm running the latest version of all software via apt-get update/upgrade.

Ubuntu starts to freak out as soon as the external monitor (in this case a Mitsubishi HDTV) is hooked up.  I'm using the proprietary ATI driver (fglrx).  I am able to configure the card, but as soon as I reboot the main display is set to 640x480 and there is no output to the external monitor.  When I return to the 'Screens and Graphics' menu, it tells me it has been set to a versa-compatible card.

It appears that settings are not sticking when I click 'ok' from the 'Screens and Graphics' menu, and Ubuntu tries to autoconfigure and fails.  I don't understand why merely hooking up an external monitor severely screws with the primary monitor.  I'm not a noob, but I certainly am far from the esteemed hacker.

Please help.

Sincerely,
Kevin

---

### Post by oakgrove on 2008-02-27
Here's what worked for me.  Open a terminal and at the prompt type: 

xrandr --output LVDS --mode 1024x768 --output VGA --mode 1024x768

Then press enter.  The LVDS is your laptop display and the VGA is the external monitor.  Obviously, you can change the modes to whatever you want.

To see available modes, just type xrandr by itself at the prompt.

---

### Post by ncwv44b on 2008-02-28
The output to the HDTV didn't change.  I tried rebooting and it appeared it almost worked.  The screen  on the computer and HDTV went black, the TV suggests it has detected a 720p source, and then the external monitor dies and the computer displays an error.  

The error box appears to be xwindows, and it tells me that the computer can't autodetect my monitor  (local and external) and that I have to configure it.  I adjust the settings, click, okay, and it forces a reboot.  Repeat.

If the external the monitor (rgb) cable isn't attached, the computer will eventually reboot in 800x600.  The suggested graphics card is set to vesa-compliant.

---

### Post by ncwv44b on 2008-03-09
Help!  Come on guys!  What about Ubuntu's legendary community support? :)

Perhaps the following info will help.

```

<prompt>:  sudo aticonfig --initial 

Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-2
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfc139e0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7cdf92b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c88050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:01 5423999    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:01 5423999    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c64000-b7c65000 rw-p b7c64000 00:00 0 
b7c65000-b7c67000 r-xp 00000000 08:01 1622068    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c67000-b7c69000 rw-p 00001000 08:01 1622068    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c69000-b7c6a000 rw-p b7c69000 00:00 0 
b7c6a000-b7c6e000 r-xp 00000000 08:01 5424724    /usr/lib/libXdmcp.so.6.0.0
b7c6e000-b7c6f000 rw-p 00003000 08:01 5424724    /usr/lib/libXdmcp.so.6.0.0
b7c6f000-b7c71000 r-xp 00000000 08:01 5424713    /usr/lib/libXau.so.6.0.0
b7c71000-b7c72000 rw-p 00001000 08:01 5424713    /usr/lib/libXau.so.6.0.0
b7c72000-b7db6000 r-xp 00000000 08:01 1622043    /lib/tls/i686/cmov/libc-2.6.1.so
b7db6000-b7db7000 r--p 00143000 08:01 1622043    /lib/tls/i686/cmov/libc-2.6.1.so
b7db7000-b7db9000 rw-p 00144000 08:01 1622043    /lib/tls/i686/cmov/libc-2.6.1.so
b7db9000-b7dbc000 rw-p b7db9000 00:00 0 
b7dbc000-b7ddf000 r-xp 00000000 08:01 1622075    /lib/tls/i686/cmov/libm-2.6.1.so
b7ddf000-b7de1000 rw-p 00023000 08:01 1622075    /lib/tls/i686/cmov/libm-2.6.1.so
b7de1000-b7ece000 r-xp 00000000 08:01 5424707    /usr/lib/libX11.so.6.2.0
b7ece000-b7ed2000 rw-p 000ed000 08:01 5424707    /usr/lib/libX11.so.6.2.0
b7ed2000-b7edf000 r-xp 00000000 08:01 5424728    /usr/lib/libXext.so.6.4.0
b7edf000-b7ee0000 rw-p 0000d000 08:01 5424728    /usr/lib/libXext.so.6.4.0
b7ee0000-b7ee1000 rw-p b7ee0000 00:00 0 
b7ee1000-b7ee8000 r-xp 00000000 08:01 5424750    /usr/lib/libXrender.so.1.3.0
b7ee8000-b7ee9000 rw-p 00006000 08:01 5424750    /usr/lib/libXrender.so.1.3.0
b7ee9000-b7eee000 r-xp 00000000 08:01 5424748    /usr/lib/libXrandr.so.2.1.0
b7eee000-b7eef000 rw-p 00005000 08:01 5424748    /usr/lib/libXrandr.so.2.1.0
b7ef2000-b7efc000 r-xp 00000000 08:01 1622083    /lib/libgcc_s.so.1
b7efc000-b7efd000 rw-p 0000a000 08:01 1622083    /lib/libgcc_s.so.1
b7efd000-b7f00000 rw-p b7efd000 00:00 0 
b7f00000-b7f1a000 r-xp 00000000 08:01 1622029    /lib/ld-2.6.1.so
b7f1a000-b7f1c000 rw-p 00019000 08:01 1622029    /lib/ld-2.6.1.so
bfbff000-bfc14000 rw-p bfbff000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

Any ideas?

Settings just don't seem to "take."  It doesn't matter how many times I configure the monitors, the computer tries to and fails to properly detect settings.  It doesn't even get the right driver card.

Please help!

Thanks,
Kevin

---

### Post by jakupl on 2008-03-15
never heard of this.

---

### Post by bfallik on 2008-03-25
I have a T43 and the same problem.  I have gotten the external display to work if a VGA cable is plugged in when the laptop boots.  Otherwise, this hasn't worked on Edgy, Feisty, Gutsy, or Heron beta.

---

