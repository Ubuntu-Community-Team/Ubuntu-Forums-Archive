---
title: "Change default tty from tty7 (GUI) to tty2"
date: 2013-05-10
forum: General Help
---

### Post by terminator14 on 2013-05-10
Anyone know how to change the default tty? I've made some changes to /etc/init/tty2.conf to make tty2 run a script at boot, but the script is interactive and I need tty2 to show on boot instead of the regular tty7 (GUI).
On other distros, I was able to at least simulate this by adding "/bin/chvt 2" to rc.local, but in Ubuntu, this seems to work for a second and then immediately switches back to tty7. What controls which tty is the default one? Or is this hard coded somewhere?

---

### Post by slickymaster on 2013-05-10
As I understand it, you want to be tty2 started at boot time instead of tty7. Am I correct?

I think that's controlled by the parameter _vt.handoff_ in the **/etc/grub.d/10_linux** file, but I'm not 100% sure, so it's probably for the best that you either research on that or wait for a better answer here in the forum from someone more knowledgeable than me.

---

### Post by terminator14 on 2013-05-10
> **slickymaster said:**
> As I understand it, you want to be tty2 started at boot time instead of tty7. Am I correct?

I think that's controlled by the parameter _vt.handoff_ in the **/etc/grub.d/10_linux** file, but I'm not 100% sure, so it's probably for the best that you either research on that or wait for a better answer here in the forum from someone more knowledgeable than me.

Thanks. I'll look into that.
I've been trying to find an answer to my question through google for the past 3 days with no luck, so I thought I'd ask if anyone knew.

---

### Post by tgalati4 on 2013-05-10
It might be a permissions problem with the script that you are using:

```
cat /etc/securetty
man securetty
```

Why can't this script run after logging in?  You could put a line in .bash_login to run a terminal with your script.

Because of the handoff from root booting to user login, this might be difficult to do without breaking something.

A less elegant way of doing it is to change runlevels, start with runlevel 1, run your script and at the end of your script, change to runlevel 2.  But again, I would expect breakage.

```
man runlevel
```

tgalati4@Mint14-Extensa /etc/init.d $ apropos runlevel
runlevel (7)         - event signalling change of system runlevel
runlevel (8)         - output previous and current runlevel
startpar (8)         - start runlevel scripts in parallel
telinit (8)          - change system runlevel

Tell us what your script does, there may be a better way to perform the task than changing runlevels or running in tty2.

---

### Post by terminator14 on 2013-05-10
> **tgalati4 said:**
> It might be a permissions problem with the script that you are using:

```
cat /etc/securetty
man securetty
```

Why can't this script run after logging in?  You could put a line in .bash_login to run a terminal with your script.

Because of the handoff from root booting to user login, this might be difficult to do without breaking something.

A less elegant way of doing it is to change runlevels, start with runlevel 1, run your script and at the end of your script, change to runlevel 2.  But again, I would expect breakage.

```
man runlevel
```

tgalati4@Mint14-Extensa /etc/init.d $ apropos runlevel
runlevel (7)         - event signalling change of system runlevel
runlevel (8)         - output previous and current runlevel
startpar (8)         - start runlevel scripts in parallel
telinit (8)          - change system runlevel

Tell us what your script does, there may be a better way to perform the task than changing runlevels or running in tty2.

Getting the script to run is not a problem - it's already running at boot on tty2. I can manually switch to tty2 with Ctrl+Alt+F2 and see its progress, as well as answer its questions. The problem is switching to tty2 automatically. 

What the script does is this:

When an nvidia driver is installed manually (downloaded from the nvidia website rather than installed from the repos), a kernel update will often kill the GUI after a reboot. To fix this, a reinstallation of the nvidia driver is required. While this only takes a few minutes, I'm trying to automate the process so that every time there is a kernel update, the system automatically reinstalls the nvidia driver. The script is already successful at temporarily changing tty2 to start the installation of the nvidia driver instead of showing a login screen. All I need now is a way to automatically switch to tty2 at boot. This is easily done on Mint with the "/bin/chvt 2" line in rc.local as stated above, but does not work on Ubuntu.

---

### Post by terminator14 on 2013-05-10
> **slickymaster said:**
> I think that's controlled by the parameter _vt.handoff_ in the **/etc/grub.d/10_linux** file

Sounded promising but doesn't look like it made a difference. Any other ideas?

---

### Post by tgalati4 on 2013-05-10
What desktop environment are you running on Mint versus Ubuntu?

---

### Post by terminator14 on 2013-05-10
> **tgalati4 said:**
> What desktop environment are you running on Mint versus Ubuntu?

Mate on Mint
Unity on Ubuntu

---

### Post by slickymaster on 2013-05-10
> **terminator14 said:**
> Sounded promising but doesn't look like it made a difference. Any other ideas?

Sorry, but to be honest nothing else comes to mind.

But did you tried to change the value of **vt.handoff** in ```
/etc/grub.d/10_linux
``` from 7 to some lower number? And after it, did you updated grub and rebooted?

---

### Post by terminator14 on 2013-05-10
> **slickymaster said:**
> Sorry, but to be honest nothing else comes to mind.

But did you tried to change the value of **vt.handoff** in ```
/etc/grub.d/10_linux
``` from 7 to some lower number? And after it, did you updated grub and rebooted?

Yup - changed number from 7 to 2, ran update-grub2, and reboot. Nothin.

---

### Post by tgalati4 on 2013-05-10
So Mate (based on Gnome2) correctly interprets the *chvt* command but Unity does not.

Mint automatically tags kernel and xorg updates as 4 or 5 severity so that they don't happen automatically.  Perhaps only upgrade the kernel once a year and manually run your script in Rescue (console) mode, then reboot back into normal mode.  

The binary blob hook system used in the kernel for proprietary video drivers works, but it leaves you without a display whenever you upgrade the kernel image.  As I recall, the post-install script reverts to an open driver so that you have a fallback display.  Does that not work?  Then a pop-up notification should happen after a while that says "Hey, there is a proprietary driver available.  Would you like to install it?"

Perhaps there is a Gnome3 or Unity utility that works similarly to* chvt*.

---

### Post by terminator14 on 2013-05-10
> **tgalati4 said:**
> So Mate (based on Gnome2) correctly interprets the *chvt* command but Unity does not.

Not exactly. Both switch to tty2 if you open gnome-terminal and enter "chvt 2". Besides that, when I add "/bin/chvt 2" to rc.local on Ubuntu it does switch to tty2 at boot, but only for a second - something causes it to switch back to tty7. On Mint, this addition to rc.local switches it to tty2 but does not switch it back to tty7, which is the expected and preferred behaviour.

> **tgalati4 said:**
> Mint automatically tags kernel and xorg updates as 4 or 5 severity so that they don't happen automatically.  Perhaps only upgrade the kernel once a year and manually run your script in Rescue (console) mode, then reboot back into normal mode.

The script's purpose is to:

[LIST=1]
[*]Make the process of reinstalling an NVIDIA driver easier than the 5 minutes it takes to do it by hand
[*]Automate the launch of the nvidia driver setup at boot
[/LIST]

Updating the kernel only once a year is a terrible solution - much worse than doing it by hand and spending the 5 minutes every few weeks to do a simple NVIDIA driver reinstall.
Also, the script is useless if you're gonna do it manually, since it's entire purpose in life is to automate the process.


> **tgalati4 said:**
> The binary blob hook system used in the kernel for proprietary video drivers works, but it leaves you without a display whenever you upgrade the kernel image.  As I recall, the post-install script reverts to an open driver so that you have a fallback display.  Does that not work?

The boot process has stopped just short of loading the GUI after a kernel update multiple times on different distros over the years (when I use a driver downloaded directly from the NVIDIA website), and I don't think I've ever seen it fallback to an open driver, even though that would be the most logical thing for it to do.

> **tgalati4 said:**
> Perhaps there is a Gnome3 or Unity utility that works similarly to* chvt*.

I'll look into it, but I don't see why there would be - chvt works great. If something wasn't causing the switch back to tty7 in Ubuntu after rc.local runs, it would be a good solution.

---

### Post by terminator14 on 2013-05-10
If I don't find a cleaner solution, I'm going with:

/etc/rc.local:

```
{/bin/sleep 5; /bin/chvt 2; } &
```

Which I just came up with and tested. It seems to work great. It just waits until after whatever causes Ubuntu to switch back to tty7 runs first, and then runs chvt.

---

### Post by matt_symes on 2013-05-10
Hi

It's LightDM changing to VT7 and that runs after rc.local. That is why the sleep statement works. It forces the chvt command to run after lightdm has changed to VT7.

I set LightDM and X to run on VT8 so my logs are a bit misleading but...

```
[+0.02s] DEBUG: Plymouth is running on VT 7, but this is less than the configured minimum of 8 so not replacing it
[+0.02s] DEBUG: Using VT 8
[+0.02s] DEBUG: Activating VT 8
```

...i'm quite sure yours will say 'Activating VT 7'.

If the only reason you are switching to VT2 is so you can answer questions for the installer, i wondering if you would be able to use a heredoc to answer them and then it would be totally automated. 

You may not even need to change VT at all if it works.

Kind regards

---

### Post by terminator14 on 2013-05-11
> **matt_symes said:**
> Hi

It's LightDM changing to VT7 and that runs after rc.local. That is why the sleep statement works. It forces the chvt command to run after lightdm has changed to VT7.

I set LightDM and X to run on VT8 so my logs are a bit misleading but...

```
[+0.02s] DEBUG: Plymouth is running on VT 7, but this is less than the configured minimum of 8 so not replacing it
[+0.02s] DEBUG: Using VT 8
[+0.02s] DEBUG: Activating VT 8
```

...i'm quite sure yours will say 'Activating VT 7'.

My lightdm.log does indeed say "using VT 7" and "Activating VT 7" so LightDM seems like a good candidate to be causing this problem I'm experiencing, but so far I have not been able to track down exactly where this is happening. The 2 config files in /etc/lightdm/ are very short 3-4 lines each, and appear to have nothing relevant to tty's in them. I can't say I understand every bit of /etc/init/lightdm.conf, but it does not seem to deal with chvt or tty's either - not directly anyway (it might be referencing some files that I'm missing that deals with them I suppose).

I also did a:

```
grep -iI 'chvt\|tty' `dpkg-query -L lightdm{,-remote-session-freerdp,-remote-session-uccsconfigure} | grep -v "^$" | grep -v '\/\.'` 2>/dev/null
```

which basically took the 3 packages on my Ubuntu system that had the words "lightdm" in them, listed all the files the packages had in them, and greped every file for chvt or tty. No hits. Of course, doing a grep this way wasn't a sure thing since a) lightdm might use something other than a chvt command to switch the tty's and b) it might just do it with code in one of its binaries, which grep wouldn't find, but I figured it was worth a shot. Some googling suggests that a chvt option could be added to either the display-setup-script section of /etc/lightdm/lightdm.conf, or the actual script the section points to (I'm a bit unclear). Either way, nothing resembling that section exists in my lightdm.conf file.

Any ideas where else I can look?

> **matt_symes said:**
> If the only reason you are switching to VT2 is so you can answer questions for the installer, i wondering if you would be able to use a heredoc to answer them and then it would be totally automated. 

You may not even need to change VT at all if it works.

Automatic responses would definately be a good solution in most cases, but unfortunately, I do not know of every possible question that the nvidia driver installer may ask the user. I know every question it asks me, but it might ask someone with a differently configured system, or a different video card something else which an automated script would not pick up on. Even if I knew every question that could be asked by the driver, I would rather have people choose the options they want while installing the video driver rather than me choose for them - I can't say that I'm so experienced that I know exactly what options will work best for everyone.

The idea of automating responses like that is interesting though. By "heredoc", do you mean this:

[http://en.wikipedia.org/wiki/Here_document]("http://en.wikipedia.org/wiki/Here_document")

If you do, then I was not aware that it could be used to automate responses to scripts. Interesting...

---

### Post by matt_symes on 2013-05-11
Hi

> **terminator14 said:**
> My lightdm.log does indeed say "using VT 7" and "Activating VT 7" so LightDM seems like a good candidate to be causing this problem I'm experiencing, but so far I have not been able to track down exactly where this is happening. The 2 config files in /etc/lightdm/ are very short 3-4 lines each. and appear to have nothing relavent to tty's in them. I can't say I understand every bit of /etc/init/lightdm.conf, but it does not seem to deal with chvt or tty's either - not directly anyway (it might be referencing some files that I'm missing that deals with them I suppose).

I also did a:

"grep -iI 'chvt\|tty' `dpkg-query -L lightdm{,-remote-session-freerdp,-remote-session-uccsconfigure} | grep -v "^$" | grep -v '\/\.'` 2>/dev/null"

which basically took the 3 packages on my Ubuntu system that had the words "lightdm" in them, listed all the files the packages had in them, and greped every file for chvt or tty. No hits. Some googling suggests that a chvt option could be added to either the display-setup-script section of /etc/lightdm/lightdm.conf, or the actual script the section points to (I'm a bit unclear). Either way, nothing resembling that section exists in my lightdm.conf file.

Any ideas where else I can look?



Changing the VT is hardcoded in the lightdm binary by the looks of it, although i would have to look through the code more to see exactly what it's doing.

```
matthew-S206:/home/matthew % sed -n '/vt_set_active/,/^}/ p' /home/matthew/storage/linux_source/lightdm/lightdm-1.4.0/src/vt.c
vt_set_active (gint number)
{
#ifdef __linux__
    gint console_fd;

    g_debug ("Activating VT %d", number);

    /* Pretend always active */
    if (getuid () != 0)
        return;   

    console_fd = open_console ();
    if (console_fd >= 0)
    {
        int n = number;

        if (ioctl (console_fd, VT_ACTIVATE, n) < 0)
            g_warning ("Error using VT_ACTIVATE %d on /dev/console: %s", n, strerror (errno));

        /* Wait for the VT to become active to avoid a suspected
         * race condition somewhere between LightDM, X, ConsoleKit and the kernel.
         * See https://bugs.launchpad.net/bugs/851612 */
        if (ioctl (console_fd, VT_WAITACTIVE) < 0)
            g_warning ("Error using VT_WAITACTIVE %d on /dev/console: %s", n, strerror (errno));

        close (console_fd);
    }
#endif
}
matthew-S206:/home/matthew % 

```

> Automatic responses would definately be a good solution in most cases, but unfortunately, I do not know of every possible question that the nvidia driver installer may ask the user. I know every question it asks me, but it might ask someone with a differently configured system, or a different video card something else which an automated script would not pick up on. Even if I knew every question that could be asked by the driver, I would rather have people choose the options they want while installing the video driver rather than me choose for them - I can't say that I'm so experienced that I know exactly what options will work best for everyone.

The idea of automating responses like that is interesting though. By "heredoc", do you mean this:

[http://en.wikipedia.org/wiki/Here_document](http://en.wikipedia.org/wiki/Here_document)

If you do, then I was not aware that it could be used to automate responses to scripts. Interesting...

Yep ! That is what i mean. I'll give you a contrived example that i knocked up to show you and a real world example of how to use it.

```
matthew-S206:/home/matthew/useful_commands_dir % cat tmp
#!/bin/bash

# This line wants input
read -p "hello" read1
echo "hello 1: $read1"

# and so does this one.
read -p "hello 2" read2
echo "hello2: $read2"

matthew-S206:/home/matthew/useful_commands_dir % ./tmp << EOF
heredoc> This is line input 1
heredoc> And here is line input 2
heredoc> EOF
hello 1: This is line input 1
hello2: And here is line input 2
matthew-S206:/home/matthew/useful_commands_dir % 

```

Very contrived but you get the point. The heredoc is created at the command line but can also be created in a script.

This is a real world example from the slackware script usbimg2disk.sh.

```
  # create a FAT32 partition (type 'b')
  /sbin/fdisk $TOWIPE <<EOF
n
p
1


t
b
w
EOF
```

Kind regards

---

### Post by terminator14 on 2013-05-11
> **matt_symes said:**
> Hi



Changing the VT is hardcoded in the lightdm binary by the looks of it, although i would have to look through the code more to see exactly what it's doing.

```
matthew-S206:/home/matthew % sed -n '/vt_set_active/,/^}/ p' /home/matthew/storage/linux_source/lightdm/lightdm-1.4.0/src/vt.c
vt_set_active (gint number)
{
#ifdef __linux__
    gint console_fd;

    g_debug ("Activating VT %d", number);

    /* Pretend always active */
    if (getuid () != 0)
        return;   

    console_fd = open_console ();
    if (console_fd >= 0)
    {
        int n = number;

        if (ioctl (console_fd, VT_ACTIVATE, n) < 0)
            g_warning ("Error using VT_ACTIVATE %d on /dev/console: %s", n, strerror (errno));

        /* Wait for the VT to become active to avoid a suspected
         * race condition somewhere between LightDM, X, ConsoleKit and the kernel.
         * See https://bugs.launchpad.net/bugs/851612 */
        if (ioctl (console_fd, VT_WAITACTIVE) < 0)
            g_warning ("Error using VT_WAITACTIVE %d on /dev/console: %s", n, strerror (errno));

        close (console_fd);
    }
#endif
}
matthew-S206:/home/matthew % 

```



Wow - thanks. That is definitely useful - at least now I know why it was automatically switching to tty7, and where it is happening. The script is meant to be much simpler, and more portable (the initial intent was to have the script work on multiple distros like Ubuntu, Mint, CentOS, maybe others) than adding code to recompile lightdm would make it, so I'll see if I can use sed on the binary itself to nullify that section without killing the rest of lightdm. I've seen sed used on binaries before, though mostly on strings or filenames of libraries that sed can pick out of a binary - I don't have my hopes up for it in this case but maybe I'll get lucky. Either way, the "sleep 5" solution kind of works - worst case is I'll stick with that. My only concern with it is that on a slower system, the 5 seconds may need to be longer or they will expire before lightdm has a chance to switch the tty first, once again causing the same problem. 

> **matt_symes said:**
> Yep ! That is what i mean. I'll give you a contrived example that i knocked up to show you and a real world example of how to use it.

```
matthew-S206:/home/matthew/useful_commands_dir % cat tmp
#!/bin/bash

# This line wants input
read -p "hello" read1
echo "hello 1: $read1"

# and so does this one.
read -p "hello 2" read2
echo "hello2: $read2"

matthew-S206:/home/matthew/useful_commands_dir % ./tmp << EOF
heredoc> This is line input 1
heredoc> And here is line input 2
heredoc> EOF
hello 1: This is line input 1
hello2: And here is line input 2
matthew-S206:/home/matthew/useful_commands_dir % 

```

Very contrived but you get the point. The heredoc is created at the command line but can also be created in a script.

This is a real world example from the slackware script usbimg2disk.sh.

```
  # create a FAT32 partition (type 'b')
  /sbin/fdisk $TOWIPE <<EOF
n
p
1


t
b
w
EOF
```

Kind regards

Holy crap, that's awesome! I didn't know you could do that to fdisk, or any other program or script. It's this kind of stuff that makes linux awesome - I'm definitely adding this trick to my linux notes folder.

Thanks guys - I think I've got enough info to come up with something. I'll post a link to the script on this thread once I have it uploaded so you can see what the heck this was all about if anyone is curious.

---

### Post by matt_symes on 2013-05-11
Hi

> so I'll see if I can use sed on the binary itself to nullify that  section without killing the rest of lightdm. I've seen sed used on  binaries before, though mostly on strings or filenames of libraries that  sed can pick out of a binary

That's actually the source code and not the binary i was seding.

```
sudo apt-get source lightdm
```

Even then i would have to have a proper look through the source code to make sure it was changing vt in the compiled binary. That is what i suspect is happening though even though the bit i posted doesn't exactly show that.

It would be great to see your script when you have finished it.

Kind regards

---

### Post by terminator14 on 2013-05-11
> **matt_symes said:**
> Hi



That's actually the source code and not the binary i was seding.

```
sudo apt-get source lightdm
```

Even then i would have to have a proper look through the source code to make sure it was changing vt in the compiled binary. That is what i suspect is happening though even though the bit i posted doesn't exactly show that.

It would be great to see your script when you have finished it.

Kind regards

I'm aware that your example was the source, but unless my script intends to recompile the binary from source, there's really no point in it changing lightdm's source code. I was talking about editing the binary directly with sed, but as I suspected, it appears to be of limited use unless it's done to a string. Ex. I can use:

```
sed -i.bak 's/Using VT/Using RS/g' /sbin/lightdm
```

to change the binary directly, and the log file at next reboot will actually say "Using RS" instead of VT, but that appears to only work because "Using VT" is a string that's easy for sed to find in the lightdm binary. It's difficult, if not impossible to change actual code with that method.

I'm no C programmer, but it appears from the source code you've posted that this is the line that does the switching:

```
if (ioctl (console_fd, VT_ACTIVATE, n) < 0)
```

Where the if statement just checks its error code. My best guess for a fix if I was to edit the source code would be either to replace the content of vt_set_active with a single return line:

```
vt_set_active (gint number)
{
return;
}
```

or to change the line:

```
if (ioctl (console_fd, VT_ACTIVATE, n) < 0)
```

to read

```
if (0 < 0)
```

but I don't see a way to do it with sed on the binary, so that idea is out. 

The next idea I had, which I think may actually work would be to tell rc.local to wait for the log line that comes after:

```
if (ioctl (console_fd, VT_ACTIVATE, n) < 0)
```

before executing chvt. I don't have the lightdb.log in front of me, but I think the next log line was "Using VT" (I'll check later) so something like:

/etc/rc.local:

```
{ until grep -q "Using VT" /var/log/lightdm/lightdb.log; do sleep 1; done; /bin/chvt 2; } &
```

might do the trick.

---

### Post by matt_symes on 2013-05-11
Hi

> **terminator14 said:**
> I'm aware that your example was the source, but unless my script intends to recompile the binary from source, there's really no point in it changing lightdm's source code. I was talking about editing the binary directly with sed, but as I suspected, it appears to be of limited use unless it's done to a string. Ex. I can use:

```
sed -i.bak 's/Using VT/Using RS/g' /sbin/lightdm
```

to change the binary directly, and the log file at next reboot will actually say "Using RS" instead of VT, but that appears to only work because "Using VT" is a string that's easy for sed to find in the lightdm binary. It's difficult, if not impossible to change actual code with that method.

I'm no C programmer, but it appears from the source code you've posted that this is the line that does the switching:

```
if (ioctl (console_fd, VT_ACTIVATE, n) < 0)
```

Where the if statement just checks its error code. My best guess for a fix if I was to edit the source code would be either to replace the content of vt_set_active with a single return line:

```
vt_set_active (gint number)
{
return;
}
```

or to change the line:

```
if (ioctl (console_fd, VT_ACTIVATE, n) < 0)
```

to read

```
if (0 < 0)
```

but I don't see a way to do it with sed on the binary, so that idea is out. 

The next idea I had, which I think may actually work would be to tell rc.local to wait for the log line that comes after:

```
if (ioctl (console_fd, VT_ACTIVATE, n) < 0)
```

before executing chvt. I don't have the lightdb.log in front of me, but I think the next log line was "Using VT" (I'll check later) so something like:

/etc/rc.local:

```
{ until grep -q "Using VT" /var/log/lightdm/lightdb.log; do sleep 1; done; /bin/chvt 2; } &
```

might do the trick.

Excellent. I glad you can read the function i posted. I'm glad you understood the ioctl command as well.

When i posted my last post, i did not mean to sound patronising. I think i may have come across that way.

We get many different users with many different technical abilities on these forums and it's difficult to gauge a persons technical skill after only a couple of posts.

I would not bother changing the binary for the reasons you have stated, so leave the code alone.

The simplest method may be the last one you suggested or a variation of it....

> 
[+0.02s] DEBUG: Plymouth is running on VT 7, but this is less than the configured minimum of 8 so not replacing it
[+0.02s] DEBUG: Using VT 8
[+0.02s] DEBUG: Activating VT 8
[+0.03s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.03s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.03s] DEBUG: Launching X Server

You could grep the log, wait for the file /var/log/lightdm/x-0.log to be create, (Launching X Server) assuming this is actually starting the X server then you could wait for the X server pid....

Kind regards

---

### Post by terminator14 on 2013-05-11
> **matt_symes said:**
> Hi



Excellent. I glad you can read the function i posted. I'm glad you understood the ioctl command as well.

When i posted my last post, i did not mean to sound patronising. I think i may have come across that way.

We get many different users with many different technical abilities on these forums and it's difficult to gauge a persons technical skill after only a couple of posts.

I would not bother changing the binary for the reasons you have stated, so leave the code alone.

The simplest method may be the last one you suggested or a variation of it....



You could grep the log, wait for the file /var/log/lightdm/x-0.log to be create, (Launching X Server) assuming this is actually starting the X server then you could wait for the X server pid....

Kind regards

I've done some testing and this is what I've found:

We know that according to the source code, lightdm's call to request a change in tty occurs between the debug line:

DEBUG: Activating VT 8
and
DEBUG: Logging to /var/log/lightdm/x-0.log

We also know that if rc.local has a single line of "/bin/chvt 2" in it, it tries to execute the command sometime before lightdm's call to change the tty.

However, if I change /etc/rc.local to read:

```
cp /var/log/lightdm/lightdm.log /home/test/temp/
```

just to see exactly how far lightdm gets in executing its code when rc.local starts to run, we get this:

> [+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.4.0, UID=0 PID=967
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.10s] DEBUG: Registered seat module xlocal
[+0.10s] DEBUG: Registered seat module xremote
[+0.10s] DEBUG: Adding default seat
[+0.10s] DEBUG: Starting seat
[+0.10s] DEBUG: Starting new display for greeter
[+0.10s] DEBUG: Starting local X display
[+0.13s] DEBUG: X server :0 will replace Plymouth
[+0.17s] DEBUG: Using VT 7
[B][+0.17s] DEBUG: Activating VT 7
[+0.17s] DEBUG: Logging to /var/log/lightdm/x-0.log
[/B][+0.19s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.19s] DEBUG: Launching X Server
[+0.21s] DEBUG: Launching process 1065: /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.23s] DEBUG: Waiting for ready signal from X server :0
[+0.23s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.23s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.52s] DEBUG: Got signal 10 from process 1065
[+0.52s] DEBUG: Got signal from X server :0
[+0.52s] DEBUG: Stopping Plymouth, X server is ready
[+0.58s] DEBUG: Connecting to XServer :0
[+0.60s] DEBUG: Starting greeter
[+0.60s] DEBUG: Started session 1206 with service 'lightdm-greeter', username 'lightdm'
[+0.74s] DEBUG: Session 1206 authentication complete with return value 0: Success
[+0.74s] DEBUG: Greeter authorized
[+0.74s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+0.75s] DEBUG: Session 1206 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter


Which means that the simple act of copying the 1.7k log file to a temp file takes long enough for lightdm to call tty7 and keep running. A quick test of the time it takes to copy a 1.7k log file (time cp lightdm.log testfile) reveals that it takes exactly 0.01 seconds. That means that the time scale we are dealing with is so small that any tests that can be performed to check if lightdm.log says tty7 has already been called are pretty much useless, since the time it takes to perform the tests themselves will give lightdm enough time to complete the call to tty7. At this point, I'm thinking that even the slowest systems should have no problems with the original solution of

```
{/bin/sleep 5; /bin/chvt 2; } &
```

I think that's what I'll go with, and see if people leave comments about problems with it. If they do, I'll do an actual test to see if lightdm has run tty7 yet.

Thanks again matt_symes.

---

### Post by terminator14 on 2013-05-11
Posted. See the script here: [http://ubuntuforums.org/showthread.php?t=2144333&p=12644025](http://ubuntuforums.org/showthread.php?t=2144333&p=12644025)

---

