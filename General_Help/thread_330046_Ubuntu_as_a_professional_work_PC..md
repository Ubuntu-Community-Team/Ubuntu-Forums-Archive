---
title: "Ubuntu as a professional work PC."
date: 2007-01-02
forum: General Help
---

### Post by FeraTech on 2007-01-02
I have Ubuntu Edgy installed on my laptop. I choose Edgy because it was the only one that did not have the dreaded ACPI bug. The wireless problems that Edgy has were a hassle but after a quick rebuild and an installation of "Network Manager" everything worked seamlessly.

Now into the problems. 

As a home PC ubuntu is almost perfect. I say almost because it seems to me at least that for simply a home PC Ubuntu isn't the most practical since it requires someone with a little more experience with computers than an average user when a problem arises and those people are more likely to use Ubuntu as more than just a home PC.

Also, OpenSource applications offered while in many cases can surprise at how functional they are many lack refinement.

Here are the problems I have run into so far:

After seeking a looking for a decent web editor I ended up installing Wine and getting Dreamweaver as my primary editor. All the other options lack the versatility of Dreamweaver as a WYSIWYG editor. However, I have found Aptana as a very useful editor for code.

For graphics I tried using Gimp. While for an OpenSource app it is amazing. It's versatility and features pale in comparison to Adobe, Photoshop. Which after about 16 hours I finally managed to get working in Wine. Which is another problem in itself because of the time needed to spend simply getting it to work.

For FTP I use gFTP, which is a pretty functional little FTP client. However, when uploading directories to a web server gFTP does something strange to the permissions and the entire directory can't be access from the web. Also, these permissions can't be changed at all and the directory has to be manually created then all the files copied individually to avoid this.

The terminal server client surprised me very much. It is very functional and easy to use. However, for some reason it likes to disconnect at random times. While annoying it's better than it's windows alternative.

Anyway, I just wanted to add my own experience of Ubuntu. I have never worked on linux systems before and in the past year I have installed Ubuntu on my webserver and use it every day on my laptop. While I still feels it needs work it is my OS of choice.

---

### Post by altaaa on 2007-01-02
I don't do FTP and webdesign. Remote Desktop is very stable for me, it never crashes. I use it in an Xnest window (because I want 16 bit colour while using aiglx). The only problem I have is that more than one Xnest window with remote desktop really slow down my laptop, but that could be related to my cheap and slow laptop. For your Photoshop experience, did you consider using gimpshop? I believe it is available on linux too, and it converts the Gimp in such a way that it resembles Photoshop pretty accurate.

---

### Post by Astro96 on 2007-01-02
> **FeraTech said:**
> After seeking a looking for a decent web editor I ended up installing Wine and getting Dreamweaver as my primary editor. All the other options lack the versatility of Dreamweaver as a WYSIWYG editor. However, I have found Aptana as a very useful editor for code.
The [wine application database for dreamweaver]("http://appdb.winehq.org/appview.php?iAppId=183") recommends two alternivties to Dreamweaver.  I have not used either one myself, but they are probably worth looking into:
[Nvu]("http://www.nvu.com/index.php")
[Quanta]("http://quanta.kdewebdev.org/")
Both of those should be installable using apt-get too.

> **FeraTech said:**
> For graphics I tried using Gimp. While for an OpenSource app it is amazing. It's versatility and features pale in comparison to Adobe, Photoshop. Which after about 16 hours I finally managed to get working in Wine. Which is another problem in itself because of the time needed to spend simply getting it to work.
I started on the GIMP so Photoshop baffles me but I have heard of a photoshop-like interface for the GIMP.  Take a look here:
[Gimpshop]("http://www.gimpshop.net/")

> **FeraTech said:**
> For FTP I use gFTP, which is a pretty functional little FTP client. However, when uploading directories to a web server gFTP does something strange to the permissions and the entire directory can't be access from the web. Also, these permissions can't be changed at all and the directory has to be manually created then all the files copied individually to avoid this.
On Windows I loved Filezlla for an FTP client and the new version has a native Linux port.  It is working great for me, although it is defiantly still in a beta phase:
[Filezilla Download Page]("http://sourceforge.net/project/showfiles.php?group_id=21558&package_id=206762")

The install for it isn't too bad -- just unpack the archive and run the executable named "filezilla"

> **FeraTech said:**
> The terminal server client surprised me very much. It is very functional and easy to use. However, for some reason it likes to disconnect at random times. While annoying it's better than it's windows alternative.
Sorry, I can't help you there... maybe someone else has a suggestion?

Well that's my $0.02.  Hope it helps you out a little bit.

Andy

---

### Post by FeraTech on 2007-01-02
Gimpshop simply changes the Gimp interface. It does not increase the Gimp functionality, primarily Gimps layer handling. There are plugins you can get to get almost the same kind of effects but it's still a long way off from Photoshop.

As for FTP, have you had any similar problems with folder permissions with gFTP?

---

### Post by FeraTech on 2007-01-02
Nvu is the only WYSIWYG editor out there. However, Nvu is actually Komposer. Komposer is the current version which fixes the bugs in Nvu until a new version of Nvu is released. Nvu in it's current state is not pratically useable.

I have tried Quanta and its so basic that it's almost easier to use gFTP and gEDIT as your web authoring solution.

---

### Post by dasunst3r on 2007-01-02
Believe it or not, there is actually no need for gFTP.  When you go into GNOME's file explorer, there is a built-in FTP/SSH client.  All you need to do is select File -> Connect to Server

The FTP and SSH servers will then be "mounted" and will feel a lot like a drive to you.  Hope that tip helps. :)

---

### Post by Quillz on 2007-01-02
For an FTP client, have you tried the FireFTP extension for Firefox? It's what I use and it works very well.

---

### Post by Quillz on 2007-01-02
> **dasunst3r said:**
> Believe it or not, there is actually no need for gFTP.  When you go into GNOME's file explorer, there is a built-in FTP/SSH client.  All you need to do is select File -> Connect to Server

The FTP and SSH servers will then be "mounted" and will feel a lot like a drive to you.  Hope that tip helps. :)
Wow! I never knew that. That's very useful for me, as I have my own personal FTP server that I'm constantly accessing throughout the day. Thanks very much for this!

---

### Post by dasunst3r on 2007-01-04
You're welcome! :)

---

