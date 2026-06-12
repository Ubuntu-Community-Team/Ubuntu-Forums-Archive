---
title: "Aunt Tilly installation gone bad :/"
date: 2007-03-11
forum: General Help
---

### Post by roongpatoong on 2007-03-11
Hi All

Just wanted to throw this out there incase someone with a bit of windows experience can help me out.

My daughter's babysitter is a 60+ yr old woman who purchased her first PC one year ago with windows preinstalled (of course). Now that the 1 yr is over - she is bombarded with prompts to renew her 'trial' software that came preinstalled ... I suggested we try linux out ... she said ok.

So I start off with gparted and decided to totally delete the HP 'rescue' partition that was on sda1 and i then moved windows c: to sda1, created a 'share' drive at sda2, then put linux on a single partition on sda3. (swap is on sda5, and a separate grub partition on sda6 and yes i do know what i am doing with the separate grub partition - it is not an error)

gparted happily chugged along and did everything that i asked - as it has done for me every single time I have used it without one single error. Booted up the Edgy live cd and installed to sda3. All good so far. Reboot time.

Test if system boots into linux - yep - no worries. Reboot.

Choose windows from the grub menu - oh oh - error message saying can't find windows files needed for booting. I kick myself and then realise that the boot.ini is still pointing to the second partition.

Boot into Edgy - install ntfs-3g and try to mount sda1 - error message "cannot mount partition coz filesystem check needs to be performed - can be bypassed with --force". Well I tell myself - if I can't even get windows to start to boot, then it can't run chkdisk to clean up the filesystem so lets go with the --force option.

So I --force mount sda1 and then edit boot.ini so that it reflects the first partition - not the second one as it was originally. Reboot.

Select windows and this time windows kicks in - niiiiice. chkdisk screen comes up and says it is going to check the filesystem - great! just what I wanted! chkdisk finishes and before I get time to read the final line of output it goes on to the blue (not BSOD) screen with the window logo - the one just before the user login page comes up. There is some disk activity for a few seconds but then nothing. No user login page - no disk activity - just a blue screen with a windows logo in the middle of the screen laughing at me for trying to mess with an ntfs filesystem.

Needless to say this has caused Aunt Tilly copious amounts of stress because she no longer has her windows safety blanket and is panicking when faced with this new and 'different' linux interface. Does anyone have any tips on how to repair the ntfs filesystem on sda1 (and sda2 actually) so that I can get her booting into windows again?

Some classic quotes from Aunt Tilly during the 'switch' event.

Me : "Oh your 17" LCD is at 1024x768 - I will put it to 1280x1024 and things will look much cleaner"
Aunt Tilly : "Will that make my computer go faster?"

Scenario : Aunt Tilly ragging on linux because she doesn't like it and her windows is 'dead'.
Aunt Tilly : "I don't like linux. I feel like I am more on a network when I'm in linux"
Me : "Uhhhh what do you mean by a network?"
Aunt Tilly : "I dunno"

Scenario : Windows is 'dead' and I am coming back to try and rescue it. Aunt Tilly pulls out her HP user manual with a magnifying glass and starts reading the fine print to me.
Aunt Tilly : " ... does not support the installation of third party software and is not responsible for any issues caused by such software ..."
Aunt Tilly : "Windows is not working because you installed software not supported by HP and they have locked the computer so I can't use it. Now my contract with HP is broken which means they won't help me fix it"
Me : *sigh*

pAntZ

---

### Post by dcstar on 2007-03-11
> **roongpatoong said:**
> 
......
So I start off with gparted and **decided to totally delete the HP 'rescue' partition that was on sda1** and i then** moved windows c: to sda1**, created a 'share' drive at sda2, then put linux on a single partition on sda3. (swap is on sda5, and a separate grub partition on sda6 and yes i do know what i am doing with the separate grub partition - it is not an error)
........

Ok, the original Windows was on the second partition (which now doesn't exist).

IIRC the HP partition would have been a DOS one, so I would recommend you create a (small) dummy DOS partition as the first partition - after you have moved your Windows back to the second partition.

That will probably make Windows a lot happier and give it a better chance of booting up - and you can use **partimage** to move your existing partitions around to make space to do all the work.

---

### Post by roongpatoong on 2007-03-11
Thanks for the quick reply dcstar but the issue is a corrupt ntfs filesystem now - due to me changing the boot.ini file under the 'force mount' option with the ntfs-3g driver.

Grub sees the right partition and windows does boot - just falls a couple of seconds short of hitting the login page :(

pAntZ

---

### Post by SishGupta on 2007-03-11
Ok i have something you can try, and a last resort.

Try:
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1

I dont know if that will work.

as a last resort, copy over important personal windows files to back it up, and reformat and reinstall.

It is nice that you are even trying with Aunt Tilly. I wouldn't have bothered with someone that old. It is hard to get an old person to switch to new things i find.

---

### Post by roongpatoong on 2007-03-11
Thanks SishGupta

Unfortunately I already tried that too (should have mentioned it earlier).

And regarding Aunt Tilly - I don't think I will do the same thing again. She is finding it difficult and she only has one person to turn to. Whereas with windows - she has her grandsons, her neighbor and her neighbor's dog to help out when she gets stuck, or a virus, or loses a file that didn't automatically get saved to her desktop.

I would only recommend taking on such a project for someone who has the time to spend to retrain someone that Favourites are now called Bookmarks and the blue E icon is now a globe with a fox wrapped around it.

BTW - I found a tool for repairing ntfs partitions which boots from a floppy disk. Would have been nice if there was a floppy drive in this machine!! Now to find a way to get the app. onto a bootable usb key ...

pAntZ

---

### Post by SishGupta on 2007-03-11
My sentiments exactly.


Good luck!

---

