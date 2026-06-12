---
title: "F-Spot Null Reference When trying to use picasaweb gallery"
date: 2006-11-24
forum: General Help
---

### Post by machaval on 2006-11-24
I am having problems using f-spot 0.2.1 under edgy when trying to export a picture to the photo alnum
```

System.NullReferenceException: Object reference not set to an instance of an object
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

```


Does anyone have this problem? It happens when i open the export-> picasaweb. So i'm being stuck. Does any one knows where the configuration files of this is being saved. Is this fixed in a new version of picasa. If yes does anyone knows where to download the .deb file.
Thanks for any answer.
Machaval

---

### Post by fragos on 2006-11-24
I'm using the 0.2.1 version of F-spot that came with Edgy 6.10 and have been successfully exporting to Picasa albums on the web.

---

