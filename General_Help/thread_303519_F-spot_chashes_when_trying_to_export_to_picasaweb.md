---
title: "F-spot chashes when trying to export to picasaweb"
date: 2006-11-20
forum: General Help
---

### Post by honda on 2006-11-20
I'm completely unable to get f-spot to export anything to picasaweb gallery. The first time I clicked the picasaweb menu item a dialog opened. I clicked the add gallery button and entered my google username and password. Gnome-keyring asked me to create a keyring which I did. Then f-spot crashed... Now whenever I click the export to picasaweb menu item, f-spot instantly crashes.. This is the error info given:

[I]
An unhandled exception was thrown: Object reference not set to an instance of an object

  at Mono.Google.Picasa.PicasaWeb.GetAlbums () [0x00000] 
  at FSpot.GoogleExport.PopulateAlbumOptionMenu (Mono.Google.Picasa.PicasaWeb picasa) [0x00000] 
  at FSpot.GoogleExport.Connect (FSpot.GoogleAccount selected, System.String token, System.String text) [0x00000] 
  at FSpot.GoogleExport.Connect (FSpot.GoogleAccount selected) [0x00000] 
  at FSpot.GoogleExport.Connect () [0x00000] 
  at FSpot.GoogleExport..ctor (IBrowsableCollection selection) [0x00000] 
  at MainWindow.HandleExportToPicasa (System.Object sender, System.EventArgs args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr gch) [0x00000] 
  at (wrapper native-to-managed) GLib.Signal:voidObjectCallback (intptr,intptr)
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) Gtk.Application:gtk_main ()
  at Gtk.Application.Run () [0x00000] 
  at Gnome.Program.Run () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 1.1.4322.2032[/I]

Anybody have some clues? Googleing the subject does not reveal anything, seems to be working for everybody but me.

---

### Post by Johnny5Net on 2006-11-20
I have the same problem, It seems related to the gnome keyring. When I delete the value called google account from the key ring then I can get to the export dialog in f-spot, but when f-spot tries to work with the keyring again, it crashes. 

I'm on Edgy with F-spot 0.2.1

---

### Post by honda on 2006-11-21
Nice to know I'm not alone.. The same goes for me, if I delete the key in keyring, I get to the export dialog again. Also I figured out that if I enter a wrong password in the dialog, it sort of reqognizes that the password was wrong, without crashing, and asks for a new one. That sort of confirms that it is really talking to google. But as soon as I enter the correct password it crashes again. 

One thing I maybe did wrong was that I tried the 'export to picasaweb' feature before I had actually created a picasaweb account, that is google account existing but no picasaweb album. If that is what's causing the crash, how can I revert the situation? Tried uninstalling, reinstalling f-spot. Deleteing fspot folder, deleteing .gnome2/f-spot, deleteing keyring...

Anyone got this working on edgy? I might even try reinstalling, if someone confirms that it is working on edgy.

---

### Post by anomie.lin on 2006-11-22
hey guys, I got the same problem with f-spot. I don't know how to delete the keyring. Would you tell me how to do this to make the export to picasaweb work again? 

Thank you ~!

---

### Post by honda on 2006-11-23
Actually, deleteing the key does NOT help, it will only let you enter your username&password again, but it will crash like before.

If someone is using picasaweb export without problems, please let me know, even if you have absolutely no idea how to help us...

---

### Post by Freedreamer on 2006-11-23
same problem!!!
](*,) ](*,)

---

### Post by honda on 2006-11-24
So here is the answer:
[http://comments.gmane.org/gmane.comp.gnome.apps.f-spot/2572]("http://comments.gmane.org/gmane.comp.gnome.apps.f-spot/2572")
[I]
"It means that google changed slightly the protocol for the export to
picasaweb.
This issue is already fixed in CVS, the fix will be available in the
next release and I hope that package maintainers will backport (package
maintainers, contact me if you need help) the fix to the packaged
versions of f-spot."[/I]

Hopeing for a backport then... Or maybe try to compile myself...

---

### Post by Freedreamer on 2006-11-24
how can install CVS version?  is there a .deb ?

---

### Post by machaval on 2006-11-24
I have try to compile it but i fail over and over. Isn't there any repository where we can download it.

---

### Post by machaval on 2006-11-24
is this fixed under the 0.2.2 version?

---

### Post by Freedreamer on 2006-11-24
no in 0.2.2 there is the bug

---

### Post by machaval on 2006-11-24
When I try to compile the cvs repository version i get this error
checking for System.Runtime.Remoting.dll... configure: error: missing required mono 2.0 DLL: System.Runtime.Remoting.dll
How can i fix it?

---

### Post by Freedreamer on 2006-11-24
same error.....

---

### Post by machaval on 2006-11-24
Is there any way that we can find the patch for this fix so that it can be applied to 0.2.2?

---

### Post by Freedreamer on 2006-11-24
mhhh no. the problem is fixed only in the cvs :(

---

### Post by machaval on 2006-11-24
What i mean if may be you know where to downalod the fix and a add it manually to my 0.2.2 code.

---

### Post by Freedreamer on 2006-11-24
i don't know.

---

### Post by prashmohan on 2006-11-27
> **machaval said:**
> When I try to compile the cvs repository version i get this error
checking for System.Runtime.Remoting.dll... configure: error: missing required mono 2.0 DLL: System.Runtime.Remoting.dll
How can i fix it?

System.Runtime.Remoting.dll seems to be part of libmono-system-runtime2.0-cil

---

### Post by honda on 2006-11-29
F-spot 0.3.0 has been released. I just compiled it and picasaweb export works. Available from [http://www.f-spot.org/Download]("http://www.f-spot.org/Download")

---

### Post by spykecub on 2006-11-29
> **honda said:**
> F-spot 0.3.0 has been released. I just compiled it and picasaweb export works. Available from [http://www.f-spot.org/Download]("http://www.f-spot.org/Download")

sounds great - but... not too good at compiling here - any idea if a .deb is going to be made or the repos are going to be updated with 0.3.0?

---

### Post by honda on 2006-11-30
I guess you can check when it is added to feisty and then file a backport request. But, really, compiling wasn't hard. I'm a noob myself on this, but this is how I did it: 

You might have to start by installing the build-essentials package, I had it already installed.

Then:
*sudo apt-get install mono-gmcs libmono-sqlite2.0-cil libmono-cairo2.0-cil*
(from [http://www.f-spot.org/How_To_Build_from_CVS](http://www.f-spot.org/How_To_Build_from_CVS))

Download the archive, extract to eg. ~/f-spot-0.3.0
run the configure script in there: 
*./configure*
It will complain about missing libraries. Search with synaptic for the missing library (and the -dev version of it) and install it. Try ./configure again... Some libraries doesn't match with their package names for some reason, "google ubuntu package <missing library name>" was my friend
The mono.pc file is in package libmono-dev
System.Runtime.Remoting.dll is in package libmono-system-runtime2.0-cil

When it doesn't complain any more run:
*make all*

and when it succeeds, run:
*sudo checkinstall*
It asks for a name for the package and then installs it

And this is NOT a HOW-TO. Just a beginner's notes how he did it to encourage other beginners to try...

---

### Post by anomie.lin on 2006-11-30
I have successfully compiled the new f-spot on my ubuntu edgy. Here is my process. Hope it is helpful.

(This is actually the first time I compile something by myself. And I am so excited.. hoho :P)

First, follow the guide on [http://f-spot.org/How_To_Build_from_Release]("/http://f-spot.org/How_To_Build_from_Release")

```
sudo apt-get build-dep f-spot
sudo apt-get install automake1.9 build-essential intltool libtool
```

Then, download the new f-spot at [http://ftp.gnome.org/Public/GNOME/sources/f-spot/0.3/f-spot-0.3.0.tar.bz2]("http://ftp.gnome.org/Public/GNOME/sources/f-spot/0.3/f-spot-0.3.0.tar.bz2"), and use tar or file-roller or any other tools to extract the package to any direction, and then enter the direction.

If you run ./configure now, it will give out a lot of errors to say some files are missing, for example, mono.pc, etc. I think the simplest way to install these missing files is to use apt-file.

```
sudo apt-get install apt-file
```

Then, use apt-file to find out which package is the missing file in. For example, for missing file mono.pc:

```
apt-file search mono.pc
```

It will show you the name of the package who contains mono.pc. Then use apt-get to install the package.

Do this again and again until ./configure gives no error. Then:

```
sudo make all 
```

On my edgy system, it gives some error message and aborted. The error message says:

** (/usr/lib/mono/2.0/gmcs.exe:7638): WARNING **: Could not load file or assembly 'Mono.Cairo, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

It seems the file 'Mono.Cairo' is missing. (Why there is no warning during configuration? ) Use apt-file to find it. It is in the package libmono-cairo2.0-cil. Install it. Then do make again:

```
sudo make all
sudo make install
```

Now everything is OK.


Here I list all the packages I installed during the process, in case you don't want to use apt-file

```
sudo apt-get build-dep f-spot
sudo apt-get install automake1.9 build-essential intltool libtool libmono-cairo2.0-cil libmono-sqlite2.0-cil libmono-system-runtime2.0-cil libmono-dev
 
```

---

### Post by anomie.lin on 2006-11-30
Oh.. is it so simple? I met a little more problem while compiling it. Anyway, I will write out my compiling process. :)

> **honda said:**
> I guess you can check when it is added to feisty and then file a backport request. But, really, compiling wasn't hard. I'm a noob myself on this, but this is how I did it: 

You might have to start by installing the build-essentials package, I had it already installed.

Then:
*sudo apt-get install mono-gmcs libmono-sqlite2.0-cil libmono-cairo2.0-cil*
(from [http://www.f-spot.org/How_To_Build_from_CVS](http://www.f-spot.org/How_To_Build_from_CVS))

Download the archive, extract to eg. ~/f-spot-0.3.0
run the configure script in there: 
*./configure*
It will complain about missing libraries. Search with synaptic for the missing library (and the -dev version of it) and install it. Try ./configure again... Some libraries doesn't match with their package names for some reason, "google ubuntu package <missing library name>" was my friend
The mono.pc file is in package libmono-dev
System.Runtime.Remoting.dll is in package libmono-system-runtime2.0-cil

When it doesn't complain any more run:
*make all*

and when it succeeds, run:
*sudo checkinstall*
It asks for a name for the package and then installs it

And this is NOT a HOW-TO. Just a beginner's notes how he did it to encourage other beginners to try...

---

### Post by rlaska on 2006-12-01
There's a bug report for this:
[https://launchpad.net/distros/ubuntu/+source/f-spot/+bug/69427](https://launchpad.net/distros/ubuntu/+source/f-spot/+bug/69427)

---

### Post by anomie.lin on 2006-12-03
that's a different bug.

---

### Post by bdp on 2006-12-11
By following the instructions here
[http://ubuntuforums.org/showthread.php?t=268687](http://ubuntuforums.org/showthread.php?t=268687)
I was able to build my own backport of f-spot.  It's not perfect, but it is allowing me to upload pictures to picasaweb. (When uploading an album of 195 pictures, it crashes once in a while and has to be restarted.  I had to do this four or five times to get all 195 pictures uploaded.)

I have submitted a bug report suggesting that f-spot be added to the edgy backports repository. In the meantime I've put the .deb at [http://www.stat.ufl.edu/~presnell/Downloads/](http://www.stat.ufl.edu/~presnell/Downloads/)
in case anyone is interested.  I'll try to leave it there until something appears on the backports respository.

---

### Post by uBob on 2006-12-30
Thanks for posting the backport version. As a newby (3 days linux&ubuntu experience...) I'm not yet ready for doing a compile myself. Your files installed without any problem. The upload feature now works. Thanks again!

---

### Post by State on 2007-01-08
I've build a deb package with checkinstall

[http://www.ulfmaier.de/ubuntu/f-spot_0.3.0-1_i386.deb](http://www.ulfmaier.de/ubuntu/f-spot_0.3.0-1_i386.deb)

have fun

---

### Post by Hoshimaru on 2007-01-31
I'm trying to build a .deb for f-spot 0.3.2 
Whenever I try to run **dpkg-buildpackage -rfakeroot** or [B]sudo make install
[/B], I get this error: 
```
/home/jcapraro/Source/f-spot-0.3.2/libeog/ui-image.c:134: undefined reference to `g_source_remove'
.libs/zoom.o: In function `zoom_fit_size':
/home/jcapraro/Source/f-spot-0.3.2/libeog/zoom.c:75: undefined reference to `g_assert_warning'
/home/jcapraro/Source/f-spot-0.3.2/libeog/zoom.c:52: undefined reference to `g_return_if_fail_warning'
collect2: ld returned 1 exit status
make[3]: *** [libfspoteog.la] Error 1
make[3]: Leaving directory `/home/jcapraro/Source/f-spot-0.3.2/libeog'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/jcapraro/Source/f-spot-0.3.2/libeog'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/jcapraro/Source/f-spot-0.3.2/libeog'
make: *** [install-recursive] Error 1
jcapraro@naruto:~/Source/f-spot-0.3.2$ 
```
Any idea what could be wrong ?

---

### Post by Hoshimaru on 2007-02-20
Eeeeeh ?! What kind of error is this ?

[http://img487.imageshack.us/img487/9761/screenshotip4.png](http://img487.imageshack.us/img487/9761/screenshotip4.png)

Does it mean my F-Spot is somehow not working as it should or does my host fail to do its job? My Gallery² is hosted by [www.free.fr](www.free.fr)

---

### Post by avilella on 2007-03-29
> **bdp said:**
> By following the instructions here
[http://ubuntuforums.org/showthread.php?t=268687](http://ubuntuforums.org/showthread.php?t=268687)
I was able to build my own backport of f-spot.  It's not perfect, but it is allowing me to upload pictures to picasaweb. (When uploading an album of 195 pictures, it crashes once in a while and has to be restarted.  I had to do this four or five times to get all 195 pictures uploaded.)

I have submitted a bug report suggesting that f-spot be added to the edgy backports repository. In the meantime I've put the .deb at [http://www.stat.ufl.edu/~presnell/Downloads/](http://www.stat.ufl.edu/~presnell/Downloads/)
in case anyone is interested.  I'll try to leave it there until something appears on the backports respository.

I succesfully installed this deb but still I get the authentication error:

GoogleAccount.Connect()
Can't get the albums
Can not connect to Picasa. Bad username ? password ? network connection ?
Can't get the albums
GoogleAccount.Connect()
Can't get the albums
Can not connect to Picasa. Bad username ? password ? network connection ?
Can't get the albums

Do I need to activate any option in picasaweb to allow this? I am using edgy.

---

### Post by jms830 on 2007-03-29
> GoogleAccount.Connect()
Can't get the albums
Can not connect to Picasa. Bad username ? password ? network connection ?
Can't get the albums
GoogleAccount.Connect()
Can't get the albums
Can not connect to Picasa. Bad username ? password ? network connection ?
Can't get the albums

I get the same error.

---

### Post by macness on 2008-06-01
I'm reviving this thread here...

It seems that this behavior was not fixed in Hardy?

I tried to export a photo to picasaweb unsuccessfully today.  Initially, I was able to enter in my credentials, but now, I select a photo and then go to file>export to>picasaweb and it crashes.

](*,)](*,)

---

### Post by donatell0 on 2008-06-06
Same problem for me in Hardy 8.04! This is the only way to upload to pictures to Picasa without installing extensions to firefox or installing Picasa neither of which I can do right now :confused:

Any help is appreciated!

---

### Post by Freedreamer on 2008-06-06
try deb i've made for last version

[http://www.freedreamer.it/wp-content/uploads/2008/05/f-spot_044_i386.deb](http://www.freedreamer.it/wp-content/uploads/2008/05/f-spot_044_i386.deb)

---

### Post by donatell0 on 2008-06-07
Why don't you submit a patch or file a bug report so that the fixed version can go upstream?

[EDIT]: The deb you gave me also had the same problem. When I try to export, it crashes. It did not even ask me to enter any account details.

---

### Post by macness on 2008-06-07
Installed the deb and it still crashes, so this is definitely in need of a bug report. :(

Edit: So I did :) [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/238212]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/238212")

---

### Post by ryth on 2008-06-15
Same problem here on Hardy when exporting to Picasa.  Irritating to say the least.  Anyone come up with any new info?

Added this info to the bug report, but maybe someone will have some insight over here.  This is the output of f-spot --debug:

```

** Running f-spot in Debug Mode **
** Running Mono with --debug   **
Starting new FSpot server
Reloading
item changed
error checking orientation
System.IO.FileNotFoundException: Could not find uri "file:///home/ryth/Photos/2002/01/30/110 Bloor St W. Mural-5-2.jpg".
  at Gnome.Vfs.VfsStream..ctor (System.String text_uri, FileMode mode, Boolean async) [0x00000] 
  at Gnome.Vfs.VfsStream..ctor (System.String uri, FileMode mode) [0x00000] 
  at (wrapper remoting-invoke-with-check) Gnome.Vfs.VfsStream:.ctor (string,System.IO.FileMode)
  at FSpot.ImageFile.Open () [0x00000] 
  at FSpot.ImageFile.PixbufStream () [0x00000] 
  at FSpot.AsyncPixbufLoader.Load (System.Uri uri) [0x00000] 
  at FSpot.PhotoImageView.PhotoItemChanged (FSpot.BrowsablePointer item, FSpot.BrowsablePointerChangedArgs args) [0x00000] 

(f-spot:19207): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
System.IO.FileNotFoundException: Could not find uri "file:///home/ryth/Photos/2002/01/30/110 Bloor St W. Mural-5-2.jpg".
  at Gnome.Vfs.VfsStream..ctor (System.String text_uri, FileMode mode, Boolean async) [0x00000] 
  at Gnome.Vfs.VfsStream..ctor (System.String uri, FileMode mode) [0x00000] 
  at (wrapper remoting-invoke-with-check) Gnome.Vfs.VfsStream:.ctor (string,System.IO.FileMode)
  at FSpot.ImageFile.Open () [0x00000] 
  at FSpot.JpegFile.get_Header () [0x00000] 
  at FSpot.JpegFile.Select (StatementSink sink) [0x00000] 
  at InfoBox+ImageInfo..ctor (FSpot.ImageFile img) [0x00000] 
  at InfoBox.Update () [0x00000] 
GoogleAccount.Connect()
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentOutOfRangeException: Index is less than 0 or more than or equal to the list count.
Parameter name: index
0
  at System.Collections.ArrayList.get_Item (Int32 index) [0x00000] 
  at System.Collections.Specialized.NameObjectCollectionBase.BaseGet (Int32 index) [0x00000] 
  at Mono.Google.Picasa.PicasaAlbumCollection.get_Item (Int32 index) [0x00000] 
  at FSpotGoogleExport.GoogleExport.HandleAlbumOptionMenuChanged (System.Object sender, System.EventArgs args) [0x00000] 
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.OptionMenu.gtk_option_menu_set_menu(IntPtr , IntPtr )
   at Gtk.OptionMenu.gtk_option_menu_set_menu(IntPtr , IntPtr )
   at Gtk.OptionMenu.set_Menu(Gtk.Widget value)
   at FSpotGoogleExport.GoogleExport.PopulateAlbumOptionMenu(Mono.Google.Picasa.PicasaWeb picasa)
   at FSpotGoogleExport.GoogleExport.Connect(FSpotGoogleExport.GoogleAccount selected, System.String token, System.String text)
   at FSpotGoogleExport.GoogleExport.Connect(FSpotGoogleExport.GoogleAccount selected)
   at FSpotGoogleExport.GoogleExport.Connect()
   at FSpotGoogleExport.GoogleExport.Run(IBrowsableCollection selection)
   at FSpot.Extensions.ExportMenuItemNode.OnActivated(System.Object o, System.EventArgs e)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)

```

---

