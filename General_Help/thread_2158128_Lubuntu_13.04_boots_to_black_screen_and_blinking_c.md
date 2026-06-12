---
title: "Lubuntu 13.04 boots to black screen and blinking cursor"
date: 2013-06-27
forum: General Help
---

### Post by woodensoul on 2013-06-27
Hello. I'm looking for some help with a problem I recently encountered using Lubuntu 13.04.

I installed it fresh and set it up as a file server and all was well for a couple weeks.  But now when booting up, I just get the Lubuntu loading screen and then a black screen with a blinking cursor.  If I type <alt> + F4, I get a prompt allowing me to login.  Login still works and the samba shares show up on other devices on my network but I can't figure out how to get my desktop back.

Steps I took after installing from CD:

Installed and configured samba.
Configured samba to see NTFS shares.
Configured remote desktop access (can't remember the app I used to do this).
Everything was working well until one day I fired it up and got the blinking cursor.

Can anyone help?

Edit: After searching the forums, I tried this:

sudo service lightdm start

And after a few seconds the desktop appeared.  Now to try rebooting to see if it boots to blinking cursor again.  Anyone know how I can tell why it's booting to the bliking cursor by default?

2nd Edit: This appears to have fixed my problem completely.  Only question now is what happened to cause this?

---

### Post by woodensoul on 2013-07-02
The system booted normally for a while but now it's back to the blinking cursor. When I try to start lightdm I get "start: job failed to start."  Please help.

---

### Post by Valiid on 2013-07-02
> **woodensoul said:**
> The system booted normally for a while but now it's back to the blinking cursor. When I try to start lightdm I get "start: job failed to start."  Please help.
I have somthing very similar to your situation. (My post [here]("http://ubuntuforums.org/forumdisplay.php?f=326")) I tried "sudo service lightdm start" (and "restart") but it said it was already running! :(

---

### Post by woodensoul on 2013-07-03
Valiid:
Thanks for the link to your thread. Unfortunately nothing works at this point. I have tried multiple versions of ubuntu on multiple machines and every time, without fail, I end up trashing it or reinstalling because of a massive failure. I really want to like this OS but the (apparent) unreliable nature of ubuntu is making it useless for me.

---

### Post by cwsnyder on 2013-07-03
Have you tried the 'nomodeset' option in your GRUB linux boot line? It would look something like:```
/boot/vmlinuz-3.8.0-25-generic root=UUID=f71dd1ba-bbe0-402c-ab0f quiet splash nomodeset
```Make sure you add it at the end of the line when you edit it at the GRUB menu.

---

### Post by woodensoul on 2013-07-03
Thanks for the suggestion.  Can you tell me how to edit the grub config file?  (I'm off to search how to do this from the command line.)

---

### Post by cwsnyder on 2013-07-03
First, to try out the edit, simply hit the **e** key when you are at the GRUB menu at the proper entry, then edit the line with vmlinuz close to the beginning, adding nomodeset at the end.  If this works, you need to edit the /etc/default/grub (as root) to add to the end of the line as follows: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **nomodeset**"
```
The original top of the file looks like this:```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
```

---

### Post by cwsnyder on 2013-07-03
I forgot to mention at the end of the last post that this change would make it (semi)permanent (until you changed it again) as soon as you do an **sudo update-grub** in a terminal, and would be included in your GRUB menu from that point forward.

---

### Post by woodensoul on 2013-07-03
Thanks again for the additional help. I was reading about the nomodeset.  This fix is meant to address a problem with display drivers, yes?  I'm not sure that is my issue as I was able to use Lubuntu for a few weeks before this problem surfaced.  But I'm willing to give it a shot...

Is it possible to edit the grub config file once logged in?  I don't see the grub menu when booting because Lubuntu is the only OS currently installed.

---

### Post by cwsnyder on 2013-07-06
Editing /etc/default/grub would change for the next boot, but would not help you if your display driver is badly mismatched enough that you need **nomodeset** to avoid the black screen with a blinking cursor.

You can always force the GRUB screen by pressing the <esc> key when Lubuntu first starts after the BIOS/EFI checks.

---

### Post by jamesisin on 2013-07-06
No one has mentioned this so I'll offer it.  Do you have any USB drives attached during boot?  The system may be attempting to boot from an attached USB drive (iPod too) and not finding a bootable OS.  Solution: unplug that device during boot.

---

