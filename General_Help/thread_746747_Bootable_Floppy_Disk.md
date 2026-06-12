---
title: "Bootable Floppy Disk"
date: 2008-04-05
forum: General Help
---

### Post by twi124 on 2008-04-05
I want to Upgrade my machine's BIOS.
I have Pheonix Bios.  Version # is *4W4SB0X0.15A.0017.P12*

I downloaded the upgrade from the Gateway website ([_~:Clickie:~_]("http://support.gateway.com/support/drivers/getFile.asp?id=14952&dscr=BIOS%20update%204W4SB0X0.15A.0019.P14&uid=192113702")).  

The readme included with this BIOs upgrade says it's for version *4W4SB0X0.xxx.xxxx.Pxx*.

There was a note on the upgrade.  It read as follows:
"*When updating your computer's BIOS, the update process fails if you use a floppy disk formatted in Microsoft® Windows® 2000, Windows NT®, or Windows XP. Instead, use a new IBM pre-formatted disk. Refer to Readme.txt file for more details.*"

I tried writing the upgrade to a floppy disk with Windows XP (following the instructions given in the readme just in case) anyways to see if I had a little luck on my side.  I inserted the floppy with the upgrade on it and powered on my machine.  It told me "*remove the media or other divice and press enter to continue ...*".  I removed the floppy and the machine proceeded to boot into the OS.  It failed the upgrade just as Gateway said it would.

So I decided to try to write the disk in Ubuntu this time.  I formatted the disk, wrote the files to the disk, popped it into my machine, and powered it on.  This time it gave me this message:
"*This is not a bootable disk.  Please insert a bootable floopy and press any key to try again ...*"

So my question:
How do I make a bootable floppy with Ubuntu?  


Oh, and I don't have any pre-formatted floppy disks, and I don't have the money to get any at the moment.  This is the option I can think of at the moment.


So how do I make the floppy disk bootable using Ubuntu?

---

### Post by oilchangeguy on 2008-04-05
please explain why are you wanting to flash (upgrade) the bios? done wrong you'll turn the computer into a large doorstop.

---

### Post by twi124 on 2008-04-05
It's not that I need to, I just want to.  The Bios are really old anyways.  The computer works as is, but it could be better.
I know the risks of flashing the bios incorrectly, but those risks are the reason we have instructions.

[I]Performing the update

1.  From the Start menu, click Shut Down.  In the Shut Down Windows dialog box, click Restart, and then click Yes.  Leave the disk in the floppy disk drive while the computer restarts.

2.  When the computer restarts, an Intel Flash Memory Update Utility screen appears.  Press any key on the keyboard.

3.  In the Main Menu, select Update flash memory area from a file, and then press the ENTER key.

4.  In the Update Flash Area window, select Update System BIOS, and then press ENTER.

5.  In the Enter Path\Filename window, press the DOWN ARROW key once to select P14-0019.BIO, and then press ENTER.

6.  In the Please Confirm BIOS Version Information window, select Continue with programming, and then press ENTER.

7.  The BIOS is upgraded.  When complete, a warning displays to let you know the computer will restart.  Remove the disk from the floppy disk drive, and then press ENTER.

8.  The computer restarts.  As the computer restarts, begin pressing the F1 key in one-second intervals.  If you perform this step correctly, you see the BIOS Setup Utility menu.  If Windows loads normally, repeat this step.

9.  After the BIOS Setup Utility opens, press F10 to exit, and then ENTER.[/I]



Following that I think there isn't much room for error.
I just need a bootable disk that will successful preform the upgrade.



How can I get Ubuntu to make my floppy disk bootable?

---

