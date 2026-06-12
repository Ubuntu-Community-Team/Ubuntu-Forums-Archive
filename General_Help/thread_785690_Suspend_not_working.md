---
title: "Suspend not working"
date: 2008-05-07
forum: General Help
---

### Post by Rowie1 on 2008-05-07
Updated to Hardy from Gutsy, couldn't get suspend to work with Gutsy, but it worked with Hardy.
Installed some recent updates and suspend no longer works, I just get a black screen.

I'm sure one of the updates was for the graphics (ATi 200).

I'm using a Toshiba Satellite L30 101.

Does anybody know of a workaround.

---

### Post by astadolfo3 on 2008-05-08
Yap! same for me! Vaio VGN SZ450. suspend and hibernate worked great up to 7.04, then stopped working on 7.10 and the upgrade to 8.04 didn't solve the problem. There must be a solution since it worked great on past versions! Suspend and hibernate is vital to me to say the least.

I tried also uwsusp, but when I put the log level higher, it hangs on "suspending console(s)", then I have to do a painfiul hard powerdown.

Please help!!

---

### Post by Z47isthenew42 on 2008-05-08
I am also having Suspend Problems on my Dell Inspiron 1525 with a dual boot between Windows Vista and Ubuntu 8.04 Hardy Heron.  Sleep works fine with Vista.

---

### Post by jflaming on 2008-05-10
Same here, Inspiron 700m.

---

### Post by astadolfo3 on 2008-05-25
Hello,

I had both problems (hibernate and suspend) and I was able to fix them.

If suspend is working and hibernate is not, you can try the following:

1-make sure that you have enough swap space (at least bigger than your ram size) and that swap is turned on and available to the system.

2-in the /boot/grub/menu.lst file and on the entry of my installation
added a resume option making it look like this:
[I]
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=fe14f446-7cc3-4f6a-bcde-e4c58ebab4c1 ro quiet splash resume=UUID=0b13b111-429e-4c4a-b93c-8c0f648c6ca2[/I]

Obviously you need to put the UUID of your own swap partition. You may get it at the /etc/fstab file

**Suspend** (this could fix also hibernate)

here is what I did (I'm NOT using uswsusp, but just the standard power management delivered with Hardy):

on this file, /etc/default/acpi-support edited as su, I added the module "ptyq4" to the list of modules to be suspended in this position:
[I]
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
**MODULES="ptyq4"**[/I]

evidently the module **ptyq4** was the one that got the suspend and hibernate process stuck. You can try this first. If this does not work, the module that prevents suspend is not ptyq4 in your case. You can try to find which module must be unloaded in your machine before suspend by [following this procedure]("https://wiki.ubuntu.com/DebuggingKernelSuspend?highlight=(suspend"):

Then insert the module in the file /etc/default/acpi-support as described above

---

