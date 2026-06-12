---
title: "Upload image preview: BIG show stopper for wife"
date: 2007-06-25
forum: General Help
---

### Post by MCSE_Crossover on 2007-06-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89381](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89381) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ok. Although i'm the computer guy in the house, my wife has a big problem with linux that she just can't seem to get over and I can't find a fix for. I know there is currently a bug report listed for this issue, but I am wondering if there is anyone that has found a fix or work around for this issue.

My wife communicates with a lot of people on MySpace. But it isn't only for that program. It is really for any online source that you try to upload pictures for. And I have tried to find a work around for this on both Gnome and KDE, but cannot. I would like to get this working in Firefox because this seems to be the most stable browser.

For example, in Firefox, if i'm on a website and I want to upload a picture, when I am browsing the files on my local machine, I am not able to view a preview picture of an image file. Using Firefox on both Gnome and KDE, it seems to bring up a very similar file browser. I can see the text description, but have no option to have a preview pane or even switch the view to "Thumbnail." You know how in Windows when browsing for files, you can change the view to "Thumbnails, tiles, icons, list, or details?" There is no option for this under Firefox.

I've tried Opera under Kubuntu, and it doesn't give the option to preview an image either when browsing for files. The strange thing is, it uses a DIFFERENT file browser when selecting files then Firefox or Konquerer does.

Now, Konquerer DOES give the option to preview the images, but for some strange reason, every time I try to upload images, Konquerer crashes. Konquerer crashes quite a bit on me when doing anything having to do with Java or Flash, so this is a no go as well.

I just don't understand why each web browser uses a different native web browser. Is there a way to change the specification? Why is it that some programs, like OpenOffice or Gimp will allow image previews when searching your files, but the web browser won't? This just seems rediculous.

I hope I explained this clearly enough. If you need further clarification on anything, please let me know and i'll try to explain the best I can...

Thanks "community" !!

---

### Post by Happy_Man on 2007-06-25
Lemme get this straight.... your problem is that neither Konq, nor Firefox, nor Opera gives you image previews? Konq would be the logical choice for this, as you need a web browser and a filemanager, but Konqueror is no go. 

Each web browser doesn't use its own file selector, Konq uses its own (KDE standard) and Firefox and Opera use a version of GNOME's. I can't explain it any better than that.....

As far as I know, Konq seems your ideal solution, but Konq is crashing. Perhaps we should fix the crash issue first, then you'll be able to use it. Could you please run Konq from a terminal and crash it again. Then post whatever is in the terminal here. Thanks!

---

### Post by MCSE_Crossover on 2007-06-25
Yes, your description is exactly correct. I actually think you understand it perfectly. Rock on!

I will have to do the Konq crash tonight when I get home as I am at work right now. The issue it that happens in Konq occurs on MySpace when trying to upload photos to your profile. I believe the window is either flash or java based. I can click browse, find the image, select it - but then when I hit "ok" is when it crashes. Weirdness. I'll be sure to post that bug report tonight.

On a side note...Opera and Firefox use the Gnome browser? Why is that? I thought it looked a little "gnome'ish." They are both GTK-based applications? Is there a way to *switch* their default browsing method?

---

### Post by Happy_Man on 2007-06-25
> **MCSE_Crossover said:**
> Yes, your description is exactly correct. I actually think you understand it perfectly. Rock on!

I will have to do the Konq crash tonight when I get home as I am at work right now. The issue it that happens in Konq occurs on MySpace when trying to upload photos to your profile. I believe the window is either flash or java based. I can click browse, find the image, select it - but then when I hit "ok" is when it crashes. Weirdness. I'll be sure to post that bug report tonight.

On a side note...Opera and Firefox use the Gnome browser? Why is that? I thought it looked a little "gnome'ish." They are both GTK-based applications? Is there a way to *switch* their default browsing method?
Doubt it.... not without good knowledge of code.... which I don't have. Yes, Firefox and Opera are both GTK-based at the moment, which explains the dialog look. Opera however, is rumored to go Qt-based in the next few releases.

---

### Post by MCSE_Crossover on 2007-06-25
Good deal. i'll be sure to post those dumps tonight.

---

### Post by MCSE_Crossover on 2007-06-25
Ok. Here is the dump. Hope this helps:

@Cronos:~$ konqueror
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(process:15398): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:15398): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 84 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
KCrash: Application 'nspluginviewer' crashing...

---

### Post by MCSE_Crossover on 2007-06-25
Here is the backtrace from the browser window:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1233021232 (LWP 15864)]
[New Thread -1267881072 (LWP 15868)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb6a77460 in pthread_mutex_lock ()
   from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb79ccf26 in pthread_mutex_lock () from /lib/tls/i686/cmov/libc.so.6
#8  0xb6036858 in ?? () from /home/kevin/.mozilla/plugins/libflashplayer.so
#9  0xb48bf024 in ?? ()
#10 0x08099b08 in ?? ()
#11 0xbfaa4884 in ?? ()
#12 0xb64e812c in ?? () from /home/kevin/.mozilla/plugins/libflashplayer.so
#13 0x00000000 in ?? ()

---

### Post by Beatbreaker on 2007-07-08
MCSE - it might be better next time if you wrap those dumps in between ["CODE"] ["/CODE"] brackets (without the "")

i'm also interested in this one, i'm getting trustrated when uploading images to different programs (mainly firefox and thunderbird) and not being able to browse the pictures that i've got on there. This should really be a fundamental issue being addressed on a later release - i don't know how ppl cope without it really.

anyway to illustrate what i mean here a screenshot of me browsing for a pic attachment in thunderbird:

[IMG]http://img486.imageshack.us/img486/215/previewpicsge4.png[/IMG]

---

### Post by meditator1 on 2007-07-13
I too find the portion of this thread dealing with no preview of images when sending mail with Thunderbird annoying. Surely more than two users find this troubling. Any suggestions?

Thanks.
meditator1
Carl

---

### Post by yabbadabbadont on 2007-07-13
There is already a thread around here somewhere about the lack of image previews when using GTK+ file dialogs.  I think that it started as a rant about features that Windows Explorer has that Nautilus doesn't and then changed into a dicussion about the GTK+ file selectors.

---

### Post by MCSE_Crossover on 2007-07-14
Again though...I don't think it is straight up GTK+ file dialogs because some programs take advantage of that file picker but have the features available. Specifically, the ones that seem to really be lacking are Mozilla based products (Thunderbird and Firefox. Look at my attachments. The first is an image of Gimp - with the preview available. The second is an "open file" dialog from Firefox.

---

### Post by yabbadabbadont on 2007-07-14
Well, according to the GTK+ programming documentation, it appears to me that it is up to the individual application to provide a custom preview widget, which can then be displayed in the dialog.  I would guess that this is what the Gimp developers have done.  I think that QT actually provides a preview option itself, instead of making each individual application do it.  I'm not positive about that though as I haven't read the QT programming docs.

Here is the relevant GTK+ documentation section:
[http://developer.gnome.org/doc/API/2.0/gtk/GtkFileChooser.html#GtkFileChooser--preview-widget](http://developer.gnome.org/doc/API/2.0/gtk/GtkFileChooser.html#GtkFileChooser--preview-widget)

---

### Post by MCSE_Crossover on 2007-07-14
Well, what makes it even more annoying is that when launching Firefox or Thunderbird from within KDE - it still uses the GTK file picker. Sucks, huh?

---

### Post by yabbadabbadont on 2007-07-14
> **MCSE_Crossover said:**
> Well, what makes it even more annoying is that when launching Firefox or Thunderbird from within KDE - it still uses the GTK file picker. Sucks, huh?

Those applications are designed using and compiled against the GTK+ libraries.  It doesn't matter at all which window manager/desktop environment you are using when you launch them.  Just FYI.  :D

---

### Post by marsbt on 2007-07-14
Just tested Konqueror 3.5.7-2 for a file upload on a Debian box and was able to see preview images and it successfully uploaded an image too. Just wanted to post it so that everyone knows that crash is not KDE bug.

---

### Post by ldrn on 2007-07-14
Hello! I hope this is able to help.  I just checked, and it should preview images the way you want; there's a delicious little program someone wrote that allows you to use the KDE file dialog with some gtk apps.  It works great with firefox, not so great with some others... but it should solve your problem.

You do need to have KDE installed, but you can use gnome; the latest version of it works fine with either.

If you changed ui.allow_platform_file_picker to false, you need to change it back to true. If you don't know what I'm talking about, then don't worry about it -- it doesn't do image previews either, although it is nicer than the default one.

If your architecture is i386, you can download a .deb package here -- it says Edgy, but it works fine on Feisty as well:
[http://www.kde-apps.org/content/show.php/KGtk+for+Kubuntu+Edgy?content=58584]("http://www.kde-apps.org/content/show.php/KGtk+for+Kubuntu+Edgy?content=58584")

If you have AMD64, you can get a package here:
[http://members.inode.at/499177/software/kubuntu/kgtk_0.8-1_amd64.deb]("http://members.inode.at/499177/software/kubuntu/kgtk_0.8-1_amd64.deb")

Otherwise, you'll have to compile it with the link here:
[http://www.kde-apps.org/content/show.php?content=36077]("http://www.kde-apps.org/content/show.php?content=36077")

After it is installed, close firefox and open a terminal and type:
sudo ln -s /usr/bin/kgtk-wrapper /usr/local/bin/firefox

(Your path will be different if you compiled it from source. In fact, I wasn't able to find the wrapper script when I compiled and ended up copying it from my x86 box.)

It'll work after that from the command line; you may have to edit your menu items or shortcuts to say "/usr/local/bin/firefox %u"  instead of "firefox %u"; I'm not sure.

You should now be able to get thumbnail previews -- right click and select view -- if everything worked alright. If it did, you'll be able to tell as soon as you to to open or save something; it won't look anything like the GTK dialogs.  Good luck!

---

### Post by cutlerite on 2007-12-16
Is there a way to install this without KDE?  I can't believe there isn't a larger demand for this.

---

### Post by markst on 2007-12-25
This lack of previewing images in Firefox when uploading is one BIG issue my wife has with linux.  She'd be a good convert from Windows if it weren't for this problem.  I hope someone either at Firefox or Ubuntu or wherever incorporates this feature.  Little annoying things like this can be a real turnoff to users like my wife who just want things to work.  No excuses please from the Linux geeks on this either.  Fix it and be done with it.  

Take care,

Mark:confused:

---

