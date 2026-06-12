---
title: "RAZR V3xx and RAZR2 with Ubuntu?"
date: 2008-02-08
forum: General Help
---

### Post by Levander on 2008-02-08
I'm looking at switching phones and getting a RAZR V3xx.  So, I'm wanting to know how well they interoperate with Ubuntu.  I'm also kind of interested in the RAZR2 V9, so I'm interested in the same questions about it.

Has anyone used a V3xx to transfer music back and forth between it and a Gutsy system using Rhythmbox?  I probably will try Banshee soon, so I'm interested in using it with Banshee too.

I think the V3xx is a UMS phone.  So, I think it will just act like a USB hard drive, so Rhythmbox should be able to use it easily.  Can someone confirm this?

I think the V9 is an MTP phone though and I'll have to use libmtp to talk to it which doesn't support all devices very well.  Has anyone used a V9 to transfer music back and forth with a Gutsy system?

Then there's PIM stuff.  I'm mainly interested in contacts, calendar stuff is kind of interesting too.  I saw the opensync project, but they seem mostly interested in Nokia phones.  Has anyone tried a V3xx with opensync?  What about with the V9?

---

### Post by Levander on 2008-02-08
These are pretty popular phones.  No one's using them to putting music onto from Ubuntu?

---

### Post by brianwarner on 2008-02-10
Hi Levander,
Can't speak for the RAZR2 myself, but I just picked up a v3xx.  As long as your USB mode is set to "Mass Storage", the system will mount it as a normal disk and it will show up in Nautilus.

I haven't played around with it in Rhythmbox (other than opening it up and saying "nope, doesn't show up there automatically"), but since it does just appear as another disk it should be pretty straightforward.  I do know that getting just about anything onto the phone is much easier - just dump your mp3s, images, java apps, etc into the appropriate folder and go.  

This version of the RAZR software is much more graceful - and using your mp3s as ringtones is considerably easier (no more deleting and rebuilding the ringtone database a la the v3).

Hope this helps...
Brian

---

### Post by Levander on 2008-02-10
Have you actually used a RAZR with Ubuntu, or you're just speaking from experience with the UMS protocol?

Are there other settings on the V3xx besides UMS?  I thought it was an MTP only phone?

I'm pretty sure the RAZR2 is an MTP only phone.

---

### Post by leech on 2008-02-12
I can say that so far my luck with Hardy Heron and my Razr 2 has been more successful than using Windows XP.  It just works "Out of the box" with Rhythmbox.  Though I couldn't get it to work right on my Debian Sid Laptop, so not sure if it works with Gutsy.  The main differences I've seen, are that both Debian Sid and Gutsy run 0.11.2 and Hardy is at 0.11.4 but I noticed that Gutsy's Rhythmbox uses libmtp6 and the experimental version of Sid uses libmtp7.

Under Hardy Heron, it just pops up as "V8" then you can copy whatever MP3s over that you'd like.  And yes, the RAZR 2 V8 is an MTP Device.

Leech

---

### Post by Superslobberface on 2008-03-27
I use a motorola V3XX with Ubuntu.  I have a 2GB micro SD card in the phone.  I set the usb on the phone to Mass Storage Device and I can drag and drop files to the mobile/music directory on the phone.  If you want MP3's to show up as ring tones, they have to meet the following specifications...
[LIST=1]
[*]Less than 30 seconds long
[*]<=128kbps
[/LIST]

This is what I do to convert the songs:
[LIST]
[*]Open the MP3 in audacity
[*]Delete everything past 30 seconds
[*]Fade out the last 5 seconds with the "Fade Out" effect
[*]Select the whole track
[*]Normalize the track
[*]File->Export
[*]Select MP3 and select  the bitrate of 128kbps
[/LIST]
After you have the converted mp3, copy it to your /mobile/music directory on your phone.  It should show in your media finder and you can apply the song as a ring tone.

The exported files are around 460kb and sound great as a ring tone or alarm.

---

