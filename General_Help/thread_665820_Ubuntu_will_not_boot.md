---
title: "Ubuntu will not boot"
date: 2008-01-12
forum: General Help
---

### Post by Scramble on 2008-01-12
A couple of days ago the computer crashed and I was forced to re-boot but then it wouldn't so I thought little of it, powered down and went to bed.
I'll type what I get:

[I]/dev/hdb contains a file system with errors, check forced
/dev/hdb1:[/I]

then it goes up to around 32% before showing the following:\

[I]* An automatic file system check (fsck) of the root fielsystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read only mode.

* The root filesystem is currently mounted in read only mode. A maintenance shell will now be started. After performing system maintainence, press CONTROL-D to terminate the maintainence shell and restart the system.

Give root password for maintenance
(or type Control-D to continue)[/I]

Then I type my password and it gives the following lines:

[I]bash: no job control in this shell
bash: groups: command not found
bash lesspipe: command not found
bash: command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: command: command not found
bash: The: command not found
root@george-desktop:~#[/I]

So then I press CONTROL_D and it just goes through the same procedure over and over.

Please help :-)

---

### Post by kool_kat_os on 2008-01-12
Hmmm..........

Is reinstallation an option for you????

---

### Post by iris-n on 2008-01-12
You might try doing the manual check:

```
sudo fsck /dev/hdb1
```

---

### Post by Scramble on 2008-01-12
Thanks, I'll try that and report back.

---

### Post by Scramble on 2008-01-12
Ok so maybe I'm being a bit thick here but the result is:

*The command could not be located because '/usr/bin' is not included in the PATH environment variable*

I'm guessing I need to slightly amend that command line?

---

### Post by iris-n on 2008-01-12
No, the command is fine.
That error is quite creepy, for all i know.
Something else, try booting the live CD and running the command from there.

PS: Make sure that /dev/hdb1 is your partition with errors, it seems that from the error message, but.

---

### Post by CamCollie on 2008-01-12
*That error is quite creepy, for all i know.*

I'm having the exact same problem as Scramble and have followed the same suggestions only to get the same error. 

I'd rather not do a reinstall so I'm keen to see how this all pans out.

---

### Post by iris-n on 2008-01-12
Have you tried the live CD?
I ran the command in my pc, it's exaclty that, unless...
sudo isn't necessary, since you're in maintenance mode logged as root, maybe that's causing that trouble.
And i don't think a reinstall would be necessary.

---

### Post by CamCollie on 2008-01-12
No I haven't run the live CD. I'll give it shot and report back. 

Is this something to do with Gutsy Gibbon? I never had an issue with Feisty Fawn....

---

### Post by Scramble on 2008-01-12
That doesn't work for me either. I just get...
*/bin/sh: sudo: not found*

---

### Post by CamCollie on 2008-01-12
Nup - me either. Looks like a reinstall is imminent...

---

### Post by CamCollie on 2008-01-12
Reinstall complete. Problem fixed but data lost :(

---

### Post by lizadove on 2008-01-13
When you reinstalled did you get this error??
____
Quote:
Go back to the menu and correct errors?

The test of the file system with type ext3 in partition #2 of IDE1 master (hda) found uncorrected errors.
If you do not go back to the partitioning menu and correct these errors, the partition will be used as is.
____

I am having the same problem (ARGH!! - what's the deal here, we are not alone in this problem, I'm sure of it!)  and I guess I should just use the partition as is, since I don't know how to fix it (the whole reason I am reinstalling...duh)

---

### Post by CamCollie on 2008-01-13
> **lizadove said:**
> When you reinstalled did you get this error??
____
Quote:
Go back to the menu and correct errors?

The test of the file system with type ext3 in partition #2 of IDE1 master (hda) found uncorrected errors.
If you do not go back to the partitioning menu and correct these errors, the partition will be used as is.
____

I am having the same problem (ARGH!! - what's the deal here, we are not alone in this problem, I'm sure of it!)  and I guess I should just use the partition as is, since I don't know how to fix it (the whole reason I am reinstalling...duh)

Hey Lizadove

When I reinstalled I got no errors at all. Everything is working fine now. 

In regards to partitions I choose no partiton and to use the whole disk. I'm am running Feisty Fawn on my older Toshiba laptop and it only has a 20G HD so I figured what's the use.

Try selecting the second partition option on the reinstall and use the whole disk. Maybe that will help.

Cam

---

### Post by iris-n on 2008-01-13
So,try it without sudo, just ```
fsck /dev/hdb1
```

---

### Post by Scramble on 2008-01-13
ok, will try that

---

### Post by Scramble on 2008-01-13
Hurrah, thanks for the help. It did work that time although it was a little tricky as it would sometimes look like it wasn't doing anything and I'd press keys and it'd still look like it wasn't doing anything....it would also say something failed but it still eventually booted up on the first try. Is there some kind of maintenance that I can run from within the GUI that is more user friendly?
Thanks again.

---

### Post by iris-n on 2008-01-13
It's good to hear that.

Why, don't you think a command line friendly?
Just kidding.

You can, through gparted. You will have to download it, ```
sudo apt-get install gparted
```

It's a bit different, but quite good.

Just go to the tab Partition->Verify.

---

