---
title: "[SOLVED] want to 1.disable compiz 2. run a pgm 3.enable compiz"
date: 2008-07-02
forum: General Help
---

### Post by Pacopag on 2008-07-02
Hi.
I have a program (Mathematica 6) that is having some conflicts with compiz (I think) on startup.  I can go to System>Preferences>Appearance>Visual Effects then click "None".  Then run the program, and everything works fine.

Is there a way (maybe a script) that could disable the visual effects (is that compiz?), then run the program, then when I close the program, re-enable compiz?
I tried the following,
#
metacity --replace
mathematica
compiz --replace gconf

but this doesn't work.  It seems to execute the first line only. Any help?

Thanks.

---

### Post by rossjman1 on 2008-07-02
you can get the fusion icon from synaptic, then disable it from the system tray (notification area). Once installed you can right click on it and go to select window manager > Metacity (to disable) and Compiz (to enable).

---

### Post by Pacopag on 2008-07-02
I installed fusion icon, but I don't see it anywhere.

---

### Post by soccerboy on 2008-07-02
if you put those three commands in a .sh file and put ```
#!/bin/sh
``` as the first line, it should work.

---

### Post by rossjman1 on 2008-07-02
try logging out and back in. Or run it from the Applications > System Tools Menu

---

### Post by Pacopag on 2008-07-02
I tried putting #!/bin/sh, but it doesn't work.  Mathematica just doesn't open.

---

### Post by sisco311 on 2008-07-02
You can try something like:

#!/bin/bash
metacity --replace&
mathematica&
wait
compiz --replace gconf

---

### Post by rossjman1 on 2008-07-02
So did the Fusion-Icon work?

---

### Post by Pacopag on 2008-07-02
fusion icon is working.  So that's one way around the problem.  Thank you.  But to get the script working would be more convenient. 

The script is working better.  Mathematical starts up now, but compiz remains disabled even after I exit the program.

---

### Post by soccerboy on 2008-07-02
I believe the last command should read ```
compiz --replace
``` without the gconf.  I may be wrong though.

---

### Post by sisco311 on 2008-07-02
try:
>  #!/bin/bash
metacity --replace&
mathematica&
wait `pidof mathematica`
compiz --replace

---

### Post by Pacopag on 2008-07-02
works the same either way

---

### Post by Pacopag on 2008-07-02
still same

---

### Post by soccerboy on 2008-07-02
change the script to ```
#!/bin/bash
metacity --replace&
mathematica&
wait `pidof mathematica`
echo "Replacing with Compiz"
compiz --replace
``` and see if the terminal prints out that message before you exit mathematica.

---

### Post by Pacopag on 2008-07-02
Nope.  The echo is not getting executed.

---

### Post by soccerboy on 2008-07-02
so, does the message print out at all?  if it does, it prints out after exiting mathematica?

---

### Post by Pacopag on 2008-07-02
No.  Even after I exit mathematica it doesn't print out.  The terminal is hung up after I exit.  I have to push ctrl-c to get the command prompt back.  It's like it never finishes the script.

Right when I run the script I get the output
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x1e00006 specified for 0x1e00026 ().

then it just stays hung up here even after I exit mathematica (until I ctrl-c).

---

### Post by sisco311 on 2008-07-02
> [FONT=monospace]
[/FONT]#!/bin/bash[FONT=monospace]
[/FONT]metacity --replace&[FONT=monospace]
[/FONT]mathematica[FONT=monospace]
[/FONT]compiz --replace&???Sorry, I can't test the commands.

---

### Post by ajgreeny on 2008-07-02
You could also try using compiz-switch from [here]("http://forlong.blogage.de/article/pages/Compiz-Switch").  It is just what you are trying to produce, ie a script file to switch compiz on and off.  I know it works as I have been using it for quite a while now, and why re-invent the wheel; if there is already a script to do it why not use that instead.  Of course, you might be doing this as an exercise in scripting, for all I know.  If so, just ignore me.

Sorry, I've just re-read you original post and see what you are trying to do.  Try 
```
#!/bin/bash
metacity --replace &&
mathematica &&
compiz --replace
```as the bash script file and I'm sure the first bit will work, I'm just not sure about the final bit when you stop mathematica, which may need the **wait 'pidoff mathematica' **line.  Try versions of that and you may gat somewhere.  Your problem was only using a single & and not having a space before it I think.  Could be wrong though!

---

### Post by Pacopag on 2008-07-02
Yep sisco.  That works.  Command line is still hung up, but otherwise it works fine.  Thanks a bunch.

---

### Post by edm1 on 2008-07-02
Have a search around the forums. Somewhere there is a script exactly for this. Once installed it's just a matter of running a program using 'nocompiz mathmatica' as the command. I cant remember for the life of me what the thread is called.

---

### Post by Pacopag on 2008-07-02
ajgreeny:  thanks for the link to the compiz switch.  That's pretty handy.
I'd like to thank everyone that helped me out with this. How do I actually add "thanks" to your profiles? (I see under your handles that your were thanked x number of times...)

I appreciate all your help, and I apologize that I am so superficial.  Almost an entire afternoon was consumed because I want to see my windows zip up and down, and my desktops scoot back and forth all cool-like, when my real problem could have been solved just by disabling visual effects.  Well, I guess it's nature.  And I'm grateful to all of you.

Cheers,

---

### Post by sisco311 on 2008-07-02
[**** All about the Thanks feature ****]("http://ubuntuforums.org/showthread.php?t=702596")
[**How do I mark my thread as solved?**]("http://ubuntuforums.org/showpost.php?p=4527051&postcount=6")

EDIT: Just realised, the links are in my signature:)

---

### Post by isaacj87 on 2008-07-02
> **Pacopag said:**
> ajgreeny:  thanks for the link to the compiz switch.  That's pretty handy.
I'd like to thank everyone that helped me out with this. How do I actually add "thanks" to your profiles? (I see under your handles that your were thanked x number of times...)

I appreciate all your help, and I apologize that I am so superficial.  Almost an entire afternoon was consumed because I want to see my windows zip up and down, and my desktops scoot back and forth all cool-like, when my real problem could have been solved just by disabling visual effects.  Well, I guess it's nature.  And I'm grateful to all of you.

Cheers,

Hi,

I've actually got something working that will disable compiz and re-enable it, plus you don't have to run any commands. I found a working script and modified it a bit. I think you'll like it. But, before that, can you run these commands in terminal and tell me the results? First, I need you to replace CF with Metacity.

```
metacity --replace
```

then, re-enable CF

```
compiz --replace
```

Does that work for you with no problems? I know it sounds a bit strange, but I ask because "compiz --replace" doesn't work for me, but if it does for you, then my solution will work wonders for you.

Plus, one other question...where is the bin file for "mathematica" located? Is it in /usr/bin/ ? If you can answers these questions, I may be able to give you a solution.

---

### Post by isaacj87 on 2008-07-02
I decided to put up "my fix"

I hope that it works for you. Like I said, the command "compiz --replace" doesn't seem to work for me, so I had to change the script up a little bit for me. This "fix" apparently can be used with *any* program. So, any other programs you have that doesn't like compiz, you can try this for them as well.

1) First install this:

```
sudo apt-get install libnotify-bin
```

2) Open up terminal and type:

```
gksudo gedit /usr/local/bin/compizswitcher
```

This will open up gedit and a blank file. Copy and paste all of this (the script basically):

```
#!/bin/sh
#
# Shell script to run programs that have problems with Compiz Fusion.
# This script will temporarily disable Desktop Effects,
# and re-enable it after the program closes.
#

# Check for arguments
if [ -z $1 ]; then
echo "No command-line specified."
exit 1
fi

if [ -z $DISPLAY ]; then
echo "Display not defined."
exit 1
fi

# Disable CF
DISPLAY=$DISPLAY metacity --replace &
notify-send --expire-time=5000 --icon=gtk-info "Desktop Effects" \
"Desktop Effects has been disabled temporarily due to an incompatible \
application. This will be restored after the program is closed."

# Run the program
$@

# Re-enable CF
DISPLAY=$DISPLAY compiz --replace &
sleep 1
notify-send --expire-time=5000 --icon=gtk-info "Desktop Effects" \
"Desktop Effects have been restored."
```

Save and close. Then, run this command in terminal:

```
sudo chmod 777 /usr/local/bin/compizswitcher
```

**You only have to create the script once.**

3) Now you're going to create a wrapper application. Run these commands in terminal:

```
sudo mv /usr/bin/mathematica /usr/bin/mathematica.real
```

**Keep in mind that I'm assuming that's the location for Mathematica's bin**

Then do this:

```
sudo touch /usr/bin/mathematica
```

Now this:

```
sudo chmod 777 /usr/bin/mathematica
```

and finally this:

```
echo 'compizswitcher mathematica.real $@' > /usr/bin/mathematica
```

Done! Now, you should be able to run Mathematica and it will disable CF and notify you at the bottom that it has. After the program exits, CF will re-enable itself (and will notify you at the bottom). **Like I said, rinse and repeat for other applications if you want. You don't have to keep on creating the script. Just repeat everything past step 3, but substitute the bin name.** Hope this works for you. Here's where I found the information for this: [http://quietmint.com/blog/2008/06/make-vlc-and-ati-graphics-cards-get.php]("http://quietmint.com/blog/2008/06/make-vlc-and-ati-graphics-cards-get.php")

---

### Post by Pacopag on 2008-07-02
Thanks isaac.  That worked for me too.  And that's a sweet pic in your profile.  I like it.

Many thanks to everyone.

---

### Post by nick2588 on 2008-08-27
Please see [http://quietmint.com/blog/2008/06/make-vlc-and-ati-graphics-cards-get.php](http://quietmint.com/blog/2008/06/make-vlc-and-ati-graphics-cards-get.php) again; I've updated my blog post to have an improved script that works better when multiple wrapper applications are in use (Compiz Fusion won't be re-enabled when quitting one application if there is another wrapper application open).

The new script is also posted below:
```

#!/bin/bash -u
# quietmint.com Compiz Fusion wrapper script (8/26/08)

if [ $# -lt 1 ]; then
	echo "Usage: $0 <command>"
	exit 1
fi
ICON="/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-showdesktop.svg"
LOCKFILE="/tmp/compizswitcher.lock"

# Disable?
if [ ! -e $LOCKFILE ]; then
	echo "[compizswitcher] Disabling Compiz Fusion"
	DISPLAY=$DISPLAY metacity --replace 2>/dev/null | cat /dev/null &
	notify-send --expire-time=3500 --icon=$ICON "Application Compatibility" "Visual effects are temporarily disabled."
else
	echo "[compizswitcher] Duplicate instance, Compiz Fusion was already disabled by another process"
fi

echo "$$" >> "$LOCKFILE";
trap unlock INT TERM EXIT

# Run the original command
$@

unlock() {
	# Enable?
	OTHERS=$(grep -v "^$$$" "$LOCKFILE")
	if [ ! -z "$OTHERS" ]; then
		echo "$OTHERS" > "$LOCKFILE"
		echo "[compizswitcher] Duplicate instance, leaving Compiz Fusion disabled for other processes"
	else
		rm -f $LOCKFILE
		echo "[compizswitcher] Enabling Compiz Fusion"
		DISPLAY=$DISPLAY compiz --replace >/dev/null 2>/dev/null &
		sleep 2
		notify-send --expire-time=3500 --icon=$ICON "Application Compatibility" "Visual effects have been re-enabled."
	fi
}

```

---

