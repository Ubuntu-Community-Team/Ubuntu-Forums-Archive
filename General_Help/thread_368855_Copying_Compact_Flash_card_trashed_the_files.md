---
title: "Copying Compact Flash card trashed the files"
date: 2007-02-23
forum: General Help
---

### Post by chaosmedia on 2007-02-23
I'm kind of going to pieces here.. I just got back from shooting a concert and connected my Compac Flash reader and started to copy the photos off my cards (manually). I shoot Nikon so the files are in NEF format (Nikons raw format). I didn't react to the fact that when I connected one of the cards it only showed the image icon for the first photo; the rest had a text icon instead. When the files where copied I fired up Bibble to read the files and.. nothin.. They're broken... And now I can't copy the files off the card anymore; neitehr in Ubuntu nor in Windows, and my camera won't recognize the files..

The thing is: I didn't touch the files; I jus copied them... Why would that affect the content on the card at all?!? Does anyone have any ideas on where I could go from here, I'd REALLY appreciate it?!

---

### Post by chaosmedia on 2007-02-23
Pwew, now I've relaxed.. I bought PhotoRescue (for Windows: [http://www.datarescue.com/photorescue/](http://www.datarescue.com/photorescue/)) and managed to recover all the photos.. Are there any similar Linux sofware btw (OSS or commercial)?

Now I just need to figure out wha went wrong so I can prevent it from happening again.. I'm the first to admit that I did something wrong.. I know that I'm a bit lazy with safely removing the external devices (Compact Flash cards in this case), but over the years in Windows that never led to anything..

This is exactly wha I did:

1) I copied a full card of photos and everything worked fine..

2) I replaced the compact flash card with another one (without safely demounting it in Ubuntu), went to the root of the card's file structure and refreshed (and got a new file listing)

3) When I looked at the files, only the first file was reported as an image; the rest said "program" or something (with a textfile icon). I copied the files anyway and that worked.

4) Reading the copied files didn't work and looking at them in a hex editor they look all scrambled. I also couldn't copy the files from the card agai, neither in WIndows nor Linux, or read the card in my camera (the files were corrupt).

5) I correcty unmounted the CF drive and replaced the card with a THIRD card and reconnected the drive. The photos were all reported as program and not images upon which I panic and reboot into Windows where I can safely copy the unharmed files off the third card...

Now, could be not unmounting the drive between the first and second cards mess with the file table of the second card or something? So the data is there, but the indices in the table point to the wrong locations? But I can't understand why the files on the third card where all of the sudden reported as programs, when I did a corrct unmount/remount of the card..

If anyone could shed some light on all of this (and point out my stupidity/mistakes) I'd really really appreciate it.. Right now, I'm sacred to connect another CF card to Ubuntu again.. ;)

Cheers,
Henrik

---

### Post by telovoyagarcar on 2007-02-23
search sourceforge.net
i have downloaded free software from there before to recover deleted pictures in flash memory. I dont recall the name though that was long time ago.

I also had problems with my USB pen drive in ubuntu. If i unplug it without ¨safely removing it¨, windows (vista) will detect that there are errors in the file system of the drive, and offers the option to scan it for errors and fix them... but after the scan, there are no errors. It is some bug in linux  that does not like to not unmount file systems before  unplugging the media. Windows does not like it neither but at least does not mess up the file system.

---

### Post by the.phantom on 2007-02-23
> 2) I replaced the compact flash card with another one (without safely demounting it in Ubuntu), went to the root of the card's file structure and refreshed (and got a new file listing)

ya, you have to click "eject" bofore removing the usb !
pretty sure that is what got you !
when i was a real newbie i made that bobo and lost some jpgs ;-D

---

### Post by chaosmedia on 2007-02-24
Thanks for the answers guys... I will check Sourceforge for that app and see if it works with my messed up cards.. :)

I know that it's always best to unmount the device before unplugging it (regardless if it's Windows or Linux). When using my CF reader in Windows this would mean that I have to unplug & replug the acual reader for every card I read, hence I've become lazy and just switch the cards without unmounting/ejecting and it's worked fine..

However, I did some test here and ejecting the CARD in Linux still leaves the reader mounted, so I can easily switch cards the proper way without unplugging/replugging the reader which is MUCH better when you get home with 8 cards to copy..

What seems to have happened in my case when I switched cards, was that the file allocation table of the first card was written to the seconds card, so when the files where copied, the entries into the data was all misaligned which resulted in broken files (and a broken file structure n the card). While I won't repeat the same mistake again (hopefully ;)), it's still not good that this occurs especially since I only did (apparently) read-only operations on the card..

---

