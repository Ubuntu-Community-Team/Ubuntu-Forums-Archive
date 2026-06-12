---
title: "How to access GRUB or command line when booting encrypted Ubuntu"
date: 2023-03-01
forum: General Help
---

### Post by raif on 2023-03-01
I've just installed Ubuntu 22.10 using the full encryption option on a new laptop (Zenbook 13 with AMD integrated graphics), having previously used dual boot on my old laptop.

System boots and decrypts fine but then Ubuntu is freezing on the login page. So I want to be able to either access the GRUB menu or find another way to boot into the command line.

On switching on, F2 takes me to the UEFI menu, escape + shift make screen flicker then go to a boot device choice. After entering the decryption password nothing seems to have any effect and I get to the login screen. 

After the Ubuntu login screen appears, once or twice ctrl + alt + F3 worked once to get me to the command line but now it freezes first.


Guessing this is an issue with Gnome extensions - maybe need to delete them via Live USB - but in any event I still want to find out how to boot differently in case of any issues in future. 

Any help appreciated!

---

### Post by MAFoElffen on 2023-03-01
Modify the /etc/default/grub file to always show the Grub2 menu, so you can be a bit more interactive by passing boot parameters...

Do you need more detailed instructions for that?

---

### Post by raif on 2023-03-02
Many thanks for your response.

So I followed instructions here fully to mount [https://support.system76.com/articles/login-from-live-disk/](https://support.system76.com/articles/login-from-live-disk/)
Then edited /etc/default/grub and also ran apt update then upgrade and downloaded the new -35 kernel. But when trying to update grub got error message 275: cannot create /boot/grub/grub.cfg.net Directory non-existent

On booting, I could enter the encryption password, got the grub menu but then ended up in emergency mode, with ls only showing snap. System seems absolutely non-functioning now unfortunately and I'm wondering if a fresh install would be easier.

More broadly - it would surely be a good idea if there were instructions somewhere about how to resolve errors booting Ubuntu with encryption, given that it's a install option. Have looked further and still can't find anything. 
Not being able boot easily into a safe mode when problems arise does not seem a user-friendly default.

---

### Post by MAFoElffen on 2023-03-02
It might help us if your ran the boot-info script from a LiveCD or Boot Repair CD so we can see what is going on... Please post the URL of where it uploads to.

---

### Post by grahammechanical on 2023-03-02
> More broadly - it would surely be a good idea if there were instructions  somewhere about how to resolve errors booting Ubuntu with encryption,  given that it's a install option. Have looked further and still can't  find anything. Not being able boot easily into a safe mode when problems arise does not seem a user-friendly default. 				

I have never installed Ubuntu with encryption. Please keep that in mind. I ask: What is the point of encrypting or password protecting a drive if it can easily be bypassed by a few clicks of a mouse? 

I found this an interesting read. 

[https://www.linuxquestions.org/questions/linux-security-4/full-disk-encryption-useless-as-it-seems-easy-to-bypass-4175677849/](https://www.linuxquestions.org/questions/linux-security-4/full-disk-encryption-useless-as-it-seems-easy-to-bypass-4175677849/)

In my opinion making encryption user friendly would also make things more friendly for the criminal. 

Regards

---

### Post by MAFoElffen on 2023-03-02
This is how I change a /etc/default/grub file to always show (from this workstation):
```

mafoelffen@Mikes-B460M:~$ grep . /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=[COLOR=#ff0000]show[/COLOR]
GRUB_TIMEOUT=[COLOR=#ff0000]5[/COLOR]
[COLOR=#ff0000]GRUB_RECORDFAIL_TIMEOUT=5[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- splash kvm-intel.nested=1 intel_idle.max_cstate=4 video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid intel_iommu=on systemd.unified_cgroup_hierarchy=0"
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
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"
# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER=false

```
When the Grub2 menu comes up, you can then edit the boot line, starting with "linux" to try different Linux kernel boot parameter options... Note that I add "--" to the start of my 'GRUB_CMDLINE_LINUX_DEFAULT=' line content. I have found that adding this helps Grub to honor the given boot parameters. I do not know why, but it does...

Also note that by removing "quiet splash" and replacing with "3", that the system will boot the system in run level mode 3, which is multi-user text console mode. It will boot up without a graphics layer or graphics session, just like, as if, you are booting the server edition. I do this often to repair problems on a machine with a graphics problem.

---

### Post by raif on 2023-03-08
Many thanks for the further advice. Unfortunately got further errors trying to use boot-info, so cut my losses and reinstalled. Didn't take that long as had hardly set anything up. Have now updated grub as helpfully suggested.

BTW regarding encryption, despite it being somewhat off topic of this thread, anyone using their laptop for work is likely to need to follow "data protection by design and by default" principles, which include the recommendation of encryption, e.g in the UK: 
[https://ico.org.uk/for-organisations/guide-to-data-protection/guide-to-the-general-data-protection-regulation-gdpr/security/encryption/](https://ico.org.uk/for-organisations/guide-to-data-protection/guide-to-the-general-data-protection-regulation-gdpr/security/encryption/)
In any event, many consumer organisations recommend it as default for home use in case a laptop is stolen.

---

