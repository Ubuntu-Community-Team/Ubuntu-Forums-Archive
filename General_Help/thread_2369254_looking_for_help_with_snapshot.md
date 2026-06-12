---
title: "looking for help with snapshot"
date: 2017-08-20
forum: General Help
---

### Post by edstevens on 2017-08-20
I know this isn't an Ubunu question, per se, but I can't seem to find anywhere else to ask.  If someone can point me to a more appropriate forum, I'll be glad to take my question there.

The specific problem is that after I've taken a snapshot (say of an application window) and edited it, I save it to clipboard, then try to paste the image into a Libre Office document, but that just returns the message, "requested clipboard format is not available."

---

### Post by TheFu on 2017-08-20
[https://help.libreoffice.org/Common/Inserting_Pictures](https://help.libreoffice.org/Common/Inserting_Pictures) ??

I initially came here to help with LVM snapshots. ;)  [https://www.howtoforge.com/linux_lvm_snapshots](https://www.howtoforge.com/linux_lvm_snapshots) something like that.

---

### Post by gordintoronto on 2017-08-20
Save it as a file.

---

### Post by edstevens on 2017-08-21
For the earlier responders  - after reading my opening post and seeing the nature of the responses, I realize that when I said "snapshot" I was working on too little coffee.  I was referring to the screenshot program "shutter', which appears from all of the reviews to be the primo screenshot program for linux.  

As for the idea of saving the snapshot as a file, that would work, but even Windows programs don't require those extra steps.  

Just to clarify a bit more, now that I have sorted out the "shutter" vs. "snapshot" mistake . . . I've got to believe what I'm doing is possible, but I'm not sure if I'm wrong on the 'shutter' (copy to clipboard) or the Libre Write end (paste from clipboard).  I tend to believe its on the 'copy to clipboard' end of things, but in spite of all of the rave reviews for 'shutter', there is really a dearth of actual help available on it.  It even lacks a 'help' item on its own menu system.  Even the 'help and FAQ' at [http://shutter-project.org/faq-help/man-page/](http://shutter-project.org/faq-help/man-page/) is devoid of any help at all.

---

### Post by gordintoronto on 2017-08-21
I've created many screenshots, some of which have been published in Full Circle Magazine.

I had never heard of Shutter. Every version of Ubuntu (which one?) includes a screen capture program "out of the box." I don't find it terribly onerous to save to a file and import that into Libre Office.

If you run GIMP (might need to install it) you should be able to paste from the clipboard, if it contains an image. I've used this feature many times.

---

### Post by vasa1 on 2017-08-21
> **edstevens said:**
> For the earlier responders  - after reading my opening post and seeing the nature of the responses, I realize that when I said "snapshot" I was working on too little coffee.  I was referring to the screenshot program "shutter', which appears from all of the reviews to be the primo screenshot program for linux.  

As for the idea of saving the snapshot as a file, that would work, but even Windows programs don't require those extra steps.  

Just to clarify a bit more, now that I have sorted out the "shutter" vs. "snapshot" mistake . . . I've got to believe what I'm doing is possible, but I'm not sure if I'm wrong on the 'shutter' (copy to clipboard) or the Libre Write end (paste from clipboard).  I tend to believe its on the 'copy to clipboard' end of things, but in spite of all of the rave reviews for 'shutter', there is really a dearth of actual help available on it.  It even lacks a 'help' item on its own menu system.  Even the 'help and FAQ' at [http://shutter-project.org/faq-help/man-page/](http://shutter-project.org/faq-help/man-page/) is devoid of any help at all.
I'm sure the developers would love to accept your assistance in fixing whatever issues you may have. This forum is run by volunteers who are users just like you and has nothing to do with developing Shutter or LibreOffice and their help/FAQs.

---

### Post by edstevens on 2017-08-22
> **vasa1 said:**
> I'm sure the developers would love to accept your assistance in fixing whatever issues you may have. This forum is run by volunteers who are users just like you and has nothing to do with developing Shutter or LibreOffice and their help/FAQs.

I realize the forum is just other users like myself.  I wasn't looking for any "inside" info or bug reporting.  I just thought that, just perhaps, someone here might be more familiar with the use of the tools involved and be able to ask some focused questions to point out something I might be doing wrong.

---

### Post by edstevens on 2017-08-22
> **gordintoronto said:**
> 
I had never heard of Shutter. 

Seriously?  (No sarcasm intended, seriously!) When I started googling 'screenshot progams for linux'  "shutter" is the name that just kept coming up over and over again.


> Every version of Ubuntu (which one?) includes a screen capture program "out of the box." I don't find it terribly onerous to save to a file and import that into Libre Office.

Perhaps not "particularly onerous", but compared to 3 mouse clicks - one to save the edited image to the clipboard, one to switch windows to the receiving app, and one to paste.  Yeah, I'd prefer not to have to work through the dialogs of 'save as' and 'insert from'.

> If you run GIMP (might need to install it) you should be able to paste from the clipboard, if it contains an image. I've used this feature many times.
By no means am I wedded to 'shutter'.  I'm only there because when I googled for screenshot programs that was the name that kept coming up over and over again.  Multiple review sites had it at the top of their lists.

Perhaps I should redirect and ask this:

What screenshot programs do you like for Ubuntu?  On the Windows platform I've used SnagIt and find it meets my expectations very well.  Able to capture by window or by selected region, good editing tools, and one-click 'save to clipboard'.

---

### Post by TheFu on 2017-08-22
> **edstevens said:**
> What screenshot programs do you like for Ubuntu?

I've been using ImageMagick tools for about a decade.
```

import(1)                   General Commands Manual                  import(1)

NAME
       import  -  saves any visible window on an X server and outputs it as an
       image file. You can capture a single window, the entire screen, or  any
       rectangular portion of the screen.
```

---

### Post by gordintoronto on 2017-08-22
> **edstevens said:**
> Perhaps not "particularly onerous", but compared to 3 mouse clicks - one to save the edited image to the clipboard, one to switch windows to the receiving app, and one to paste.  Yeah, I'd prefer not to have to work through the dialogs of 'save as' and 'insert from'.

Perhaps I should redirect and ask this:

What screenshot programs do you like for Ubuntu?  On the Windows platform I've used SnagIt and find it meets my expectations very well.  Able to capture by window or by selected region, good editing tools, and one-click 'save to clipboard'.

I have never thought about what screenshot program I was using. I am currently running Xubuntu 17.04, and it turns out that the included screen capture program is xfce4-screenshooter,  but it calls itself Screenshot. It offers a few options, including "save" and "copy to the clipboard". "Save" is one click, and that is what I have always used.

Other members of the Ubuntu family include other screen capture programs. Some of them are more sophisticated. In any case, I have never installed a screen capture program.

One of the reasons I might be file-oriented is that I sometimes send screenshots as email attachments. Oh, and insert them in Google Docs.

---

### Post by vasa1 on 2017-08-22
One other point: the clipboard issue in Linux appears to be a bit complex and LibreOffice, previously, and maybe even now, had "issues" with clipboard contents. IIRC, LibreOffice's move to gtk3 was supposed to have fixed these issues, but I'm not sure.

---

