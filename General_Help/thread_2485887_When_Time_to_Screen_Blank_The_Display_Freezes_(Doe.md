---
title: "When Time to Screen Blank The Display Freezes (Doesn't Turn Black)"
date: 2023-04-13
forum: General Help
---

### Post by denismc on 2023-04-13
[LIST=1]
[*]The system hasn't crashed.  It just doesn't visually update (ie. screen refresh), when it's time to blank, to show that the screen has blanked/locked. 
[*]Problem only occurs in v22.04 using Wayland. 
[*]Problem does NOT occur in v22.04 using XOrg. 
[*]Problem does not occur at all in v20.04 using Wayland (or any other configuration). 
[*]This problem has nothing to do with the desktop manager like GNOME, Unity.  It is specific to the Windowing protocol of Wayland. 
[*]The screen blanks correctly on first login, but the moment i go to "Settings" > "Screen" to look at the screen locking options it is then that the problem occurs permanently (until i reboot). 
[*]Enabling or Disabling animations makes no difference.  The problem still occurs. 
[*]Screen blank/lock is set correctly:
> 
gsettings get org.gnome.desktop.lockdown disable-lock-screen = false
gsettings get org.gnome.desktop.screensaver lock-enabled = true
gsettings get org.gnome.desktop.session idle-delay = unit32 60
gsettings get org.gnome.desktop.screensaver lock-delay = unit32 30
gsettings get org.gnome.desktop.screensaver ubuntu-lock-on-suspend = true 
[*]Under working conditions, after 60 secs the screen should turn black.  After 30 secs more the screen is locked, requiring the user to input a password.  This is what happens in v20.04  using Wayland. Works correctly. 
[*]However, when using Wayland in v22.04, after 60 secs the screen stops updating (never turns black). It looks like the pc crashed.  It hasn't. The screen just hasnt refreshed to show its black now.  A clock,  showing in my task bar,t stops updating. 
[*]Moving the my mouse (or pressing a key) the screen finally updates, revealing it is black (it had screen blanked at the correct time but just didn't show on screen).  So, its a screen refresh issue. 
[*]I am using Ubuntu within a VM (Workstation 17).  3D Acceleration is disabled and my virtual gfx driver is the default VMware: vmwgfx (llvmpipe - LLVM 15.0.6, 256 bits).  1 monitor.  In Ubuntu 22.04 (Gnome 42.5, mutter, gdm3, gtk v3.24.33, kernel 5.15.0-69-generic, x86_64. Open-VM-tools v 12.1.0 
[*]Screen Display: Refresh rate: 60Hz; Fractional Scaling is disabled; Resolution: 1680x1050 (16:10). 
[*]I enabled 3D Acceleration for the VM and it made no difference.  The problem persists.  When enabled Ubuntu now sees it as a SVGA gpu that supports OpenGL. 
[*]Power Mode is set to "Balanced".  In this vm it does not have an option for "Performance".  It only shows "Balanced" and "Power Saver" 
[*]I checked /var/log/syslogs and it shows no errors of any kind related to the screen blanking/locking.  From the system's pov it is all working correctly.  And it is working correctly, but the user just isnt visually seeing it. 
[/LIST]
 I have to assume some underlying Wayland libraries are broken w/this generic virtual gfx driver, or VMWare's gfx driver for 22.04 has a bug when used with Wayland.

---

### Post by MAFoElffen on 2023-04-13
From the VMware VMTN Communities Forum, VMware Workstation Pro Section, RE: [https://communities.vmware.com/t5/VMware-Workstation-Pro/Ubuntu-22-04-freezes-randomly-on-VMWare-Professional-17/td-p/2942773](https://communities.vmware.com/t5/VMware-Workstation-Pro/Ubuntu-22-04-freezes-randomly-on-VMWare-Professional-17/td-p/2942773)

Quoted from the VMware Support on this problem:
> 
Sorry for the late response.  I have checked provided link. This is a known issue with different CPU cores after some of Windows updates in VMware workstation, we hope it will be resolve in next update.

Seems to be a known problem in VMware Workstation Pro 17...

---

### Post by denismc on 2023-04-13
> **MAFoElffen said:**
> From the VMware VMTN Communities Forum, VMware Workstation Pro Section, RE: [https://communities.vmware.com/t5/VMware-Workstation-Pro/Ubuntu-22-04-freezes-randomly-on-VMWare-Professional-17/td-p/2942773](https://communities.vmware.com/t5/VMware-Workstation-Pro/Ubuntu-22-04-freezes-randomly-on-VMWare-Professional-17/td-p/2942773)

Quoted from the VMware Support on this problem:

Seems to be a known problem in VMware Workstation Pro 17...

Ahhh very much appreciated for the reply.  Was racking my brain out for weeks.   Now i can leave it be until its resolved.

---

