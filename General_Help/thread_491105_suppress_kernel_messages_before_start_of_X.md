---
title: "suppress kernel messages before start of X"
date: 2007-07-03
forum: General Help
---

### Post by ashwin_cse on 2007-07-03
Hi,

I have removed the quiet option from the menu.lst in /boot/grub/menu.lst . This enables the livecd style boot where below the progress bar it shows what happing . This was what i wanted, but the undesirable side effect was that the kernel throws lots message to the terminal screen before the graphical boot screen appears. I want the messages to appear in gui boot screen , but i dont want the messages to apear in terminal screen. I have searched the web & found that uspash is responsible for gui boot. I feel passiong arguments to uspalsh should produce the verbose gui boot & removing quiet from menu.lst is not the best method to do it. But there is **very little to no** documentation on usplash. how do i suppress verbose mode for CUI & switch on verbose for GUI boot ?

---

### Post by u-foka on 2007-08-19
Hy!

Right now i'm working on the same problem.
I changed a lot of initramfs scripts looking for quiet cmdline option, and my idea is to have a quiet and a splashquiet option separately. I replaced the check of the quiet parameter to splashquiet in:[LIST]
[*]/usr/share/initramfs-tools/init
[*]/usr/share/initramfs-tools/scripts/init-top/usplash
[*]/sbin/usplash_down
[/LIST]
but it only works while loading from initramfs, so after the "Running scripts /init-bottom" i can't get any message, and when shut down, i only see in the textbox: "System is restarting, please wait."

---

### Post by u-foka on 2007-08-19
Ok. My modifications seem to work on a fresh feisty install... I just changed quiet to splashquiet in the files in the previous post, where it's processing the kernel's command line.
Now i look at why it doesn't work on my machine... May be because of an update, or my previous modifications.

---

### Post by ashwin_cse on 2007-08-20
Hi,

This is really exciting. If you can find a solution, do post back on how to do it. One request is when you post back the solution make it as elaborate as needed b'cos not all who are looking for the solution are as knowledgeable as you are. It from my experience. I make a Google search for a solution, in the solution the author makes lots of assumption, which i am not aware of. In the end the solution which works for the author does not work for me.

regards,
ashwin_cse

---

### Post by u-foka on 2007-08-20
Hy!

Now i tested it on some different installations, and it always works except my computer :confused::D:D:D
But i find out it's some other problem with my old and upgraded install because it wont show more messages even if i remove quiet option.

So my modifications are:

In /sbin/usplash_down script:
Old part of the script at line 6:
```
for x in $(cat /proc/cmdline); do
        case $x in
        splash*)
                SPLASH=true;
                ;;
        quiet*)
		VERBOSE=false;
                ;;
        esac
done
```
Changed to:
```
for x in $(cat /proc/cmdline); do
        case $x in
	splashquiet*)
		VERBOSE=false;
                ;;
        splash*)
                SPLASH=true;
                ;;
        esac
done
```

In /usr/share/initramfs-tools/init script:
Old part of the script at line 98:
```
	quiet)
		quiet=y
		;;
```
Changed to:
```
	splashquiet)
		quiet=y
		;;
```
And in /usr/share/initramfs-tools/scripts/init-top/usplash script:
Old part of the script at line 22:
```
for x in $(cat /proc/cmdline); do
	case $x in
	splash*)
		SPLASH=true
		;;
        quiet*)
                VERBOSE=false
                ;;
	esac
done
```
Changed to:
```
for x in $(cat /proc/cmdline); do
	case $x in
        splashquiet*)
                VERBOSE=false
                ;;
	splash*)
		SPLASH=true
		;;
	esac
done
```

If that's done, you also need to run this command to regenerate initramfs:
```
update-initramfs -uk `uname -r`
```
Or if you want to regenerate initramfs for all installed kernels:
```
update-initramfs -uk all
```

So now if you boot with the default kernel command line (ro quiet splash) then the usplash screen is verbose :)
And you can control separately the kernel's and the usplash's quiet mode with quiet (kernel) and splashquiet (usplash) switches.

P.S.: The grub configuration:

In the file: /boot/grub/menu.lst you can set the default kernel options in this line:
```
# defoptions=quiet splash vga=792
```
So if you remove the quiet option the kernel is verbose too, and if you add the splashquiet option the usplash is keept quiet by default. And remember to leave it commented out, because this is not an option of the grub boot loader, but this is used by the update-grub command.
So after you save this file you need to run the
```
update-grub
```
command to apply the changes to all autmatically generated kernel line.

---

