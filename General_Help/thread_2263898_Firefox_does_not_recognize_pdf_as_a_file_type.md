---
title: "Firefox does not recognize pdf as a file type"
date: 2015-02-04
forum: General Help
---

### Post by gwm on 2015-02-04
Lately, when I try to open a pdf file while browsing with Firefox, it fails to recognize pdf file types. I have searched the forums and all I can find is 2 other posts about Gedit. Those threads failed to pick up that Firefox wasn't recognizing the file type and that is why it was offering Gedit. Trying to fix how to view pdf file types is fruitless since Firefox uses those settings for known file types. In this case, it is telling us that the file type is not known.

I checked if this problem was already posted and found this link.
[http://ubuntuforums.org/showthread.php?t=1603961&highlight=Firefox+pdf+file+type](http://ubuntuforums.org/showthread.php?t=1603961&highlight=Firefox+pdf+file+type)

Two users mentioned they also had this problem but no one responded. So I'm trying again.
I have Firefox 35.0.1 on Ubuntu Unity, 14.10.
Nautilus and Thunderbird recognize pdf just fine.

I am guessing that it is somehow related to plugins but I don't know how to reset Firefox's ability to recognize file types.
I recently tried some plugins for saving video streams. Perhaps one of them clobbered some setting. I finally chose DownloadHelper 4.9.24. Disabling it doesn't help though.

Can someone help me with resetting Firefox's ability to recognize pdf files as a known file type?
Thanks

---

### Post by TheFu on 2015-02-04
I think it might be a security setting. Firefox should open PDF files that are not local - keep them in a sandbox. Opening local files is a security violation to firefox and breaks that sandbox model.
I use one of the many other PDF viewers - evince, xournal, okular ... for local files.

Firefox is a beachhead for system security. Lose that and everything is lost.

I have no idea what thunderbird would do with a PDF ... here it send it to evince. It doesn't view it.

---

### Post by SeijiSensei on 2015-02-04
In Firefox, Edit > Preferences > Applications.  Find the entry for "Portable Document Format" and click on it. You'll see a drop-down box that lets you choose the application to open the file, probably evince or okular depending on your flavor of Ubuntu.

---

### Post by vasa1 on 2015-02-04
> **gwm said:**
> Lately, when I try to open a pdf file while browsing with Firefox, it fails to recognize pdf file types. ...
What happens when you click on [http://dl.fullcirclemagazine.org/issue89_en.pdf?](http://dl.fullcirclemagazine.org/issue89_en.pdf?)

If you have a local .pdf file, what happens when you open it via File > Open?

For me, in both cases, Firefox uses its internal pdf.js reader to open the files. I'm on Firefox 35.0.1 (direct from Mozilla) and Lubuntu 14.04.

---

### Post by vasa1 on 2015-02-04
And what do you see when you search for *pdf* in *about:config*? Here's what I see:

---

### Post by gwm on 2015-02-04
> **SeijiSensei said:**
> In Firefox, Edit > Preferences > Applications.  Find the entry for "Portable Document Format" and click on it. You'll see a drop-down box that lets you choose the application to open the file, probably evince or okular depending on your flavor of Ubuntu.

Hi,
Thanks for all the replies!
It feels like either SeijiSensei didn't read my post or I am so fixed in my understanding of the problem that I am missing something. I believe I have done all those things. I have screen shots of the error and the application settings but don't know how to include them in this post. The error message basically says:
[I][B]You have chosen to open:
blah_blah.pdf
which is: _unknown_ (1.1MB)
from: [http://download.website.org](http://download.website.org)

What should Firefox do with this file?[/B][/I]

Then it offers me radio buttons for gedit(default) or save file.
If I save the file then double click on it in the file browser, everything is fine. However, Firefox doesn't recognize a pdf file as being a pdf file. We have told it what to do with pdf files but it doesn't know that it has one.
Also, because it feels this is an unknown type, the check box to automatically apply one's choice is disabled (grayed out).

It feels to me like the code goes through something like
if type is A then apply app_A
else if type is B then apply app_B
else if type is C then apply app_C
...
else offer gedit since no matching type was found

What SeijiSensei is telling me to do is done. That process pairs type A with app_A, type B with app_B etc. The type pdf pairing is there but since it doesn't know it has  a type pdf, it doesn't apply app_pdf and falls through to the default clause of the switch construct.

> **vasa1 said:**
> And what do you see when you search for *pdf* in *about:config*? Here's what I see:

I'd like to be able to respond but unfortunately I don't know how to do that.
Maybe if I knew what about:config? was I could then answer your question.

---

### Post by TheFu on 2015-02-04
about:config - that is how to access firefox's settings. Just type it in on the URL like, <enter>

Have you tried different PDFs? Does it work?  1 PDF could be corrupt.  Linux doesn't use extensions to determine file types. It uses "magic numbers" which are part of the header in each file. If that isn't correct, Unix systems don't know what to do with a file.

---

### Post by gwm on 2015-02-04
> **vasa1 said:**
> What happens when you click on [http://dl.fullcirclemagazine.org/issue89_en.pdf?](http://dl.fullcirclemagazine.org/issue89_en.pdf?)

If you have a local .pdf file, what happens when you open it via File > Open?

For me, in both cases, Firefox uses its internal pdf.js reader to open the files. I'm on Firefox 35.0.1 (direct from Mozilla) and Lubuntu 14.04.

I tried clicking and I get a blank tab - maybe because the question mark is in the url
I'm putting it here without the question mark so I can try again: [http://dl.fullcirclemagazine.org/issue89_en.pdf](http://dl.fullcirclemagazine.org/issue89_en.pdf) then I'll post what happened.
File>Open on a local pdf file works 100%.

Hi vasa1,
It is a big pdf so it took a while before displaying for me in a seperate tab:

Full Circle THE INDEPENDENT MAGAZINE FOR THE UBUNTU LINUX COMMUNITY
ISSUE #89 - September 201 4

with all the graphics etc. displaying correctly.

It seems then, that the problem only manifests itself when we are downloading a pdf.
Thank you for helping to narrow it down this far.

---

### Post by mc4man on 2015-02-04
Why don't you just provide a link to one of these problem pdf files, that's where the issue is really..

---

### Post by gwm on 2015-02-04
> **TheFu said:**
> I have no idea what thunderbird would do with a PDF ... here it send it to evince. It doesn't view it.

Thunderbird itself isn't doing the reading, it is when I open a pdf attachment.

All this fiddling has changed my Firefox behaviour. Somehow clicking on the fullcircle link has corrected something.
Now it recognizes the downloads as being pdf. What changed matters, I don't know. Now I can get consistent behaviour from it.
in the applications settings I have tried a few options.
1. save the file - it now recognizes that it is a pdf and works fine
2. always ask - it now recognizes that it is a pdf and offers me evince or save
3. use document viewer (default) - it now recognizes that it is a pdf but doen't display. instead it asks and offers me gedit or save
4. use adobe reader (in firefox) - it doesn't ask, doesn't display but saves the file directly to downloads folder
5. preview in Firefox - doen't preview. instead asks and offers gedit or save with save selected
6. use evince - asks and offers me evince or save

It seems that gedit is now set as the default document viewer. Where is this setting? How does one put it back the way it was?

> **mc4man said:**
> Why don't you just provide a link to one of these problem pdf files, that's where the issue is really..

The behaviour is consistent for all the pdf downloads I have and in diverse applications, such as viewing my service account with the council. To do that, I had to switch to my Windows VM and view it from Internet Explorer. Now things have changed a bit and I can set Firefox to always ask.
Here is a link to a download pdf file:

[http://download.jw.org/files/media_magazines/ac/wp_E_20150201.pdf](http://download.jw.org/files/media_magazines/ac/wp_E_20150201.pdf)

---

### Post by mc4man on 2015-02-04
> **gwm said:**
> . Now things have changed a bit and I can set Firefox to always ask.
Here is a link to a download pdf file:

[http://download.jw.org/files/media_magazines/ac/wp_E_20150201.pdf](http://download.jw.org/files/media_magazines/ac/wp_E_20150201.pdf)
That one works fine here in that FF recognizes the filetype & 'offers' to either open in Docu viewer or save,  scr. 1
(- it doesn't open in FF's viewer

Does your pop up use gedit in the ^ link or is it like my screen?

Small ex. that opens in FF's viewer - 
[http://www.analysis.im/uploads/seminar/pdf-sample.pdf](http://www.analysis.im/uploads/seminar/pdf-sample.pdf)

In this case if  I click on the small download icon in upper r. toolbar I get a similar popup, if you were to  do this,  is it proper or use gedit? (scr. 2

---

### Post by mc4man on 2015-02-04
> **gwm said:**
> It seems that gedit is now set as the default document viewer. Where is this setting? How does one put it back the way it was?

right click on any .pdf > properties > open with. Choose app, then click set as default button

---

### Post by gwm on 2015-02-06
Now that FF has somehow started recognizing that the files are pdf, the behaviour is now influenced by the settings. Like in the post I made above, there are six options and the check box for "Do this automatically for files like this from now on." is always disabled (Grayed out).

I don't know what is special about the links you have given me. I did each of the following and then clicked on your sample link.

1. Set application to use Document Viewer (Default).
    My links offered gedit as before but your test file opened directly in the Document Viewer.
2. Set application to view in FF
    With this option my links misbehaved, offering me gedit or save but yours did everything like in your sample pictures.
    In this case, with your file, I could set the automatic behaviour. The check box was enabled.

I have been thinking to reinstall FF. To this end, I have exported my book marks and saved a screen shot or two of all my saved passwords.
Now I am not sure it will help. The behaviour seems to depend on the data. It doesn't depend on the website, because I am clicking on the two links in your posting.
I don't know how these things work. Does the source website report the type to the web browser and in this case it is doing something different?

I don't know what is special about the links you have given me. I did each of the following and then clicked on your sample link.

1. Set application to use Document Viewer (Default).
    My links offered gedit as before but your test file opened directly in the Document Viewer.
2. Set application to view in FF
    With this option my links misbehaved, offering me gedit or save but yours did everything like in your sample pictures.
    In this case, with your file, I could set the automatic behaviour. The check box was enabled.

I have been thinking to reinstall FF. To this end, I have exported my book marks and saved a screen shot or two of all my saved passwords.
Now I am not sure it will help. The behaviour seems to depend on the data. It doesn't depend on the website, because I am clicking on the two links in your posting.
I don't know how these things work. Does the source website report the type to the web browser and in this case is it doing something different?

I have tried FF on my Windows 7 virtual machine. It is a brand new install (the VM never had it before) from the Mozilla website. Next I imported my bookmarks.
I set the application to be "Preview in Firefox" and once again, the behavior is different for the two files.
The link you supplied creates a new tab and opens a preview there. When I click the download icon, it opens the what to do dialog, offering Adobe Reader or Save, with the Save radio button preselected.
The "from now on" check box is enabled.
Absolutely perfect!!

However, the link I supplied does not open in a preview tab.
Instead, it asks what to do. Since this is now a Windows environment, it offers Adobe Reader or Save with the "Open With" radio button preselected.
The "from now on" check box is _disabled_

What is the difference? I don't get it.
At any rate, all this testing has somehow magically fixed my FF in Ubuntu so that it once again recognizes pdf formats

---

### Post by SeijiSensei on 2015-02-06
> **gwm said:**
> Does the source website report the type to the web browser?
Well-behaved web servers that comply with the [HTTP/1.1 specification]("http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html") should send a Content-Type header that reports the MIME type of each object.  A PDF should be sent with "Content-Type: application/pdf" as its MIME type.
> and in this case it is doing something different?
Can't answer that, I'm afraid.

---

### Post by gwm on 2015-02-06
Thanks for all your help guys.
We haven't found out why pdfs were not being recognised and then what fixed it.
I suppose that would need one to be sitting with the source code for Firefox and run it with a debugger.
I haven't ever got to writing code in a Linux environment so I suppose we need to close this thread and call it solved.
Thank you all for your help.

---

### Post by mc4man on 2015-02-06
> **gwm said:**
> 

However, the link I supplied does not open in a preview tab.
Instead, it asks what to do. Since this is now a Windows environment, it offers Adobe Reader or Save with the "Open With" radio button preselected.
The "from now on" check box is disabled

What is the difference? I don't get it.


well maybe because the link you provided is a download link

---

### Post by Prodoc on 2015-05-19
Where the link to [http://download.jw.org/files/media_magazines/ac/wp_E_20150201.pdf](http://download.jw.org/files/media_magazines/ac/wp_E_20150201.pdf) caused the problem of the file being offered to be opened with gedit to occur, the link to [http://www.analysis.im/uploads/seminar/pdf-sample.pdf](http://www.analysis.im/uploads/seminar/pdf-sample.pdf) did not and offered me to open it with document viewer as expected.

The difference is the server configuration. The first file is offered with the *application/octet-stream* mime-type, the latter with *application/pdf* mime-type as it should be.
To prevent Firefox from opening every file offered with the general *application/octet-stream* mime-type with gedit you should alter the following files:

[list]
[*]~/.local/share/applications/mimeapps.list
[*]~/.config/mimeapps.list
[/list]

Find the following line in those files and remove it.
> application/octet-stream=gedit.desktop;

Save the file, restart Firefox and enjoy your downloads again.

---

### Post by gwm on 2015-05-20
Wow! Thank you Prodoc.
In my case, only **~/.config/mimeapps.list** had the octet-stream entry.
I have fixed it and now it runs correctly, as you said it would.

(As a thought, perhaps one could somehow dumb that down and somehow offer a "forget setting" when asking the user whether they want to use gedit or whatever. Maybe under preferences?)

---

### Post by gwm on 2015-05-20
Wow! Thank you Prodoc.
In my case, only **~/.config/mimeapps.list** had the octet-stream entry.
I have fixed it and now it runs correctly, as you said it would.

(As a thought, perhaps one could somehow dumb that down and somehow offer a "forget setting" when asking the user whether they want to use gedit or whatever. Maybe under preferences?)

---

### Post by TheFu on 2015-05-20
For a deeper understanding, not directly related ... 

Just be aware that whatever you do to modify which programs are used to open which mime-types are GUI specific - gnome has different settings than other "desktop environments" though some do overlap. Linux doesn't care about extensions at all. The 'magic number' for a file matters more and should work across the platform ... except browser downloads (I suppose). For any file, you can get the file type using the "file" command.   Open a terminal, and run it on a few different files to see the different results.
$ file /etc/hosts
$ file /bin/bash
$ file /usr/lib/i386-linux-gnu/libc.a
$ file /usr/lib/i386-linux-gnu/libc.so
$ file /usr/bin/cautious-launcher

Of course, you'll want to change the arch value to x86_64, if that is your system type. Magic numbers are used in the CLI.

---

