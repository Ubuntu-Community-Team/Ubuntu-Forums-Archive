---
title: "Hard disk issue"
date: 2006-10-24
forum: General Help
---

### Post by ryan s on 2006-10-24
hey everyone,
i wanted to give linux a shot so i dont have to buy vista when it becomes mainstream, but as of now, im still using xp. basically, i know nothing about linux ](*,) heres my problem: i was installing ubuntu using the first option on the live cd (create partition on hard drive) and i guess i moved the slider down to 34.8gb. now, when i log into windows, i only have have 1.someGB free space, even though my hdd is 160gb! the ubuntu install wont let me slide the slider back to full size for the partition. am i stuck with a 34gb hdd :confused: i just paid $100 a couple weeks ago to get windows reinstalled (new mobo), and windows works perfectly as well as ubuntu. is it possible to uninstall ubuntu (my keyboard doesnt work on the very first screen for some reason!) and get the partition back? am i sol and have to pay another $100 to get my hdd wiped and xp reinstalled? please help me, im freaking out since i couldnt find an answer on here and i dont want to waste more money. if you can help me, please make it so i can understand it cause i dont get ubuntu at all ](*,)

---

### Post by Kateikyoushi on 2006-10-24
This guide explains how to uninstall ubuntu from your machine. [LINK]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

You can use the livecd to resize your windows partition, or can create another partition from windows. But you have to restore the MBR before deleting the linux partition or you won't be able to boot.

---

### Post by kvonb on 2006-10-24
There are several ways to tackle the problem:

1) Go back to the store that charged you $100 to re-install winows, act dumb and say that there is some hard disk space missing since you got it back.  If you sound as if you are accusing them of changing your original hdd for a smaller one, they will sort it out without charging you again (I'm saying this with tongue in cheek because I own a computer shop and that's what the buggers try on me all the time!).

2) If you have a CD/DVD burner and a blank writeable CD, download and burn the following Linux rescue tool CD:

[http://prdownloads.sourceforge.net/systemrescuecd/systemrescuecd-x86-0.2.19.iso?download](http://prdownloads.sourceforge.net/systemrescuecd/systemrescuecd-x86-0.2.19.iso?download)

Boot from the CD and look for the tool "qtparted", it should allow you to delete your Ubuntu partition and resize your WinXP one.  ### NB: I would make a complete backup of your XP partition before you attempt any of this, there is a tool for doing that on this CD called "parted".

May the Ubuntu be with you :)

Oh yes, and as katiekyoshu just said, make sure you overwrite the MBR when you use qtparted, it has an option in the menus for that :)

---

### Post by ryan s on 2006-10-25
ok, i did the mbrfix and downloaded the gparted iso, but i cant get it to boot. i disable everything but my cd drive and it stills boots windows. do i need to run this in ubuntu? even dumber question: how do i boot ubuntu 8-[ #-o

---

### Post by kvonb on 2006-10-25
When you first turn on the computer, there should be a message on the screen, something like "F12 select boot device", or something along those lines.

Press the corresponding key (you have to be quick or it will continue booting, if so press the reset button and try again.), and it should give you a menu which will have the CDROM (or DVD drive) as an option, select that and it should boot from the CD.

Re-post if you get stuck.

---

### Post by ryan s on 2006-10-26
my computer doesnt give me an f12 option and if i push it, it wont even work. i can disable all other boot devices and the cd wont boot but xp will. ubuntu is the only disk of mine with an iso image that does boot. 

i might have to use my spare 60gb hard drive and move everything i have onto that, clear my 160gb main drive, then transfer everything back. wait, that wouldnt work since ubuntu still isnt uninstalled ](*,) 

the qtparted nor gparted cds boot ](*,)

---

### Post by kvonb on 2006-10-26
Can you boot from ANY CD?  I'm wondering if it is a problem with the computer or the CD.

Try booting from your Windows CD.

---

### Post by ryan s on 2006-10-26
i never got a windows cd, my xp came with the "recovery console." 

my mobo cd and ubuntu cd are the only bootable cds i have and the only ones that work.

---

### Post by kvonb on 2006-10-26
Sounds like your computer is set to boot from only the hard disk.

Did you get a manual or instruction book with the computer?  If so, look in it for a section about "bootable CDs" or "how to boot from CD".

If no instructions, then reset the computer and on the very first screen that appears, hit the "Pause" key, (you might have to do this a few times to get it right), hit pause again to un-pause.

Look around the screen and look for things like:

Press DEL to enter setup, F10 setup, anything at all that offers a key or key combination.

When you have figured out which key, go into the setup and look for a section on "boot order", the wording might not be the same, but what you need to do is change this boot order from hard disk to CDROM first.

If you manage this, save and exit, reboot with the Ubuntu CD in the drive and it should now boot.

---

### Post by ryan s on 2006-10-27
its a custom made pc with xp reinstalled on it. to enter the BIOS screen is the DEL button. my boot order is:
1. cd rom
2. hdd
3. disabled

even when i disable hdd booting, it will still boot xp from the hdd. the only cd that boots is the ubuntu livecd. that wont allow me to mess with the size of the partition, ie, set it to 15x.xx gb instead of 34.xxgb like i accidentally did. it gives me some error like "cant do something to the disk."

---

### Post by kvonb on 2006-10-27
Oh well that's good if you can boot from the Ubuntu CDROM.

Boot from the Ubuntu live CD and run Gnome Partition Editor (Menu: System -> Administration -> Gnome Partition Editor).

When you are in the part-ed, press the "Print Scrn" key (between F12 and Scroll Lock usually), just click "save" when the dialogue box pops up, then post another message and attach the screen shot (when you are writing a post, scroll down the window a little and you will see a button marked "Manage Attachments", click that and browse to your "Desktop" folder, the Screenshot.png will be there, attach and upload).

I mean no offence by the simplicity, I tried to make this as clear as possible just in case you get stuck :)

I have attached some screen shots of my computer booted from the Ubuntu CDROM.

---

### Post by ryan s on 2006-10-28
looks like my previous reply didnt work...here goes again. 

i dont take any offense. i know im a noob at this :rolleyes: attached is my screenshot. i hope its ok [-o<

---

### Post by kvonb on 2006-10-28
If you click on the drop down box (top right) where it says [/dev/hdc], are there any other devices listed?  Do you have more than one HDD?

Please re-post with the answer to that one.

Seems odd that your NTFS partition is reported as hdc!

From that information, it looks like your HDD is on the secondary IDE port, rather than the "normal" primary.  Maybe that's what is causing the confusion.

If you are feeling brave you could open the computer and swap the cables around, but that might give XP a heart attack!

Also Gparted is reporting that it is full, which is why it won't let you re-size it.

Can you still boot into XP?  If so, you might want to run the disk checker, (right click on the drive in My Computer, then tools I think).

I don't believe that you have used up 153gigs already!

This is frustrating, if I was there I could sort it out in seconds :)

But on the up-side it looks like your XP is still there, it's just a matter of sorting out this mess.

---

### Post by ryan s on 2006-10-28
yes, i have a slave drive. its listed in the part-ed, but i dont remember what it is off hand. 

i feel 100% comfortable taking apart the computer, as i built it myself :D i just put on some rounded ide last week as a matter of fact lol. but, i had installed ubuntu already. ill switch the master and slave and see what it does. 

xp still works fine (im using it now). you could always hop on a plane and come here to fix it lol :rolleyes:

---

### Post by NZ-Wanderer on 2006-10-28
Excuse me for poking my nose in, but was reading the thread and thought you might try downloading the trial version of Acronis disk director and use that to do your partitioning before you install Ubuntu again, then you won't have to muck around with the ubuntu partitioning thingie :D - I always do my partitioning in Windowz before installing any OS, cause IMHO windowz has better partitioning wizards/tools than other OS's

Just my 2c worth, going back to lurking again :D

---

### Post by kvonb on 2006-10-28
That's a good idea NZ-Wanderer, I will be doing the same thing when I get around to installing Edgy.

So, let's recap, I'm getting a bit lost here :)

Your XP partition on /dev/hdc should be around 160gig, and Parted reports it as being full.

XP is now booting which is good.

You also have a second drive, size as yet unknown, contents unknown.

You can obviously boot from the CDROM now as your screenshot shows.

So if XP reports it's partition as being around the 160gig mark, that would mean that you are back to where you started no?

If your other hard disk is free, you might want to just use that to install Ubu on and just leave the XP drive alone for now.

I would suggest setting your 'other' hard disk as the master on the primary IDE port, your 160gig as the slave on the primary port, and your CD/DVD as the master on the secondary port.  Turn the system on and hit the [DEL] key to get into the BIOS.  Look through there for 'boot order' and set it to this order: FLOPPY CDROM C-DRIVE, insert the Ubu CDROM, save and exit to reboot.

You should then find that Ubuntu will boot.  Press enter to select the default option, and use the 'other' hard disk as a dedicated Ubuntu disk, (assuming that you don't need anything on the disk!), just select the default setting for the partition (use entire disk), and install GRUB on the same disk.

This will give you a GRUB boot menu on the 'other' hdd with the option of booting into XP from the menu.  It will NOT touch your 160 gig, which means that if you decide to ditch Ubu, all you have to do is disable the 'other' drive, XP won't be affected.

Let me know how you go.

Regards,  Kev :)

---

### Post by handy on 2006-10-28
Most modern motherboards will now let you boot from any of the IDE channels, but be careful of windows C: drive not being on the primary master, just keep your eye on that in case your board is finicky?

---

### Post by ryan s on 2006-10-29
> **kvonb said:**
> Your XP partition on /dev/hdc should be around 160gig, and Parted reports it as being full.
check
[QUOTE=kvonb]XP is now booting which is good.[/quote]
check
[QUOTE=kvonb]You also have a second drive, size as yet unknown, contents unknown.[/quote]
71.8gb total, 13.2gb free. this is just videos and stuff. still has tons of stuff i never deleted when i copied my stuff to the 160gb. i have a spare 60gb drive with only ubuntu installed.
[QUOTE=kvonb]You can obviously boot from the CDROM now as your screenshot shows.[/quote]
check
[QUOTE=kvonb]So if XP reports it's partition as being around the 160gig mark, that would mean that you are back to where you started no?[/quote]
xp says about 160gb drive: 34.6 used, 116mb free.

im going to try some other partitioning programs and see what happens. if none of those work, itll be time to dig into the hardware ](*,)

---

### Post by ryan s on 2006-10-29
> **NZ-Wanderer said:**
> Excuse me for poking my nose in, but was reading the thread and thought you might try downloading the trial version of Acronis disk director and use that to do your partitioning before you install Ubuntu again, then you won't have to muck around with the ubuntu partitioning thingie :D - I always do my partitioning in Windowz before installing any OS, cause IMHO windowz has better partitioning wizards/tools than other OS's

Just my 2c worth, going back to lurking again :D
worthless. you need to buy the full version to resize. ](*,)  what pisses me off even more is that acronis tells me that i have used 26.88gb of 153.4gb total (which is correct) but my c drive is still only 34.8gb. acronis tells me what i want to hear but its not true cause "its impossible to apply the changes you have made" with the trial version ](*,) ](*,) ](*,) ](*,)

---

### Post by ryan s on 2006-10-31
bump to the top...any other options to try?

---

