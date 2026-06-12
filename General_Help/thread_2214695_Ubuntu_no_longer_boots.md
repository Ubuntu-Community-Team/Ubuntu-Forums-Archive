---
title: "Ubuntu no longer boots"
date: 2014-04-02
forum: General Help
---

### Post by nessy777 on 2014-04-02
I've been using Ubuntu for about 18 months without any issues. I installed it on an old IBM Thinkpad T60.
I turned the laptop on today to be greated with a screen I haven't seen before. It's headed with - gnu grub version..... And it gives me five options;
Ubuntu, with Linux
Ubuntu, with Linux (recovery mode)
Previous Linux versions
Memory test
Memory test (serial console 115200)

As I've never had to play about with Ubuntu before (it's always worked) I have absolutely no idea what to do. I've clicked enter on the options above and nothing happens.
As above I really don't know where to start, can anyone help?
Thanks

---

### Post by oldfred on 2014-04-02
That is the normal grub menu.

If you only have one install, it normally skips menu and just automatically boots first entry. To see menu then you have to hold shift key from BIOS until menu appears.

But menu will appear if previous boot did not work or you had an abnormal shutdown or possibly other errors.
If not real issues you should be able to boot first entry. If some issue you may be able to boot second or recovery mode to get to recovery options and maybe command line to make repairs.

If you try second entry to you get any errors? It may take longer if it is trying to do something in background.

If an abnormal shutdown, you may need to run chkdsk from your live installer.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by nessy777 on 2014-04-02
Thanks for the response but I genuinely have no idea what any of that means! Lol
Only answer I can give is when I choose the 2nd option (recovery mode) I get a a lot of scrolling writing that stops after a few seconds and that's it, no error messages though.

---

### Post by QIII on 2014-04-02
Hello!

Can you possibly use your cell phone to snap a picture of the screen when the text stops and post that back here?

---

### Post by nessy777 on 2014-04-02
Here you go

---

### Post by oldfred on 2014-04-02
It looks like it is running all sorts of fixes for ACPI limitations on your computer. Not related to boot issue, but is BIOS updated to newest version? Very old computers may not have any recent fixes and Linux has to create work arounds as shown.

Sometimes error is before last entries posted. It may be doing some things in parallel. Any warnings, errors in previous screen? It may go by pretty quick. 

From a live installer you can mount install and see the entire log of the boot in /var/log/dmesg.

 Change example sda6 to your Ubuntu partition
sudo mount /dev/sda6 /mnt
gksudo gedit /mnt/var/log/dmesg
or if you can boot to a terminal.
sudo nano /var/log/dmesg

---

### Post by nessy777 on 2014-04-02
I couldn't see any error messages, again after that you have lost me completely.

---

### Post by oldfred on 2014-04-02
You may need to look at dmesg as that is a copy of everything you see scroll by.

From live installer DVD or flash drive.
If you do not know which partition run this:
sudo parted -l

And then change sda6 in previous post to correct partition for your install. 
Mount and view dmseg log file.

---

### Post by Ace..... on 2014-04-02
From your earlier remarks re: not understanding....

Most of the help you will get here, relates to commands written in in non-graphical mode.

In effect... all the icons and links that you click (while doing your normal computing) relate to basic commands that are normally hidden.
You know a picture for google chrome - this is easier to click than writing 'google-chrome'.

Lots of ubuntu users still use these fundamental commands, because it cuts out any problems that might be occurring with the graphics.

But also..... there are many deeper commands that only exist in this 'typed' format.

These are the commands you will need to type, or copy and paste.

To do this, you must press ctrl + Alt + T 

Hold these 3 keys down together, and you'll gain entry to these fundamental commands.

Paste the commands at the point of the flashing cursor after $.

If your password is required, then type it in.
You will see nothing.
If you typed it correctly, the result of your command will be listed in the box.

Usually, you need simply copy the result to this forum.
Sometimes, there may be a special site where you should post your results (you'll be told).

Note: if you did not set up ubuntu with a password...... this can cause problems.
Remember to always setup a password when installing ubuntu. ;)

Step by step, you WILL get the hang of it, even if, for the first period you are simply copying and pasting :)

---

### Post by nessy777 on 2014-04-03
Thanks for the help, I tried to boot it from a USB stick but it just stuck on the Ubuntu loading screen?

---

### Post by oldfred on 2014-04-03
Even older systems may have video issues. Did you have to add a boot parameter before?
But sometimes the updates to Ubuntu have changed it to now need those parameters.

If nVidia or AMD, nomodeset usually works, but if Intel it often is other parameters.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Instead of nomodeset:

 Older Intel video card: 
i915.modeset=1 or i915.modeset=0 
newer:
  i915.i915_enable_rc6=1


  Generic: 
xforcevesa
 or
 nouveau.modeset=0

---

