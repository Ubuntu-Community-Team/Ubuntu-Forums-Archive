---
title: "PyMusique:How do i add a country?"
date: 2005-05-15
forum: General Help
---

### Post by madzzoni on 2005-05-15
I just installed pymusique to use for [www.itunes.dk](www.itunes.dk) and it's very nice, but how do i add Denmark to the country-list?

I seems that i need some kind of a 6-digit number for that, but i don't know where to find it! :-?

---

### Post by rwabel on 2005-05-15
[QUOTE=madzzoni]I just installed pymusique to use for [www.itunes.dk](www.itunes.dk) and it's very nice, but how do i add Denmark to the country-list?

I seems that i need some kind of a 6-digit number for that, but i don't know where to find it! :-?[/QUOTE]
 I think the new stores aren't in that version of pymusique integrated. I guess there will soon coming an updated version. 

there is also sharpmusique, maybe they have more stores, but I couldn't compile it so far.

---

### Post by Bo Rosén on 2005-05-15
Sharpmusique does indeed have the new stores for us Scandinavians. It doesn't seem to add proper tags however and I've no idea how to do that with another application.

---

### Post by rwabel on 2005-05-15
[QUOTE=Bo Rosén]Sharpmusique does indeed have the new stores for us Scandinavians. It doesn't seem to add proper tags however and I've no idea how to do that with another application.[/QUOTE]
 could you compile it or did you find a compiled package?

---

### Post by Bo Rosén on 2005-05-16
I compiled it. If I remember correctly all I did was 'make'. But you need all the Mono stuff as well of course.

---

### Post by rwabel on 2005-05-16
I do have mono installed, maybe I'm missing something. From where did you get the gtk-sharp 2? Here are the errors I get
 ```
Checking for System.Web.dll...yes
Checking for ICSharpCode.SharpZipLib.dll...yes
gtksharp=`if pkg-config --exists gtk-sharp-2.0; then echo -pkg:gtk-sharp-2.0 -pkg:glade-sharp-2.0; else echo -pkg:gtk-sharp -pkg:glade-sharp; fi`; \
mcs  -target:winexe -out:SharpMusique.exe -r:System.Web.dll -r:ICSharpCode.SharpZipLib.dll $gtksharp -resource:SharpMusique.glade -resource:AboutDialog.glade -resource:AlertDialog.glade -resource:LoginDialog.glade -resource:RedeemDialog.glade -resource:TextDisplayDialog.glade -resource:PurchaseDialog.glade -resource:SharpMusique.png -resource:COPYING -win32icon:SharpMusique.ico ./AssemblyInfo.cs ./SharpMusique.cs ./FairStore.cs ./iTMS.cs ./Utility.cs ./GladeDialog.cs ./AboutDialog.cs ./AlertDialog.cs ./LoginDialog.cs ./RedeemDialog.cs ./TextDisplayDialog.cs ./PurchaseDialog.cs ./VLC.cs ./CompatFileChooser.cs ./MP4.cs
./FairStore.cs(1264) error CS0165: Use of unassigned local variable `strSubmit'
./SharpMusique.cs(256) warning CS0169: The private method 'SharpMusique.OnWindowDeleteEvent( object,  Gtk.DeleteEventArgs)' is never used
./SharpMusique.cs(289) warning CS0169: The private method 'SharpMusique.OnPreferences( object,  System.EventArgs)' is never used
./SharpMusique.cs(374) warning CS0169: The private method 'SharpMusique.OnLogin( object,  System.EventArgs)' is never used
./SharpMusique.cs(390) warning CS0169: The private method 'SharpMusique.DoAlertBox( AlertType,  string)' is never used
./SharpMusique.cs(419) warning CS0169: The private method 'SharpMusique.OnLoginStateChanged( bool)' is never used
./SharpMusique.cs(437) warning CS0169: The private method 'SharpMusique.OnPendingSongs( object,  System.EventArgs)' is never used
./SharpMusique.cs(457) warning CS0169: The private method 'SharpMusique.OnAbout( object,  System.EventArgs)' is never used
./SharpMusique.cs(462) warning CS0169: The private method 'SharpMusique.OnSearch( object,  System.EventArgs)' is never used
./SharpMusique.cs(514) warning CS0169: The private method 'SharpMusique.DoTreeViewUpdate( object)' is never used
./SharpMusique.cs(740) warning CS0169: The private method 'SharpMusique.OnRedeemPepsiCap( object,  System.EventArgs)' is never used
./SharpMusique.cs(772) warning CS0169: The private method 'SharpMusique.OnRedeemGiftCertificate( object,  System.EventArgs)' is never used
./SharpMusique.cs(806) warning CS0169: The private method 'SharpMusique.OnRowActivated( object,  Gtk.RowActivatedArgs)' is never used
./SharpMusique.cs(843) warning CS0169: The private method 'SharpMusique.OnButtonPressEvent( object,  Gtk.ButtonPressEventArgs)' is never used
./SharpMusique.cs(938) warning CS0169: The private method 'SharpMusique.OnSignup( object,  System.EventArgs)' is never used
./SharpMusique.cs(969) warning CS0169: The private method 'SharpMusique.OnSignupEvent( System.Collections.Hashtable)' is never used
./FairStore.cs(49) warning CS0169: The private field 'FairStore.signupCCTypeHandled' is never used
./VLC.cs(65) warning CS0169: The private method 'VLC.VLC_AddIntf( int,  string,  bool,  bool)' is never used
./VLC.cs(67) warning CS0169: The private method 'VLC.VLC_Die( int)' is never used
./VLC.cs(85) warning CS0169: The private method 'VLC.VLC_PositionGet( int)' is never used
./VLC.cs(87) warning CS0169: The private method 'VLC.VLC_PositionSet( int,  float)' is never used
./VLC.cs(89) warning CS0169: The private method 'VLC.VLC_TimeGet( int)' is never used
./VLC.cs(91) warning CS0169: The private method 'VLC.VLC_TimeSet( int,  int,  bool)' is never used
./VLC.cs(93) warning CS0169: The private method 'VLC.VLC_LengthGet( int)' is never used
./VLC.cs(95) warning CS0169: The private method 'VLC.VLC_SpeedFaster( int)' is never used
./VLC.cs(97) warning CS0169: The private method 'VLC.VLC_SpeedSlower( int)' is never used
./VLC.cs(99) warning CS0169: The private method 'VLC.VLC_PlaylistIndex( int)' is never used
./VLC.cs(101) warning CS0169: The private method 'VLC.VLC_PlaylistNumberOfItems( int)' is never used
./VLC.cs(109) warning CS0169: The private method 'VLC.VLC_VolumeSet( int,  int)' is never used
./VLC.cs(111) warning CS0169: The private method 'VLC.VLC_VolumeGet( int)' is never used
./VLC.cs(113) warning CS0169: The private method 'VLC.VLC_VolumeMute( int)' is never used
./VLC.cs(115) warning CS0169: The private method 'VLC.VLC_FullScreen( int)' is never used
./CompatFileChooser.cs(260) warning CS0169: The private method 'CompatFileChooserDialog.gtk_file_chooser_dialog_new_with_backend( string,  System.IntPtr,  int,  string,  System.IntPtr)' is never used
./MP4.cs(298) warning CS0169: The private method 'MP4Box.ParseSTSD( System.IO.BinaryReader)' is never used
./MP4.cs(304) warning CS0169: The private method 'MP4Box.ParseMP4A( System.IO.BinaryReader)' is never used
./MP4.cs(309) warning CS0169: The private method 'MP4Box.ParseDRMS( System.IO.BinaryReader)' is never used
./MP4.cs(335) warning CS0169: The private method 'MP4Box.ParseSTSZ( System.IO.BinaryReader)' is never used
./MP4.cs(357) warning CS0169: The private method 'MP4Box.ParseSTCO( System.IO.BinaryReader)' is never used
./MP4.cs(376) warning CS0169: The private method 'MP4Box.ParseSTSC( System.IO.BinaryReader)' is never used
./MP4.cs(403) warning CS0169: The private method 'MP4Box.ParseMETA( System.IO.BinaryReader)' is never used
./MP4.cs(459) warning CS0169: The private method 'MP4Box.WriteBytesSTSZ( System.IO.MemoryStream)' is never used./MP4.cs(481) warning CS0169: The private method 'MP4Box.WriteBytesSTCO( System.IO.MemoryStream)' is never used./MP4.cs(500) warning CS0169: The private method 'MP4Box.WriteBytesSTSC( System.IO.MemoryStream)' is never usedCompilation failed: 1 error(s), 42 warnings
make: *** [SharpMusique.exe] Error 1

```

---

### Post by Bo Rosén on 2005-05-20
[QUOTE=rwabel]I do have mono installed, maybe I'm missing something. From where did you get the gtk-sharp 2? Here are the errors I get
[/QUOTE]

Not sure. I have backports and the manno repositories for mono and beagle stuff, so it should be from one of those two I guess. As far as I can remember, I followed the istructions at [http://beaglewiki.org/Ubuntu_Installation](http://beaglewiki.org/Ubuntu_Installation)

---

### Post by rwabel on 2005-05-20
q[QUOTE=Bo Rosén]Not sure. I have backports and the manno repositories for mono and beagle stuff, so it should be from one of those two I guess. As far as I can remember, I followed the istructions at [http://beaglewiki.org/Ubuntu_Installation]("http://beaglewiki.org/Ubuntu_Installation")[/QUOTE]
indeed I'm missing mono-devl,,how could I miss that one because I also went through that wiki and I've installed beagle. I've compiled several mono based application..strange!

well, this didn't help neither :-(

---

