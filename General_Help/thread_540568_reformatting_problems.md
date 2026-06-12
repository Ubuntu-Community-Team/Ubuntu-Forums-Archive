---
title: "reformatting problems"
date: 2007-09-01
forum: General Help
---

### Post by mzracer360 on 2007-09-01
My family owns a Mirra backup server that has gone bad.  We sent it back to Mirra but the warranty has ended.  So, instead of paying for repairs, we decided to have them send it back to us so we can goof around with it.  I have taken out the hardrive and hooked it up to my XP machine.  According to Disk Management it is still healthy, so I went ahead and deleted the partitions and reformatted.  

Now, my problem that I am facing it that the BIOS has been password protected by Mirra.  They have also disabled  booting from a CD-Rom drive, which I have temporarily attached.  I have found a BIOS upgrade and flash utility from the Motherboard manufacturer's website.  The Problem I am facing now is how to apply the new bios using the flash utility.  Booting from a floppy is also disable in the BIOS.

Can someone enlighten me on how to fix these problems so I can install Ubuntu? 

thanks,

mzracer360

---

### Post by expatCM on 2007-09-02
I think as a first step you need to remove the CMOS battery and wait for ten minutes before putting it back.  This will have the effect of returning the BIOS to manufacturers default settings and also clear the password.  You will then be able to load the BIOS default settings and change the boot order to make the CD drive the first boot drive.

The CMOS battery is silver color and found on the motherboard.  Looks like a coin.  

It is best NOT to install the BIOS update unless you find that there is something fundamentally wrong....   the update file is very often not well documented so you do not know what changes are in the new file and flashing BIOS has been known to be a headache........  so if it ain't broke, no need to mend it ....

---

### Post by mzracer360 on 2007-09-02
Took out the battery and left it for a couple hours, put it back in and still has a password.
I then found an MS-DOS bootable CD and installed it onto the HD using my XP machine.  I put the bios update and flashing utility onto the HD, installed it back into the Mirra, but MS-DOS could not run the program.
So now, Im basically back to where I started.  
Are there any bios password crackers I can use?  If I install Ubuntu onto the HD is there anything I can use to remove the password?

---

### Post by expatCM on 2007-09-02
Could you please look at the motherboard........  there will be the make and model number of the board printed on it.  Would you please let us know this information .......

Could you also please have a look at the hard drive and see if there is a hidden partition there.  It may be easier to remove the hard drive and install a different hard drive and power on to see if the BIOS password still appears...  if you have a spare hard drive.  It has been known for BIOS settings to be stored on a hidden partition on the hard drive.

---

### Post by mzracer360 on 2007-09-03
The motherboard is the [VIA EPIA Mini-ITX]("http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=21")

[IMG]http://www.via.com.tw/en/images/products/mainboards/mini_itx/epia/epia_mini_itx.jpg[/IMG]

How do I go about finding a hidden partition?  There was one hidden on the hard drive, when we installed MS-DOS it was still booting up to Linux even though we had formatted it.  My dad was somehow able to remove it when we reinstalled MS-DOS though.

edit - I'll see if I have an extra hard drive laying around!

thanks,

mzracer360

---

### Post by expatCM on 2007-09-03
It sounds like the partition may still be there ....  

Why not take out the drive and install as a slave on any other machine.  Then boot that machine from the Ubuntu Live CD and have a look at the drive using the Gnome Partition Manager (Gparted).  This will show clearly what is on the drive ....

---

### Post by mzracer360 on 2007-09-04
I did that before I put MS-DOS on.  It has a 160GB hard drive and it had about 6-7 partitions on the drive.  I got rid of them all then.  Ubuntu doesn't show any other partitions.

---

### Post by expatCM on 2007-09-04
So the drive is clear and has been fully formatted to something like ext3?

I have not yet had time but if you look up your motherboard there should be a manual to download from the manufacturers site.   The manual will tell you how to clear the existing BIOS settings where removing the CMOS battery does not help.  Often this is moving a jumper.

I would be inclined to try and focus on that since it sounds a little like there is still something stored in BIOS.   Once this is cleared then either the BIOS default will be restored and you will be able to move forward or perhaps you will need to update the BIOS with the file you downloaded but at least you will then be able to do that since the CD drive should be accessible.

---

### Post by expatCM on 2007-09-04
I take it that the CMOS chip is soldered to the board and not socketed?

---

### Post by xs4545x on 2007-12-01
I just started reading this:

[http://forums.viaarena.com/messageview.aspx?catid=6&threadid=78941&enterthread=y](http://forums.viaarena.com/messageview.aspx?catid=6&threadid=78941&enterthread=y)

[http://forums.viaarena.com/messageview.aspx?catid=6&threadid=78941&enterthread=y](http://forums.viaarena.com/messageview.aspx?catid=6&threadid=78941&enterthread=y)

it looks to have a wealth of information.  I bought one and realized that it's not quite going to do what i need it to do.  Instead of returning it, I think I'm going to make the effort to get it to do what I want it to...  when I quit being lazy.

---

### Post by Craigus on 2007-12-01
Here's somebody with the exact same problem and a solution:

[http://forums.viaarena.com/messageview.aspx?catid=32&threadid=70115&enterthread=y]("http://forums.viaarena.com/messageview.aspx?catid=32&threadid=70115&enterthread=y")

---

