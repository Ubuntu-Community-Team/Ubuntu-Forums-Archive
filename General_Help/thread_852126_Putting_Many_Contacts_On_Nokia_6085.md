---
title: "Putting Many Contacts On Nokia 6085?"
date: 2008-07-07
forum: General Help
---

### Post by varanasi on 2008-07-07
I have over a hundred contacts I'd like to put on my phone, and I'd like to know a good way to do it.

Here are the basics: Nokia 6085, wammu connected via Bluetooth.  I can browse the contacts already on the phone.

Using Wammu/Read Data, I can read a vcf file - whether it contains one vcard or several.  The new contacts appear italicized in wammu.  I can, using Backups/Save, create a backup file from the italicized contacts. Then, using Backups/Import, wammu pops up a box correctly identifying the phone, backup date, and the number of contacts in the backup file.

If there is only one contact in the backup file, wammu imports it to the phone's contacts without a problem.  If there is more than one contact in the file, wammu pops up this error message:

>Error while communicating with phone
>. . .
>Function:AddMemory
>Error code: 16

And adds only the first contact in the file to the phone.  In either case, importing a file with one contact successfully or importing only a  single contact from a file containing many, a "second" popup reports that the file was successfully imported.

Phone/Send File reports an error sending either a backup or a vcf file to the phone.  The error message is:

>Error while communicating with phone
>Your phone doesn't support this function.

The Gnome Bluetooth Applet can send a single file to the phone successfully, but again, if the file contains more than one contact, the phone gets only one contact.  

I can envision using the Applet to send the contacts one after another to the phone, but I don't really want to do it manually over a hundred times, and I'm not sophisticated enough to know how to automate the process.

---

### Post by cszikszoy on 2008-07-07
Try this:
[http://ubuntuforums.org/showthread.php?t=705103](http://ubuntuforums.org/showthread.php?t=705103)

This worked with my N73, which is also a S60 3rd ed phone.  I think the 6085 is a S40 dev, but this might work with that too.  Eitherway, some googling will help you.  Multisync works very well with evolution contacts, calendar, notes, etc.

---

### Post by varanasi on 2008-07-07
cszikszoy, Thanks.  I started with multisync and evolution but could not, after many tries - and many permutations and perusals of that thread - get it to work.  

(If I could have gotten that to work, I would have considered moving from Thunderbird/Lighting to Evolution - though Evolution doesn't appear to let one modify web-based calendars.)

Edit:  I should mention that I have also put all the contacts into Evolution, dumped out the address book into a single file, but can't get more than the first contact from that file into the phone.

---

