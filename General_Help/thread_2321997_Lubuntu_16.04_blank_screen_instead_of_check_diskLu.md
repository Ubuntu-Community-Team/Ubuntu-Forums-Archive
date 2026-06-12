---
title: "Lubuntu 16.04 blank screen instead of check disk/Lubuntu boot logo"
date: 2016-04-25
forum: General Help
---

### Post by fall2 on 2016-04-25
Just updated to Lubuntu 16 from 15. When I boot up it loads a blank screen that is suppose to be the Lubuntu logo and password prompt. I noticed if I press esc, del or a F1-12 key the screen color changes from blue to black.


 I can still type in my chk-dsk password while in blank screen, press enter and it boots to my os password screen.

---

### Post by Dennis N on 2016-04-25
There is a Plymouth theme bug that your problem may be a case of:
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1370707](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1370707)
For 2016 reports - see posts #17 and after.

---

### Post by fall2 on 2016-04-25
I don't have a /lib/plymouth/themes/ubuntu-logo/ directory.
The Lubuntu logo image file I believe is suppose to be there, but there is nothing.
there is a /lib/plymouth/themes/ubuntu-text directory but its empty.

I tried another plymouth logo and text, selected them using terminal and didn't fix anything.

---

### Post by fall2 on 2016-04-25
If I use my old kernel image 4.2.0-35.40 instead of 4.4.0-21.37 the problem is gone.

---

### Post by Dennis N on 2016-04-25
I looked into the problem and found what was wrong. First, the Plymouth themes in Lubuntu 16.04 are now located in **/usr/share/plymouth/themes**. The theme in use is **lubuntu-logo**.  The reason the Plymouth splash screen shows no Lubuntu logo and dot animation is that the needed graphics images are missing in a new installation.

The solution is just to copy the missing graphics from some source into the folder **/usr/share/plymouth/themes/lubuntu-logo**.

Contents of the theme folder in Lubuntu 16.04, before fix:
```
dmn@Roxanne:/usr/share/plymouth/themes/lubuntu-logo$ ls
lubuntu-logo.plymouth  lubuntu-logo.script  

```
Files in RED were added:
```
dmn@Roxanne:/usr/share/plymouth/themes/lubuntu-logo$ ls
lubuntu-logo.plymouth  lubuntu-logo.script  [COLOR="#FF0000"]progress_dot_off.png
lubuntu_logo.png       password_field.png   progress_dot_on.png[/COLOR]

```
I took the images from a Lubuntu 14.04 install*.

I did a new install. If you upgraded in place, then I imagine the images survived from the previous 15.xx installation, and you really had a different problem. My 4.4 kernel is working fine so no need to mess with that.

* if you don't have an installation of Lubuntu to get the images from, then see post #11 for how to get them, beginning at "Then download the Trusty version of the Plymouth theme...".

---

### Post by fall2 on 2016-04-26
It looks like the update process must of removed those files, what ever reason I don't have them. It says the Lubuntu plymouth theme is installed in synaptic, guess its just missing the files like you said.
 I did download the plymouth ubuntu gnome theme but that is in the path /usr/share/plymouth/themes/ and doesn't work when I select it using
sudo update-alternatives --config default.plymouth
sudo update-alternatives --config text.plymouth

Not sure how to get the files and then move them into the correct location.

---

### Post by fall2 on 2016-04-26
Since my old kernel works, I must have the files some place, right. So, I need to find the 4.2.0-35.40 files and copy/paste them.

I copied [COLOR=#FF0000]password_field.png [/COLOR]from the ubuntu gnome folder to the lubuntu logo one, reset and it did not show up in the boot menu.

:confused:
Do I need all images for it to work?

---

### Post by Dennis N on 2016-04-26
The old location for the theme files in 14.04 was:
[FONT=Courier New]/lib/plymouth/themes/lubuntu-logo[/FONT]

In Lubuntu 15.xx they might also be there, or in the new location. I don't have these 15.xx releases any longer to check if this switch was made.

You can do a file search starting from / to find them. PCManFM has a file search.

Those graphics would be missing from the final release iso (unless they re-do the iso), so anyone using it to do a new install would not have the Lubuntu logo and progress dots on the splash screen. Both 32-bit and 64-bit, in fact. I also looked at the release notes, and no mention of the graphics being intentionally removed.

Might also be fixed by an update, of course.

---

### Post by Dennis N on 2016-04-26
Missed your last post while I was answering the previous one, so:
Yes, All 4 images are needed to get the splash screen graphics.

---

### Post by fall2 on 2016-04-27
I could not find the files. I tried to use the Ubuntu gnome files I downloaded, put them in the correct folder and changed the names so they match the correct files, didn't work.

Then I just disabled /etc/default/grub by editing the file.

before
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
after
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

then; sudo update-grub

Now it boots in text mode :neutral:. 

Bonus: I always had a problem when I attempted to shutdown using the logout program it would reboot my laptop. Now it shuts down my laptop when I click the shutdown button=d>. I undid the grub changes and confirmed that was what fixed it.

Also, I got a warning while updating grub
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
I don't know what that means, I didn't change any values or anything else in grub.

Anyway 2 problems fixed but I lost the nice looking boot screen. They should change the file name from GRUB to SCRUB.:lolflag:

---

### Post by Dennis N on 2016-04-27
> I could not find the files. I tried to use the Ubuntu gnome files I downloaded, put them in the correct folder and changed the names so they match the correct files, didn't work.

ok, here is how to get them:

First delete all the files you added yourself to the lubuntu-logo folder, but leave the two original files:  lubuntu-logo.plymouth and lubuntu-logo.script. 
Then download the Trusty version of the Plymouth theme from:

[http://packages.ubuntu.com/trusty/all/plymouth-theme-lubuntu-logo/download](http://packages.ubuntu.com/trusty/all/plymouth-theme-lubuntu-logo/download)

You get a deb file, but don't install it - all you need are the four .png images inside. So open it with archive manager, navigate in the archive to: 
/lib/plymouth/themes/lubuntu-logo, select the four image files in this folder and extract them. Then copy them to the lubuntu-logo folder in 16.04.

The splash logo and animation should now work.

---

### Post by fall2 on 2016-04-27
didn't work.

---

### Post by bill101 on 2016-04-30
I too tried this recommendation and now I do see the Lubuntu logo on shutdown, but not on startup.

Note, my GRUB includes:
GRUB_CMDLINE_LINUX_DEFAULT:&nbsp; silent splash acpi=off

---

### Post by Dennis N on 2016-04-30
> **bill101 said:**
> I too tried this recommendation and now I do see the Lubuntu logo on shutdown, but not on startup.

Note, my GRUB includes:
GRUB_CMDLINE_LINUX_DEFAULT:&nbsp; silent splash acpi=off

Since it showed on shutdown, it means the script is working and using the images you put in. 

'silent' should be 'quiet' in the command line. I tried 'silent' to see how the system reacts, and it just ignores it. All the system messages up to the splash were displayed. With 'quiet' they would not be shown. Nevertheless, it eventually showed the Lubuntu splash screen with the logo and dot animation.

My command line in /etc/default/grub:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

---

### Post by fall2 on 2016-05-07
Kernel update fixed this issue.

---

### Post by angelo16 on 2016-05-31
> **fall2 said:**
> Kernel update fixed this issue.

Sorry, as a newbie I have to ask:

How to update the kernel ?

I spent two entire days trying every change in grub cfg file  and nothing happens. I still dont have a Splash screen in my Lubuntu 16.04.

---

### Post by hartleymartin on 2016-06-16
I tried adding the image files to the directory, but I got an error message saying that I did not have permission to do so. Is there a set of commands in Terminal I can use?

---

### Post by Dennis N on 2016-06-17
> **angelo16 said:**
> Sorry, as a newbie I have to ask:

How to update the kernel ?

I spent two entire days trying every change in grub cfg file  and nothing happens. I still dont have a Splash screen in my Lubuntu 16.04.

I don't see how a kernel update would fix this. You need to add the missing graphics files as explained in post #5.

---

### Post by Dennis N on 2016-06-17
> **hartleymartin said:**
> I tried adding the image files to the directory, but I got an error message saying that I did not have permission to do so. Is there a set of commands in Terminal I can use?

You need to use sudo with the cp (copy) command.

In the terminal, change directory to where you have the the 4 image files stored and run the command:

```
sudo cp progress_dot_off.png lubuntu_logo.png password_field.png progress_dot_on.png /usr/share/plymouth/themes/lubuntu-logo
```

restart and the logo and animation should appear.

---

### Post by hartleymartin on 2016-06-17
Cheers! The files are copied. About to do a restart to see if it works. I have rather missed having the Lubuntu spash screen. It is quite a novelty at my college where everyone either uses Windows 10 or OSX.

*edit*

Just did the reboot and it worked a treat.

---

### Post by hartleymartin on 2016-06-17
Not that I want to sound picky, but is there a way to get the splash screen to display over that little message that appears before the desktop loads?

---

