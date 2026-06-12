---
title: "Can't view thumbnail previews"
date: 2017-09-09
forum: General Help
---

### Post by russkyca on 2017-09-09
Ubuntu is switching to Gnome as the default DE but it is not good with 'files' in my opinion - why can't they figure out what name to use?!?   It's called 'Files' now?   Before it was called 'nautilus?'

Anyway, the GUI options for this program is not good in Gnome in my opinion.   I searched how to view thumbnail previews and apparently, the default is not to show them but you have to change the setting.   Okay, except it is not there for the program, 'Files!'

There's a few older 'solutions' but they don't seem to apply as those options aren't there.    There were, at least, intuitive.   Look at how easy it used to be?:
[https://askubuntu.com/questions/539902/how-can-i-view-thumbnails-of-pictures](https://askubuntu.com/questions/539902/how-can-i-view-thumbnails-of-pictures)

I don't know what the CLI solution is or I'd try it.  

I guess that is why Ubuntu is falling in the distrowatch list because they keep changing things and making it worse?

I am still trying to google/web search this problem as it's annoying when you have a bunch of pictures etc. loaded from a smartphone but can't tell which is which/what is what since each thumbnail is a 'tree branch' picture.   

I think it used to work but the most recent load of the data on the phone, there is no thumbnail preview (pic).

I don't think it's a Gnome issue either.... (those solutions from the older posts look like the user is using Unity).

Edit:  THIS -> [https://help.ubuntu.com/stable/ubuntu-help/nautilus-preview.html](https://help.ubuntu.com/stable/ubuntu-help/nautilus-preview.html)
Does not work either.

---

### Post by russkyca on 2017-09-09
Update:   I booted up my other OS in another partition - Ubuntu 16.04 Gnome - the thumbnails load but again, I cannot find the options to change the preview settings.

Does anyone know how?   And can anyone answer my question - why does Ubuntu Documentation state there is a setting to change the preview?   They are talking about 17.04 and the program 'Files' (formerly, Nautilus) but I couldn't find it anywhere.

They claim it works for local files but I don't see any option to do that - in any location.

That is why it's so frustrating even though it seems like a minor thing.   

Also, I booted up my last partition with an OS there - Kubuntu - I forget what version it is - but, the situation is even worse.   It sometimes cannot open my smartphone files.   Dolphin fails until I click my phone and also, the bottom right corner menu pops up with two 'notifications' (identical).    This was one reason I decided to go with Gnome instead of KDE - I would always have problems when I wanted to access my phone with the OS/computer.    So, I guess Kubuntu is still out as an option.   The KDE/phone access problem has been going on several versions in a row - they still haven't fixed the problem.   

Anyway, that is just strange.

IF only Gnome didn't mess around with the file browser program.

---

### Post by russkyca on 2017-09-09
[https://askubuntu.com/questions/888707/how-to-enable-thumbnail-previews-in-nautilus-in-xubuntu-16-04](https://askubuntu.com/questions/888707/how-to-enable-thumbnail-previews-in-nautilus-in-xubuntu-16-04)

Others have the same question (?) but someone keeps giving unhelpful answers (I would say worse but maybe that will be removed?).   

It's a simple question - is there a way to obtain the options in settings someplace?   Because the new file program, 'Files' has almost no options at all and there's nothing intuitive that allows you to change / add thumbnail previews.   So, you see a 'clock' or 'tree/tree branch' pic for every file or a 'movie projector' pic for every video file instead of preview pic.   There should be a setting allowing an option to show the preview pic if one wants it.

Edit:  To be clear, the problem where there's no thumbnail preview at all - is Ubuntu Gnome 17.04.   I had an extra partition so I upgraded the Ubuntu version to that (17.04)

On my 'main' OS - or main system - I left it at 16.04 and there, when I try everything the same - to access my files from my smartphone, the thumbnail preview works - it works as it should (as I think it should) but I don't see any settings for the thumbnail preview option (that is, it doesn't look like there is one - same issue as in 'Files' using 17.04).

I appreciate any assistance/advice/help and I hope it's less confusing now.

---

### Post by russkyca on 2017-09-09
Is it a bug?   See:
[https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/1665602](https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/1665602)

I am also using linux kernel, 4.10
$ uname -r
4.10.0-33-generic

Gnome version is 3.24

---

### Post by russkyca on 2017-09-09
I got it to work.

Here's what I did:
1) I rebooted - I changed the login mode from Gnome Classic to regular Gnome
2) I started 'Files'
3) the window looked the same; the settings looked the same....was gonna give up....disappointed .....but..
4) I noticed at the top left - the icon and file name is there - whatever you are working on.....
5) I went to the icon and with the mouse pointer over the icon, I right-clicked
6) After the right-click, there was a drop down 'menu' with the option for 'Preferences'
7) this is the 'Preferences' option I kept reading about - clicking that had the 'Thumbnail' options under the 'Search and Preview' heading

I changed something there - to 'all files' and changed the size of files - to a larger number.... not sure which is needed but maybe 'all files' is required?

Anyway, it's now working although I'll boot back to 'Gnome Classic' to see if there is a way to do it there.   It's disappointing if there isn't.   

I guess I was just lucky to find this and it's very COUNTER intuitive.   If anyone talks to Gnome developers, it's Mickey Mouse, imho.   You shouldn't have to go to the 'small icon' on the top left to find 'Preferences.'   C'mon...Please?

Someone must agree with me here?

---

### Post by Geoffrey_Arndt on 2017-09-09
Of course you can always right-click any graphic file in Nautilus (files) and then choose to open with the program of your choice.   If you like Thumbnails, then install "gthumb" or even "digikam" . . . . don't need the file manager program to view and manage thumbnails at all.

---

