---
title: "Boot - xserver big problem"
date: 2008-03-02
forum: General Help
---

### Post by Kalidor on 2008-03-02
Hi everybody. Just installed Kubuntu 7.10 64-bit on a system with 4gb ram and a geforce 8800gt. Unfortunately, after the kernel loads my lcd monitor just goes completely blank and the led flashes as if the computer was off and the monitor on. What is it? xserver problem? How do i solve it? Recovery mode?

Thanks everybody.

---

### Post by Nzer24 on 2008-03-02
Sounds like Ubuntu is having a tough time with your graphics card. The 8800 series currently has no open source drivers, but you can enable the proprietary ones. 

First you need basic graphics. Boot up your computer in single-user/recovery mode (choose it from the bootloader menu). This should bring you to a shell where you have root access.

Type in this:

nano /etc/X11/xorg.conf

This will pop up a text editor in your window. Scroll down with the arrow keys until you find the section labeled "Device" with the name of your video card. Now replace the part that says:

driver "nv" or driver "nvidia"

with 

driver "vesa"

This will enable non-accelerated framebuffer support.

Now restart your computer. The login window should appear. Go to the restricted drivers manager and check the checkbox for your video card. Now restart again. You should have full accelerated graphics now.

That's how I got it to work on my 8800GTS, but that's on a 32-bit system. If the last step makes the problem reappear, you will have to use the vesa driver again. You won't get accelerated graphics, but at least your computer will work.

---

### Post by Kalidor on 2008-03-02
Ok I tried and it does get farther. It tries to start kdm i guess, but immediately after i get the message from my monitor "Not Optimum mode: recommended mode 1280x1024 60 hz". Then i get bounced back to that shell where i see some writings:

Starting k display manager: kdm
                                                                                                                                                                     [ OK]
...
...
..
.
Checking Battery state

Running local boot scripts (/etc/rc.local)

at that point i can get to another shell login with ctrl-alt-F2.

What can i do?

---

### Post by Kalidor on 2008-03-02
Up

---

### Post by JKyleOKC on 2008-03-04
I've been trying to customize my login sequences and encountered a somewhat similar apparent freeze after the "Loading scripts" message. By accident, I found that simply hitting Enter at that point would give me a command-line login prompt, allowing me to get into the system.

I then removed the "quiet" and "splash" parameters from grub's menu.lst file, giving me a full *nix-style log of what was happening -- and found that after the first message about loading rc.local scripts, I was getting a "Login:" prompt but the boot process was continuing as if it were looping back to an earlier stage. The apparent freeze was simply that first login prompt waiting for me to respond!

I don't know if this is what you're experiencing but it's worth looking into. I'm still trying to determine what I messed up to cause that looping action during the boot sequence (I disabled the graphical login package, and also disabled a number of services I don't use; probably one of those was required for something that's still there).

---

