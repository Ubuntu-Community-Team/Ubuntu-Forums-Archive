---
title: "Ubuntu 12.04.1 Strange Issues"
date: 2012-11-04
forum: General Help
---

### Post by jewishj on 2012-11-04
My computer started to not restore from suspend successfully.  When I would hit the keyboard the monitors would turn on, and it would just show the cursor against a black background.
The cursor was responsive, but nothing else did anything.  I hit ctrl+alt+F2 to get back to the CLI and was presented with a login prompt.  When I enter my username, however, I would get 
two I/O errors for /dev/sdc (which is the SSD system drive).

Then doing a hard reboot had mixed results:

- Sometimes it would get to the point it starts to load the GUI (just a solid purple background screen with no cursor/etc.)
- Sometimes it would get to the login screen and then freeze again at some random point afterwards, but always within a couple of hours or so
- Also, when it would go to suspend, it would almost always freeze

Occasionally, grub would also be corrupted and it would just give me some sort of file not found error when it tried to boot the OS.  Using the live cd to do re-install grub fixed this problem when it would occur.

After a while of this, grub was corrupted again and I went into the live cd and tried to run SMART on the harddrive and it gave an error (not a SMART error I don't think, it was like it couldn't write to the drive to test it or something like that when it tried to start the test).
Then shortly thereafter, the drive wouldn't even show up from the livecd (although it never disappeared from the bio).

I bought a new harddrive (Samsung 830 128GB SSD) and tried to re-install.  The first time it gave an I/O error when I tried to install, but I rebooted and the install went through without a hitch.
But, shortly thereafter, I had the same issues start and now I'm at the point where the new drive is not showing up in the live cd either.

Does anyone have any idea what could possibly be going on here?
I'm not sure what extra information I can post, but let me know and I can try to get whatever I can (keeping in mind I may not be able to get to the installed OS to run dmesg, etc.)

Here are my system specs:

ASRock x58 Extreme6 (BIOS v2.67)
Core i7 950
12 GB DDR3 1066 (3x 4GB in triple-channel configuration)
128 SSD Samsung 830 (original drive was a 64GB OCZ SSD)
500 GB WD Caviar Black
1 TB WD Caviar Black
nVidia GTX 460 (three monitors configured through the Matrox TripleHead2Go Digital with a custom xorg.conf which I have used for years with various distros/versions without issue)
LG Blueray Burner
LG DVD Burner
Logitech K800 Wireless keyboard
Logitech wireless mouse

It's running a stock Ubuntu 12.04.1 (64 bit) with the latest kernel from the official repo, the nvidia binary driver, and some changes to optimize for ssd (TRIM activated, swappiness to 0, /tmp to tmpfs, mount system drive as noatime,nodiratime,discard, and other common optimizations).

Thanks in advance for any help!

---

### Post by apollothethird on 2012-11-04
> **jewishj said:**
> My computer started to not restore from suspend successfully.  When I would hit the keyboard the monitors would turn on, and it would just show the cursor against a black background.
The cursor was responsive, but nothing else did anything.  I hit ctrl+alt+F2 to get back to the CLI and was presented with a login prompt.  When I enter my username, however, I would get 
two I/O errors for /dev/sdc (which is the SSD system drive).

Then doing a hard reboot had mixed results:

- Sometimes it would get to the point it starts to load the GUI (just a solid purple background screen with no cursor/etc.)
- Sometimes it would get to the login screen and then freeze again at some random point afterwards, but always within a couple of hours or so
- Also, when it would go to suspend, it would almost always freeze

Occasionally, grub would also be corrupted and it would just give me some sort of file not found error when it tried to boot the OS.  Using the live cd to do re-install grub fixed this problem when it would occur.

After a while of this, grub was corrupted again and I went into the live cd and tried to run SMART on the harddrive and it gave an error (not a SMART error I don't think, it was like it couldn't write to the drive to test it or something like that when it tried to start the test).
Then shortly thereafter, the drive wouldn't even show up from the livecd (although it never disappeared from the bio).

I bought a new harddrive (Samsung 830 128GB SSD) and tried to re-install.  The first time it gave an I/O error when I tried to install, but I rebooted and the install went through without a hitch.
But, shortly thereafter, I had the same issues start and now I'm at the point where the new drive is not showing up in the live cd either.

Does anyone have any idea what could possibly be going on here?
I'm not sure what extra information I can post, but let me know and I can try to get whatever I can (keeping in mind I may not be able to get to the installed OS to run dmesg, etc.)

Here are my system specs:

ASRock x58 Extreme6 (BIOS v2.67)
Core i7 950
12 GB DDR3 1066 (3x 4GB in triple-channel configuration)
128 SSD Samsung 830 (original drive was a 64GB OCZ SSD)
500 GB WD Caviar Black
1 TB WD Caviar Black
nVidia GTX 460 (three monitors configured through the Matrox TripleHead2Go Digital with a custom xorg.conf which I have used for years with various distros/versions without issue)
LG Blueray Burner
LG DVD Burner
Logitech K800 Wireless keyboard
Logitech wireless mouse

It's running a stock Ubuntu 12.04.1 (64 bit) with the latest kernel from the official repo, the nvidia binary driver, and some changes to optimize for ssd (TRIM activated, swappiness to 0, /tmp to tmpfs, mount system drive as noatime,nodiratime,discard, and other common optimizations).

Thanks in advance for any help!

You might have a problem drive.  I've experienced similar and found the changing the drive cured it.  You might consider investing in a new drive and see if this cures your problem.  It might not hurt having an extra experimental drive around for other purposes such as backup and test.

If this cures the problem, you can then backup all your data to the new drive, then spend some time experimenting and seeing if you can fix the problem with the original drive.

I'm also see occasions where a drive will work (or appear to work fine) under Windows but not under Linux as well as Vice-Versa.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by jewishj on 2012-11-04
> **apollothethird said:**
> You might have a problem drive.  I've experienced similar and found the changing the drive cured it.  You might consider investing in a new drive and see if this cures your problem.  It might not hurt having an extra experimental drive around for other purposes such as backup and test.

If this cures the problem, you can then backup all your data to the new drive, then spend some time experimenting and seeing if you can fix the problem with the original drive.

I'm also see occasions where a drive will work (or appear to work fine) under Windows but not under Linux as well as Vice-Versa.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

I originally had a 64GB OCZ which was working fine in this system for almost 2 years (since Jan 2011) and I thought the drive was bad too, so I just bought a new one (128GB Samsung 830) and the same thing started happening.

It seems unlikely that this problem appeared in the first drive after working for so long and then also happened to start immediately in the replacement.  

Perhaps its some hardware related to the drive?  Do you think this may indicate a bad cable or SATA controller or something like that?

---

### Post by techvish81 on 2012-11-04
> **jewishj said:**
> I originally had a 64GB OCZ which was working fine in this system for almost 2 years (since Jan 2011) and I thought the drive was bad too, so I just bought a new one (128GB Samsung 830) and the same thing started happening.

It seems unlikely that this problem appeared in the first drive after working for so long and then also happened to start immediately in the replacement.  

Perhaps its some hardware related to the drive?  Do you think this may indicate a bad cable or SATA controller or something like that?

yes, i think that could be a bad cable, in my view, you should purchase a new sata 3 cable with clips on it.  sometimes cables that come without clips,  loosen after some time.  as you have changed the drive and still the problem remains, it could cable.  

if,  in the worst case,  if the problem is not fixed even after changing the cable, it could be your mother board.

---

### Post by varunendra on 2012-11-05
> **techvish81 said:**
> if,  in the worst case,  if the problem is not fixed even after changing the cable, it could be your mother board.or maybe just the port ? That motherboard is a good one, so indeed it will be the 'worst case', but there may be many things in-between.

My usual troubleshooting method is to reset BIOS, disconnect everything and leave only essentials to boot the system, then run it long enough to ensure it is working correctly, then add one device and repeat the process...

In OP's case, I'd reset BIOS, disconnect everything but the CPU, 'One' RAM module (yep! sometimes it is good to be paranoid :)), MB power cables, Monitor (connected to 'onboard' VGA port if available), KB/Mouse. No hard drives at all, nor any additional cards! Then using a bootable flash drive, I'd load an OS which can be run entirely from RAM and run from there (like "Slax"). If everything goes well, I'd shut-down > connect the drive in question to a DIFFERENT sata port (preferably on a different sata controller if available) > reboot as before (loading OS in RAM) and experiment with the drive. Then if :

[LIST]
[*]Errors (I/O errors - corrupting data) again > repeat the tests with the other drives (@ same cable/same port). Errors again > change the cable. Still errors > the SATA controller maybe faulty. If there is a second controller available (usually its ports are differently coloured), repeat the tests with it. Still errors > replace the RAM > repeat tests. Still errors > board is gone! :( No errors at any stage > the last changed entity was faulty.
[*]No errors > Re-connect one device at a time and repeat tests until the error reappears > the last added entity is faulty > replace > retest.
[/LIST]
I wish I could explain it with a flow chart (it's fun, but too time taking) :)

---

