---
title: "Constant disk access. Why?"
date: 2007-10-24
forum: General Help
---

### Post by pgmer6809 on 2007-10-24
I have found this problem on all Debian based distros. Mepis, Ubuntu (all flavors).
I am running Feisty on a stock DESKTOP. No wireless card. standard graphics adapter etc. 
at least every minute something accesses the disk. This is true whether I am running anything or not.
I even hibernate the computer, the screen goes black etc. but every minute chunk, chunk chunk it accesses the disk.
is there any way I can discover what the HECK this is, and tell it to quit and shut up?
My centos distro for example does not do this even though it is set up as a web server.
Of course my Centos distro does not run X, so the problem may be with X or it may be something else.
But definitely debian related. 
pgmer6809

---

### Post by malangaman on 2007-10-24
I just ran into this article. 


[http://digg.com/linux_unix/Explanation_of_Ubuntu_Hard_Drive_Wear_and_Tear](http://digg.com/linux_unix/Explanation_of_Ubuntu_Hard_Drive_Wear_and_Tear)

"The problem is simply that the drives are spinning up and down too often, and the sliders are being forced to roll on and off the ramp where they’re stored when in off use, causing wear and tear on the slider assembly (not to mention the motor spinning the drive).

The solution, as the original poster pointed out, is relatively simple:

“The fix?

hdparm -B 255 /dev/sda

and the spinning-down stops"

I hope it helps.

---

### Post by pgmer6809 on 2007-10-25
> **malangaman said:**
> I just ran into this article. 


[http://digg.com/linux_unix/Explanation_of_Ubuntu_Hard_Drive_Wear_and_Tear](http://digg.com/linux_unix/Explanation_of_Ubuntu_Hard_Drive_Wear_and_Tear)

"The problem is simply that the drives are spinning up and down too often, and the sliders are being forced to roll on and off the ramp where they’re stored when in off use, causing wear and tear on the slider assembly (not to mention the motor spinning the drive).

The solution, as the original poster pointed out, is relatively simple:

“The fix?

hdparm -B 255 /dev/sda

and the spinning-down stops"

I hope it helps.

Thanks for the tip, but it did not work for me. Maybe my drive is too old.
When I issue the cmd, I get
```
HDIO_DRIVE_CMD failed: Input/output error.
```
When I try hdparm -C on that drive, it reports active/idle. On the hdb drive it reports standby.

But my question is really why should the drive be spinning up and down at all? I leave the machine for a day. Doing absolutely nothing on it. You would think that after spinning down, the drive would have no reason to spin up again.
Or if it did that the spin up might be every hour or so, at worst.
So what is causing it to restart every couple of minutes?
pgmer6809

---

### Post by Roboticus on 2007-10-25
Have you checked crontab for useless junk?
Failing that ... you could start shutting down nonessential processes to see if the accesses go away.  Then you can figure out what to reconfigure...

...roboticus

---

### Post by Maestro23 on 2007-10-25
> **pgmer6809 said:**
> Thanks for the tip, but it did not work for me. Maybe my drive is too old.
When I issue the cmd, I get
```
HDIO_DRIVE_CMD failed: Input/output error.
```
When I try hdparm -C on that drive, it reports active/idle. On the hdb drive it reports standby.

But my question is really why should the drive be spinning up and down at all? I leave the machine for a day. Doing absolutely nothing on it. You would think that after spinning down, the drive would have no reason to spin up again.
Or if it did that the spin up might be every hour or so, at worst.
So what is causing it to restart every couple of minutes?
pgmer6809

Maybe you don't have a** serial-ATA hard drive**... try sudo hdparm -B255 /dev/hda

---

### Post by pgmer6809 on 2007-10-31
> **Maestro23 said:**
> Maybe you don't have a** serial-ATA hard drive**... try sudo hdparm -B255 /dev/hda

I know I dont have an ATA drive, and the cmd I used WAS hdparm -B 255 /dev/hda

Let me repeat what to me is the main issue:
Why is the drive being accessed AT ALL?

From all the posts I have read the hdparm -B cmd just tells the system to leave the drive spinning.
In general if the choice is between spinning with no head up/down and spin-up/spin-down way to often, then I agree, leave it spinning. (My CENTOS system does that.)

But  my real question is HOW CAN I STOP DISK ACCESSES FROM OCCURRING AT ALL when there is nothing being done on the machine?

Crontab and other obvious culprits are not the issue. My crontabs (root, cron.daily etc.) do not have anything in them that occurs nearly often enough to account for this behaviour.

There is some daemon, or kernel issue, that is accessing the drive way to often. 
I would like to know what it is so I can kill it.

Everything else is a workaround. Maybe a useful workaround, though not in my case, but not a solution.

pmger6809

---

### Post by Dave / Mosaic on 2007-11-15
I have a similar thing going on, that I'm trying to figure out...

The disk access LED is just always blinking on every couple of seconds or so,,,,  blip....  blip...  blip....  like a slow heartbeat...

Annoying as all hell; I keep thinking it's some log file being written to uselessly, but I haven't figured it out yet.

For me, this is a new problem with Gutsy; it wasn't doing this when I had Feisty installed on the same machine.

If anybody has any ideas, I'd love to hear 'em....

---

### Post by colonel_fury on 2008-05-14
As Dave replied:

"I have a similar thing going on, that I'm trying to figure out...

The disk access LED is just always blinking on every couple of seconds or so,,,, blip.... blip... blip.... like a slow heartbeat...

Annoying as all hell; I keep thinking it's some log file being written to uselessly, but I haven't figured it out yet.

For me, this is a new problem with Gutsy; it wasn't doing this when I had Feisty installed on the same machine.

If anybody has any ideas, I'd love to hear 'em...."


I am having the same problem with Ubuntu Hardy 8.04.  The constant access is to my NTFS drive (I have a dual-boot system).  I just upgraded and was **not** having this problem with Gutsy 7.10.  It is very annoying and I'll try to post this reply on the Ubuntu 8.04 forum and see if anybody there knows what is causing this.

It seems this problem may be re-inserted into the new releases, and maybe, it gets patched early on (after a new install), and doesn't ever get noticed again until the next release.

I worry about Linux doing continuous reads or writes to NTFS especially!

---

### Post by another_sam on 2008-06-03
> **malangaman said:**
> I just ran into this article. 


[http://digg.com/linux_unix/Explanation_of_Ubuntu_Hard_Drive_Wear_and_Tear](http://digg.com/linux_unix/Explanation_of_Ubuntu_Hard_Drive_Wear_and_Tear)

"The problem is simply that the drives are spinning up and down too often, and the sliders are being forced to roll on and off the ramp where they’re stored when in off use, causing wear and tear on the slider assembly (not to mention the motor spinning the drive).

The solution, as the original poster pointed out, is relatively simple:

“The fix?

hdparm -B 255 /dev/sda

and the spinning-down stops"

I hope it helps.


My hero.

I did not suffer this bug with Ubuntu 7.10 but yes I did until now with Ubuntu 8.04.


> **colonel_fury said:**
> As Dave replied:

"I have a similar thing going on, that I'm trying to figure out...

The disk access LED is just always blinking on every couple of seconds or so,,,, blip.... blip... blip.... like a slow heartbeat...

Annoying as all hell; I keep thinking it's some log file being written to uselessly, but I haven't figured it out yet.

For me, this is a new problem with Gutsy; it wasn't doing this when I had Feisty installed on the same machine.

If anybody has any ideas, I'd love to hear 'em...."


I am having the same problem with Ubuntu Hardy 8.04.  The constant access is to my NTFS drive (I have a dual-boot system).  I just upgraded and was **not** having this problem with Gutsy 7.10.  It is very annoying and I'll try to post this reply on the Ubuntu 8.04 forum and see if anybody there knows what is causing this.

It seems this problem may be re-inserted into the new releases, and maybe, it gets patched early on (after a new install), and doesn't ever get noticed again until the next release.

I worry about Linux doing continuous reads or writes to NTFS especially!


I don't know which precise partition was on my case, but the rest matches (did not on 7.10 and did on 8.04), so try the magic:

hdparm -B 255 /dev/sda

---

### Post by wolfchri on 2008-07-19
> **Dave / Mosaic said:**
> I have a similar thing going on, that I'm trying to figure out...

The disk access LED is just always blinking on every couple of seconds or so,,,,  blip....  blip...  blip....  like a slow heartbeat...

Annoying as all hell; I keep thinking it's some log file being written to uselessly, but I haven't figured it out yet.

For me, this is a new problem with Gutsy; it wasn't doing this when I had Feisty installed on the same machine.

If anybody has any ideas, I'd love to hear 'em....

```
sudo hal-disable-polling --device /dev/cdrom
```

will stop this permanently - but also prevents Ubuntu from opening Nautilus automatically when you insert a CD.

Powertop is a nice tool to find out what is waking up your machine. Add its hints to /etc/rc.local and get ramlog, that might save you a lot of power on your notebook or netbook and does not wake your hard drive any more.

More here: [http://vale.homelinux.net/wordpress/2008/07/17/ubuntu-links-for-july-17-2008/](http://vale.homelinux.net/wordpress/2008/07/17/ubuntu-links-for-july-17-2008/) 
and here: 
[http://vale.homelinux.net/wordpress/2007/10/24/potential-risk-for-your-nx6325s-harddrive/](http://vale.homelinux.net/wordpress/2007/10/24/potential-risk-for-your-nx6325s-harddrive/)

Hope this helps!

:guitar:

---

