---
title: "LibreOffice writer problem"
date: 2020-01-21
forum: General Help
---

### Post by lesliek2 on 2020-01-21
I posted about my problem at Ask LibreOffice, but got no substantive response, so I'm trying here, given the seriousness for me of my problem.

Background: I've uploaded over thirty papers to the Social Science Research Network in the past decade. After uploading them, I keep editing them when I get new information. All papers were created using various versions of Ubuntu and either OpenOffice or, later, Libreoffice writer. Right now, I'm using Ubuntu 16.04 and LibreOffice 6.2.8.2. The papers have all been saved in .doc format. Many are lengthy and contain many footnotes and images.

Current problem: I'm trying to edit one of my documents. It's about twenty-five pages long, with about fifty footnotes, though no images. When working through the document, I came to a lengthy footnote I wanted to edit. When I tried to save after completing the edit of the footnote, writer froze and I had to force quit to end the situation. I tried numerous times, always with the same result. I found suggestions to delete my profile and to uninstall LO and reinstall it. I did both, one after the other. No effect. Writer froze again after retyping the footnote and attempting to save. Then I found suggestions about increasing certain memory settings: totalcachesize and objectcachesize. Did that. No effect.

I don't know what to try now. I'm afraid that I may have lost the ability to edit other papers of mine as well.

I'd be very grateful for any suggestions.

---

### Post by sdsurfer on 2020-01-21
May not be helpful, but worth a try. Open a terminal and test tail /var/log/syslog. This will ensure you can read the log (you may need to sudo)

Then move the terminal where you can see it while you open the program. Execute

```
tail -f /var/log/syslog
```

This follows the file as it changes. CTRL + C will exit it. For the moment leave it open, you want to see if anything gets added.

In your Writer window attempt the action that locks it up, and watch the terminal window. Does it addd anything or give you output?

I haven't looked but there may be information in crash logs as well, you'd have to do a search to see if that leads anywhere.

---

### Post by webaake on 2020-01-21
If you haven't tried it already you could try opening the document from commandline in a terminal. Like so;

libreoffice --writer  your_file.doc

The messages in the terminal can give more clues to what is wrong. There will probably be some warnings like "(soffice:19562): Gtk-WARNING **...." But those can be ignored for your problem.

Another thing you can try is to convert the document to .odt also in the terminal (with a backup first). Like so;

cp your.doc yournew.doc
soffice --headless --convert-to odt --outdir documents/ your.doc

You can then hopefully edit it and then resave it as .doc again.

Good Luck!

---

### Post by lesliek2 on 2020-01-21
Thanks for the reply, webaake.

I opened the document from the command line, as you suggested. I got only this when I did: "Warning: failed to read path from javaldx". I assume that, as you say, that warning can be ignored.

I'll now try your second suggestion.

---

### Post by lesliek2 on 2020-01-21
webaake, when I tried to run the second command you suggested, I got the following message: "The program 'soffice' is currently not installed. You can install it by typing: sudo apt install libreoffice-common".

Can this be a problem caused by the fact that I have LibreOffice 6.2.8.2 installed and there's been some name changing between versions?

---

### Post by webaake on 2020-01-21
Yes, try that; 

sudo apt install libreoffice-common

There might some libreoffice "helper" files missing. And then you can try converting from the terminal again.

The first error message about "javadlx" could also be a problem. It means that libreoffice doesn't see av Java runtime installation on your system. But I don't think that's the primary problem (but it might be..)

---

### Post by lesliek2 on 2020-01-21
webaake, not being able to follow your second suggestion in terms, I opened my unedited .doc file in writer in the usual way, saved it as an .odt file, edited the footnote in the .odt file and saved the file in .odt without difficulty. Since I upload my papers to the SSRN in .pdf format, I assume that I can now convert the .odt file to a .pdf file just like I've always converted my .doc file to .pdfs.

Before I do that, however, I'll have to go through the edited .odt file to make sure that the switch from .doc to .odt didn't cause formatting difficulties. Fingers crossed.

As you obviously use LibreOffice, can I ask: do you save all your word processing documents in .odt format? Should I be doing that for the future instead of saving them in .doc format? Can it be that my current problem is related to some defect in writer's ability to save in the .doc format?

---

### Post by lesliek2 on 2020-01-21
Thanks for the reply, sdsurfer. Simultaneously with your suggestion, webaake put forward some suggestions. Since I understood them better than I understood yours (I'm not much at these technical things!), I tried his/hers first. It seems to have got me an edited saved document, though in .odt format, not .doc format. I'm now going to check the document produced, to see that it's satisfactory. When I've finished that exercise, I'll come back to your suggestion, to see if I can find what caused the problem in the first place. Thanks again.

---

### Post by webaake on 2020-01-21
I started a long time ago, even before PDF was an accepted file format. So I've come across a lot of Microsoft doc files in my day. But the conversion to and from .doc has gone better and better over the years. But today, when PDF is well accepted I always export copies in that format and keep my own documents in .odt format. Then, if some odd user really want .doc or .docx, I can export it just for them.

So, go with .odt on your home system and export other formats as needed. I think .odt always will be safer along new version of Libreoffice.

---

### Post by rsteinmetz70112 on 2020-01-21
To chime in here. I always use .odt if I can and next use .docx and reserve .doc for cases when I absolutely have no other choice.

---

### Post by lesliek2 on 2020-01-21
Hi  rsteinmetz70112.

Thanks for your reply.

It now appears to me that I may have been lucky for years using .doc as my default format for saving word processing documents, instead of LO's native format. I did it because I often send such documents to others whom I expect will be using MS Word. However, there are many documents that I don't send to others in that way, for instance, all my papers that I mentioned in my original post. With them, once I've saved them in .doc format, I then resave them in .pdf format for uploading to the SSRN. If I want to end up with a pdf, I can just as easily start with an .odt file as with a .doc file.

I'm going to change my habits now. I'll always save in .odt and, if I want a .doc file, I'll convert my final saved .odt file.

Thanks again.

---

### Post by kurt18947 on 2020-01-22
Yes, doing edits is preferred in .odt formats. I don't have complex documents but have never had a problem using .odt. I too tend to export to pdf when sending documents to someone else. Some people advocate using .doc over .docx when forced fo send in MSO format. The thinking being .doc is a static format no longer being developed so not a moving target. Docx formats can change over time and LibreOffice hasn't caught up to the latest iteration yet.

---

### Post by lesliek2 on 2020-01-22
I apologise for being a pest about this, but I was overly optimistic yesterday that my problem was solved. webaake's suggestion to convert my .doc file to an .odt file did get me an .odt file, which I was then able to edit normally. HOWEVER, when I then tried to convert that edited file to a .pdf file, my ultimate goal, that failed. Writer froze again.
sdsurfer had suggested that I try to track what was happening using the tail command. I ran tail as suggested and then opened LO and tried again to convert the .odt file to a .pdf file. Here's what appeared in the terminal as I did:

Jan 22 06:57:44 leslie-X555UA gnome-session[1488]: Warning: failed to read path from javaldx
Jan 22 06:57:44 leslie-X555UA org.gnome.zeitgeist.SimpleIndexer[1393]: ** (zeitgeist-fts:2216): WARNING **: Unable to get info on application://nautilus-autostart.desktop
Jan 22 06:58:20 leslie-X555UA dbus[979]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jan 22 06:58:20 leslie-X555UA systemd[1]: Starting Hostname Service...
Jan 22 06:58:20 leslie-X555UA dbus[979]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jan 22 06:58:20 leslie-X555UA systemd[1]: Started Hostname Service.
Jan 22 07:00:01 leslie-X555UA gnome-session[1488]: [7582:1:0122/070001.797190:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.

Right now, writer is frozen and I'll have to force it to quit again.

I haven't said this yet, but this is the scariest thing that's happened to me since I first began to use some version of Linux in 2005. The papers that I've written using OO and then LO and that I edit from time to time are my main intellectual activity in retirement. I just can't lose access to them.

---

### Post by sdsurfer on 2020-01-22
> It seems to have got me an edited saved document, though in .odt format, not .doc format.

This is likely an important clue. There is some converting going on to get to .doc, and though I'm not experienced on **how** it does that, you might try as suggested, work in native .odt then try exporting as .doc.

> Warning: failed to read path from javaldx

Same error you got attempting to start from command line, though it may be a needle in a haystack, a web search might locate some clues. Java related issues are always such a pain to solve. :-\

Hopefully someone can chime in on the syslog errors, I would have to do the same searching around to figure it out.

Have you tried uninstalling and re installing the latest version of OpenOffice supported by your OS? Sometimes that can work when you get obscure errors, generally an install ensures the correct dependencies are present. This won't remove your documents, but I would back them up anyway before trying.

---

### Post by lesliek2 on 2020-01-22
sdsurfer, you ask whether I've [COLOR=#000000] tried uninstalling and re installing the latest version of OpenOffice supported by my OS. Yes, I have. When I began to get problems, I uninstalled LO and then reinstalled it (version 6.2.8.2, the current stable version).

I'll now search for information about the java business.

Thanks for your help with this. I appreciate it very much.[/COLOR]

---

### Post by kurt18947 on 2020-01-26
> **lesliek2 said:**
> 
..........................................
I haven't said this yet, but this is the scariest thing that's happened to me since I first began to use some version of Linux in 2005. The papers that I've written using OO and then LO and that I edit from time to time are my main intellectual activity in retirement. I just can't lose access to them.

Please excuse me if I'm being obvious but have you backed up what's important to you? Flash drive and external hard drive storage is cheap, online storage can be free. There are few things more disheartening than reading about someone begging for help because their computer died and they did not have backups of irreplacable pictures, videos, documents etc.

---

