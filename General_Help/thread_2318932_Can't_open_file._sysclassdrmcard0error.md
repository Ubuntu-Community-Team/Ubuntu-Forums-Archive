---
title: "Can't open file. /sys/class/drm/card0/error"
date: 2016-03-30
forum: General Help
---

### Post by fall2 on 2016-03-30
I need to open this file. How do I open it.

Failed to open file '/sys/class/drm/card0/error': open() failed: Permission denied.

---

### Post by Bashing-om on 2016-03-30
fall2; Welp.

As a thought for:
> 
Failed to open file '/sys/class/drm/card0/error': open() failed: [color=red]Permission denied[/color].

It is a system file, and the system wants that you be very sure you want to go there . As such ya got to exercise administrative authority.
What do you see:
```

ls -al /sys/class/drm/card0/error

```
comes up that 'root' owns it, huh ?
like such:
> 
-r--r--r-- 1 root root 4096 Mar 30<snip>

In that ^ arrangement, only root can only read that file. To do else you will have to have a long talk with the system and tell it that "you" want to do something else.

Opening a file manager with root privileges will allow you to 'read' the file .

[INDENT][INDENT]security, security
[INDENT][INDENT]making sure you know what you are doing
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by fall2 on 2016-03-30
-rw------- 1 root root 0 Mar 30 11:28 /sys/class/drm/card0/error

Thats what I see^.

I don't know how to root it.

---

### Post by fall2 on 2016-03-30
root ls -al /sys/class/drm/card0/error
The program 'root' is currently not installed. You can install it by typing:
sudo apt-get install root-system-bin

Should I install that to get root?

---

### Post by Bashing-om on 2016-03-30
fall2; Ok.

So 'root' can read and write ( rw) to that file.
If all you want to do is read the contents of that file then open up a file manager of your choice - dependent on your Desktop Environment -  with elevated privileges . Or directly: Say it is gedit that is installed for a text editor on your system.
You could do:
```

sudo -H gedit /sys/class/drm/card0/error

```
to open that file and read the contents.

[INDENT][INDENT]but,
[INDENT][INDENT][INDENT]there are many paths to one end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2016-03-30
> **fall2 said:**
> root ls -al /sys/class/drm/card0/error
The program 'root' is currently not installed. You can install it by typing:
sudo apt-get install root-system-bin

Should I install that to get root?
No! Don't do that.  Use ```
sudo <command> to raise your status to that of root temporarily.

```
If all you need to do is read the file open it with ```
sudo cat /sys/class/drm/card0/error
```
If you *really* need to edit it for some reason, and it would be interesting to know why, use ```
sudoedit /sys/class/drm/card0/error
``` which will open it in nano, the command line text editor.

BE VERY CAREFUL!
You can do great damage editing system files if you are not sure what you're doing or why.

EDIT:
Ninja'd by Bashing-om. Just a slightly different command used to view the file.

---

### Post by fall2 on 2016-03-30
Thank you.

It opened but the file was empty. It must erase during reboot. Its good to know and now I am ready for it the next time my computer decides to take a dump.

---

### Post by deadflowr on 2016-03-30
It's an empty file.
Why do you want to look at it anyway?

Edit: Op ninja foo

---

### Post by Bashing-om on 2016-03-30
@ AJ ; Whewwhhhh ..

Sure glad you caught that " Should I install that to get root?" as I missed the posting !

YEAH !
> 
BE VERY CAREFUL!
You can do great damage editing system files if you are not sure what you're doing or why.

+10

-----------------------
> 
It opened but the file was empty. It must erase during reboot. Its good to know and now I am ready for it the next time my computer decides to take a dump


All good now .. system is in a happy state ?

[INDENT][INDENT]going merrily on our way
[/INDENT][/INDENT]

---

### Post by fall2 on 2016-03-30
Oh hey, Thanks ajgreeny
Does the read file show up as a list in the command term cuz thats what I got.
Nah I have been getting DRM or DRI, gpu hangs and I need the dump file to report the problem.
Very helpful.

Here is a piece of my kernel log to show you whats up.

[15027.003109] [drm] GPU HANG: ecode 2:0:0x4167ffc1, in Xorg [1188], reason: Ring hung, action: reset
[15027.003116] [drm] GPU hangs can indicate a bug anywhere in the entire gfx stack, including userspace.
[15027.003121] [drm] Please file a _new_ bug report on bugs.freedesktop.org against DRI -> DRM/Intel
[15027.003125] [drm] drm/i915 developers can then reassign to the right component if it's not a kernel issue.
[15027.003129] [drm] The gpu crash dump is required to analyze gpu hangs, so please always attach it.
[15027.003134] [drm] GPU crash dump saved to /sys/class/drm/card0/error
[15027.008394] drm/i915: Resetting chip after gpu hang
[15027.008462] [drm:i915_reset [i915]] *ERROR* Failed to reset chip: -19

---

### Post by fall2 on 2016-03-30
GPU HANG: ecode 2:0:0x7e7bff03, in Xorg [1165], reason: Ring hung, action: reset
Time: 1459355293 s 501423 us
Kernel: 4.2.0-34-generic
Active process (on ring render): Xorg [1165]

---

### Post by X-RED_Tech on 2016-03-30
Now it's time to tell us what graphics card you have and what driver is being used...

---

### Post by fall2 on 2016-03-30
> **X-RED_Tech said:**
> Now it's time to tell us what graphics card you have and what driver is being used...

Oh, well ok.


2400mhz pentium 4
Intel Corporation 82852/855GM Integrated Graphics Device (rev 01) 


I have reported it to freedesktop.org yet if you want to take a swing at it, batters up. :)

---

### Post by fall2 on 2016-03-30
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
    Subsystem: Gateway, Inc. Device 0402
    Flags: bus master, fast devsel, latency 0
    Memory at <unassigned> (32-bit, prefetchable)
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
    Subsystem: Gateway, Inc. Device 0402
    Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
    Subsystem: Gateway, Inc. Device 0402
    Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01) (prog-if 00 [VGA controller])
    Subsystem: Gateway, Inc. Device 0402
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
    Subsystem: Gateway, Inc. Device 0402
    Flags: bus master, fast devsel, latency 0
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

---

### Post by X-RED_Tech on 2016-03-31
"[COLOR=#000000]Intel Corporation 82852/855GM" is very old and 'buggy'. Most likely nothing to do about it.[/COLOR]

---

### Post by fall2 on 2016-03-31
> **X-RED_Tech said:**
> "[COLOR=#000000]Intel Corporation 82852/855GM" is very old and 'buggy'. Most likely nothing to do about it.[/COLOR]



"Its very old and buggy."I know. so what?
"Most likely nothing to do about it."- translation: =; I am not going to look into it, It could be fixable.
I heard of people with this issue rolling back their kernel and fixing it.


If I install Widows xp I know there is software that can fix this bug on there, if installing xp doesn't fix the bug by its self.
The biggest problem with Linux is there is no software "like in Windows" that can find the darn software errors.

---

### Post by mörgæs on 2016-03-31
It is indeed old but I have not heard of serious bugs. 
Though, it could require UXA drivers. See the Old Hardware link in my signature for how to enable them.

---

### Post by fall2 on 2016-03-31
I just noticed I have a new display option I never had before, screen resolution 512x384?

Thats weird


Morgaes i'm not sure what i'm suppose to be looking at.

---

### Post by mörgæs on 2016-03-31
If you open the link and search on the page for UXA you will find some guidance.

---

### Post by fall2 on 2016-03-31
> **mörgæs said:**
> If you open the link and search on the page for UXA you will find some guidance.

That is not the issue I am experiencing. I tried it though, it didn't help, it might of made it worse.

---

### Post by fall2 on 2016-03-31
I made some progress.

After trying usb boots of lubuntu 14, puppy, puppy lxde, and xubuntu with no difference.
I tried ubuntu 12 off a usb. First I tried to load it 5 times off the usb and it kept stalling, so I did the scan disc which went smooth and everything checked out good. After that it then loaded ubuntu 12 off my usb. I then installed ubuntu 12. It is now running better then all the OS I listed above.

I still do get the same errors when I try to do a disc scan with a ubuntu 14 usb"before the scan starts", but i'm making progress and its running better. ;)

---

### Post by fall2 on 2016-03-31
hey guys, thanks for all the help. I got my laptop working with Ubuntu 12 as good as it was ever working with xubuntu 14 with a few tweaks.
\\:D/

I need to create that etc/x11/xorg.conf file, but what is the permission code and the text editor for Ubuntu? I tried sudo nano or sudo or nano? I can't seem to save the file.

---

### Post by mörgæs on 2016-04-01
X11 has a capital X.

---

### Post by fall2 on 2016-04-01
capitol X does not work with nano or sudo nano.
I open nano, paste the file, write is Ctrl+Alt+O, says are you sure? I hit enter. says no permissions.

---

### Post by deadflowr on 2016-04-01
```
sudo nano /etc/X11/xorg.conf
```
would open a blank page, if you did not have an existing xorg.conf file.
Which you can then fill with the appropriate entries, following the basic guidelines of xorg files.

Then press ctrl +x, which will start the save process and exit.

It'll ask if you want to save the modified buffer. You must press Y or N. 
Then it'll ask for file name. You can simply press the enter key.
It'll then exit nano and return you to the terminal prompt.

---

### Post by fall2 on 2016-04-01
"ctrl +x":rolleyes:

---

### Post by fall2 on 2016-04-01
I get this message

"""""ACPI invalid _PTC data"""""


ACPI = (*Advanced Configuration and Power Interface*) 
PTC = (*Processor Throttling Control*)

---

