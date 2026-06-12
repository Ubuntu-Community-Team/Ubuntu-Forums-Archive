---
title: "Do you have the driver for Lexmark Z600 Z615 and Dell Photo Printer 720"
date: 2007-05-20
forum: General Help
---

### Post by wulfhound on 2007-05-20
It is no longer on the server at Lexmark.  I really would like to have the file, if anyone has it to email to me or somehow get to me. Thanks,

L

---

### Post by wulfhound on 2007-05-20
> **sandaili said:**
> It is no longer on the server at Lexmark.  I really would like to have the file, if anyone has it to email to me or somehow get to me. Thanks,

L

Anyone? LOL! I can't afford a new printer. I know some people use it. Hopefully someone stumbles across this post.

L

---

### Post by rkh on 2007-05-20
Have you tried this one?

[http://www.downloaddelivery.com/en/cpddrivers/390.html](http://www.downloaddelivery.com/en/cpddrivers/390.html)


its for the z604, but you might have luck with it. 

 Since it seems to be available as an RPM, you'll have to convert it to a Deb using alien -I don't recall how to do that off hand,  just google it-its not that hard.

I used to have a dell 720 working with Mepis. Unfortunately, when I switched to Ubuntu I did a clean install & never bothered to install the 720, so I can't send you whatever driver it was that I used-it might have been this one.

 Best of luck!

---

### Post by wulfhound on 2007-05-21
I'll try it. Here's the response I got from Lexmark:

"Thanks,

l 
Subject: Re:Lexmark Technical Support (Req# DD3082030)
From: [email]support@lexmark.com[/email]
To: XXXXXXXX
Message-ID: <OFF79DD9E5.67BCC7F0-ON852572E1.001552DB-852572E1.001552DB@lexmark.com>
Date: Sat, 19 May 2007 23:52:54 -0400
X-MIMETrack: Serialize by Router on Lextra03/LExtranet(5012HF718 | May 06, 2004) at 05/19/2007
 11:52:55 PM
MIME-Version: 1.0
Content-type: text/plain; charset=us-ascii


Dear s,

Thank you for contacting us regarding this matter. I appreciate the
opportunity to assist you, and I hope my suggestions will provide a
suitable response applicable to this situation.

Currently our only inkjet printers that have Linux support are the Lexmark
3000, the 1020 Business Edition (model 4078-001), the 4079 Plus and the
Optra Color 40/45 with Postscript Level 2 or PCL 5 emulation. As of
November 1st we now have support and drivers available for the LINUX OS on
the Z32 (Z22 if you have both cartridges installed) and the Z52.

Supported Linux versions:

Red Hat 6.1+
SuSe 6.3+
Mandrake 7.0+


Minimum system requirements:

200 MHz
32 MB RAM
20 MB HD


Z32 (Z22) Parallel support only
Z52 Parallel and USB support


All of our other inkjet printers are host based printers that were
developed for Windows 3.1 and Windows 95/98, NT/2000, and MacIntosh in some
cases. We appreciate your comments and customer feedback helps in
determining the interest level of our Lexmark customers with the various
operating systems. Although we do not have a solution for you at this time,
we will pass your comments on to our marketing department. They are
constantly evaluating our product line and input such as yours is extremely
valuable.

If you have any more questions or concerns, please contact me at your
convenience and I will be happy to assist you. (If I am not available,
another representative will reply to you as soon as possible.) To respond,
please select "Reply" in your e-mail software, and be sure that the past
e-mail is included in this reply.

[AOL Users: In order to include the previous e-mail, you must highlight it
with your mouse when you are replying.]

If you need to reply, please be sure to include in your message all
information from prior e-mail messages & replies. If your e-mail client
automatically deletes prior e-mail thread information, it will cause a
delay while we look up your support history. If this is the case you may
want to save the old e-mails as attachments and attach them to the current
e-mail."

What a bunch of crap...

L

---

### Post by gtmaneki on 2007-05-21
I just finished web-chatting with a helpful Lexmark tech.  The z600 printer driver is located [here]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=22%209:1:0:389:0:0&fileID=1151&searchLang=en&searchLang=en&os_group=Redhat").

---

### Post by wulfhound on 2007-05-21
> **gtmaneki said:**
> I just finished web-chatting with a helpful Lexmark tech.  The z600 printer driver is located [here]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=22%209:1:0:389:0:0&fileID=1151&searchLang=en&searchLang=en&os_group=Redhat").

OMG! Thank you so very much. I owe you a favor. 

I guess it goes to show you some people in tech support can't be counted on! :( 

Thank you again,

L:D

---

### Post by linux4africa on 2007-05-23
I followed the instructions on [http://www.thorubio.org/cms/space/Linux/Dell+Photo+Printer+720](http://www.thorubio.org/cms/space/Linux/Dell+Photo+Printer+720)

To get the rpm I edited the file ./z600cups-1.0-1.gz.sh and changed the list option to extract the tar files. Changed "tar tvf" to "tar xvf" and then ran
 sh ./z600cups-1.0-1.gz.sh -list

Then you will have the rpm files.

After converting the rpm to dep files the driver was in:
/usr/share/cups/model/Lexmark-Z600-lxz600cj-cups2.ppd.gz

Use this can be added as a driver from the System->Administration->Printing menu.
After installing the driver, the printer is listed under Lexmark, Z6001-1.

---

### Post by BHSPitMonkey on 2007-07-15
I can't seem to edit that z600cups-1.0-1.gz.sh, as it's some kind of binary format.

EDIT:  Never mind, it worked in nano.  The problem was the binary that was embedded into the script.

EDIT:  Good, I made the edit in nano.  And it only got through extracting the first file before it went kaput on me:

```

$ sh ./z600cups-1.0-1.gz.sh -listTarget directory: installer
tail: Warning: "+number" syntax is deprecated, please use "-n +number"
globals.tcl
tar: Skipping to next header

gzip: stdin: invalid compressed data--format violated
tar: Error exit delayed from previous errors

```

---

