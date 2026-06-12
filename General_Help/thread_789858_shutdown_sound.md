---
title: "shutdown sound"
date: 2008-05-10
forum: General Help
---

### Post by ebe326 on 2008-05-10
I did kind of a hack workaround for the no sound on shutdown problem some people are having. I just put together some other fixes I read about and so far it seems to work. The only problem is if you want to change the sound that is played requires modifying the script. Not that big a deal I guess. Anyway, this is what I did. In a terminal type "gksudo nautilus" without the quotes. Enter password and your now in nautilus with root privilege. Navigate to the /sbin folder. From the 'File' menu select 'Create Document' > 'Empty File'. It will create a file called “new file”. Open this file and add the following: 

[I]#!/bin/sh 
#Put your custom commands after this line 

aplay /usr/share/sounds/shutdown.wav 

# The next line is the regular gnome logout command 
/sbin/shutdown -h now "Shut Down via gdm."[/I] 

Save the file and rename it “shutdown_mod”. Now make the file executable by right clicking on it then click on properties. Go to the 'Permissions' tab and check 'Allow executing file as program'. Close the properties window. Close Nautilus. Now go to the 'System' menu > 'Administration' > 'Login Window'. Click 'Edit Commands' at the bottom of the 'General' tab. Select 'Halt command' from the Command type box. Write down what you see in the Path box just in case you need to change it back. Now replace what's in the Path box with “/sbin/shutdown_mod” without the quotes. Now click 'Apply Command Changes' then close the window. Close the 'Login Window Preferences' window. 

You should also do this for the reboot command. The only difference will be to name the file “reboot_mod” and add the following lines:
[I]
#!/bin/sh
#Put your custom commands after this line

aplay /usr/share/sounds/shutdown.wav

# The next line is the regular gnome logout command
/sbin/shutdown -r now "Rebooted via gdm."[/I]

Don't forget to make this file executable also. Now modify the 'Reboot command' in the 'Login Window' the same way you did before. Type “/sbin/reboot_mod” without the quotes in the Path box.

This worked for me on a fresh 8.04 install. As I said before, I just put this together using some other info I found in different places. I'm not really that knowledgeable about Linux so do this at your own risk. If anyone with more knowledge sees a problem with this, please let me know. Good luck.

david

---

### Post by Kenneth D. Gladden on 2008-05-18
Thanks - This worked for me.

jdg

---

### Post by Yanski on 2008-06-04
Thanks for that David... it worked  \\:D/

---

### Post by exploder on 2008-06-04
ebe326, thank you! Your solution worked perfectly!

---

### Post by blackmachine on 2008-06-05
It works!! Thanx man. I've been searching this for days.
now I have my shutdown and reboot sound back. Cheers

---

### Post by lukjad on 2008-06-27
First of all, thank you. I didn't know that there *was* a shutdown sound. Now though, we need to get to the serious part. I think that your hack was very well explained through and through. There was one thing that, though it was my fault entirely, made me stumble. When you said: "Now replace what's in the Path box with “/sbin/shutdown_mod” without the quotes." I took that to mean the WHOLE line. Again, my fault but someone else could make that mistake too. When I clicked apply I was whisked away from GNOME and dropped in what looked like a terminal gone rogue. I tried to do Ctrl+Backspace but got no response. I had to think back to my Window 98 days and hit Ctrl+Alt+Del to restart. Thank you for telling us to backup the line. Whew! Anyways none of the login sounds were working so I replaced the Path ONLY. Now it works perfectly. 
Thanks again.
Luke

---

### Post by send4m3 on 2008-11-24
Hi.. I managed to do your step-by-step sound. Thanks... how to make it with logout sound ? please let me know in [email]send4m3@yahoo.com[/email]

Thank you

---

### Post by dcstar on 2009-02-10
> **send4m3 said:**
> Hi.. I managed to do your step-by-step sound. Thanks... how to make it with logout sound ? please let me know in [email]send4m3@yahoo.com[/email]

Thank you

[http://ubuntuforums.org/showthread.php?t=25857](http://ubuntuforums.org/showthread.php?t=25857)

I now have a (global) logout sound in my 8.04 system by doing the following:

[LIST=1]
[*]Installing the **bplay** package;
[*]Add the following to /etc/gdm/PostSession/Default (just before the "exit 0"):

```
bplay /pathto-wav/logout.wav
``` (or where-ever your preferred sound is)

[/LIST]
Hurrah!

---

### Post by CheeseQueen452 on 2009-03-01
I tried this & it didn't work. Btw, I'm using Linux Mint which, under the hood, is basically the same as Ubuntu, so if it works in Ubuntu it should work in Mint.... Anywho, I've had no shutdown sound like many others here, I just hear a beep instead. So I attempted this procedure unsuccessfully, & I'm wondering if I entered the wrong path? I put "bplay /username/filename.wav".... should I put "home" before the username? If anyone can help me get this issue fixed, I'd greatly appreciate it!

> **dcstar said:**
> [http://ubuntuforums.org/showthread.php?t=25857](http://ubuntuforums.org/showthread.php?t=25857)

I now have a (global) logout sound in my 8.04 system by doing the following:

[LIST=1]
[*]Installing the **bplay** package;
[*]Add the following to /etc/gdm/PostSession/Default (just before the "exit 0"):

```
bplay /pathto-wav/logout.wav
``` (or where-ever your preferred sound is)

[/LIST]
Hurrah!

---

### Post by linux_tech on 2009-03-01
works for me

---

### Post by CheeseQueen452 on 2009-03-01
Ok, I added "home" to my path, & it worked!! Thankyou dcstar!! But I still hear the system beep at the same time :-? This brings up a question, though.... Would it work if I put "aplay" instead of "bplay"?

> **CheeseQueen452 said:**
> I tried this & it didn't work. Btw, I'm using Linux Mint which, under the hood, is basically the same as Ubuntu, so if it works in Ubuntu it should work in Mint.... Anywho, I've had no shutdown sound like many others here, I just hear a beep instead. So I attempted this procedure unsuccessfully, & I'm wondering if I entered the wrong path? I put "bplay /username/filename.wav".... should I put "home" before the username? If anyone can help me get this issue fixed, I'd greatly appreciate it!

---

### Post by CheeseQueen452 on 2009-03-01
It still works! Ok, now I just have to get rid of that beep....

> **CheeseQueen452 said:**
> Would it work if I put "aplay" instead of "bplay"?

---

### Post by exploder on 2009-03-01
> 
	
Re: shutdown sound
Quote:
Originally Posted by send4m3 View Post
Hi.. I managed to do your step-by-step sound. Thanks... how to make it with logout sound ? please let me know in [email]send4m3@yahoo.com[/email]

Thank you
[http://ubuntuforums.org/showthread.php?t=25857](http://ubuntuforums.org/showthread.php?t=25857)

I now have a (global) logout sound in my 8.04 system by doing the following:

   1. Installing the bplay package;
   2. Add the following to /etc/gdm/PostSession/Default (just before the "exit 0"):

      Code:

      bplay /pathto-wav/logout.wav

      (or where-ever your preferred sound is)

Hurrah!
__________________
Regards, David.

I am interested in this fix, could someone explain where I might find the log off sound file?  Also, a step by step instruction for doing this?  I am running Mint 5 based on Hardy and now have the shutdown and restart sound thanks to the first post. Any help or details would be greatly appreciated!

---

### Post by exploder on 2009-03-01
I found the sound file, is this how PostSession sould be configured because the logout sound is not working for me?

#!/bin/sh

PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}
  bplay/usr/share/sounds/logout.wav 
exit 0

I have bplay installed, am I missing something?

---

### Post by CheeseQueen452 on 2009-03-01
> **exploder said:**
> I found the sound file, is this how PostSession sould be configured because the logout sound is not working for me?

#!/bin/sh

PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}
  bplay/usr/share/sounds/logout.wav 
exit 0

I have bplay installed, am I missing something?

Just put a space after "bplay". You can also put "aplay" instead, & it should still work.

---

### Post by exploder on 2009-03-01
That kind of worked. I have the logout sound now but when I shutdown or restart, two sounds play.

---

### Post by dcstar on 2009-03-09
> **exploder said:**
> That kind of worked. I have the logout sound now but when I shutdown or restart, two sounds play.

Then simply remove the Logout sound in your preferences.

---

### Post by BigSilly on 2009-06-27
Still no logout/shutdown sound in Jaunty. It used to work just fine in Feisty years ago, but every release since has had no logoff sound. I don't understand the problem, since it's fine in other distros, so it can't be PulseAudio. It's kinda silly, but I have to say that it's a shame it hasn't been sorted. Hack workarounds, though obviously useful and empowering for the user, are not really a great solution for what is a very simple thing.

I'm annoyed that it annoys me! :D

---

### Post by kurci2 on 2009-06-29
that solutin work only when you shutdown or restart in GDM login screen
but if i shutdown with fast-user-switch-applet that solution doesn't work.
any ideas?

---

### Post by lance bermudez on 2009-08-09
i'm running 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

and this did not work did i do something wrong or does this not work any more?

---

### Post by HasioR on 2009-09-02
Hi.
This didn't work for me :confused: I wrote all the scripts, put in the right place, check "Allow executing file as program" and nothing :(
I must  change last line on this "*/sbin/shutdown -h now"* , becouse when there was [I]"Rebooted via gdm." I can't close the system. It only logoff user and back to GDM screen.
So I don't now what I'm doing wrong, but I still doesn't have this sound :(
HELP please.
[/I]

---

### Post by SPARTAN-118 on 2009-10-03
So.... this works in Jaunty Jackalope?

And what do you mean by "global"?

Sorry, complete n00b in this respect...

EDIT: Okay tried this, still no shutdown OR reboot sounds....

I followed it by the letter; what did I do wrong?

---

### Post by lance bermudez on 2009-10-04
I followed this to the letter to and it did not work for me either.
I'm running 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

---

### Post by SPARTAN-118 on 2009-10-04
Okay, just tried that "global" logout sound, doesn't work for me.

I did a "space" after *bplay*.

I tried *aplay*.

I typed in this path to my desired logout sound: */usr/share/sounds/dream/stereo/desktop-logout-long.wav*

I'll even post the whole dang script if you'd like.
I guess it just doesn't work in Jaunty. Here's to hoping it'll work - *without* a hack required - in Karmic Koala! *drops not-so-subtle hints for Ubuntu Staff programmers*

EDIT: okay, just tried renaming the .wav file "logout.wav" still doesn't work.

Am I missing something here? I am using the User menu to go to -> Log out Matthew.... -> Log out
Do you users to whom it does work use a different, more obscure method of logging out?
...this is also how I shut down my computer and restart it...

---

### Post by SPARTAN-118 on 2009-10-04
Nevermind! I got it working by using "aplay" instead of "bplay" in the global script. When I said I tried aplay earlier, I meant using the other method.

So yeah, anybody having problems getting the logout/shutdown/restart sounds do this if you're having trouble.

Now, for some reason, XScreensaver makes Banshee close if I go full screen....

Oh well, for some reason, I found a website where this guy said his visualizations were "implemented" into the latest Banshee release. 
Have it, and don't see any here.
So it's not like I'm missing anything. ;)

---

### Post by lance bermudez on 2009-10-05
could you provide a copy of what you did. I'm having troulbe following what you are saying i would like to see what you are talking about please.

---

### Post by BigSilly on 2009-10-05
It's a pity this didn't make the 100 Paper Cuts thing, since it's been winding me up for some time and it's such a simple thing. There's a mention of the beep on shutdown there, but it's not really focused on the lack of shutdown audio.

Grrr!

---

### Post by SPARTAN-118 on 2009-10-05
Okay I will provide screenshots for each step.

---

### Post by SPARTAN-118 on 2009-10-05
Okay here's with screenies:

1. First, install bplay, as aplay (the program I used) may not work for you.

[IMG]http://i33.tinypic.com/21o80w1.png[/IMG]

2. Then open up the file containing the script for shutdown/logout/restart:

[IMG]http://i36.tinypic.com/2iqyj6b.png[/IMG]

3. Edit the line just before the "exit 0" text.

[IMG]http://i38.tinypic.com/1zp70us.jpg[/IMG]

OR

[IMG]http://i33.tinypic.com/9pur21.png[/IMG]

Note: You must replace the text I entered (before the cursor) with the path to your logout sound; it doesn't necessarily have to be in usr/share/sounds, but that's the recommended spot.

Example: /usr/share/sounds/logout.wav 
OR
/home/???/Music/Logout Sounds/logout.wav
It doesn't have to be logout.wav, as long as its a .wav file.

---

### Post by BigSilly on 2009-10-20
Those of you using the Karmic beta - is there now a shutdown sound, or is all still silent? Cheers.

---

### Post by sittingpenguin on 2009-10-26
Hi
As long as [this]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/214370") bug is not closed the logout sound is not implemented. People interested in its implementation should tick the "this bug affects me too" option in that bug, so that the developers know that this is actually something people care about.

If you want to see the attitude of some developers towards this feature check for example post #8 in [this]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/229245") bug (duplicate of the one I linked above).

---

### Post by dcstar on 2009-12-20
I have just posted a solution to the Logout Sound problem here:

[https://bugs.launchpad.net/bugs/214370](https://bugs.launchpad.net/bugs/214370)

This fixes your system as you would expect with each Ubuntu user account able to have their own particular logout sound.

Here it is anyway:

```
This works on my Ubuntu 9.04 system (tested with multiple user accounts).

Edit the following file:

/etc/gdm/PostSession/Default

And add this in before the "exit 0":

/usr/share/gnome/shutdown/libcanberra-logout-sound.sh

Now your logout of a Gnome session should play whatever logout sound you have specified (do I get a lollipop for this?).
```

---

### Post by atari130xe on 2010-01-10
> **sittingpenguin said:**
> Hi
As long as [this]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/214370") bug is not closed the logout sound is not implemented. People interested in its implementation should tick the "this bug affects me too" option in that bug, so that the developers know that this is actually something people care about.

If you want to see the attitude of some developers towards this feature check for example post #8 in [this]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/229245") bug (duplicate of the one I linked above).

Sincerely: no words... :(

---

### Post by Fenboy on 2010-02-12
Huge thanks for that.
dcstar you are a star all right.

Must admit I had n't noticed that the shutdown sound wasn't working* until I tried to make my own sound theme. Your fix works like a dream.


*Probably because I rarely turn it off.

---

### Post by BigSilly on 2010-05-01
Do we have a shutdown sound now in Lucid, or is it still silent? I haven't installed it yet as I haven't done my back ups. Let me know. :)

---

### Post by BigSilly on 2010-05-02
Installed. It appears not. :(

---

### Post by lance bermudez on 2010-05-03
I have sound working for loging out on kubuntu 10.4. I did a complete reinstall from 9.10. However i have not tired ubuntu 10.04 yet. I will probley me moveing back as dolphine will not let me use script in it like gnome's nautilus does

---

### Post by BigSilly on 2010-06-01
Kubuntu's fine. I tried that out the other day. It's regular ol' Ubuntu that's still missing the logout sound.

---

