---
title: "understanding growisofs"
date: 2007-02-02
forum: General Help
---

### Post by sheine on 2007-02-02
In trying to copy a movie from hard drive to a disk, I got this message:

:-[ READ DVD STRUCTURE #10h failed with SK=8h/ASC=ABh/ACQ=80h]: Input/output error

What does it mean?

---

### Post by meng on 2007-02-02
What command did you give?

---

### Post by jimbob on 2007-02-02
Any reason you don't want to use k3b ?&#65279;
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by sheine on 2007-02-02
k3b did something peculiar. It copied the original, then said that it could not eject the disk, and erased the stored file.

The command that I gave was:
growisofs -dvd-compat -Z /dev/hdc=prod

---

### Post by meng on 2007-02-02
Is /dev/hdc your DVD drive?

---

### Post by sheine on 2007-02-02
> **meng said:**
> Is /dev/hdc your DVD drive?

Yes.

---

### Post by russo.mic on 2007-02-03
Everytime I have used K3b in Gnome it does this, for some reason it is unable to send the Optical drive the eject command, and for some reason this crashes it.  

So, all you have to do is uncheck the "Delete Image" under the Image tab after you hit the burn button.  Then, Swap the CD manually, and burn the image. 

Russo

---

### Post by sheine on 2007-02-03
> **russo.mic said:**
> Everytime I have used K3b in Gnome it does this, for some reason it is unable to send the Optical drive the eject command, and for some reason this crashes it.  

So, all you have to do is uncheck the "Delete Image" under the Image tab after you hit the burn button.  Then, Swap the CD manually, and burn the image. 

Russo

How do I burn the image? I cannot use growisofs.

---

### Post by jimbob on 2007-02-03
If you have k3b installed,
 just click on tools and select Burn DVD ISO image.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by sheine on 2007-02-03
> **jimbob said:**
> If you have k3b installed,
 just click on tools and select Burn DVD ISO image.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

As far as I can tell, k3b cannot handle files larger than 4.3Gb. I am trying to copy a larger file.

---

### Post by jimbob on 2007-02-03
The command I have used successfully in the past is:

growisofs -speed=1 -dvd-compat -Z /dev/hdc -dvd-video /<path to your .iso file>

 I take it you cannot get your hands on the original DVD disk.   If you could k9copy would give you a good burnable .iso file.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by sheine on 2007-02-03
I got a copy of k9copy. Unfortunately the instructions that I used said that I was to click a gear in the upper left. There was no gear.

Using dd I can make a copy to my hard drive. What I can't do is copy from the hard drive to a blank disk.

---

### Post by jimbob on 2007-02-03
dd isn't going to shrink the file so you can burn it to a 2-hour DVD.

Don't be intimidated by k9copy.  The same thing happened to me when I used it about clicking on the gear.  I ignored it and proceeded anyhow.

It is prety simple to figure out.  Go for it - it works.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by sheine on 2007-02-03
> **jimbob said:**
> The command I have used successfully in the past is:

growisofs -speed=1 -dvd-compat -Z /dev/hdc -dvd-video /<path to your .iso file>

 I take it you cannot get your hands on the original DVD disk.   If you could k9copy would give you a good burnable .iso file.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

The response that I got was:

Executing 'mkisofs -dvd-video /home/sidney/prod | builtin_dd of=/dev/hdc obs=32k seek=0'
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: Value too large for defined data type. File /home/sidney/prod is too large - ignoring
mkisofs: Unable to make a DVD-Video image.
:-( write failed: Input/output error

k9copy didn't work either.

---

### Post by sheine on 2007-02-03
> **jimbob said:**
> The command I have used successfully in the past is:

growisofs -speed=1 -dvd-compat -Z /dev/hdc -dvd-video /<path to your .iso file>

 I take it you cannot get your hands on the original DVD disk.   If you could k9copy would give you a good burnable .iso file.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]


The response was:
Executing 'mkisofs -dvd-video /home/sidney/prod | builtin_dd of=/dev/hdc obs=32k seek=0'
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: Value too large for defined data type. File /home/sidney/prod is too large - ignoring
mkisofs: Unable to make a DVD-Video image.
:-( write failed: Input/output error

k9copy didn't work either, no gear to click.

The response that I got was:

Executing 'mkisofs -dvd-video /home/sidney/prod | builtin_dd of=/dev/hdc obs=32k seek=0'
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: Value too large for defined data type. File /home/sidney/prod is too large - ignoring
mkisofs: Unable to make a DVD-Video image.
:-( write failed: Input/output error

k9copy didn't work either.

---

### Post by jimbob on 2007-02-03
Try this from a terminal:

dvdbackup -i /dev/hdc -M -o /opt/

Maybe try it on a shorter DVD to start with so we can get a better handle on the problem.  The file will be created in the /opt directory and it will be assigned a name based upon what it finds on the DVD.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by sheine on 2007-02-03
> **jimbob said:**
> Try this from a terminal:

dvdbackup -i /dev/hdc -M -o /opt/

Maybe try it on a shorter DVD to start with so we can get a better handle on the problem.  The file will be created in the /opt directory and it will be assigned a name based upon what it finds on the DVD.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

Short and simple:
bash: dvdbackup: command not found

---

### Post by jimbob on 2007-02-03
apt-get install dvdbackup

---

### Post by sheine on 2007-02-03
sidney@sidney-desktop:~$ dvdbackup -i /dev/hdc -M -o /opt/
Failed creating title directory
Permission denied

I checked and ls -l indicates x for everybody.

---

### Post by jimbob on 2007-02-04
sudo apt-get install dvdbackup

Before you do that though, I'm wondering if you have all the DVD tools installed.

What version of Ubuntu are you running?

Try this to see about the DVD tools and post the result:

apt-get install libdvdread3
apt-get install libdvdcss2
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by sheine on 2007-02-04
My latest failure, using growisofs, led to:

k3b_image.iso
Executing 'mkisofs -dvd-video /root/k3b_image.iso | builtin_dd of=/dev/hdc obs=32k seek=0'
mkisofs: Value too large for defined data type. File /root/k3b_image.iso is too large - ignoring
mkisofs: Unable to make a DVD-Video image.
:-( write failed: Input/output error

I copied with k3b.

---

### Post by sheine on 2007-02-04
> **jimbob said:**
> sudo apt-get install dvdbackup

Before you do that though, I'm wondering if you have all the DVD tools installed.

What version of Ubuntu are you running?

Try this to see about the DVD tools and post the result:

apt-get install libdvdread3
apt-get install libdvdcss2
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

I have the newest versions of both files installed.
I am using Dapper Drake.

---

### Post by jimbob on 2007-02-04
Exactly how big is it ?

---

### Post by sheine on 2007-02-04
> **jimbob said:**
> Exactly how big is it ?

About 8 Gb.

---

### Post by jimbob on 2007-02-04
If I was you at this point I would grab a spare DVD lying around that was smaller and prove to myself that at least the dvdbackup command will work.

Did you get your multimedia stuff installed via Automatix?  If so, you should have everything.

Also, run this command to make sure you have all the decryption stuff installed:

   sudo /usr/share/doc/libdvdread3/examples/install-css.sh

---

### Post by sheine on 2007-02-04
By going to root, dvdbackup worked on a regular 4.3 disk.

I have now transferred the disk with k3b to my hard drive, using root and a folder other than /tmp (when I restarted the computer after storing in /tmp, the k3b default, it was not there when I restarted the computer). Totem plays the movie from my hard drive. But when I try to transfer to a disk, I get the kind of errors reported above depending on the way that I try to make the transfer. 

What I need is a way to transfer the file to a dual layer DVD-R disk.

---

### Post by jimbob on 2007-02-04
I have a Liteon Dual-layer burner but I have never purchased nor tried to burn a dual layer disk.

Have you checked out Nero?  I think they offer a free 30-day trial copy to see if it works.

---

### Post by sheine on 2007-02-04
I have an LG burner that got very good reviews. It came with Nero but then I would need to use Windows. I want to do everything with linux.

---

### Post by jimbob on 2007-02-04
Nero has a Linux version but they want to sell it only - no free trials.

I know this because I tried to get them to substitute my Winblows version when I bought my burner and they wouldn't do it.

---

### Post by sheine on 2007-02-05
The latest development is that I was able to copy the movie with dvdshrink but it only plays on my computer not on my dvd player. In the process it used 12.5 Gb which is all that I had free on my hard drive. Would it have been playable if I had more free space  on my hard drive?

I still think that with the right program or instructions I should be able to copy the whole dvd movie.

---

### Post by jimbob on 2007-02-05
Maybe your DVD player won't handle dual-layer ...

---

### Post by sheine on 2007-02-05
Back to where I started. I tried gnomebaker and got his message:
Executing 'builtin_dd if=/tmp/GnomeBaker-sidney/gnomebaker_copy_dvd.iso of=/dev/hdc obs=32k seek=0'
:-[ READ DVD STRUCTURE #10h failed with SK=8h/ASC=ABh/ACQ=80h]: Input/output error

This is the same error as with my first post. Can somebody tell me what it means?

---

### Post by sheine on 2007-02-05
> **jimbob said:**
> Maybe your DVD player won't handle dual-layer ...

It has no trouble reading them and its specifications include writing dual layer.

---

### Post by hotdoog on 2007-09-11
:confused:This is the exact same problem I have. I just bought these DVD-R DL discs hoping to be able to stoare more at once. I have been quite sucessful in the past burning both DVD- and +R (The RW may not have worked...)

I was worried that my LG drive only did DVD+R DL because it seems to have that logo (but it is written really really small) so I'm not sure. But according to k3b, it does burn them. I've tried various configurations of k3b and growisofs to no avail. It seems this problem is different than others, it's not the speed - it's a very fundamental I/O error:

> :-[ READ DVD STRUCTURE #10h failed with SK=8h/ASC=ABh/ACQ=80h]: Input/output error

I was thinking that maybe the drive had to be mounted or unmounted in order to burn and somehow because the dual layer confused it it needed manual setting. But, When I tried it said it was already unmounted.

Incidentally, the automounting thing of ubuntu doesn't recognise my blank media in the same way it does for all others. Normally it pops up a dialogue saying: blank media - do you want to burn. It usually can tell CDs and DVDs. But this just shows up as CDROM on the desktop. I was thinking it wasn't able to deal with my media but k3b did at one point ask for a single layer DVD instead of a dual layer one when I forced it into DAO mode...

Anybody any clues since february?

I found a similar unanswered threat on debian [http://lists.debian.org/cdwrite/2007/03/msg00022.html]("http://lists.debian.org/cdwrite/2007/03/msg00022.html")
from march

:confused::confused::confused:

---

