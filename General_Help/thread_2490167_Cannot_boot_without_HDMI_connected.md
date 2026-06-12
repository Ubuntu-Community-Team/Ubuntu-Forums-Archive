---
title: "Cannot boot without HDMI connected?"
date: 2023-08-24
forum: General Help
---

### Post by n-pat on 2023-08-24
I just installed 22.04 server on a mini pc. Updated, upgraded, got ssh and samba running. All was well

However when i try to boot without my HDMI monitor connected, it stalls. If I connect and boot then disconnect the HDMI the machine seems to freeze. I notice this because I have a remote ssh session running at the time. If I reconnect, the ssh unfreezes and everything works again.

I saw no problem in syslog. Can someone point me to the right logs or share any other ideas about this. I'd like to boot without monitor or keyboard since it is just a server.

Thanks

---

### Post by #&amp;thj^% on 2023-08-24
Is this with a nVidia GPU?
Ubuntu (or any Linux for that matter) doesn't care if a monitor or keyboard is connected. The BIOS however does care. So you need to disable the wait/ask for keyboard settings in your BIOS
Can you disable the HDMI port and keyboard in your Bios?

---

### Post by n-pat on 2023-08-24
No GPU AFAIK.

I will try disabling HDMI but then I can never use in the case of a problem connecting via ssh. There is only DP and HDMI for connectors and I only have an HDMI display.

Worth a try but not ideal.

---

### Post by MAFoElffen on 2023-08-24
For nVidia and AMD GPU's, the drivers, by deault, pole the ports for connections to a display device, if not found, then fail and throw an error.

For headless servers, there are "Null Device" connectors that they sell to trick a computer into thinking it has a display connected. (For example: [https://www.amazon.com/Headless-Display-Emulator-Headless-1920x1080-Generation/dp/B06XT1Z9TF](https://www.amazon.com/Headless-Display-Emulator-Headless-1920x1080-Generation/dp/B06XT1Z9TF)) That is one solution for headless servers.

The other is to configure the display driver to NOT pole the devices, and to ignore EDID, if found or not. For example, using X11, and in the xorg.conf file, in Section "Device":
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7050 PV 7 nForce 630a"
    Option         "UseEDID"        "FALSE"
EndSection

```
But this will only work if it has a GUI installed... So a pseudo Linux Server (Linux Desktop Edition running server services). ...Which many people still refer to as their server. A normal Server Edition sevrer will never hit this file.

The third thing to do for a headless server... especially if no graphics engine is loaded (most Linux Servers) is to edit file /etc/default/grub and add "nomodeset" to line GRUB_CMDLINE_LINUX_DEFAULT... Most people know that this boot parameter will help system to start if they do have GPU's that may need 3rd-party graphics drivers... But most do not realize that it does this by telling the kernel to not look for an EDID connected device. Remember to use 'update-grub' after editing that file to pick up the changes. This "IS"" the solution I recommend. Most of my servers, start without a connected display, though they are connected to a single display and keyboard, shared to my other severs via a KVM Switch... So I also set the kernel KMS modesetting video resolution via the boot cmdline in Grub. 

All 3 of those are accepted solutions for headless servers.

---

### Post by #&amp;thj^% on 2023-08-24
> **MAFoElffen said:**
> 

All 3 of those are accepted solutions for headless servers.
+1
And not to forget an "init3" option as well. (more on that if needed)

---

### Post by MAFoElffen on 2023-08-24
Yes. For init 3 on boot, just add "-- 3" as the boot parameter in line GRUB_CMDLINE_LINUX_DEFAULT in place of "quiet splash" and/or at the end of that line...

---

### Post by #&amp;thj^% on 2023-08-24
> **MAFoElffen said:**
> Yes. For init 3 on boot, just add "-- 3" as the boot parameter in line GRUB_CMDLINE_LINUX_DEFAULT in place of "quiet splash" and/or at the end of that line...

Ya What he said. :)

---

### Post by n-pat on 2023-08-24
Wow thanks for the help.

I have ONLY Ubuntu 22.04 server + ssh + samba installed, no GUI, no X11 no desktop so a "real" server install :). My "spash screen" is a terminal shell asking for password.

I see the GRUB_CMDLINE_LINUX_DEFAULT in /etc/grub.d/... but am a bit unclear about where to safely add to this since it is modified in several .d files. Does grub source this into a shell? Should I add to some shell variable? I have never messed with grub before.

init 3?

Can someone translate this into noob for me :confused:[COLOR=#000000]

[/COLOR]

---

### Post by MAFoElffen on 2023-08-25
At your Console prompt via ssh
```

sudo nano /etc/default/grub

```
That will open that file in the nano editor, with elevated permissions. Go to the line that says
```

GRUB_CMDLINE_LINUX_DEFAULT=""

```
Change it to
```

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

```
Press <Cntrl><O>... Confirm the filename, <Enter>. to save the changes. Press <Cntrl><X> to exit back to the command line.

Then do
```

sudo update-grub

```
To pick up the changes.

Then do 
```

sudo reboot

```
to reboot and test.

---

### Post by #&amp;thj^% on 2023-08-25
> **n-pat said:**
> 
init 3?

Can someone translate this into noob for me :confused:[COLOR=#000000]

[/COLOR]

From the man page:
> In Unix-based computer operating systems, init (short for initialization) is the first process started during booting of the computer system. Init is a daemon process that continues running until the system is shut down. It is the direct or indirect ancestor of all other processes and automatically adopts all orphaned processes. Init is started by the kernel using a hard-coded filename, and if the kernel is unable to start it, a kernel panic will result. Init is typically assigned process identifier 1.
An init3 is without a graphical session.
> daemon(3), org.freedesktop.systemd1(5), systemd.unit(5),
        3. Interface Portability and Stability Promise

And MAFoElffen has lay-ed out a nice and easy to use suggestion.

---

### Post by MAFoElffen on 2023-08-25
Please remember mode "init 3".

That is a fail-safe mode to boot into when @#$% hits the fan in the Linux Graphics Layer. From that mode you can boot your installed OS without the graphics layer starting, get to a 'Console Only' command prompt, and make changes to recover.

That is something you can always depend on...

On Server Edition, by default, it is a VGA pseudo framebuffer graphics mode. Most people assume that it is text only. It can be if you force it to be. It can still be affected by graphics challenges on some hardware combinations. 

I use that (Server) graphical mode. I use server pallet theming on my servers, just because I can. LOL Things do not need to be boring.

---

