---
title: "[SOLVED] Verbose usplash?"
date: 2008-05-08
forum: General Help
---

### Post by Zorael on 2008-05-08
Is there any way to make usplash be verbose *without* making the terminal verbose? If that makes sense.

If I modify /boot/grub/menu.lstremove the 'quiet' argument (or make it 'nonquiet') while keeping the 'splash' argument, usplash becomes verbose. However, if I at any point wish to switch to the tty terminals I'm greeted with a wall of text.

I read that with splashy it's possible to make the 'splash' argument say 'splash=verbose', but usplash doesn't seem to accept that.

edit: The man page for usplash shows this piece of information.
```
OPTIONS
       -c     Causes usplash to switch to a new console (vt8) before  display&#8208;
              ing the splash screen, rather than writing over the current one.

       -v     Put usplash into verbose mode where more messages will be shown.
              Without this flag only urgent messages will be displayed.

       -x num Set the x-axis resolution to use for the splash screen to num.

       -y num Set the y-axis resolution to use for the splash screen to num.
```
/etc/usplash.conf contains resolution definitions, so is it possible to make it also enable verbosity?


Any ideas? I could switch to splashy but there seems to be an astounding lack of themes for it.

---

### Post by hermes0710 on 2008-05-08
Install startupmanager, then run it (System>administration>startup manager) and on the first tab there is an option allowing usplash to show text (at the bottom section). Tick to have it enabled

---

### Post by Zorael on 2008-05-08
Seem to have found it; **/usr/share/initramfs-tools/scripts/init-top/usplash**.
```
	if [ "$xres" ] && [ "$xres" != 0 ] && \
	   [ "$yres" ] && [ "$yres" != 0 ]; then
		/sbin/usplash -c _**-v**_ -x "$xres" -y "$yres" $varg &
	else
		/sbin/usplash -c _**-v**_ $varg &
	fi
```
Thanks though.

---

### Post by rodendahl on 2008-09-17
Based on the above, I looked at /usr/share/initramfs-tools/scripts/init-top/usplash and I added verbose the for...case statement whic will assign VERBOSE to true. Farther down, if VERBOSE is true, then varg = -v. $varg is already in the /sbin/usplash command line farther down.

Code:
[ -f /etc/usplash.conf ] && . /etc/usplash.conf

SPLASH=false
VERBOSE=true

for x in $(cat /proc/cmdline); do
        case $x in
        splash*)
                SPLASH=true
                ;;
        quiet*)
                VERBOSE=false
                ;;
        verbose*)

                VERBOSE=true
                ;;
        esac
done

if [ $SPLASH = "true" ]; then
        mknod -m 640 /dev/mem c 1 1
        mknod -m 666 /dev/zero c 1 5
        for i in 0 1 2 3 4 5 6 7 8; do
                [ -c /dev/tty$i ] || mknod /dev/tty$i c 4 $i
        done
        modprobe -q i8042
        modprobe -q atkbd
        if [ "$VERBOSE" = true ]; then
                varg=-v
        else
                varg=
        fi
        if [ "$xres" ] && [ "$xres" != 0 ] && \
           [ "$yres" ] && [ "$yres" != 0 ]; then
                /sbin/usplash -c -x "$xres" -y "$yres" $varg &
        else
                /sbin/usplash -c $varg &
        fi

---

