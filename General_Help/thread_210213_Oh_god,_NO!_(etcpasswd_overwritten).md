---
title: "Oh god, NO! (/etc/passwd overwritten)"
date: 2006-07-06
forum: General Help
---

### Post by JLH113 on 2006-07-06
*Sigh* I'm at work, SSH'd into my home system, setting up wu-ftpd for some file-movements around the home network.

I read conflicting opinions about whether or not to copy /etc/passwd into the /home/ftp folder, and set permissions there.

I figured what the hey, and went: 
cd/home/ftp (prompt changed to /home/ftp$)
cp /etc/passwd .
sudo vipw ./passwd

Removed all the lines but the ftp user info

:w!

That's when I noticed

/etc/passwd written


Panic Mode

Now I'm completely locked out.

There is a /etc/passwd- , however I have no way to restore it.

Any ideas?   I'm sure I have a knoppix CD around the house somewhere, as well as Breezy and Dapper install CD's.

---

### Post by aysiu on 2006-07-06
Can't boot into recovery mode?

---

### Post by JLH113 on 2006-07-06
I've never needed to - (relative n00b - been working with linux only about a year and a half.)

I'll have to wait till I get home this afternoon, what's the procedure?

---

### Post by taurus on 2006-07-06
At the GRUB prompt, just pick the recovery mode.

---

### Post by JLH113 on 2006-07-06
I'll give it a go, thanks!

---

### Post by sktx on 2006-07-06
have you tried to just boot your box into single user mode (recovery mode in grub) and "cp /etc/passwd- /etc/passwd" ?

---

### Post by JLH113 on 2006-07-06
That's what I'm planning to do when I get off work.

---

### Post by JLH113 on 2006-07-06
Quick question about recovery mode - just tried it on my Kubuntu 6.06 laptop at work, so I'd know what to expect when I get home.

It wanted the root password, for maintenance, or Ctrl-D to continue.

Since my home machine is now blissfully unaware that it has a root user, how could I enter the password?

Or will it recreate the user?

---

### Post by aysiu on 2006-07-06
You will be prompted for a root password only if you've set one. Otherwise, it should log you in straight as root.

---

### Post by JLH113 on 2006-07-06
even though root no longer exists in /etc/passwd?

---

### Post by mannheim on 2006-07-06
[QUOTE=JLH113]even though root no longer exists in /etc/passwd?[/QUOTE]

If that doesn't work, just boot from the ubuntu live cd and do something like:

```

sudo -i
mkdir /mnt/rescue
mount /dev/hda1 /mnt/rescue
cp /mnt/rescue/etc/passwd- /mnt/rescue/etc/passwd

```

and hope that passwd- is really similar to passwd.

---

### Post by JLH113 on 2006-07-06
Oh, it is... I'm still logged in, and can do minimal things like cat the passwd-.

I could also RDP into my windoze box, fat lot of good that does me...

---

### Post by JLH113 on 2006-07-07
As expected, with no root to log in as, just booting into Recovery Mode was a no-go.  I did some googling before I left work, and had mailed myself a bunch of cut-n-paste, I don't remember where I copied this from, apologies to whoever on whatever forum originally posted this but, this was the solution:

> For just about any linux system, if your boot loader allows the addition of more parameters (after the bios boot, before linux boot, hit ESC or F2 or whatever)

* add init=/bin/bash to the list of your kernel-parameters

This puts you into a limited console during boot, then at the prompt type

* mount -o remount,rw /

This remounts your harddrive read/write instead of read-only because you are going to need to edit a file

* then use passwd or edit /etc/shadow 

This booted up to a very limited console.  I was able to:
cp /etc/passwd- /etc/passwd

then SYNC a few times and reboot.

Worked like a charm.

Thanks for the input, folks!

---

