---
title: "Unable to mount blank DVD-R"
date: 2012-12-07
forum: General Help
---

### Post by brantpadams on 2012-12-07
I'm having an error pop up when trying to mount a DVD-R. 

The error reads: UNABLE TO MOUNT BLANK DVD-R DISC. Location is already mounted.

I'm trying to burn an iso to my DVD-R but I'm unable to because of this error. Haven't found a fix yet and I was hoping for some help. 

I just recently upgraded to 12.10 and I'm running on a Dell Inspiron-1525 laptop. Thanks.

---

### Post by leclerc65 on 2012-12-07
Install k3b, very reliable.
Before this I had to use Imgburn in Windows.
I don't like Kubuntu but some of the K programs are quite good like k3b, kTorrent ...

---

### Post by brantpadams on 2012-12-09
Thanks for the suggestion. I installed k3b, but I'm not sure how to use it to burn an iso image to a disc. I'm still having the issue with the "medium already being mounted" problem. 

I've been using Furius iso mount and it's served my purposes well enough, but because of this issue the program doesn't read my blank disc.

---

### Post by brantpadams on 2012-12-17
In 12.10, any time I put a DVD-R in my disc drive I'm presented with this prompt:
[IMG]http://i47.tinypic.com/2vcg7px.png

I'm trying to mount an .iso image to a disc with Furius ISO mount, but the disc drive is not recognized in the program and I have to assume it's because of this issue. I've tried watching standard DVDs and haven't had a problem with them, so it seems to only be problematic with DVD-R. 

I'd very much appreciate any help on this issue. Please let me know if any more info is needed.

---

### Post by LeadFingers on 2012-12-18
I would appreciate an answer to this as well

While I can mount blank DVD-R, Can't burn them for nothing.
What's up with that??

---

### Post by LeadFingers on 2012-12-18
K3b doesn't work with DVD-R for me.
It'll burn DVD+R just fine, but DVD-R gives an Error message saying it might be the media.

If it was just K3b I could live with that but I can't find a single burning app or plugin that likes DVD-R.

---

### Post by overdrank on 2012-12-18
Threads merged.

---

### Post by #1udancqSHv% on 2012-12-18
> **brantpadams said:**
> I'm having an error pop up when trying to mount a DVD-R. 

The error reads: UNABLE TO MOUNT BLANK DVD-R DISC. Location is already mounted.

I'm trying to burn an iso to my DVD-R but I'm unable to because of this error. Haven't found a fix yet and I was hoping for some help. 

I just recently upgraded to 12.10 and I'm running on a Dell Inspiron-1525 laptop. Thanks.
Hi brantpadams,
I'd been getting the same error message when inserting a blank DVD-R, in Linux Mint 14 (based on 12.10).

The autorun dialogue came up too, asking if I want to open 'CD/DVD Creator' - I just clicked Cancel, and went to right-click the ISO and burn using Brasero, k3b or Xfburn. None of these worked.

What _**has**_ worked since is using the Autorun dialogue to open Brasero, then opening the ISO within the application, using Project>Open to open the ISO as a new project. The DVD-R then burns fine. Not ideal, and not as easy as right-clicking the ISO, but a workaround until we can work out how to fix this...

Hope this works for you too! :)

---

### Post by brantpadams on 2012-12-18
Hi guys. 

Thanks for the input. What I've found so far is that the autorun script will always pop up saying that it's already mounted, but I opened up Furius and inserted the disc when I arrived to the burn command box. The program then recognized the disc and I was able to burn successfully. I used to read it regardless, but this seems to be a fix of sorts. 

I'm still not sure how to get rid of the dialog box, but as long I know I can still burn then it shouldn't be a huge issue. Thanks for all the help.

---

### Post by farmercyst on 2013-01-20
> **jfj33 said:**
> Hi brantpadams,
I'd been getting the same error message when inserting a blank DVD-R, in Linux Mint 14 (based on 12.10).

The autorun dialogue came up too, asking if I want to open 'CD/DVD Creator' - I just clicked Cancel, and went to right-click the ISO and burn using Brasero, k3b or Xfburn. None of these worked.

What _**has**_ worked since is using the Autorun dialogue to open Brasero, then opening the ISO within the application, using Project>Open to open the ISO as a new project. The DVD-R then burns fine. Not ideal, and not as easy as right-clicking the ISO, but a workaround until we can work out how to fix this...

Hope this works for you too! :)

Thanks for your suggestion.  It worked for me too!

---

### Post by comacaptain on 2013-01-25
Hello folks I have also had this issue plague me to no avail. I'm desperate for a solution. Here is a link to my own thread [http://tinyurl.com/bclfrrq](http://tinyurl.com/bclfrrq). I have tried your solution but it failed to work can anyone please hyelp me.

---

### Post by comacaptain on 2013-01-25
Yet again I beseech the Ubuntu Communitty to notice and acknowledge the obvious continued bug that shows everytime I attempt in anyway to use a DVD-R, CD, or USB Stick to transfer data to any media. This is the error message I get everytime I place a DVD-R, CD, or USB Stick in my computer.

"Unable to mount Blank DVD-R Disc"
Location is already mounted


I was able to use my DVD Drive in all ways until upgrading to Ubuntu 12.10 then BLAM! nothing no burning of any sort after that. This has occurred in previous Distro's and yet the Ubuntu Communitty ignores it as a whole. I'm a huge advocate of Linux and Ubuntu but I'm not a programmer I need your help folks.

---

### Post by ken78724 on 2013-01-25
Glad to see error is +/- worked out

Am curious if going to 12.10 has been worth it? Have the bugs been worked thru?  ):P

---

### Post by jgdsuresh on 2013-04-15
With the DVR-R in the drive, i rebooted the system.
After rebooting, opened Bracero.
From the main menu selcted "burn image to DVD..."
Selected the ISO image.. and "Burn"
It just worked...

---

### Post by emmbio on 2013-06-10
thanks it worked for me too

---

