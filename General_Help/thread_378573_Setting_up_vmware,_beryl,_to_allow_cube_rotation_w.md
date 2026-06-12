---
title: "Setting up vmware, beryl, to allow cube rotation with windows fullscreen"
date: 2007-03-07
forum: General Help
---

### Post by rjs82vette on 2007-03-07
Hi guys,

I was a hard core windows user (although I have been an Sun Solaris/Unix Administrator for years), until I saw the Ubuntu,XGL,Beryl video. So I had to install them. I have been using ubuntu for about a month now and love it.

my specs

Intel Dual Core 3.8
2 gig ram
ati x1300
sata hard drive

ubuntu 6.10 64bit
beryl
vmware workstation 5.5

That being said, I have almost everything working that I want. Ubuntu setup was easy, Beryl was easy, ATI drives PITA, VMware easy.

But now I want to have Windows XP on one side of the cube running full screen, and OSX86 on one side of the cube running full screen. I can get them fullscreen but I cannot seem to find out how to configure them to allow me to rotate the cube without exiting the fullscreen mode. I know it can be done, as I have seen the video on Youtube.com

Wondering if anyone can point me in the right direction...

(I would not use windows at all, but need it to access work stuff)

---

### Post by cortes2k on 2007-03-07
Hi.
You have to enter in full screen in vmware, if you move the mouse to the top of your screen the vmware toolbar will apear, click in the area not in the buttons press Ctrl+Alt+MouseButton1 and you can make it rotate. You can't do it clicking in the windows window because vmware believes you want to use that buttons in windows.

Enjoy

---

### Post by fjm03 on 2007-03-07
First, a disclaimer. I am new to Linux. That be said, some expanations, from a newbies' perspective, may be helpful:

When a VMware GSX Server is activated there are two monitor presentations that may be displayed. 

1) A GSX Server window, ether default or maximized. Those widows may contain server configuration menus and a virtual machine display. Generally, when powering up a virtual machine, the server window starts at default size and then automatically maximizes during the "boot" process of the virtual machine. Once the maximized server window  presents the virtual machine display, the operator may further enlarge the virtual machine presentation by selecting "full screen".

2) When a virtual machine presentation is at "full screen", any evidence of the local host or the GSX Sever disappears from the display presentation.

Understanding these differences is important because of the ownership of the GUI pointer (mouse pointer).

When the display contains a GSX Server window, the GUI pointer may be controlled by either the local host, an XGL server in the case of Beryl, the VMware server, running under XGL or the virtual machine's emulation, not running under XGL. Control depends on the location of the pointer.

In a default configuration, on a monitor presenting a maximized GSX Sever window, the mouse pointer, at the top of the display, above the GSX Server window, controls the Ubuntu task bar. That mouse pointer is shaped like a stylized arrow. 

Lower the mouse pointer into the GSX Server window and the pointer remains as a stylized arrow and now controls GSX Server functions.

Lower the pointer even further, into the virtrual machine presentation on the server window and the mouse pointer changes to a stylized, gloved hand. The gloved hand presentation indicates that the mouse pointer is still controlled by the GLX server, not the virtual machine hypervisor. Click on the #1 mouse button and the mouse pointer changes to a stylized arrow and is now in control of the virtual machine through the hypervisor layer.

When the monitor presentation of the virtual machine is at "full screen" the mouse pointer is a stylized arrow and only controls the virtual machine, not any host facilities.

A reminder that any graphic acceleration (eye candy) is control by a server on the host, not on the virtual machine. Therefore it is only possible to  manipulate accelerated graphics (rotating the cube) when a GSX server window is present. It is not possible to manipulate the accelerated graphics server when the virtual machine presentation is at "full screen", nor is it possible, even when the GSX Server window is visible, if the pointer is under control of the hypervisor (a stylized arrow pointer inside a virtual machine presentation).

If you want to rotate, you must use a gloved hand.

---

### Post by rjs82vette on 2007-03-21
Cool.... Got it. can't rotate the cube in full screen, but can rotate it in switch mode if I get the VMware menu bar and use my dirty gloved hand.

Thanks,

RJ

---

### Post by DasClown on 2007-11-03
Thanks for the post gang! I too was wondering how to rotate the cube with full screen xp.  Now I know!!

---

### Post by Tanker Bob on 2007-11-04
That's not correct. You can always release the cursor from the virtual machine by pressing Ctrl-Alt together, even in full screen. That will turn the cursor to a closed hand with a pointing finger, signifying that the host now controls the pointer. At that point, you can then rotate the cube using Ctrl-Alt-Mouse1. I do this with WinXP running full screen in VMWorkstation. Hope that helps clear the air a bit.

---

### Post by fjgaude on 2007-11-04
> **Tanker Bob said:**
> That's not correct. You can always release the cursor from the virtual machine by pressing Ctrl-Alt together, even in full screen. That will turn the cursor to a closed hand with a pointing finger, signifying that the host now controls the pointer. At that point, you can then rotate the cube using Ctrl-Alt-Mouse1. I do this with WinXP running full screen in VMWorkstation. Hope that helps clear the air a bit.

Good show! Where is all this going, say in five more years?

---

### Post by ymmot on 2007-12-06
How exactly do you set it up to do that?  Whenever I press ctrl+alt it boots me out the the vmware console?

---

