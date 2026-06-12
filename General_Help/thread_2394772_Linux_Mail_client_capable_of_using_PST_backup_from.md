---
title: "Linux Mail client capable of using PST backup from Office 2007"
date: 2018-06-21
forum: General Help
---

### Post by hennmann on 2018-06-21
After doing a search I have found this topic posted but the threads are quite old so I'm attempting to find updated info.
My question is I'm using Office Professional 2007 on Windows 7 Ult and have extensive backups using PST backup files and I'm wondering if there is a Linux NOOB method to transfer all of my backed up emails, contacts etc. to a Linux Mail Client such as Thunderbird Mail? If Windows 7 crashes as is most certainly can and will I can reinstall Windows 7, then Microsoft Office 2007 and then to a total restoration of everything using these PST files.

---

### Post by dragonfly41 on 2018-06-21
I have moved away from Microsoft Office but a quick search shows that there is an SDK
which might allow you to export *.pst files to another format.

[https://msdn.microsoft.com/es-es/library/office/gg615595(v=office.14).aspx](https://msdn.microsoft.com/es-es/library/office/gg615595(v=office.14).aspx)

i would then explore if document converters such as [pandoc]("https://pandoc.org/") can help in restructuring
the exported *.pts files into some format which Thunderbird can import.

Make sure that MS Office is closed before copying your *.pst archives.

[COLOR=#b22222]**[Later Edit]**[/COLOR]

It seems that there are established practices for Thunderbird to import *.pst archives.

[https://support.mozilla.org/en-US/questions/1154588](https://support.mozilla.org/en-US/questions/1154588)

My guess is that you will probably need to install Thunderbird into Windows as a first step.

Then consider importing Thunderbird (Windows) folders to Thunderbird (Linux) folders.

The earlier pandoc idea now seems to be redundant. Forget it.

---

### Post by HermanAB on 2018-06-21
Not what you want to know exactly, but the easiest way to transfer email from one format to another, is to drag and drop it via an IMAP server. Do not forward the mail; do not copy the mail - since those commands will change all the mail headers - drag and drop the mail with the mouse between two accounts, which causes an IMAP move command to happen and then the mail will end up in the new account looking exactly the same as in the old account.

You can do this by creating a throw away account with gmail.  Log in with your existing account into your existing mail server, then log in with your new mail client into gmail, highlight drag and drop the mail from the old account to the new account, then go and watch a ball game while it goes on.

---

### Post by Holger_Gehrke on 2018-06-21
Don't know about Thunderbird, but Evolution has an importer for .pst. I don't know how well it works, but it's there.

Holger

---

### Post by hennmann on 2018-06-24
Thank you very much to all who gave suggestions !! Now that I have read these dragonfly41's point reminded me of something I read a short while ago and it also was mentioned install both on a Windoze computer, set Outlook up as default and begin the process. These PST files can be huge and the backup for mine is a gig and a 1/2 and usually when Outlook makes a backup this large file increases slightly but is always updated. It is fantastic because EVERYTHING that is selected is backed up and easily restored as it should be due to the endless possibilities of failure due to viruses, malware, worms, spiders, etc. It is as easy as my old Aiwa Bolt TD-AS10 tape backup that is identical to the Sony Superstore still languishing in my tower. Once Windows is installed, then the Seagate utility it would place everything back where it came. I will reinstall Win 7 back on a drive and install Thunderbird with Outlook and give things a try. I got sick of Win 10 making my puter look like a damn Smart Phone or should I say toooooo Appy and purchased a product key of Win7 Ult, 32/64 for 5 quid on ePain from a UK seller and it installed smoothly on my old hardware and activated nicely. A month later, this June I updated my hardware to an MSI Krait SLI 970A with an FX6350 and reinstalled and discovered it would not activate. I contacted Microsoft who informed me a month after I purchased It was blocked after being discovered to  be a pirated product key grrrrrrrrrr! So much for attempting to be honest and not using Piratebay so here I am today on Ubuntu due to this. All I have to do is go back in time when I first started trying Linux, 2001 and later back to the Mandrake, and earlier Ubuntu days and set things up with all of the proper partitions like one always had to do which is a good idea. Instead of placing everything in one kettle of fish, multiple partitions can be used in case there is one rotten fish that could spoil everything in the kettle. As it is I do not care for running things "live" on a USB drive because on older slower hardware that I have with small amounts of RAM crawls until the OS is installed on a HHD with a suitable swap partition!

---

