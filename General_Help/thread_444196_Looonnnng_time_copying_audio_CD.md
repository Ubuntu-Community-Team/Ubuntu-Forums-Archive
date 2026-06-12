---
title: "Looonnnng time copying audio CD?"
date: 2007-05-15
forum: General Help
---

### Post by andrew.46 on 2007-05-15
Hi,

 I have just installed a new DVD Burner: an LG GSA-H42N. Wrestled with playing DVDs with the default tools of Feisty Fawn (and eventually made it all work with Totem-Xine) but I am now in the process of copying an audio disk to the drive and back onto a blank CD.

 The copying to disk has taken 30 minutes so far and I am only half-way!! This is the same either using the built in burning or with Gnome Baker. Can anybody hazard a guess as to what I am doing wrong?

            Thanks,

               Andrew

PS I really think that if Ubuntu wishes to hit the main stream users will expect to be able to play Commercial DVDs 'out of the box'.

---

### Post by 3rdalbum on 2007-05-15
> **andrew.46 said:**
> Hi,
PS I really think that if Ubuntu wishes to hit the main stream users will expect to be able to play Commercial DVDs 'out of the box'.

Please put your mailing address onto your Launchpad page, so Canonical knows where to send the bill for the MPEG and CSS licensing fees for all the Ubuntu users.

As for your problem, what is the data rate like for CDs and DVDs that are not audio?

---

### Post by andrew.46 on 2007-05-15
Hi,

 Thanks for your prompt reply:

> **3rdalbum said:**
> Please put your mailing address onto your Launchpad page, so Canonical knows where to send the bill for the MPEG and CSS licensing fees for all the Ubuntu users.

As for your problem, what is the data rate like for CDs and DVDs that are not audio?

 But seriously, if Dell is going to have DVD drives in its selected computers with Ubuntu pre-installed can you imagine the fuss when movies do not play?

 I am not sure how to estimate the transfer speed of a drive but using Nautilus I transferred a 73 meg file to the HDD is 18 seconds. Is there bench-marking software that would give a more objective test?

 BTW the copied CD was a  frisbee anyway:confused: 

                    Andrew

---

### Post by andrew.46 on 2007-05-15
Hi,

 Below is some of the output from GnomeBaker when creating yet another frisbee:


12 (Cannot allocate memory), read_g1 scsi sendcmd: no error
CDB:  28 00 00 00 17 80 00 00 80 00
status: 0x0 (GOOD STATUS)
cmd finished after 0.000s timeout 40s
readom: Cannot allocate memory. Cannot read source disk
readom: Retrying from sector 6016.
...............................................................................................................................................................................................................................................................Errno: 12 (Cannot allocate memory), read_g1 scsi sendcmd: no error
CDB:  28 00 00 00 18 80 00 00 80 00
status: 0x0 (GOOD STATUS)
cmd finished after 0.000s timeout 40s
readom: Cannot allocate memory. Cannot read source disk
readom: Retrying from sector 6272.
................................................................................................................................Errno: 12 (Cannot allocate memory), read_g1 scsi sendcmd: no error
CDB:  28 00 00 00 19 00 00 00 80 00
status: 0x0 (GOOD STATUS)
cmd finished after 0.000s timeout 40s
readom: Cannot allocate memory. Cannot read source disk
readom: Retrying from sector 6400.

 This continues for some time retrying different sectors. Any thoughts?

                     Andrew

---

### Post by andrew.46 on 2007-05-17
Hi,

 In an interesting development I installed windows XP (shudder!!!!!) and burning was fine. I then wiped the disk and installed Xubuntu 6.06 and Gnomenaker and burnt a copy of an audio CD slowly but with no problems.

 Only used Xubuntu because I had it on the shelf, I plan to download the iso and install Ubuntu 6.06 and stick with that. I have a profound suspicion that Feisty + my burner + whichever kernel goes with it do not produce copies of Audio CDs.

 Guess if I regress I can also use Devede which is currently broken in Feisty :)

                  Andrew

 PS For the record the succesful audio cd was Pink Floyd 'Shine on you crazy diamond'!!!

---

