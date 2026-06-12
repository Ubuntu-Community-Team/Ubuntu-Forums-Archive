---
title: "no boot from LiveCD"
date: 2005-05-29
forum: General Help
---

### Post by Michael Stewart Salkin on 2005-05-29
After burning a LiveCD of Hoary 5.4 with my Dell's HL-DT-ST CD-RW GCE-848-3B at 8X, XP recognizes the .ISO file (Windows won't open an .ISO file...godforbid...); however, in spite of enabling booting from CD and ensuring that the boot sequence is correct, rebooting brings up XP, not Hoary.  Do I need a program to open an .ISO file?  Do I have a lousy burn?  Please help a newbie with Linux.  Thanks, Mike  [email]mssdiamonds@comcast.net[/email]

---

### Post by j.hill on 2005-06-05
Same problem here!  I'm running W2K, but otherwise my tale is the same.  I've tried countless reboots, fiddling with the BIOS, opening the CD from inside Windows, &c.  Nothing has worked, and so far Google has failed to help.  What should I (we) do about this?

---

### Post by Michael Stewart Salkin on 2005-06-06
I've sent for the ready-made LiveCD from Ubuntu.  If that boots I have to assume I had a lousy burn.  If it doesn't, I'll have two lovely coasters.  If you come up with any new ideas please let me know!

---

### Post by GrumpySimon on 2005-06-06
Hey guys, the odds are that you've got a coaster, however you can always check an md5 hash of the image and the hash of the cd to see if they're the same.

Otherwise, if you think that you can't boot from CDRom due to screwy BIOS settings, then install [Smart Boot Manager](http://linux.simple.be/tools/sbm) on to a floppy disk, and boot that up. It will allow you to pick where to boot from temporarily, and should skip past the BIOS ordering.

--Simon.

---

### Post by Michael Stewart Salkin on 2005-06-06
Thanks, GS.  I'll download the md5 hash utility and see what's up.  I'm betting on coaster.

---

### Post by millerlite86 on 2005-06-06
I'm not sure if this is related to your problem or not, but just wanted to rule it out.

Are you actually burning the ISO image to a CD (which creates a CD with the Ubuntu files and directories) or are you buring the ISO file to the CD (that 1 file)?

Windows XP cannot read an ISO file and burn the contents to a CD.  I use a freeware utlity (by Alex Feinman) to create my ISO files under Windows XP.

SP 2: [http://isorecorder.alexfeinman.com/download/ISORecorderV2B2.zip](http://isorecorder.alexfeinman.com/download/ISORecorderV2B2.zip)
Pre-SP2: [http://isorecorder.alexfeinman.com/IsoRecorder/download.asp](http://isorecorder.alexfeinman.com/IsoRecorder/download.asp)

One way to insure that your CD was atleast burned in the correct format is to insert it into your CD/DVD drive and if autorun is enabled a program will open with opensouce software.  If autorun is not enabled open up "My Computer" open you "CD/DVD" drive and see if there are many files and folders on the CD or just the 1 file (ISO file).

Hope this makes sense...kind of complicated to explain.

Here is a web site about writing ISO files (by Daniel Petri): [http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)

---

### Post by Michael Stewart Salkin on 2005-06-06
Not only is your response related to my problem, it hit the nail right on the head.  I was trying to burn the ISO file rather than the image.  Thank you for the resources which I'll put to good use.  It's a pleasure to hear from such helpful forum members.

---

### Post by j.hill on 2005-06-07
I too was burning the file rather than the image.  With that problem corrected, I tried again...and now I have a new problem.  Now it won't boot.  First I got a screen that said, "This is the Ubuntu Live CD; press ENTER to boot or F1 to enter the menu," or some such.  So I pressed ENTER and got the letter W after the prompt, but no bootage (booty?).  Pressing BACKSPACE produced the > symbol.  Many keys did nothing at all, and some produced strange symbols that belong to no alphabet I know of.  No item in the boot menu was helpful.  Two subsequent attempts to boot from the disk stopped even earlier, with the message "Boot failed.  Press a key to retry."

My wrath is great.  What is going on, and how do I fix it?

Thanks in advance --

---

### Post by j.hill on 2005-06-07
OK, new developments:

1.  the checksums don't match (assuming I'm doing it right), but I'm not sure what that means.

2.  Subsequent CDs burned from the same ISO don't do *anything*!  The computer doesn't even see them!  When I go in to Windows Explorer and click on the CD drive, I get the message: "Drive not accessable [sic]:  incorrect function."

Is this the time to file a bug report?  Or am I displaying typical newbie obtusity?  Or does this mean "choose another distro"?

---

### Post by Michael Stewart Salkin on 2005-06-07
See [ftp://ftp.cerias.purdue.edu/pub/tools/unix/crypto/md5/MD5.README](ftp://ftp.cerias.purdue.edu/pub/tools/unix/crypto/md5/MD5.README) for a quick review of checksums.  Methinks your unmatched checksums would explain your aggravation noted in 2.  I've decided to avoid the tsouris and wait for the LiveCD from Ubuntu.  I bet they matched their checksums just swell.

---

### Post by forkart on 2005-06-14
> **Michael Stewart Salkin]After burning a LiveCD of Hoary 5.4 with my Dell's HL-DT-ST CD-RW GCE-848-3B at 8X, XP recognizes the .ISO file (Windows won't open an .ISO file...godforbid...) said:**
> mssdiamonds@comcast.net[/email]
Using MagicISO to open iso image. and burn the iso image onto CD with MagicISO built-in [ISO burner](http://www.magiciso.com/tutorials/miso-burnwin.htm).
[http://www.magiciso.com/tutorials/miso-burnwin.htm](http://www.magiciso.com/tutorials/miso-burnwin.htm)

---

### Post by Michael Stewart Salkin on 2005-06-14
[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)  
I was going to use this free utility.  Do you have any experience with it?

---

### Post by millerlite86 on 2005-06-20
I'm not exactly sure about why your CD wouldn't load correctly...we are atleast getting the hardware to boot from the CD to the "Press Enter" screen.  My guess as Michael Stewart Salkin said is also that you may have a corrupted download.  :-? The easiest way to find out if this is the problem is to do a MD5Sum check on the ISO image that you downloaded.

A free MD5Sum checker for Windows (by SolidBlue) can be downloaded here:
[http://winmd5sum.solidblue.ca/](http://winmd5sum.solidblue.ca/) (Home Page)
[http://winmd5sum.solidblue.ca/winMd5Sum-install.exe](http://winmd5sum.solidblue.ca/winMd5Sum-install.exe) (Download File)

The correct MD5Sum for the Ubuntu Live CD 5.04 (as found here [http://us.releases.ubuntu.com/releases/5.04/MD5SUMS](http://us.releases.ubuntu.com/releases/5.04/MD5SUMS)) is:
77a1a8be45e0cc93a14c9b9bf00f6648  (ubuntu-5.04-live-i386.iso)

If these two sums do not match then the downloaded ISO image you have is probably not valid and this is why you are probably having problem with the boot.  You would then need to redownload the entire ISO image again.  This does happen occasionally so don't be discouraged.  If the MD5Sums match, then we have a different problem.

---

### Post by millerlite86 on 2005-06-20
[QUOTE=Michael Stewart Salkin][http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)  
I was going to use this free utility.  Do you have any experience with it?[/QUOTE]

This utility is very easy to use.  Here is the instructions that you would need (copied from Alex's website ([http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm))):

Recording ISO images

Right-click on an ISO file and select "Copy Image to CD". The wizard will open up. The file name should appear in the "File name" edit box. If, for some reason, wizard cannot use currently selected file or CD recorder, an error message will be provided and "Next" button will be disabled.

Press the "Next" button. Recording operation can be terminated by pressing "Cancel". Note that terminating the actual recording operation can take up to several minutes.

When copy is completed, the wizard will display the "Finish" page.

EDIT: fixed link

---

