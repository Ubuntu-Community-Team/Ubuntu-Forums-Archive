---
title: "X-Server not loading"
date: 2012-11-20
forum: General Help
---

### Post by learning_ on 2012-11-20
So I recently changed my splash screen and my X isn't loading. I can't figure out why.. A friend of mine suggested I create a file  called xinit.rc with basically a forced start up for x and put it in my homefolder... I may have a few details wrong.. but I remember the file was just 1 line. Anyway, that worked for a little while but I changed the splash screen back to the default and the x session isn't loading again. The splash screen shows up, then just a black blank screen. I can load the terminal with ctrl+alt+f1 and try to run startx. It prints out the following:

```

Fatal server error
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

Please consult the  X.Org Foundation support
        at http://wiki.x.org

ddxSigGiveUp: Closing log
invalid MIT-MAGIC-COOKIE-1 keygiving up
xinit: Resource temporarily unavailable (errno 11): unable to connect to X ser
ver
xinit: No such process (errno 3): Server error.

```
I am a bit lost as to what to do with all this. I have been trying to figure this all out for ages but couldn't get anything working. Please, if you can help, explain everything as simply as  possible. Still learning so I don't have all the skills down pat.

---

### Post by iRockz558 on 2012-11-20
Try editing the GRUB system startup line removing "quiet splash"

Hold SHIFT when the PC is booting to enter GRUB, press "e" key while Ubuntu is highlited and edit the conf

---

### Post by learning_ on 2012-11-21
That worked ! Thanks a lot. One thing that I thought might be related to my original problem: After changing the splash and all that other stuff happening, I also noticed that during boot while my system is scanning all attached hardware and looking for bootable partitions, after finding my HDDs it prints "No operating system found." Then loads grub as normal. Does this seem like a problem?:confused:

---

### Post by learning_ on 2012-11-21
> **iRockz558 said:**
> Try editing the GRUB system startup line removing "quiet splash"

Hold SHIFT when the PC is booting to enter GRUB, press "e" key while Ubuntu is highlited and edit the conf

Actually it only worked because it removed the splash screen entirely (which I'm assuming was the point). In order for it to boot I have to go in and edit that every time. I actually like having the splash screen and would like to find a solution which would keep it. So any other ideas??

EDIT: I can boot into ubuntu via failsafe-x so I'm sure it's the x-server issue or something of the like that I mentioned above.

---

### Post by learning_ on 2012-11-22
Any help would be greatly appreciated!

---

### Post by steeldriver on 2012-11-22
did you remove the non-standard xinitrc file? it shouldn't be necessary in the default session afaik

---

### Post by learning_ on 2012-11-23
when I added that one to the home folder I didn't see any other one there. Would it be located somewhere else?

---

### Post by learning_ on 2012-11-23
Just found something that I thought might be of use. After a kernel update I noticed the grub entry was as follows:
```
menuentry 'Ubuntu, with Linux 2.6.32-45-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ac10ae5-f0be-4996-b0e7-a3357b49758e
	linux	/boot/vmlinuz-2.6.32-45-generic root=UUID=2ac10ae5-f0be-4996-b0e7-a3357b49758e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-45-generic
}
```
I'm not sure if initrd is right or if it's supposed to be initrc or if there are multiple initr* types... just thought I'd post this to see if it's of use. Thanks for the patience.

---

### Post by learning_ on 2012-11-28
Does any one out there have any insight into the matter?

---

### Post by learning_ on 2012-12-04
@steeldriver , would the xinitrc file be somewhere else that I don't know about? 
Anyone that knows anything it'd be awesome to hear some input..

---

### Post by learning_ on 2012-12-14
It's been about a week, any one know ... anything else?

---

