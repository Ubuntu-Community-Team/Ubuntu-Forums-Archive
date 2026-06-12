---
title: "clamtk : No files were scanned"
date: 2014-11-07
forum: General Help
---

### Post by susja on 2014-11-07
Hello,
I just installed Ubuntu 14.10. Then I installed clamtk 4.45
Then I tried to scan a thumb drive. The drive has a few folders and a few text files.
The drive was recognized by clamtk and it could see the content of the drive.
I started to scan but it immidiately finished with error: No files were scanned.
When I checked the log it did not have any information ... just says that 0 files were scanned.
I tried another flash drive but the same issue.
Any clue?
What's wrong that system  could see the drive but failed to scan files?
Thanks in advance.

---

### Post by Bucky Ball on 2014-11-07
Two things:

1/ You need clamav installed for anything to happen as clamtk is the GUI only, and;
2/ You need current antivirus definitions.

So, install clamav, open a terminal and run 'freshclam'. That will update the AV definitions (use it whenever you want to update them). It can take awhile. Try again and will/should work.

---

### Post by susja on 2014-11-07
that's great!
Thanks for explanation. Well  I installed a lot of packages and likely missed that one. Will do it Monday. Btw ... this PC is standalone I.e. It's not connected to network and the only goal for is to  check flash drives. Hence my question: how could I get latest virus definition and put it on that PC? I plan to do it weekly. 
Appreciate your response

---

### Post by deadflowr on 2014-11-07
ftr
you need to run freshclam as root
```
sudo freshclam
```
After the first time, freshclam should check for updates everytime you login, and then some.
(The default should be to check 24 times a day)

---

### Post by Bucky Ball on 2014-11-07
> **deadflowr said:**
> ftr
you need to run freshclam as root
```
sudo freshclam
```
After the first time, freshclam should check for updates everytime you login, and then some.
(The default should be to check 24 times a day)

Yes, sorry, as root.

@deadflowr: OP is not online on this computer so that command is not going to work with or without sudo. ;)

@OP: Not sure how you get the antivirus definitions downloaded to a USB stick to transfer to that machine. Imagine there's a way and you'll probably find it with a little research. Good luck and please share if you come up with anything. 

[THIS]("https://www.raymond.cc/blog/manually-update-antivirus-virus-definition-signatures-without-internet/") took a few seconds to find from [HERE]("https://duckduckgo.com/?q=get+clamav+av+definitions+no+internet"). Might give you some clues. ;)

---

### Post by susja on 2014-11-10
Folks,
thanks for reply BUT my PC is not on the network. Really I have to ask one who gave that flash drive how he get virus definition on it. 
Otherwise  I am stuck.

---

### Post by deadflowr on 2014-11-10
> **susja said:**
> Folks,
thanks for reply BUT my PC is not on the network. Really I have to ask one who gave that flash drive how he get virus definition on it. 
Otherwise  I am stuck.

It'll be a pain, but from what I've read you can do is this:
First go here
[http://www.clamav.net/download.html](http://www.clamav.net/download.html)
Under the Heading "Set Up FreshClam" there are 3 links for main.cvd, daily,cvd, and bytecode.cvd.
You need to download all 3 links.

Next, you need to copy the downloaded files into the directory folder /var/lib/clamav
To do so, you wil need to be root.
Since I am guessing that this will be done via a flash drive, it'll most likely be that the flash drive will be mounted in the directory /media.
my own /media directory holds sub-folders for users on my systems, so be wary of that.
The commands to copy would be:
```
sudo cp /media/possible-user-name-here/main.cvd /var/lib/clamav
```
repeat this replacing main.cvd for the other two names.

Unfortunately, though, it is unclear if anything else needs to done, but from what I gather this is all you need to do.
If anything, a re-run of the freshclam command, but I do not think that's needed.

Hope this helps.

---

