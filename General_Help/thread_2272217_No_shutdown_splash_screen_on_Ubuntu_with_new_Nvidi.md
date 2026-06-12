---
title: "No shutdown splash screen on Ubuntu with new Nvidia card and D-sub monitor"
date: 2015-04-04
forum: General Help
---

### Post by guidry2 on 2015-04-04
[TABLE]
[TR]
[TD="class: votecell"]0     down vote          [favorite]("http://askubuntu.com/questions/605465/no-shutdown-splash-screen-on-ubuntu-with-new-nvidia-card-and-d-sub-monitor#")[/TD]
[TD="class: postcell"]                I use Nvidia driver 346 and  I have followed the instruction of this link [How to fix splash screen in all Ubuntu releases!]("http://askubuntu.com/questions/362722/how-to-fix-splash-screen-in-all-ubuntu-releases") Bui I've only managed to show the boot splash screen but not the shutdown's as you can see in this video. [https://www.youtube.com/embed/nD9OVbnp28g](https://www.youtube.com/embed/nD9OVbnp28g)
    
I guess it's probably due to that there is no D-sub socket on the  video card and I have to use the HDVI to D-sub adaptor which made Ubuntu  unable to detect it. Please help me with the issue. Thanks in advance. This is what I did:

  ```
sudo apt-get install v86d
sudo gedit /etc/default/grub
GRUB_GFXMODE=1024x768x32
GRUB_GFXPAYLOAD_LINUX=keep    
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
sudo update-grub2

```  **There is a boot-up splash screen, but no shut-down splash. How can I make shut-down splash work? **

  My OS Ubuntu 14.04 64 bit&#65292; Motherboard Gigabyte G1-sniper H6 CPU ntel® Core&#8482; i7-4790 CPU @ 3.60GHz × 8 &#65292; Video Card Nvidia GeForce GTX 750 Ti/PCIe/SSE2 Without D-sub &#65292; So I  use DVI to D-sub adaptor&#65292; Display LG E2242C LCD with ony D-sub socket

  ps: My  grub
  ```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
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
#Fix nvidia splash screen
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1024x768x32
GRUB_GFXPAYLOAD_LINUX=keep
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"
# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
[/TD]
[/TR]
[/TABLE]

---

