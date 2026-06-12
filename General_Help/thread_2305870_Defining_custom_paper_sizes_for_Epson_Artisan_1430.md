---
title: "Defining custom paper sizes for Epson Artisan 1430"
date: 2015-12-09
forum: General Help
---

### Post by cscj01 on 2015-12-09
I am on Ubuntu 14.04.3 x64 and have an Epson Artisan 1430 printer with driver epson-inkjet-printer-201114w_1.0.0-1lsb3.2_amd64.  Cups shows a Custom setting for defining custom paper sizes.  However, if I choose this option, the printer will not print the document.  I get a flashing light on the Power switch which says the printer is busy, but if I check the print queue, the job shows a status of Stopped.  If I restart it, it goes back to Stopped.  Does anyone have this printer?  If so are you able to define and print custom size documents?  I tried the other Linux drivers Epson has for the 1430, epson-inkjet-printer-escpr_1.6.0-1lsb3.2_amd64 and epson-inkjet-printer-escpr_1.6.1-1lsb3.2_amd64, but they don't even offer the Custom sizes option.

I sent a message to Epson, but they are no help because I am using a Linux driver.  They don't seem to know anything about the Linux drivers.

---

### Post by Mike_Walsh on 2015-12-10
Hallo, cscj01.

It's a bit of a 'catch 22' situation with Epson, in regard to Linux drivers. The official position is that 'We don't do Linux drivers. Period.'

This is total garbage, if the real truth of the matter be known. Epson have been supplying Linux drivers for a long time. Originally, their Linux drivers were developed for them by a Japanese firm called Avasys. If people made enquiries about Linux drivers, Epson customer reps would then direct them to the Avasys site, where the driver for whatever would be available, after searching through the archives.

About 2 years ago, at the tail end of 2013, Avasys stopped development of printer drivers for Epson. They turned over the entire archive to Epson themselves, along with the necessary scripting, etc., to continue development of new drivers.....apparently it was a largely automated process.

But instead of responding to enquiries about Linux drivers in a positive fashion, what do Epson do? They **still **insist they 'don't do' Linux drivers, despite having the entire archive under their direct control. The onus is on the individual to look for them.....still very much the 'Windows model', I'm afraid. They **are** there; you just gotta hunt them up yourself.

A strange attitude to take, given that Epson are major members of the Linux Foundation..... As far as the drivers themselves are concerned, it's rather a case of 'pot luck'. Some give full functionality, some don't. My own SX218, fortunately, **is** fully supported.....but 'Custom Sizes', although present, is, like yours, non-functional. I only experimented with it once, and came to the conclusion that I didn't really need it anyway.


Regards,

Mike. ;)

---

### Post by cscj01 on 2015-12-10
Thanks for your response Mike.  Yes, I'm aware of their history and their seeming amnesia when it comes to Linux.  I too have had drivers from Avasys as well as their current drivers which they IEKO ATTACHED TO THE NAMES FOR SOME REASON.
seem to typically list with Seiko attached to their names.

I did get this thing to work, albeit in a convoluted way.  The following is how it worked:

[LIST=1]
[*]Created the document (merge template for envelopes) in LibreOffice Writer with the page size defined as the size of the envelopes;
[*]Did a mail merge from my MySQL database;
[*]Saved the merged documents as a single ODT file;
[*]When I selected File>Print, I left the document size in the driver as Letter;
[*]Because the Epson driver wanted to destroy my envelopes if I loaded them flap side to the right, I loaded them flap side to the left as they say to do when printing envelopes;
[*]The envelopes printed beautifully except for the fact that they were upside down wrt the back.
[/LIST]
I decided it really didn't make any difference if the flap was on the bottom on the back as long as the envelope was printed correctly on the face.  I wonder if I could use something like rotate 180 degrees, which is an option in the driver.  Maybe I'll try that the next time.  I'll leave this open until I do check the rotate option out.  BTW, the epson-inkjet-printer-201114w_1.0.0-1lsb3.2_amd64 driver is listed as full function, and there are a significant number of options available.  The other two are devoid of most everything except Paper (2 choices) and Orientation.  So they are essentially useless.

---

### Post by Mike_Walsh on 2015-12-10
Hallo again, cscj01.

Yes, they're a funny lot, Epson. And not 'funny (ha-ha)', neither. I can never quite work out if they're embarrassed to be seen supporting Linux, given that more and more serious organizations are increasingly adopting it...

The policy with regard to most of their equipment seems to be to provide **one** tailored to the machine in question, then a series of mostly generic ones which will allow the printer to work, albeit in a basic, restricted fashion. Why go for the 'basic' variety, when the 'tailored' one will allow the printer to perform as intended? Yet research shows that there are about a dozen, generic Linux drivers for nearly 600 machines over the last 20 or so years......which to me, at least, proves that the control logic hasn't changed **so** much during that time-frame.

My SX218 is an early, 'baby-brother' to the business-oriented WorkForce series.....which is why it will work, pretty much, with any WorkForce driver, since these are largely interchangeable **within **the series.

Thanks for the info, by the way. I mostly use mine for graphic design printouts, but it does have to cope with the occasional letter and envelopes. Custom sizing would have its uses for me, I will admit.


Regards,

Mike. ;)

---

### Post by cscj01 on 2015-12-11
Okay, I used the Rotate 180 degrees option in the driver, and everything worked as I had hoped.  So, if you want to print on a custom size envelope, just follow the steps below:

[LIST=1]
[*]Create the document (merge template for envelopes) in LibreOffice Writer with the page size defined as the size of the envelopes, Orientation = Portrait, and Format = User;
[*]Do a mail merge from your database (MySQL, LO Calc);
[*]Save the merged documents as a single ODT file;
[*]Load the envelopes as Epson says, flap to the left;
[*]Select File>Print>Properties and leave the information in the Paper tab as is;
[*]Select the Device tab, and turn Rotate 180 degrees on;
[*]Print your envelopes.
[/LIST]
Just a note here.  I did not try to load the feeder with more than one envelope at a time.  I also selected Print Pages with the page number so that the job consisted of one envelope each time.  The next time I try this, I'll try putting a stack of envelopes in the fed tray.  That will help a lot if the feed mechanism works as one would hope.

So with that bit of good news, I'll mark this thread as Solved.  You would think that Epson could figure this out, but maybe they're not as sharp as us'ns.

---

