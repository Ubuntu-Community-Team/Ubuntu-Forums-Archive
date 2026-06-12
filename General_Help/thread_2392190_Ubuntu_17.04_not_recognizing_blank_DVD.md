---
title: "Ubuntu 17.04 not recognizing blank DVD"
date: 2018-05-17
forum: General Help
---

### Post by jgwphd on 2018-05-17
I am running Ubuntu 17.04 on a HP-EliteBook-8460p (Intel® Core™ i5-2540M CPU @ 2.60GHz × 4) and was trying to burn an 18.04 image onto a DVD. When I insert a new blank disc (right from the store package) into my DVD drive it is not recognized. I get "No disc available" (grayed out) from Brasero. Xfburn also says drive is empty. Disc image writer and Startup disc creator won't find the blank DVD either. When I just insert a blank DVD into the drive it does nothing (a message used to pop up that said you have just inserted a blank DVD and what do you want to do ...or something to that effect). Also the file manager doesn't see the new blank DVD. I tried several new blank DVDs. Finally I installed K3b and it says "**No medium present** *hp-DVD-ROM DTSON*" I did notice that k3b will open the DVD tray when I select eject. I put an old ubuntu 9.10 cd with an image on it and it was recognized with message saying what do you want to do and was seen in the file manager. It is just the blank DVDs that seem to be a problem. 

I must be doing something wrong or have something set up wrong, Can anyone give me some direction or tell me what commands to use to investigate the status of the DVD drive so I can figure out why nothing happens when I put a blank DVD in it?  Thanks! 

Regards 
John

---

### Post by Buntu Bunny on 2018-05-17
Hello John, welcome to the forums. Ubuntu 17.04 reached end of life January 2018, so suggest a newer version.

---

### Post by mörgæs on 2018-05-18
Have you considered installing using a USB stick and not a DVD?

@Buntu Bunny, I have a feeling that original poster is aware of this and that he's trying to move on to 18.04.

---

### Post by jgwphd on 2018-05-18
Thanks for the replies. I am trying to get to 18.04. I have 18.04 on another machine and I can reproduce the problem with an 18.04 machine using an external CD/DVD drive which is a Samsung Ultra Thin DVD writer model SE-208. It says it will write DVD's and the "cd-drive" utility command says the same. But when I put in a blank DVD+R disc is does nothing on the 18.04 machine. Also K3b and it says "**No medium present** *TSSTcorp - CDDVDW SE-208GB*". I am trying to get an understanding of all the DVD choices and what actually works so when I go to the store and buy a drive it supports what I need. In this case I can't burn an image to a blank DVD, which is annoying. The output of cd-drive shows it reads and writes with the "Profile List Feature" which matches what is "on the box" the drive came in at the store. But the bottom statements of the cd-drive command leads me to believe doesn't write to DVD+R which contradicts the Profile List Feature statements. What is correct or am I interpreting it wrong. Or do I need to some kind of software for compatibility? The exact output of the "cd-drive" command  is copied and pasted next: 

```
Vendor                      : TSSTcorp
Model                       : CDDVDW SE-208GB 
Revision                    : TS00
Profile List Feature
    DVD-R - Double-Layer Sequential Recording
    DVD-R - Double-layer Jump Recording
    DVD+R Double Layer - DVD Recordable Double Layer
    DVD+R - DVD Recordable
    DVD+RW - DVD Rewritable
    Re-recordable DVD using Sequential Recording
    Re-recordable DVD using Restricted Overwrite
    Re-writable DVD
    Re-recordable DVD using Sequential recording
    Read only DVD
    CD-RW Re-writable Compact Disc capable
    Write once Compact Disc capable
    Read only Compact Disc capable

Core Feature

Morphing Feature
    Operational Change Request/Notification supported
    Synchronous GET EVENT/STATUS NOTIFICATION supported

Removable Medium Feature
    Tray type loading mechanism
    can eject the medium or magazine via the normal START/STOP command
    can be locked into the Logical Unit

Write Protect Feature

Random Readable Feature

Multi-Read Feature

CD Read Feature
    C2 Error pointers are supported
    CD-Text is supported

DVD Read Feature

Random Writable Feature

Incremental Streaming Writable Feature

Formattable Feature

Management Ability of the Logical Unit/media system to provide an apparently defect-free space. Feature

Restricted Overwrite Feature

DVD+RW Feature

DVD+R Feature

Rigid Restricted Overwrite Feature

CD Track at Once Feature

CD Mastering (Session at Once) Feature

DVD-R/RW Write Feature

Unknown code 33 Feature

CD-RW Media Write Support Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Hardware                                  : CD-ROM or DVD
Can eject                                 : Yes
Can close tray                            : Yes
Can disable manual eject                  : Yes
Can select juke-box disc                  : No

Can set drive speed                       : No
Can read multiple sessions (e.g. PhotoCD) : Yes
Can hard reset device                     : Yes

Reading....
  Can read Mode 2 Form 1                  : Yes
  Can read Mode 2 Form 2                  : Yes
  Can read (S)VCD (i.e. Mode 2 Form 1/2)  : Yes
  Can read C2 Errors                      : Yes
  Can read IRSC                           : Yes
  Can read Media Channel Number (or UPC)  : Yes
  Can play audio                          : Yes
  Can read CD-DA                          : Yes
  Can read CD-R                           : Yes
  Can read CD-RW                          : Yes
  Can read DVD-ROM                        : Yes

Writing....
  Can write CD-RW                         : Yes
  Can write DVD-R                         : Yes
  Can write DVD-RAM                       : Yes
  Can write DVD-RW                        : No
  Can write DVD+RW                        : No
```

Thanks for the help in interpreting this information. I just want to be able to go to a store and buy what I need without having to take it home and try it out and use something like cd-drive command to find out if it really does what I want. This situation seems so odd. I must be missing something. Thanks again for any assistance. Best Regards John

---

### Post by mörgæs on 2018-05-18
Still waiting for what the answer to my question might be...

---

### Post by jgwphd on 2018-05-18
@[**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=939075")  Yes, I can use a bootable USB stick for 18.04 and I am now successfully using 18.04. I appreciate your help, but using a USB stick doesn't answer my  general DVD question which is: I am trying to get an understanding of all the  DVD choices and what  actually works with Ubuntu 18.04 so when I go to the store and buy a  drive it supports  what I need. In this case I can't burn an image to a  blank DVD with 18.04 and Startup Disc creator, Xfburn, Brasero and K3B using the Samsung Ultra Thin DVD Writer (model SE-208). The problem description, hardware and output of the "cd-drive" command are shown in my previous post. I just want to be able to go to a store and buy a CD/DVD writer with what I need without  having to take it home and try it out and use something like cd-drive  command to find out if it really does what I want. This situation seems  so odd. I must be missing something. Is there a software issue? Thanks again for any assistance.  Best Regards John

---

### Post by jgwphd on 2018-05-18
A picture of the box is attached: [ATTACH=CONFIG]279738[/ATTACH]

---

### Post by mc4man on 2018-05-18
I think the bottom of that cd-drive command is wrong, see the same here & I can write both dvd+r and dvd+rw media.
If this was only on 1 drive I'd suspect the drive, 2 drives I'd first suspect the media.
What brand of dvd media?

---

### Post by jgwphd on 2018-05-18
The media I am using is a Sony AccuCORE DVD+R stack of 100 blank DVDs that I have had for probably 10 years. I thought that the media might be a problem and tried them on another Ubuntu machine (A Dell Vostro 1014 laptop with a built in CD/DVD drive) and they burned two 18.04 images on two blank disc's fine yesterday. I am not sure what to think, maybe the opposite, the bottom of the cd-drive command is correct and the top is the problem because I can not see any blank disc in the Samsung external drive in any of my three Ubuntu machines (17.04, 17.10 and 18.04). I am hoping someone can tell me how to determine "exactly" what the drive capability is. I did attach a jpg picture of the DVD box read/write capabilities in my prior post. I interpret the picture of the box capability advertising that it should detect a blank DVD+R disc. Is that your interpretation? But,it seems that Ubuntu 18.04 will not detect a blank disc in this drive. A friend of mine has the identical drive and I asked him to check and he has the exact same problem with blank DVD's (he is using 17.10 and has different brand of blank DVDs). How do I determine exactly what the problem is? Is there some kind of software needed for this drive for Ubuntu?

---

### Post by mc4man on 2018-05-18
That drive certainly supports writing dvd+r media, all dvd writers from last decade+ do. So maybe both drives are done..
Can't see how this would be a Ubuntu issue, nor does one need anything additional installed to recognize dvd media, if you had access to a windows machine you could d. check.

If you go buy a new usb dvd writer then it will absolutely support dvd+r, if dual layer matters then you'd need to look for that on packaging.
(- though  most external drives  offer full dvd media support.

Here on my lenovo the dvd drive stopped working on dvd media some time ago, grabbed a usb LG drive for 30 bucks from BB, works fine on all dvd media. May not have the greatest burn quality compared to the plextors or benq's I had yrs. ago but I no longer need 'archivial' quality dvd burns.

---

### Post by jgwphd on 2018-05-18
Thanks for the reply. You are suggesting that if I go to the store and buy another DVD writer, it will work fine. Is that true?  I find it extremely odd that we have two bad drives (is this a drive age problem? ...or a manufacturer quality problem? ...both drives are at least 5 years old, probably closer to 8+ years old. This brings up another question. Do these drives have some kind of "expiration date" where they are unreliable for burning new images on blank DVD's after some time frame (it seems like mc4man has had DVD drive problems on his Lenovo too)? The drives do read data from other already recorded DVDs and music CDs without any problems. Is the write function on the drive the "weakest" part of a DVD writer?

---

### Post by mc4man on 2018-05-19
The lifetime of dvd drives could vary from manufacturer, models, & the individual drive itself.
Internal desktop pc optical drives would generally  be of much higher quality & performance than any other forms & could last/perform well for quite some time.
Laptop internal drives are generally pretty cheap,  5 years without issue would be fortuitous.
I'd put external usb drives somewhere in between depending on quality, design & care. Probably the ultra slim designs are similar to laptop ones.

---

### Post by deepsage on 2018-06-03
I have the same problem.  I just updated from 16 to 18 and while the DVD is recognized as blank (use the same machine under 16 to burn the 18.04 image to upgrade), the image writer shows it grayed out.  I ended up burning the some other versions of Ubuntu (L, X and Mate) images on an old windows 7 machine to try out.

---

### Post by wildmanne39 on 2018-06-03
Hello deepsage, if you need help please start your own thread you are more likely to receive help that way then posting in a solved thread.

Thanks

---

