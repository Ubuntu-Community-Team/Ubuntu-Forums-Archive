---
title: "I think LibreOffice is haunted"
date: 2015-11-14
forum: General Help
---

### Post by Buntu Bunny on 2015-11-14
LibreOffice Writer 3.5.7.2
Build 350m1(Build:2)

I know that saving a document as .doc or .docx causes a few changes in formatting, especially the addition of line spaces. I've found that if I re-open it in that format and fix it, however, it will usually stay fixed. I recently uploaded an eBook to Smashwords (as .doc), however, and have come to the conclusion that LO is haunted.

It started with the addition of unwanted embellishments in the final document, i.e underlining sentences or whole paragraphs and changing text color. I'd fix these, save, but they'd be back again when I re-opened. Highlighting and clearing direct formatting did *nothing.* A Smashwords tech told me that "body text" is often the culprit and to delete it. LO has "text body," but I'm not sure if that's the same thing and there is no way delete it anyway.

Since I had been simply updating the same eBook for several in a series, I decided that there must be old metadata hanging about in the LO background and causing these problems. I could not find how or where to purge old metadata, so I started with a new document.

Now, it's not only adding line spaces, but it's ignoring paragraph styles and adding page breaks. When I check the styles and formatting, they are as I set them, but the document has changed nonetheless. 

Does anyone have any idea what is going on? Or what to do about it? I love Ubuntu and open source, but have never had this much trouble with LibreOffice. Now it's beginning to infringe on how I make my living, which is troubling because I really, really, really hate Windows. Is LO going downhill? Is there an alternative? (Abiword is pretty frustrating for certain things too.)

---

### Post by mörgæs on 2015-11-14
Your version of Libre Office is from early 2012 and out of support. Same goes for your version of Xubuntu.

In stead of struggling with abandoned software I suggest that you do a fresh install of 15.10 and see if the bugs are fixed in the present Libre Office.

---

### Post by kurt18947 on 2015-11-14
Good advice. LibreOffice's handling of MS formats has improved in recent iterations. I'm not familiar with Smashwords. Does it support formats beyond MSOffice? Or even RTF? If worse comes to worse, consider something like PlayOnLinux & an older version of Word? I personally hate Word but ya gotta do what ya gotta do.

---

### Post by Buntu Bunny on 2015-11-14
> **mörgæs said:**
> Your version of Libre Office is from early 2012 and out of support. Same goes for your version of Xubuntu.

In stead of struggling with abandoned software I suggest that you do a fresh install of 15.10 and see if the bugs are fixed in the present Libre Office.

Not that it probably makes any difference, but I'm actually using Xfce 4.10 on Ubuntu 12.04. That version of LO is the only thing offered in Software Centre and Synaptic. Which of course still points to upgrading, which for me would be 14.04.3 because I need an LTS version. I've been avoiding a fresh install because saving all current data and doing the install would be another huge learning curve for this non-geeky bunny. 

I suppose I can only put off the inevitable for so long. *sigh*

> **kurt18947 said:**
> I'm not familiar with Smashwords. Does it support formats beyond MSOffice? Or even RTF? 

[Smashwords]("https://www.smashwords.com/") is an eBook conversion service which sells eBooks at their site and also formats them for all eReaders to sell at Amazon, iTunes, Oyster, B&N, etc. They require either an epub upload or .doc (not .docx). The doc upload is the most versatile, because it can be converted into all formats (via the infamous "Meatgrinder"). Since I don't do Windows anything, it's LO, I'm afraid.

---

### Post by vasa1 on 2015-11-14
> **Buntu Bunny said:**
> Not that it probably makes any difference, but I'm actually using Xfce 4.10 on Ubuntu 12.04. That version of LO is the only thing offered in Software Centre and Synaptic. Which of course still points to upgrading, which for me would be 10.04.3 because I need an LTS version. ... 

Since I don't do Windows anything, it's LO, I'm afraid.

Another option is to research if you can download a newer version of LibreOffice directly from libreoffice.org if it runs on 12.04. That way, you wouldn't need to install 14.04 LTS.

And can't you install Windows as a VM and do all your doc-specific work there? All that I've read cautions against working (editing) with the .doc format in LibreOffice other than saving an odt file as a .doc file immediately before sending it off to wherever.

---

### Post by mörgæs on 2015-11-14
I think it's much to fast to recommend Windows and MS Office. Let's wait for original poster's experience with a new Libre Office and go from there.

---

### Post by vasa1 on 2015-11-14
> **vasa1 said:**
> Another option is to research if you can download a newer version of LibreOffice directly from libreoffice.org if it runs on 12.04. That way, you wouldn't need to install 14.04 LTS.

...

> The software and hardware prerequisites for installing on Linux are as follows:

Linux kernel version 2.6.18 or higher;
glibc2 version 2.5 or higher;
gtk version 2.10.4 or higher;
Pentium-compatible PC (Pentium III, Athlon or more-recent system recommended);
256Mb RAM (512Mb RAM recommended);
Up to 1.55Gb available hard disk space;
X Server with 1024x768 resolution (higher resolution recommended), with at least 256 colors;
Gnome 2.16 or higher, with the gail 1.8.6 and at-spi 1.7 packages (required for support for assistive technology [AT] tools), or another compatible GUI (such as KDE, among others).
For certain features of the software - but not most - Java is required. Java is notably required for Base.

It is a recommended best practice to back-up your system and data before you remove or install software.From [http://www.libreoffice.org/get-help/system-requirements/](http://www.libreoffice.org/get-help/system-requirements/)

---

### Post by Buntu Bunny on 2015-11-14
> **mörgæs said:**
> I think it's much to fast to recommend Windows and MS Office. Let's wait for original poster's experience with a new Libre Office and go from there.

I actually have dual boot with Windows 7, but I'm not happy with Windows and prefer not to go to the dark side of my computer unless some tech person once again tells me, "We don't support Linux."

> **vasa1 said:**
> From [http://www.libreoffice.org/get-help/system-requirements/](http://www.libreoffice.org/get-help/system-requirements/)

vasa1, thank you for that. Very helpful and hopeful. I have an older, simple Asus CM1740 and looking at the specs I've got
Kernel Linux 3.2.0-95-generic
GNOME 3.4.2
RAM: 3.3 GiB
Processor AMD E2-3200 APU
243.2 GiB available hard disk space. 

I'll have to look into the rest of the requirements, but for now, that would be a happy option.

---

### Post by kurt18947 on 2015-11-14
Another option for LibreOffice would be installing via their PPA.

[https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-5-0](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-5-0)

I've used this method in the past and though I'm not a demanding LibreOffice user, LibreOffice 5 installed and ran as expected. As you do have Windows 7, would it help to install the Word file viewer?  It says the viewer will display all Word file versions. If the viewer displays .doc files accurately, perhaps you could save your upload as an .odt file, then save as a .doc file to external storage. Launch Win 7  and the viewer and open the saved .doc file in the Word viewer (hold your nose if necessary:razz:).  Edit as required to make it display properly in Word Viewer. Perhaps this will help you to upload a 'legal/blessed' .doc file to Smashwords. Yes it's some messing but it may take longer to describe than to do.

Latest Word file viewer:  [https://support.microsoft.com/en-us/kb/891090](https://support.microsoft.com/en-us/kb/891090)

---

### Post by Buntu Bunny on 2015-11-14
> **kurt18947 said:**
> Another option for LibreOffice would be installing via their PPA.

[https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-5-0](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-5-0)

I'm looking into all the options, thanks.

> **kurt18947 said:**
> 
 As you do have Windows 7, would it help to install the Word file viewer? <snip> Edit as required to make it display properly in Word Viewer. Perhaps this will help you to upload a 'legal/blessed' .doc file to Smashwords. Yes it's some messing but it may take longer to describe than to do.

The problem isn't what happens between LO and Word, the problem is what happens in LO itself. Every time I open the file in LibreOffice, I find changes: extra line spaces, unwanted font colors, underlining. Like I said, it acts like it's haunted!

Earlier I uploaded a 5th update to this particular eBook at Smashwords. It passed vetting and is now awaiting approval for Smashwords Premium catalog. The thing that gets me, is that I used the exact same formatting and styles in this book as I did in the previous six. Those had no problems, but this one has. We'll see what happens, but I still plan on updating to a newer version of LibreOffice. That seems to be the unanimous choice here.

---

### Post by vasa1 on 2015-11-14
> **Buntu Bunny said:**
> ...
The problem isn't what happens between LO and Word, the problem is what happens in LO itself. Every time I open the file in LibreOffice, I find changes: extra line spaces, unwanted font colors, underlining. Like I said, it acts like it's haunted!...

Just to repeat myself, IIRC, the LibO devs do not recommend editing in formats other than those native to LibO. The compatibility they strive to offer is in opening and in saving in certain closed-source formats.

---

### Post by kurt18947 on 2015-11-15
I wonder if you could determine if a newer version of LibreOffice would help by editing using a live session rather than one installed. I believe the 15.10 releases come with L.O. 5.X - at least MATE does. That might eliminate any risk to your current install associated with installing via PPA.  Keep your working files on a flash device.

---

### Post by mörgæs on 2015-11-15
With 243 GiB space left then another option is installing a supported version in a new partition, verify that everything works and then move all files here. 12.04 should not be used regardless of Libre Office problems.

---

