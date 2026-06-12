---
title: "[SOLVED] Fatal X Error in all OpenGL apps after latest updates"
date: 2008-01-18
forum: General Help
---

### Post by fyo on 2008-01-18
No, this is NOT the same error as everyone else is reporting (vlc, amule, azureus etc. failing with an X error).

After the latest round of updates, whenever I start an application that uses 3D acceleration, X restarts. Syslog reveals the following:

WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

The error occurs with all OpenGL apps, as far as I can tell. Google Earth and VegaStrike were where I noticed it, but since both these are 32bit bit binaries on my 64bit Gutsy system, they are *on the face of it* not perfect examples. I installed two native 64bit apps, Wings3D and SSystem Space Simulator and both cause the same fatal X error.

I've tried rolling back not only xserver-xorg-core, but also xserver-xorg-dev and libxfont1 that were updated at the same time. I even tried rolling back the 9 "avahi" packages that also received updates at the same time.

None of this helped. X still restarts on every OpenGL app.

If anyone has the slightest idea of what I could do, I would appreciate it greatly. I would rather NOT mess with the graphics driver unless ABSOLUTELY necessary (my 8500GT does not properly read (or follow) the EDID from my Samsung 225BW and getting it to work is an infuriating exercise).

SYSTEM INFO:
Athlon X2 5000+
NVIDIA 8500GT
Ubuntu 7.10 64bit
NVIDIA Linux driver

EDIT: Just to clarify: Everything worked peachy this morning (European time) before installing the latest round of updates. After installing everything worked fine. After REBOOTING the problems appeared.

---

### Post by oscarsfriend on 2008-01-18
I found I had to reinstall my nvidia drivers after the update or anything running 3d caused the x sever to restart.  See here: [http://ubuntuforums.org/showthread.php?t=671091](http://ubuntuforums.org/showthread.php?t=671091)

---

### Post by fyo on 2008-01-18
> **oscarsfriend said:**
> I found I had to reinstall my nvidia drivers after the update or anything running 3d caused the x sever to restart.  See here: [http://ubuntuforums.org/showthread.php?t=671091](http://ubuntuforums.org/showthread.php?t=671091)

I was really, really, REALLY hoping it wouldn't come to that.

I see in the thread you link that say that you want to install the drivers out of the restricted repository... well, good luck. Certainly didn't work for me.

The following is me wallowing in self-pity. Feel free to ignore.

I mentioned that my 8500GT and Samsung 225BW don't like each other. Well, reinstalling the NVIDIA drivers is "just" exiting X and running a script. Well... I DON'T GET A FREAKIN' IMAGE ON MY SCREEN WHEN NOT IN X. I get NOTHING until X starts (or Windows, if I dual boot into Windows). No BIOS, nothing. Not until the graphics driver can override whatever the hell stupid crap the graphics card is doing. There is one way to sorta circumvent the problem, which involves switching to an analogue VGA cable... but even that isn't foolproof. The 8500GT just loves sending resolutions/refresh times/timings/something that my monitor cannot handle. If it wasn't for the fact that it was the only decent graphics card with passive cooling I could get at anything even approaching a good price, I would've just sent the damned thing back at once...

Sigh...

---

### Post by oscarsfriend on 2008-01-18
> **fyo said:**
> I see in the thread you link that say that you want to install the drivers out of the restricted repository... well, good luck. Certainly didn't work for me.

Actually, [I tried it and it totally messed up my system](http://ubuntuforums.org/showthread.php?t=671160)! :shock:   After a couple of hours poking around the command line I managed to fix everything. 

Anyway, you say you can't install from the terminal outside of X.  I may have a fix for your original problem.  I went back and looked at the error message I got when reinstalling the drivers:
```

ERROR: File '/usr/lib/xorg/modules/extensions/libglx.so' is not a symbolic link.

```
Then I went and looked at the [files in the xserver-xorg-core package](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=xserver-xorg-core&version=feisty&arch=amd64), and I can see that the package installed the file listed above.  Upon reinstalling my nvidia drivers this file was removed and replaced with a symbolic link to my nvidia drivers:
```

$ ls -lh /usr/lib/xorg/modules/extensions/libglx.so
lrwxrwxrwx 1 root root 19 2008-01-18 14:11 /usr/lib/xorg/modules/extensions/libglx.so -> libglx.so.100.14.11

```

It is worth seeing if you can rename/remove this file, and set up a link like above (though you may have a different version of the drivers installed -- take a look in /usr/lib/xorg/modules/extensions/ to make sure).  Let me know if this works, and I'll add a note to my original post which may help others.

---

### Post by fyo on 2008-01-18
Thank you oscarsfriend, restoring the symbolic link was all it took to get me up and running in OpenGL again. Sure beats trying to reinstall the driver blind...

---

### Post by diskotek on 2008-01-18
i'm having a quite same error after latest updates (of xserver, xserver-core etc.)
i can not open amule anymore:
```
The program 'amule' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 389 error_code 11 request_code 147 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

i'm using feisty fawn on a machine with ati radeon x200. but yeah re-installing my video card is really sick-thing.

---

### Post by diskotek on 2008-01-19
```
$ cd /usr/lib/xorg/modules/extensions/
$ sudo ln -s libglx.so.100.14.11 libglx.so
```

thank you oscar, those lines helped me much :D

---

### Post by NilsHG on 2008-01-19
my X crashed right at login (probably when starting compiz) and send me back to the gdm loginscreen

```
$ cd /usr/lib/xorg/modules/extensions/
$ sudo cp libglx.so libglx.so.back
$ sudo rm libglx.so
$ sudo ln -s libglx.so.xxxx.xxxx libglx.so
```

replace .xxxx.xxxx.... with whatever driver version is listed in the directory. for me it is libglx.so.169.07 using the nvidia driver with my 8800gt. 
that solved the problem for me, without reinstalling drivers etc. although, i have not yet rebooted the system. lets hope for the best ;)

---

### Post by fpsmunkey on 2008-01-19
Excellent fix, I logged in this morning as a little "put out" to see the fancy desktop in gnome crashing out.  Fluxbox had no problems and nvidia-settings would crash out when glx information was clicked.  I figured its was glx related but  had to run.  Checked back and viola! you had already figured it out.  Thanks again!
Bye the Bye, I used the latest Nvidia drivers (169.07, rolled my own) and got such a hard time from the "restricted drivers manager" I just removed it.  Anyone else have problems with that?

---

### Post by the_mechanical on 2008-01-23
@diskotek and @NilsHG

Wow, you are a gift ;-)
That solved my problems. Was already searching and trying around for a while.  I had to install the nvidia driver everytime i rebootet :( to use Gnome with Compiz.

Now i can relax again.
:)

---

