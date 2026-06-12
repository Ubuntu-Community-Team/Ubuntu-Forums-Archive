---
title: "How Do You Set Wallpaper &amp; Dasktop Launcher Icons For Guest?"
date: 2015-07-22
forum: General Help
---

### Post by oldefoxx on 2015-07-22
I have family visiting this week, and want them to feel free to use my spare laptops.  I also want them to see and understand how great Ubuntu really is, especially against Windows 8.  (I hear that Windows 10 has its drawbacks too).

But in trying to set wallpaper and desktop shortcuts (I'm using Classical Gnome, not that tall, rowdy totem pole that Dash gives you) because just a plain purple screen looks so unappealing.  But you can't do it as Guest, because nothing lasts.

Now I can add a Friend account and do pretty much what I want, and of course their files and additions would last as well, but I was just wondering if a wallpaper and some desktop links could be added to brighten up the Guest view of Ubuntu?

---

### Post by oldefoxx on 2015-07-29
I have a friend & family account added now, but would still like to have a wallpaper setting for the guest.  I noted that there are instructions available ro disable the guest account, whuch could be an alternative I auppose.  Let's let this ride for a bit to see if any abswers are forthcoming.

When I created the friend account, I did not add it to the short list of super users.  So it is a limited account, but changes made carry forward in that it can add files.  Not new software though, as for that you have to be root or a super user.

I decided to look into the matter myself a bit more.  Using a terminal, I used "find / -name guest* | more", and got a list of results, but this is the most interesting:
 /usr/lib/lightdm/guest-session-auto.sh

The .sh at the end marks this as a script file, meaning a bash executable.  So I did a "cat  /usr/lib/lightdm/guest-session-auto.sh | more" to look at it one screen at a time,   That gave me a view of it, but to share with others, I dropped the "| more" and added "> /home/[userid]/Desktop/guest.sh" and hit the Enter key.  Instead of "[userid]", I used my own user name.  Now I am going to put the contents of guest.sh here:```
#!/bin/sh
#
# Copyright (C) 2013 Canonical Ltd
# Author: Gunnar Hjalmarsson <gunnarhj@ubuntu.com>
#
# This program is free software: you can redistribute it and/or modify it under
# the terms of the GNU General Public License as published by the Free Software
# Foundation, version 3 of the License.
#
# See http://www.gnu.org/copyleft/gpl.html the full text of the license.

# This script is run via autostart at the launch of a guest session.

export TEXTDOMAINDIR=/usr/share/locale-langpack
export TEXTDOMAIN=lightdm

# disable screen locking
gsettings set org.gnome.desktop.lockdown disable-lock-screen true

# info dialog about the temporary nature of a guest session
dialog_content () {
	TITLE=$(gettext 'Temporary Guest Session')
	TEXT=$(gettext 'All data created during this guest session will be deleted
when you log out, and settings will be reset to defaults.
Please save files on some external device, for instance a
USB stick, if you would like to access them again later.')
	para2=$(gettext 'Another alternative is to save files in the
/var/guest-data folder.')
	test -w /var/guest-data && TEXT="$TEXT\n\n$para2"
}
test -f "$HOME"/.skip-guest-warning-dialog || {
	if [ "$KDE_FULL_SESSION" = true ] && [ -x /usr/bin/kdialog ]; then
		dialog_content
		TEXT_FILE="$HOME"/.guest-session-kdialog
		echo -n "$TEXT" > $TEXT_FILE
		{
			# Sleep to wait for the the info dialog to start.
			# This way the window will likely become focused.
			sleep $DIALOG_SLEEP
			kdialog --title "$TITLE" --textbox $TEXT_FILE 450 250
			rm -f $TEXT_FILE
		} &
	elif [ -x /usr/bin/zenity ]; then
		dialog_content
		{
			# Sleep to wait for the the info dialog to start.
			# This way the window will likely become focused.
			sleep $DIALOG_SLEEP
			zenity --warning --no-wrap --title="$TITLE" --text="$TEXT"
		} &
	fi
}

# run possible local startup commands
test -f /etc/guest-session/auto.sh && . /etc/guest-session/auto.sh
```
The several "test" commands are important.  The first isto see if a folder exists and is writable or not:
> test -w /var/guest-data && TEXT="$TEXT\n\n$para2"

The 2nd test is bit more complex, in that it allows for a hidden file in "/home" to influence what happens next.  Or for a KDE alternative environment and an executable file to both exist:
> test -f "$HOME"/.skip-guest-warning-dialog || {
	if [ "$KDE_FULL_SESSION" = true ] && [ -x /usr/bin/kdialog ]
What is really being decided is whether to use kdialog or zenity scripts and scripting appropriately engines going forward at this point.

The final "test -f" command isn't very clear to me.  It checks to see if "/etc/guest-session/auto/sh file exists, but the " && . " throws me.  The && means a logical "AND", and the " . " normally means a reference to the "current directory", in which case you do whatever is in /etc/bin/auto.sh.

This appears to make sense on the leading edge, but what is the significance of the current directory in this statement?

On my install, there is no /etc/bin folder, amd no auto.sh file found anywhere.  You might almost argue that this is not the right point to be at in finding the guest environment, but the $TEXT= statement proves otherwise, because that is what appears on the Guest screen when you log in.  So I am still at a loss of what is actually taking place here.  Oh, here is a link that discusses some of the differences between zenity and kdialog.  [http://www.linux.org/threads/kdialog-kde-gui-for-scripts.5815/](http://www.linux.org/threads/kdialog-kde-gui-for-scripts.5815/)

---

### Post by oldefoxx on 2015-08-02
I haven't figured this out.    In fact, having tried to understand the guest-session.sh scriot file, I have more questions than answers.  And nobody has deemed to give me an answer either.

But I did make progress of sorts, and I want to share that with you,  I was able to change the background for the login screen, using a process given here:  [http://ubuntuhandbook.org/index.php/2014/04/ubuntu-14-04-change-login-screen-background-remove-the-white-dots/](http://ubuntuhandbook.org/index.php/2014/04/ubuntu-14-04-change-login-screen-background-remove-the-white-dots/)

It's simple enough to do, but my laptop is hyper-sensitive to hand movements near the touchpad, and this caused a real problem.  The other problem was that the handbook link does not tell you enough, and I am here to correct for that,  And of couse it does nothing to solve the riddle of changing the guest background, but who knows?  Another poke a the woodpile might get me a rattle or two,

Okay.  Here is what the above link's process boils down to.  A few easy terminal steps.  But before we get that far, you need an image to use as your new wallpaper.  Some use personal photographs.  Others use views of nature,  And some prefer artwork or some form of illusion.  A good hunting place is the internet.

Now the most critical thing about whatever you use is how well it scales to the size of your whole screen.  Start with something yoo small, it will scale badly and give you blury edges that look fuzzy.  Go for a size at least a big as the actual pixel resolution of your screen.  A modern laptop screen might be 1600x900 in width-by-height, or even 1920x1080.  My older laptop is 1440x900.  Separate monitors can go to higher resolutions,  You can use one or more of these in your search, or you could just specify HR or hi res, which is shorthand for high resolution.  

You can add additional terms that narrow your search down a bit, like color, if you want it dark, a woods or forest scene, the sea, or a sunset.  You will find thousands of pictures online to go through, and you decide.  But here is the thing:  What you are shown is a thumbnail view of the actual umage, and more often then not, what you save to your PC is that thumbnail, not the image tied to it.  You need to click on the thumbnail to get to the link it is tied to, where you should find a bigger view of the image.

But even this may not be the full size image.  You may have options here about seeing the full image, or going to a page where you can get the full image.  And you may even have choice as to what pixel size to download.  It all depends upon the supplier. 

Now some images appear over and over, while others may only be in this one place.  Big criteria for me is to get several, in case I change my mind later,  You may also have an issue with how well desktop icons and white letters stand out against the backgtround,  I do, so I go for dark colors mostly, and I have some neat dark blue ones to use, even an underwater scene of a school of fish that does very well.  But you can always come back later if you want more choices/

A good test of whether you want the picture as your wallpaper is go ahead, get it, then find it in your Downloads and right-click on it and set it as your Desktop wallpaper.  If it works for you there, it should do fine for your login screen instead, or as well (have it both ways if you want).

Now you have settled on an image.  But wait:  There is a ptonlrm here.  Your image is likely a jpeg file, which is fine for your Desktop.  It displays properly.  But the login screen is more limited.  I don't know all that it does support, but it can't handle a jpeg image.  You try to use one, it puts up a lattice of dark bars near the top of your screen.  No, for the login screen, you need a png image file.

Can't use the jpeg file?  No problem.  You just need to use an image converter program and make its contents over into a png format.  And you don't even have to search for a program to do it for you, because there is a web site that will do it on the spot, and at no charge.  [http://www.wallconvert.com/fileconvert/](http://www.wallconvert.com/fileconvert/)

Under Pictures, I have a subfolder named Wallpapers.  Did I add that way back when, or was that original?  No matter.  You can either use that, or pick another spot in your file system that will serve as well.  The real trick is, to make sure you get the path and file name down exactly,  Now some file names are very long, and I rename them first to something shorter.  That reduces the chances of later typos as I try to enter this into the settings.  My present image is simply autumn.png.

We are finally ready.  So following the guidelines in the Handbook link, I do the following:
```

cd $HOME/Pictures/Wallpapers/; dir *.png
autumn.png
cp -f autumn.png backscrn.png
sudo -i
[sudo] password for [userid]:
locate backscrn.png
# You get the complete path displayed, which makes easy copy-and-paste a bit further on
xhost +SI:localuser:lightdm
localuser:lightdm being added to access control list
# user lightdm has been added, so now switch to being that user
su lightdm -s /bin/bash
gsettings set com.canonical.unity-greeter draw-user-backgrounds 'false'
gsettings set com.canonical.unity-greeter background '[the-copy-and-paste goes here]'
# or instead, go back to default with: gsettings reset com.canonical.unity-greeter draw-user-backgrounds
dconf-editor

```
dconf-editor lists a few items in the left pane,  /the right pane is empty.  The handbook link tells you to &#8220;navigate to com &#8211;> canonical &#8211;> unity-greeter. Then change the background value to your custom image and disable both draw-grid and draw-user-backgrounds&#8221;.
What the handbook doesn't tell you is that where you see an arrow in front of a term in the left pane, you must click on the arrow, not the name itself.  Then it all works as described.

But, because my laptop is so sensitive to hand movement, I somehow lost it while in dconf-editor, and when I got back into it, unity-greeter was completely gone.  I was at a loss, but decided to use sudo apt-get purge dconf-tools, followed by a sudo apt-get install dconf-tools, and I got it back.

The other thing to note is that after I did the necessary copy-and-paste of commands from the handbook to the terminal screen (copy is highlight the line and use Ctrl+C to get it to the clipboard, paste is go to the terminal command line and use Ctrl+Shft+V to put it there).  I even did a copy-and-paste of &#8220;dconf-editor&#8221;, but BEFORE I hit Enter. 

I then went up the terminal screen with the mouse and highlighted the line where you presently see &#8220;/home/[userid]/Pictures/Wallpapers/autumn.png&#8221;/  You highlight that using just the mouse, and then use Ctel+Shft+C to copy the path/filename to the clipboard.  Then I pressed Enter to start dconf-editor.  Now I can highlight the link name after &#8220;background&#8221; and replace it by using Ctrl+V.  Close dconf-editor, then close the terminal window, and you are ready to give it a try by logging out and logging in again.

A final note is that where I have used [userid], you would use the userid that you are logged in under.

An advantage here is that any .png dile you copy to $HOME/Pictures/Wallpapers/backscrn.png becomes instantly your new wallpaper for your login and your account background.  What has not been spelled out elsewhere is that while the user account can support a number of image types, the login screen supports only .png.  Most online images are in the ,jpg or ,jpeg format, but there are four to five free online services that will convert image files of almost any type to jpeg or png in a matter of seconds.  You can even control the size of the produced image, whether it is colored or not, and how sharp you want the results to be.

But keep this in mind:  Blowing up a small image means no sharp outlines, while  shrinking down a large one gives great results.  And though you may find images with searches like dark blue 1680x900 1920x1080, you might do better with dark 1440 1680 1920 2000 2560 2880 3840.  I used "dark" so that my desktop icons stand out, but you could use other terms like autumn. water, blue, red, scuba, fish, surf, sky, plane, space, cat, dog, horse, hills, mountain, scene, sunset, or whatever suits your interest.

Another point of interest:  Most sites present you with an album view of images, and these are all minitures of the real images behind them.  You either have to click on that image to get to the real one, or click on a link label nearby.  For instance, if the image is already resized for you, the size(s) may be shown and you may have to click on the one you want.  Then when you think you have the right one, press the right mouse button as choose Save as...  Save as ... lets you decide where to save it (like in Pictures) and gives you a chance to pick a short name for it that could help you later.  As soon as it is saved, you can click on the new image and see if it is big enough to serve as your new wallpaper.  <it won't be shown full size perhaps, vut it should be large enough to give you a good idea. 
,

---

