---
title: "How to live with Windows, Ubuntu and a  smartphone without loosing your mind!"
date: 2007-11-24
forum: General Help
---

### Post by chimere32 on 2007-11-24
My windows mobile smartphone is not compatible with Ubuntu... I tried but it doesn't work.  Now, I want to leave the Microsoft world but Outlook and updating my smartphone were the only things forcing me to stay with windows.  Synchronizing data between Outlook / Linux and a smartphone is not something easy but I've found a nice compromise.

The challenge =  allow info to circulate easely / automatically between 2 non compatible system  Linux(--)windows mobile smartphone

Here's how I've done it...  Linux (--) Thunderbird/Lightning (--) Gmail/Google Calendar (--) Plaxo (--) Outlook (---) smartphone

In detail: 

Create a fat32 shared partition between xp & Linux
Automatically mount partition: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

For e-mail :  Use Thunderbird and install cross-platform with shared partition.
[http://3dgpu.com/forums/index.php?showtopic=4953&pid=55355&st=0&#entry55355](http://3dgpu.com/forums/index.php?showtopic=4953&pid=55355&st=0&#entry55355)

For scheduling : Use Lightning, a Thunderbird plugin and connect via "Provider for google calendar" to google Calendar .

Get a free Plaxo.com account.  Install Plaxo plugin for outlook.
 
Now, with this setup, you can live free for 95% of the time. You only need to boot in windows to update your smartphone. I do it 2x/week.

Your linux schedule information will be flowing from Lightning to Google Calendar and Google Calendar will be in sync with Outlook via a free plaxo plugin.

---

### Post by Naija on 2007-11-24
Thanks for the info. I've been tethered to Windows and my smartphone was one of the reasons why. I will try this and see how it goes.

---

### Post by seatowngrrl on 2008-01-16
I started doing this a while back, but could never explain it as elegantly as you have put it.  I am now having problems with my plaxo extension on my linux installation.  I probably just need to update something.  

But yes.  Once you initially have the whole set up set up it works pretty well.  

Although sometimes when I add a new device or sync a machine I havn't synced in a while I somehow loose some information.  Oh well I will get the hang of it soon.  

Thanks for the post.

---

### Post by Vadi on 2008-01-16
Could someone elaborate a bit on this? I don't have a smartphone myself, but would like to write this howto in the ubuntu help files (help.ubuntu.com/community).

First off, if you already have windows installed on another patrition, doesn't Ubuntu already mount it automatically?

So then you setup thunderbird to work across patritions, okay. With some plugin, you connect it to google, and then.. skip a link, we get plaxo for outlook. How exactly does plaxo connect with google?

---

