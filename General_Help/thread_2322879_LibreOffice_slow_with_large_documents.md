---
title: "LibreOffice slow with large documents"
date: 2016-05-01
forum: General Help
---

### Post by johnsd on 2016-05-01
Hi - I am running Ubuntu 16.04 (new install rather than upgrade from 14.04). I have used OpenOffice/LibreOffice since about 1998 with little in the way of problems. The upgrade from LO 4.xx to 5.1.2.2 with 16.04 is causing problems with large files (e.g. about 100 pages of Writer with diagrams etc). These documents have been going fine with the old version but for the first 3-4 minutes after loading they are unusable (periodically grays out and temporarily locks up). I have changed the settings in Tools->Options->Memory to have 300 MB "Use for LibreOffice", 3MB "Memory per object", remove from memory after 10 min, cache for inserted objects = 325. This has made no difference.

Also one of these large documents had about 20 blank pages added into the middle of it. 

I am not really liking LO 5!!

Any ideas would be greatly appreciated.

---

### Post by johnsd on 2016-05-02
Unfortunately many of my documents are over 100 pages long. I have noticed when I open one of them (that has always behaved well in previous version s of LO) it adds about 80 blanks pages to the document and takes about 4 minutes to remove them again. While this is happening the document is only usable for seconds at a time.

---

### Post by vasa1 on 2016-05-02
By any chance are you opening them in "web layout" instead of "normal"?

---

### Post by johnsd on 2016-05-02
No - definitely in normal view.

---

### Post by grahammechanical on 2016-05-02
I have been using Libreoffice 5 for months. I run the development version of Ubuntu. So, I have been using 16.04 & Libreoffice for months. And this problem has been present in Libreoffice 5 since it was first brought into Ubuntu all those months ago. I do not believe it is a memory issue. I only have 1 GB of RAM but there is still many MB of memory in reserve when I open Libreoffice & a large document. It seems to me that Libreoffice 5 is now very slow in reading the document into RAM. And also when saving to disk.

I work with more than one large document open at a time. Once the documents have loaded there is little, if any, noticeable slow down effect on how the user interface works. So, I am discounting lack of sufficient memory as the issue. I have seen other things as well.

Open a Libreoffice 4 document and you may find that the menus in the top panel do not drop down. I have taken to copy & pasting my documents into a new, blank Libreofffice 5 document as a way around this. 

I have also seen problems with formatting of text. Try to put a 10 cm space above the first line of a paragraph and you may end up with a 10 cm space above every line in the paragraph.

The Find function is a lot slower than in version 4.

Regards.

---

### Post by vasa1 on 2016-05-02
Glad to read I'm not alone. Dropping back to gtk2 eases some of the problems:
```
SAL_USE_VCLPLUGIN=gtk libreoffice --calc
```or```
Exec=bash -c 'SAL_USE_VCLPLUGIN=gtk libreoffice --calc %u'
```

---

### Post by vasa1 on 2016-05-02
> **johnsd said:**
> No - definitely in normal view.Can you try dropping back to gtk2?

The code for that is 
```
SAL_USE_VCLPLUGIN=gtk libreoffice --writer
```
from a terminal (or keyboard shortcut)
and
```
Exec=bash -c 'SAL_USE_VCLPLUGIN=gtk libreoffice --writer %u'
```(in your .desktop file)

---

### Post by johnsd on 2016-05-04
Got a bit more scientific about this this evening. I loaded one of my many large documents - it took close to 13 minutes to become usable - during this time it was greyed out most of the time and I could see in the bottom left corner that there were 304 pages.  After the 13 minutes of greyed screens, the number of pages dropped back to the real amount of 208. At this point the whole document became quite usable. While it was "grey screening" I looked at the CPU usage - one of my 4 cores was continually at 100%. 

I have an AMD A8-3870 APU with Radeon HD graphics and 8GB RAM - this should be ample but the CPU is ultra busy (one core at a time)  until the document becomes usable.

These documents are my teaching notes for my students so something has to improve. I guess I have to decide whether to:

1. Break the documents up into smaller sizes.
2. Go back to an older version of LO (I presume I could install this on Ubuntu 16.04?)
3. Investigate another Office product that will run on Linux.
4. Go back to using MS Word on MS Windows ( I have been a Linux user since 1998 so that would hurt!!).

Any recommendations?
Thanks
John

---

### Post by johnsd on 2016-05-04
Sorry - just read the post about gtk - what are the implications of doing this if any? I like ot know what I am doing before making changes...
Thanks
John

---

### Post by vasa1 on 2016-05-04
> **johnsd said:**
> ... it took close to 13 minutes to become usable - during this time it was greyed out most of the time and I could see in the bottom left corner that there were 304 pages.  **After the 13 minutes of greyed screens, the number of pages dropped back to the real amount of 208.** At this point the whole document became quite usable. While it was "grey screening" I looked at the CPU usage - one of my 4 cores was continually at 100%. 
...

This is exactly what I see when the document opens in "web" as opposed to "normal" layout. Please look at the image. Also see my thread here: [http://ubuntuforums.org/showthread.php?t=2321188](http://ubuntuforums.org/showthread.php?t=2321188)

> **johnsd said:**
> Sorry - just read the post about gtk - what are the implications of doing this if any? I like ot know what I am doing before making changes...
...
There are no permanent implications. It just means that you choose to launch libreoffice using the gtk2 toolkit rather than the gtk3 toolkit whenever you use those codes.

---

### Post by johnsd on 2016-05-04
> **vasa1 said:**
> This is exactly what I see when the document opens in "web" as opposed to "normal" layout. Please look at the image. Also see my thread here: [http://ubuntuforums.org/showthread.php?t=2321188](http://ubuntuforums.org/showthread.php?t=2321188)

The View menu shows "Normal" so it is not being opened in web view.
Thanks.

---

### Post by vasa1 on 2016-05-04
> **johnsd said:**
> The View menu shows "Normal" so it is not being opened in web view.
Thanks.
Okay, then all I have left is to suggest trying the gtk2 route.

1. Close all libreoffice programs. Run *pgrep soffice* in a terminal. You should just get back the prompt.
2. Run *SAL_USE_VCLPLUGIN=gtk libreoffice --writer* in a terminal. Don't close the terminal.
3. LibreOffice Writer should open. It may look ugly.
4. Open your most troublesome document. If it loads nicely, quit Writer, close the terminal, post back here and we'll take matters further. If it doesn't, I'm out of ideas.

---

### Post by johnsd on 2016-05-04
> **vasa1 said:**
> Can you try dropping back to gtk2?
The code for that is 
```
SAL_USE_VCLPLUGIN=gtk libreoffice --writer
```

Still goes grey and unresponsive but not for quite as long.

---

### Post by vasa1 on 2016-05-04
Sorry to read that.

One last blind guess... Do you have "Use Hardware Acceleration" ticked under Tools > Options > LibreOffice > View? If it's ticked, do things improve if you untick that? Same for the OpenGL stuff there and then look at Tools > Options > LibreOffice > OpenCL and turn off stuff there as well.

One more thing ... if you don't have any confidential stuff, maybe you could upload the file somewhere and post a link for us to try the same file on our systems.

---

### Post by johnsd on 2016-05-05
> **vasa1 said:**
> Sorry to read that.

One last blind guess... Do you have "Use Hardware Acceleration" ticked under Tools > Options > LibreOffice > View? If it's ticked, do things improve if you untick that? Same for the OpenGL stuff there and then look at Tools > Options > LibreOffice > OpenCL and turn off stuff there as well.

HW Acceleration was turned on - but turning it off does not seem to make any difference.

> **vasa1 said:**
> One more thing ... if you don't have any confidential stuff, maybe you could upload the file somewhere and post a link for us to try the same file on our systems.

Unfortunately while I have written these large documents they belong to the teaching institution that I work for so I don't think that I can upload them.

I am going to try OpenOffice alongside LibreOffice - there seems to be some conflicting information about whether they can coexist together to I am going to test on a virtual machine first - I use my PC up to 2 hours a night so am very careful about any changes that might upset things.

I keep wondering about the delay and the lots of extra blank pages that are there at load time in each of the several documents I am currently using - this seems to be a key to me - what is generating them? Once they are gone, everything is back to normal.

---

### Post by johnsd on 2016-05-05
I have installed Apache OpenOffice 4.1.2 and the offending documents load straight in with absolutely no issues. I may just have to use OO in the mean time - it does not look quite so polished on the screen.

---

### Post by vasa1 on 2016-05-05
Well, that's good. In case you don't know AOO has a nice support forum here: [https://forum.openoffice.org/en/forum/index.php](https://forum.openoffice.org/en/forum/index.php)

---

### Post by kurt18947 on 2016-05-05
> **johnsd said:**
> I have installed Apache OpenOffice 4.1.2 and the offending documents load straight in with absolutely no issues. I may just have to use OO in the mean time - it does not look quite so polished on the screen.

Or un-install L.O. 5 and install [L.O. 4.4.7.2. ]("https://downloadarchive.documentfoundation.org/libreoffice/old/4.4.7.2/deb/")

I don't know if there'd be any security implications using an older version or not. Windows and Word? Given a choice I'd prefer quill & inkwell. At least those don't try to read my mind -- and do a poor job of it.

---

### Post by johnsd on 2016-05-08
Now that I have used OpenOffice a bit with the offending files I am finding that it too locks up at times - but not as bad. The trouble is that I cannot save to a PDF - it crashes each time.

So back to LibreOffice - now the menus are blacked out. I changed the theme to no avail. Loaded another file and the menus are back.

I have not had so many issues since starting down the track with Linux and StarOffice in about 1998 from memory. (Bother!!)

---

### Post by vasa1 on 2016-05-08
Would you consider making a new user profile?

[https://wiki.documentfoundation.org/UserProfile](https://wiki.documentfoundation.org/UserProfile)

---

### Post by johnsd on 2016-05-08
> **vasa1 said:**
> Would you consider making a new user profile?

[https://wiki.documentfoundation.org/UserProfile](https://wiki.documentfoundation.org/UserProfile)

OK - done that - am finished for the evening so will see how that pans out tomorrow evening.
Thanks
John

---

### Post by johnsd on 2016-05-10
It seems to me after playing around with all this for a few days that the issue belongs to Ubuntu 16.04 not LibreOffice. I have a file that is over 200 pages long that takes about 30 minutes to become usable in Ubuntu 16.04. If I take this to my work and load it into a PC of lesser specifications than my home PC running MS Windows 8.1 and LibreOffice 5, there is not the slightest hesitation and the file is quite usable the second it loads.

---

### Post by johnsd on 2016-05-10
> **johnsd said:**
> OK - done that - am finished for the evening so will see how that pans out tomorrow evening.
Thanks
John
Not sure if changing the profile has made a difference - I have split the worst file into two parts but they still have a delay before the file is able to be used. The menus are back this evening though.

---

### Post by vasa1 on 2016-05-11
FWIW, [http://askubuntu.com/questions/771091/how-to-speed-up-libreoffice-libre-office-cant-handle-big-files](http://askubuntu.com/questions/771091/how-to-speed-up-libreoffice-libre-office-cant-handle-big-files)

---

### Post by kurt18947 on 2016-05-12
I don't know if this is possible but could you try opening the problem files in L.O. 5 running on a non-Ubuntu/non-Debian live session? Something like Fedora? See if you can isolate where the problem lies?

---

### Post by vasa1 on 2016-05-12
I don't work much with images in Writer documents but I seem to remember there are two ways to include them. One is to point to an external image by means of a link and the other is to actually incorporate them in the Writer file. I'm guessing the latter will be more resource-demanding.

But the sticking point is that OP had no problems with the same documents when using earlier versions of LibreOffice Writer.

---

### Post by johnsd on 2016-05-12
> **vasa1 said:**
> FWIW, [http://askubuntu.com/questions/771091/how-to-speed-up-libreoffice-libre-office-cant-handle-big-files](http://askubuntu.com/questions/771091/how-to-speed-up-libreoffice-libre-office-cant-handle-big-files)

Thanks but done that - talked about it in my first post. Have used figures far higher than the ones on the first post to no avail.  As pointed out, the same offending file works 100% fine in LibreOffice 5 and MS Windows 8.1 with the standard memory settings - which points to the fact that these settings probably have nothing to do with the problem.

---

### Post by johnsd on 2016-05-12
> **kurt18947 said:**
> I don't know if this is possible but could you try opening the problem files in L.O. 5 running on a non-Ubuntu/non-Debian live session? Something like Fedora? See if you can isolate where the problem lies?


OK - will try that. Downloading my old favourite distro before Ubuntu - PCLinuxOS. Will let you know the results.

---

### Post by johnsd on 2016-05-12
Confirming that this is looking like a Ubuntu16.04 issue. I have run PCLinuxOS from a pen drive and loaded the file into LibreOffice 5.1.1.3 with no memory configuration changes and it is snappy even when the file is loaded from a second pen drive.

---

### Post by vasa1 on 2016-05-12
> **johnsd said:**
> Confirming that this is looking like a Ubuntu16.04 issue. I have run PCLinuxOS from a pen drive and loaded the file into LibreOffice 5.1.1.3 with no memory configuration changes and it is snappy even when the file is loaded from a second pen drive.

Just for the sake of completeness can you share the specifics of the PCLinuxOS on your pendrive: version, flavor, etc? I'm guessing it's the MATE version. Anyway, all the best!

---

### Post by johnsd on 2016-05-13
The version of PCLinuxOS I used was:
[TABLE="width: 732"]
[TR="class: e"]
[TD][pclinuxos64-kde-fullmonty-2016.03.iso]("http://mirror.internode.on.net/pub/pclinuxos/pclinuxos/live-cd/64bit/pclinuxos64-kde-fullmonty-2016.03.iso")[/TD]
[TD]3947724800[/TD]
[TD]08-Mar-2016 09:58[/TD]
[/TR]
[/TABLE]

I am guessing that the issue is some kind of kernel RAM management issue? What do people think of the chances of this being solved in the near future? I am thinking that I may need to consider changing distributions?

---

### Post by vasa1 on 2016-05-13
> **johnsd said:**
> ...
I am guessing that the issue is some kind of kernel RAM management issue? What do people think of the chances of this being solved in the near future? I am thinking that I may need to consider changing distributions?
I have no idea. From a practical point of view, you should use whatever works best for you. The PCLinuxOS team is pretty decent and I enjoy reading their monthly magazine :)

---

### Post by johnsd on 2016-05-14
I guess the truth is I do not want to move away from Ubuntu - apart from this issue it has just worked for me.

---

### Post by kurt18947 on 2016-05-14
If I'm reading this correctly you can run off a live USB. PCLinux works well, is it using L.O.5.x? . What 'flavor' of Ubuntu are you using? Would it be worth the time and effort to try one of the 'lightweight' flavors with L.O. 5 such as Xubuntu or Lubuntu? Try to narrow down the offending bits, do all Ubuntu 'flavors' have this issue or just certain ones?

---

### Post by johnsd on 2016-05-15
> **kurt18947 said:**
> If I'm reading this correctly you can run off a live USB. PCLinux works well, is it using L.O.5.x? . What 'flavor' of Ubuntu are you using? Would it be worth the time and effort to try one of the 'lightweight' flavors with L.O. 5 such as Xubuntu or Lubuntu? Try to narrow down the offending bits, do all Ubuntu 'flavors' have this issue or just certain ones?
I am using the normal 64 bit desktop with Unity. PCLinuxOS is using LO5.  I could try a light version but my (limited) understanding of the Linux architecture would tend to suggest that this is not a GUI problem but rather a kernel issue???

---

### Post by kurt18947 on 2016-05-15
> **johnsd said:**
> I am using the normal 64 bit desktop with Unity. PCLinuxOS is using LO5.  I could try a light version but my (limited) understanding of the Linux architecture would tend to suggest that this is not a GUI problem but rather a kernel issue???

I'm certainly no expert but I thought Ubuntu made some changes/additions to the stock kernel. Like you I prefer to stay within the Ubuntu ecosystem because things tend to "just work". I don't know how different desktops or video subsystems might impact LibreOffice 5.x.

---

### Post by roler2 on 2016-05-15
Whenever I open a Word document greater than one page I get extra blank pages added on. For example, I have a six-page Word Document that got 7 blank pages added to it. I was informed of a temporary fix to get it back to six pages but the fix escapes me at the moment. However when I save the 'fixed' document and then re-open it all the blank pages return.

Is there any way to permanently remove the extra blank pages? Only happens with .doc extension.

The six-page document is also very slow to open on Lubuntu.

---

### Post by vasa1 on 2016-05-15
> **roler2 said:**
> Whenever I open a Word document greater than one page I get extra blank pages added on. For example, I have a six-page Word Document that got 7 blank pages added to it. I was informed of a temporary fix to get it back to six pages but the fix escapes me at the moment. However when I save the 'fixed' document and then re-open it all the blank pages return.

Is there any way to permanently remove the extra blank pages? Only happens with .doc extension.

The six-page document is also very slow to open on Lubuntu.

Are you willing to upload the file for others to look at?

---

### Post by roler2 on 2016-05-16
I am uncomfortable uploading personal documents. I would have to delete a lot of personal information, especially with six pages. However I believe this is the 'fix' I utilized to temporarily delete the blank pages: SHOW NON PRINTING CHARACTERS (Ctrl + F10)

Unfortunately when I re-save the document utilizing the 'fix', the 'fix' itself is not saved. Re-opening the document brings back the blank pages.

---

### Post by vasa1 on 2016-05-16
> **roler2 said:**
> I am uncomfortable uploading personal documents. I would have to delete a lot of personal information, especially with six pages. However I believe this is the 'fix' I utilized to temporarily delete the blank pages: SHOW NON PRINTING CHARACTERS (Ctrl + F10)

Unfortunately when I re-save the document utilizing the 'fix', the 'fix' itself is not saved. Re-opening the document brings back the blank pages.

Well, you mentioned the problem occurs with documents longer than one page:> Whenever I open a Word document greater than one page I get extra blank pages added on.Surely you can remove personal information from a one page document!

Anyway, it's your call.

---

### Post by roler2 on 2016-05-16
I am sorry I do not feel comfortable uploading personal and private medical and therapeutic information that is extremely confidential, especially concerning my disabilities, as I am permanently disabled, most of which is relevant to being brutally attacked by a transient of which I am still in recovery for. I hope you will understand. Maybe not.

---

### Post by vasa1 on 2016-05-16
> **roler2 said:**
> ... I hope you will understand. Maybe not.
No, I genuinely don't understand why an _editable_ document cannot be scoured free of identifying data.

Anyway, if you have time please see [http://ubuntuforums.org/showthread.php?t=2324762](http://ubuntuforums.org/showthread.php?t=2324762).

---

### Post by roler2 on 2016-05-16
Sorry you don't understand. I asked my Physician and she said there is no way I have any permission to upload any document that contains confidential medical information that applies to my treatment, no matter what. Maybe where you receive medical treatment things are different. Where I receive treatment there are strict confidentiality regulations which I must adhere to, no matter if the document is editable or not. 

I will look at the thread you mentioned. I will be going to the library and ask the Word expert there, however they only work in Windows and my issue is related only to LibreOffice.

Thank you for your offer of help.

---

### Post by howefield on 2016-05-17
What happens if you "fix" the file then save as an .odt file rather than the original .doc ?

---

### Post by vasa1 on 2016-05-17
> **howefield said:**
> What happens if you "fix" the file then save as an .odt file rather than the original .doc ?
I recall something similar. IIRC, the LibO people recommend that a .doc or .docx file be saved in .odt format **immediately after opening it**. All work (editing, formatting, repagination, etc) should be done in LibreOffice's native ODF format. Then, in case it has to be sent to someone in a proprietary format, a *copy* can be sent using File > Save As > Whatever format.

---

### Post by ping-wu on 2016-05-17
> **johnsd said:**
> Not sure if changing the profile has made a difference - I have split the worst file into two parts but they still have a delay before the file is able to be used. The menus are back this evening though.

Have you deleted your original LO profile by:

(1) close your LO5
(2) open a terminal window, then issue  rm -rf  ~/.config/libreoffice  ?

Then restart LO5

---

### Post by roler2 on 2016-05-18
Thank you so very much for all of your super awesome advice and guidance! I am reinstalling Lubuntu so it will be next week before I attempt the fixes posted. Actually I might wait until a new stable version of LibreOffice is released. Thank you again!

---

### Post by leunam12 on 2016-05-18
> **johnsd said:**
> 
4. Go back to using MS Word on MS Windows ( I have been a Linux user since 1998 so that would hurt!!).

Any recommendations?

MS Word runs perfectly in Linux using WINE, you can even run your VBA macros, if you have any.

---

### Post by kurt18947 on 2016-05-18
> **leunam12 said:**
> MS Word runs perfectly in Linux using WINE, you can even run your VBA macros, if you have any.

I believe *certain versions* of MS Word run perfectly using WINE. Older versions such as 2007 work pretty well, Word 2013 or 2016 perhaps not. Playonlinux may help.

---

### Post by vasa1 on 2016-05-18
Could we please keep the focus of this thread on OP's core issue? Solutions such as switching to other word processors can be discussed elsewhere.

Also, moving this thread to General Help. Maybe it'll get some fresh views.

---

### Post by Linuxisfast on 2016-05-18
On a side note I have been on LO5x via PPA on 14.04 LTS and now latest via PPA for 16.04. In both cases, enabling open GL crashes LO. I have nvidia drivers installed on both 14.04 and 16.04 and no change. Strangely in Arch, the entire option of openGL is not present but hardware acceleration is checked just like Ubuntu.

---

### Post by johnsd on 2016-05-19
> **ping-wu said:**
> Have you deleted your original LO profile by:

(1) close your LO5
(2) open a terminal window, then issue  rm ~/.config/libreoffice  ?

Then restart LO5
The old profile has been renamed which must have the same effect as deleting it?

---

### Post by johnsd on 2016-05-20
> **vasa1 said:**
> Could we please keep the focus of this thread on OP's core issue? Solutions such as switching to other word processors can be discussed elsewhere.

Also, moving this thread to General Help. Maybe it'll get some fresh views.

Thanks for that. 
Just to do a quick recap since there are many posts here!

[LIST=1]
[*]LO 5 documents with over 100 pages or so with graphics are slow (can take up to 30 min after loading to become usable on a 4 core AMD CPU with 8GB RAM and with the LO RAM settings altered. The document goes grey and is unusable except for periodic several seconds until about 30 min. is up). This became apparent after installing Ubuntu 16.04 with LO5. LO4 on Ubuntu 14.04 was fine.
[*]The exact same files work fine on MS Windows 8.1 with a desktop very similar in power to mine.
[*]The files also work fine on PCLinuxOS run from a pen drive on my PC.
[/LIST]

I have just downloaded Fedora (latest version) and again the files run fine off a pen drive. When I get a chance I should try another desktop version of Ubuntu other than the Unity one.

---

### Post by johnsd on 2016-05-20
Tried LUbuntu from a pen drive image but unfortunately LO is not installed on the image (only AbiWord). That would have been a good test if it had worked. Also tried Mint but it would not boot.

---

### Post by kurt18947 on 2016-05-22
> **johnsd said:**
> Tried LUbuntu from a pen drive image but unfortunately LO is not installed on the image (only AbiWord). That would have been a good test if it had worked. Also tried Mint but it would not boot.

If you're so inclined, you could try LXLE from a pen drive. Once difference between Lubuntu & LXLE is that LXLE includes L.O. by default. However, I'm not sure if LXLE based on 16.04 is available yet.

---

### Post by vasa1 on 2016-05-22
Or, staying within the official flavors, FWIW, [http://packages.ubuntu.com/xenial/xubuntu-desktop](http://packages.ubuntu.com/xenial/xubuntu-desktop) offers just Calc and Writer.

```
libreoffice-calc [not armhf, powerpc]
    office productivity suite -- spreadsheet 

libreoffice-gtk [not armhf, powerpc]
    office productivity suite -- GTK+ integration 

libreoffice-style-elementary [not armhf, powerpc]
    office productivity suite -- Elementary symbol style 

libreoffice-writer [not armhf, powerpc]
```

I've done something similar on Lubuntu 16.04. I've installed only Calc and Writer.

Anyway, trouble-shooting or bug reporting is difficult with a document that others can't access. Here's a link to a 16.2 MB, 388-page document with quite a bit of formatting and images: 

[https://wiki.documentfoundation.org/images/f/f3/GS50-GettingStartedLO.odt](https://wiki.documentfoundation.org/images/f/f3/GS50-GettingStartedLO.odt)

It's not at all unmanageable on my system in gtk2 mode.

gtk3 mode was not fun. One CPU showed 100% usage, the other was at ~5%. Really sluggish. So, the message for me is to stay with gtk2 mode until I get more capable hardware, whenever that is ;)

---

### Post by johnsd on 2016-05-23
> **kurt18947 said:**
> If you're so inclined, you could try LXLE from a pen drive. Once difference between Lubuntu & LXLE is that LXLE includes L.O. by default. However, I'm not sure if LXLE based on 16.04 is available yet.
Have tried LUbuntu with LO5 and all is good.

---

### Post by johnsd on 2016-05-23
> **vasa1 said:**
> 

Anyway, trouble-shooting or bug reporting is difficult with a document that others can't access. Here's a link to a 16.2 MB, 388-page document with quite a bit of formatting and images: 

[https://wiki.documentfoundation.org/images/f/f3/GS50-GettingStartedLO.odt](https://wiki.documentfoundation.org/images/f/f3/GS50-GettingStartedLO.odt)

It's not at all unmanageable on my system in gtk2 mode.

gtk3 mode was not fun. One CPU showed 100% usage, the other was at ~5%. Really sluggish. So, the message for me is to stay with gtk2 mode until I get more capable hardware, whenever that is ;)
Was a bit slow in gtk3 mode for say 30 seconds - after that fine with no high CPU usage.

---

### Post by johnsd on 2016-05-23
> **vasa1 said:**
> 
It's not at all unmanageable on my system in gtk2 mode.

gtk3 mode was not fun. One CPU showed 100% usage, the other was at ~5%. Really sluggish. So, the message for me is to stay with gtk2 mode until I get more capable hardware, whenever that is ;)

Tried again  the worst of my files by starting LO5 with [COLOR=#000000][FONT=Ubuntu Mono]**SAL_USE_VCLPLUGIN=gtk libreoffice --writer** [FONT=arial] but did not seem to be any different.[/FONT][/FONT][/COLOR]

---

### Post by vasa1 on 2016-05-23
> **johnsd said:**
> Have tried LUbuntu with LO5 and all is good.

> **johnsd said:**
> Tried again  the worst of my files by starting LO5 with [COLOR=#000000][FONT=Ubuntu Mono]**SAL_USE_VCLPLUGIN=gtk libreoffice --writer** [FONT=arial] but did not seem to be any different.[/FONT][/FONT][/COLOR]

Bit confused by "all is good" and "did not seem to be any different".

BTW, have you tried your documents with default fonts rather than using MS fonts?

---

### Post by johnsd on 2016-05-25
> **vasa1 said:**
> Bit confused by "all is good" and "did not seem to be any different".

BTW, have you tried your documents with default fonts rather than using MS fonts?

"All is good"  == running fine with no grey screens at load time.
"Does not seem any different" == does not improve - takes ages to become available to use.

I am a bit overloaded with things to do at the moment so will get back to check I have addressed all the points made here at some time in the near future!!

---

### Post by jrarrmy2 on 2016-06-02
I don't want to hijack this thread, hopefully adding some useful information as I am having the same issues with 16.04 and LO.


I just did a fresh install last month of 16.04 from 15.04 and identical files loaded relatively fast before and are now almost unusable.
I also tested on slower machines and they still load and scroll quite quickly.


I will provide two example documents...

1: The .doc is 1767 pages(no graphics 9mb) and loaded immediately in 15.04 and took about a minute if I wanted to scroll through all the pages into cache for instant use. I still have an old P4 machine with 12.04 which opens it instantly and caches fully in less than 3m. 

Under 16.04 it take 6m to load and is greyed out(unusable), when it's 'done loading' it only has 634 of the pages 'loaded' and are super slow to scroll, then loading the rest into cache takes an additional 6m and is still slow to respond when scrolling.

Sample file: [https://www.dropbox.com/s/xv12yhw6w9n9qgs/BibleNIV.doc?dl=0](https://www.dropbox.com/s/xv12yhw6w9n9qgs/BibleNIV.doc?dl=0)

2: The .xls is just a formula sheet (640kb) of about 4000 calculations and color-coding based on output. 

Sample file: [https://www.dropbox.com/s/8np9vwzngf369b0/atfsample.xlsx?dl=0](https://www.dropbox.com/s/8np9vwzngf369b0/atfsample.xlsx?dl=0)

---

### Post by vasa1 on 2016-06-02
> **jrarrmy2 said:**
> I don't want to hijack this thread, hopefully adding some useful information as I am having the same issues with 16.04 and LO.
...
Maybe you can tell us a little about your computer? Its RAM, CPU, etc?

---

### Post by jrarrmy2 on 2016-06-02
I was figuring it shouldn't make a difference as the specs are identical, all that's changed is the versions of Ubuntu and LO
However, I'm running 4gb ram on AMD FX-6300 6 core, 64 bit ubuntu 16.04, not sure if the right graphics driver is in yet but it shows(Gallium 0.4 on AMD CEDAR).

---

### Post by kurt18947 on 2016-06-02
I downloaded the 2 files and tried to load the .doc file on a machine running 16.04 64 bit Ubuntu-Gnome and L.O. 5.1.2.2. It crashed L.O. once and the second time I stopped loading after a few minutes when it was less than half done. I then tried opening the .doc file in MS Office 2010 running on Win10. It opened fine, took perhaps a minute off a flash drive. I then saved as an .odt file in MS Office 2010 and no idea how well MSO 2010 writes .odt files. The resulting .odt file didn't open any better in L.O. 5.1.2.2 than the .doc file. I didn't play around with the .xlsx file. I did have HTOP running and one core was pegged continuously at 100% when trying to open the .doc file so yeah, there's an issue.

Edit: Here's the process that's taking 100% of the processor thread:

```
usr/bin/libreoffice/program/soffice.bin --writer --splash-pipe=5
```

---

### Post by vasa1 on 2016-06-03
I very briefly tried the xlsx one on LibreOffice 5.1.3 Calc. No luck. BTW, the version of gnumeric supplied with 16.04 gagged with the same file.

Version: 5.1.3.2
Build ID: 1:5.1.3-0ubuntu1
CPU Threads: 2; OS Version: Linux 4.4; UI Render: default;

---

### Post by Linuxisfast on 2016-06-03
Ubuntu 16.04 all updates done, machine is i7 4790 with 16GB RAM and nvidia 610 card. The doc file loaded after getting grayed for around ten seconds. The cal loaded after 15 odd seconds. Libreoffice is latest via PPA.

---

### Post by kurt18947 on 2016-06-03
There were new L.O. files via software updates, the new version is 5.1.3.2. The .doc loading issue is not fixed on my machine, it still chokes.

---

### Post by Linuxisfast on 2016-06-03
and same story repeats with Gnome Arch linux all updated on same machine, this is a LO bug.

---

### Post by jrarrmy2 on 2016-06-03
So I uninstalled LO(Ubuntu wouldn't allow multiple office suites), although by synaptic since 'ubuntu software' hasn't opened since the first week.
Libre Office 4.4 vs Open Office 4.1

OO 4.1
Xls - loaded in 12s and was fully functional immediately, even new calculations with 100's of consequential changes were instant. Also noticed ram use was much lower 139mb ram.
Doc - loaded in 3m30s but was fully usable without scrolling to cache. 131mb ram.

Also tried LO 4.4
Xls - loaded in 30s with similarly satisfying results. 242mb ram.
Doc - loaded partial in 4m30s but had to manually scroll to cache for an additional 8m. 397mb ram.

Will try fresh install of newest LO at next internet connection.

---

### Post by vasa1 on 2016-06-03
Also please try with files that you've created using LibreOffice which haven't been exposed to MS Office (= saved as .doc or .docx and then back again).

I would expect LibreOffice to fix internal issues first and then only to address compatibility issues with essentially closed source formats.

Re. LibO versus OO, I'm guessing the latest OO would be somewhat equivalent to LibO version 4.2.something. From what I gather, OO is being maintained rather than actively being developed: see [https://forum.openoffice.org/en/forum/viewforum.php?f=107](https://forum.openoffice.org/en/forum/viewforum.php?f=107).

And here's a pdf file, from someone involved in the LibreOffice project, detailing how the two have diverged: [http://www.nouenoff.nl/downloads/LibreOffice_AOO_CompetitiveFeatureMatrix_20150318.pdf](http://www.nouenoff.nl/downloads/LibreOffice_AOO_CompetitiveFeatureMatrix_20150318.pdf). I didn't check to see if there's a newer version.

---

### Post by johnsd on 2016-06-06
As asked a number of pages ago, I have tried to change the font of the offending document from Verdana to a Linux font. After 20 minutes of waiting to edit the file, I could use <CTRL A> to select all the document but could not change the font since the options were greyed out. Deselected and the options came back. Tried to select a few pages at a time but the file was basically not usable. While this was happening, I was trying to type in this window and it slowed to the point of effectively being locked up.

So I then made a large document natively in LO - but it performed badly too.

As somebody has mentioned there has been a new version of LO released with the Ubuntu updates - but there is no improvement.

---

### Post by johnsd on 2016-06-06
So what do Ubuntu do to LO before they release it? (The version is called 1:5.1.3-0ubuntu1 so they must do something).  As far as I can see there are two possible sources for the problem:
1. The changes Ubuntu do to LO.
2. The Ubuntu kernel.

As mentioned way back, the offending file goes well in other distros and in MS Windows. It would be nice to know which of these two options is the source of the problem.

---

### Post by vasa1 on 2016-06-06
> **johnsd said:**
> So what do Ubuntu do to LO before they release it? (The version is called 1:5.1.3-0ubuntu1 so they must do something).  As far as I can see there are two possible sources for the problem:
1. The changes Ubuntu do to LO.
2. The Ubuntu kernel.

As mentioned way back, the offending file goes well in other distros and in MS Windows. It would be nice to know which of these two options is the source of the problem.
You can eliminate #1 by thoroughly uninstalling the LibreOffice from the software center and then getting the download from [https://www.libreoffice.org/download/libreoffice-fresh/](https://www.libreoffice.org/download/libreoffice-fresh/)

---

### Post by johnsd on 2016-06-06
yes - might try that when I have got time. I have been thinking - if there is no progress on this by my next teaching break I will be changing distros to (say) either Debian or Open SUSE. This is my work machine that I rely on every evening for class preparation and having LO run like this is time consuming and no joke.

---

### Post by Linuxisfast on 2016-06-06
> **johnsd said:**
> So what do Ubuntu do to LO before they release it? (The version is called 1:5.1.3-0ubuntu1 so they must do something).  As far as I can see there are two possible sources for the problem:
1. The changes Ubuntu do to LO.
2. The Ubuntu kernel.

As mentioned way back, the offending file goes well in other distros and in MS Windows. It would be nice to know which of these two options is the source of the problem.


I don't think Ubuntu changes LO, also the same behaviour with these files under Gnome Arch and Gentoo.

---

### Post by howefield on 2016-06-06
> **Linuxisfast said:**
> I don't think Ubuntu changes LO, also the same behaviour with these files under Gnome Arch and Gentoo.

One could always check the [changelogs]("https://launchpad.net/ubuntu/+source/libreoffice/+changelog") but most likely they would be meaningless to most peeps.

---

### Post by vasa1 on 2016-06-06
> **vasa1 said:**
> You can eliminate #1 by thoroughly uninstalling the LibreOffice from the software center and then getting the download from [https://www.libreoffice.org/download/libreoffice-fresh/](https://www.libreoffice.org/download/libreoffice-fresh/)

Another possibility is here: [https://wiki.documentfoundation.org/Installing_in_parallel](https://wiki.documentfoundation.org/Installing_in_parallel)

So you could keep the Ubuntu version and install the "direct" version side-by-side noting the precautions to keep user profiles separate.

---

### Post by dragonfly41 on 2016-06-06
What struck me in reading this thread is that you read LibreOffice documents some 1700 pages in length.

Recently I learned about pandoc and I'm now writing my notes in markdown which are then published via pandoc engine to different outputs (LibreOffice, PDF, web, slides presentation).

Pandoc seems to be used by lecturers.

[http://pandoc.org/README.html](http://pandoc.org/README.html)

[https://groups.google.com/forum/#!forum/pandoc-discuss](https://groups.google.com/forum/#!forum/pandoc-discuss)

So you can keep your notes as markdown snippets and just merge into the final document.

This seems to be a more agile approach to document management.

---

### Post by johnsd on 2016-06-14
I have decided after researching the state of distributions to change from Ubuntu to Fedora (have not been there since Core 5). It is so refreshing to have my files load almost instantaneously. So I guess for me the issue is solved although the problem continues.

---

### Post by ioannis.ilousis on 2016-06-15
To avoid slow User Interface update, a workaround is to: 
[LIST=1]
[*]Remove packages: libreoffice-gnome and libreoffice-gtk and libreoffice-gtk3 
[*]Restart (Close and Open) LibreOffice 
[/LIST]
After this, LibreOffice User Interface is being updated fast. But, when (main) window is resized, sometimes it becomes messy. So, avoid any unnecessary resizes (resizings), keep (main) window in full size.
It seems to be a gtk port only issue.
Workaround was tested with LibreOffice 5.1.3.2 and Ubuntu 16.04 64 bit. 
Issue was fixed in LibreOffice 5.1.4.2.

---

### Post by johnsd on 2016-06-17
Just to say I am happy with my "solution" of the problem - Fedora 13 is performing well. I have never used GNOME 3 before but thinking that it might win over Unity due to simplicity. The main thing is that my files all work - such luxury!!

---

### Post by kurt18947 on 2016-06-17
> **johnsd said:**
> Just to say I am happy with my "solution" of the problem - Fedora 13 is performing well. I have never used GNOME 3 before but thinking that it might win over Unity due to simplicity. The main thing is that my files all work - such luxury!!

What I've found with 'unadorned' GNOME 3 is that simplicity comes at a cost - lack of control & customization. It might be worth spending a few minutes at extensions.gnome.org. There are also packages in the repositories to restore GNOME 2 function re printer & user administration.

---

### Post by b-tainturier on 2016-07-05
Hello,

I have got the same issue on two different computers. Everything was fine with Ubuntu 15.10. In Ubuntu 16.04, LibreOffice is very slow with large documents.

Try this at home : create a new Writer document, copy and past many times any text to fill 100 pages, save the odt file and close LO. Then LO need more than 30 seconds to open the file et is very slow when you try to type something.

---

### Post by b-tainturier on 2016-07-09
I tried the solution proposed by ioannis.ilousis. I removed libreoffice-gnome and libreoffice-gtk (libreoffice-gtk3 was not installed). It works ! :D
But I use LibreOffice 5.1.4.2. That means that the issue is not fixed in LibreOffice 5.1.4.2.

---

### Post by Nutria on 2016-07-09
> **vasa1 said:**
> Anyway, trouble-shooting or bug reporting is difficult with a document that others can't access. Here's a link to a 16.2 MB, 388-page document with quite a bit of formatting and images: 

[https://wiki.documentfoundation.org/images/f/f3/GS50-GettingStartedLO.odt](https://wiki.documentfoundation.org/images/f/f3/GS50-GettingStartedLO.odt)

It's not at all unmanageable on my system in gtk2 mode.

gtk3 mode was not fun. One CPU showed 100% usage, the other was at ~5%. Really sluggish. So, the message for me is to stay with gtk2 mode until I get more capable hardware, whenever that is ;)

On **[SIZE=2]X[/SIZE]**ubuntu 16.04 with the Xenial LO deinstalled and v5.1.4 installed from [http://www.libreoffice.org/download/libreoffice-fresh/]("http://www.libreoffice.org/download/libreoffice-fresh/"), that document loads in seconds and paging through the 388 pages seems pretty fast.

---

### Post by Linuxisfast on 2016-07-09
The libreoffice getting started document opens and runs smoothly but with about 15 to 20% CPU load on my i7 Haswell so yes, it will run slower on lower specced machine. My LO is latest updated by Canonical, 5.1.4.2

---

### Post by Nutria on 2016-07-09
> **b-tainturier said:**
> I tried the solution proposed by ioannis.ilousis. **I removed libreoffice-gnome and libreoffice-gtk** (libreoffice-gtk3 was not installed). **It works !** :D
But I use LibreOffice 5.1.4.2. **That means that the issue is not fixed in LibreOffice 5.1.4.2**.

Since libreoffice-gtk and libreoffice-gtk3 are not part of the debs supplied by LibreOffice.org, what it tells me is that the Gtk integration is what slows down LO, and **that** is the problem, not LibreOffice.

---

### Post by b-tainturier on 2016-07-10
I agree with Nutria. Maybe we should report this bug of **libreoffice-gtk** on _bugs.launchpad.net_ ?

---

### Post by b-tainturier on 2016-08-10
The bug of **libreoffice-gtk **is reported here :
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1577093](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1577093)

---

### Post by vasa1 on 2016-08-10
> **b-tainturier said:**
> The bug of **libreoffice-gtk **is reported here :
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1577093](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1577093)
Thank you for sharing the bug report link.

In case anyone is interested in trying LibreOffice 5.2, please read [http://www.omgubuntu.co.uk/2016/08/install-libreoffice-5-2-on-ubuntu-ppa](http://www.omgubuntu.co.uk/2016/08/install-libreoffice-5-2-on-ubuntu-ppa) especially> LibreOffice 5.2 uses the newer LibreOffice-GTK2, so you’ll need to manually remove the old version before LibreOffice can be upgraded ...

---

