---
title: "Banter .deb packages"
date: 2007-05-22
forum: General Help
---

### Post by wolf08 on 2007-05-22
I'm looking at the Banter project ([http://live.gnome.org/Banter](http://live.gnome.org/Banter)) and it looks very interesting to me. I would like to try it out, but when I try and find its dependencies, they don't seem to have any counterparts in apt repositories.

My question is - does anyone have .debs for Banter? Alternatively, does anyone have a list of the debian dependencies that banter has?

I'm actually running an x64 machine, but I have an x32 laptop that will work if someone only has x32 .debs. 

Thanks!

---

### Post by fsf@rula on 2007-06-04
Yeah, well, I have gotten past the frigging jscall dependency, but now I need gnome-keyring-sharp, which I can't compile and can't get to install, this sucks, if you have a solution, that would be nice.
I'm trying to compile on gutsy.
the debian deps should be similar as on the banter building page, if they are in ubuntu repos. (as jscall-cil and libgnome-keyring-cil are not)

hope you have more luck, I'll post a package if I ever get it compiled.

---

### Post by ButteBlues on 2007-06-04
I couldn't manage to build gnome-keyring-sharp either.

---

### Post by fsf@rula on 2007-06-06
Well it's impossible to compile banter with ubuntu libs, you need telepathy (telepathy-sharp) svn stuff, gnome-keyring-sharp svn etc. , I guess I'll wait 'till they get voip (soon) to work and then I might give it an other try.

---

### Post by fsf@rula on 2007-06-10
well, they now have both voip and video support for jingle, but they say it's impossible to get video going at all in ubuntu without compiling gstreamer, and also I haven't been able to run banter yet.

---

### Post by fsf@rula on 2007-06-11
I've created a new thread for gutsy jingle: [http://ubuntuforums.org/showthread.php?p=2821642](http://ubuntuforums.org/showthread.php?p=2821642) , if you have any info about clients capable of jingl/voip, please tell us!

---

### Post by puccaso on 2007-08-06
ok this is gonna sound dumb

i got the src files from here

[http://download.opensuse.org/repositories/telepathy/openSUSE_Factory/src/](http://download.opensuse.org/repositories/telepathy/openSUSE_Factory/src/)

i unpacked each src rpm and installed manurally

this is where it went wrong
```

root@jt-laptop:/tmp/banter# make
Making all in Banter
make[1]: Entering directory `/tmp/banter/Banter'
gmcs -out:Banter.exe  Application.cs AssemblyInfo.cs AvatarButton.cs AvatarManager.cs AvatarMenuItem.cs AvatarSelector.cs AudioView.cs TrayLib.cs Message.cs AccountManagement.cs Account.cs Utilities.cs Person.cs PersonGroup.cs PersonManager.cs PersonSync.cs PersonView.cs PersonCard.cs Presence.cs ProviderUser.cs ProviderUserManager.cs Conversation.cs ConversationManager.cs ComplexMenuItem.cs ChatType.cs ChatWindow.cs ChatWindowManager.cs MessagesView.cs NotificationArea.cs NotificationData.cs NotificationManager.cs GConfPreferencesProvider.cs Preferences.cs PreferencesDialog.cs XmlFilePreferencesProvider.cs Logger.cs ActionManager.cs VideoView.cs Avatar.cs AvatarRequirements.cs GroupWindow.cs InterruptableTimeout.cs HIGMessageDialog.cs StatusEntry.cs SidebarTextButton.cs UriList.cs Defines.cs -r:System -r:Mono.Posix -r:System.Xml -r:/usr/lib/cli/ndesk-dbus-glib-1.0/NDesk.DBus.GLib.dll -r:/usr/lib/cli/ndesk-dbus-1.0/NDesk.DBus.dll   -r:/usr/lib/cli/ndesk-dbus-1.0/NDesk.DBus.dll   -r:/usr/lib/Gnome.Keyring/Gnome.Keyring.dll   -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gconf-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gconf-sharp-peditors.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/art-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-vfs-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/art-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-vfs-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-dotnet.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:/usr/lib/pkgconfig/../../lib/telepathy-sharp/INdT.Telepathy.dll -r:/usr/lib/pkgconfig/../../lib/telepathy-sharp/NDesk.DBus.dll   -r:/usr/lib/mono/notify-sharp/notify-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll    -resource:../data/images/banter-16.png -resource:../data/images/banter-22.png -resource:../data/images/banter-24.png -resource:../data/images/banter-32.png -resource:../data/images/banter-44.png -resource:../data/images/blank-photo-128.png -resource:../data/images/blank-photo.svg -resource:../data/images/mic.png -resource:../data/images/text.png -resource:../data/images/webcam.png -resource:./UIManagerLayout.xml 
AvatarSelector.cs(57,39): warning CS0168: The variable `imageItem' is declared but never used
AvatarSelector.cs(55,30): warning CS0219: The variable `recentMenu' is assigned but its value is never used
Account.cs(1134,52): warning CS0168: The variable `dis' is declared but never used
PersonCard.cs(214,29): warning CS0612: `Gtk.ProgressBar.BarStyle' is obsolete
Conversation.cs(672,30): warning CS0219: The variable `i' is assigned but its value is never used
Conversation.cs(736,46): warning CS0219: The variable `infos' is assigned but its value is never used
Conversation.cs(716,30): warning CS0168: The variable `tempStreamId' is declared but never used
Conversation.cs(813,46): warning CS0219: The variable `infos' is assigned but its value is never used
Conversation.cs(777,30): warning CS0168: The variable `tempStreamId' is declared but never used
ConversationManager.cs(166,33): error CS0150: A constant value is expected
ConversationManager.cs(209,33): error CS0150: A constant value is expected
Compilation failed: 2 error(s), 9 warnings
make[1]: *** [Banter.exe] Error 1
make[1]: Leaving directory `/tmp/banter/Banter'
make: *** [all-recursive] Error 1
root@jt-laptop:/tmp/banter# 

```


any ideas?

---

### Post by puccaso on 2007-08-06
EDIT:

also

i tried the svn and the source tar
and i get the same error on both

---

### Post by denkedran on 2007-08-07
how did you manage the gnome-keyring-sharp dependency ?
according to this site ([http://russell.rucus.net/2005/gnome-keyring-sharp/]("http://russell.rucus.net/2005/gnome-keyring-sharp/") this library is Deprecated cause of a new api. therefor, there is no package in gutsy that suplies the dll :confused:

EDIT: ok now i see you compiled the old gnome-keyring-sharp api from the source of suse servers

---

### Post by fago on 2007-10-11
anyone tried again with the latest gutsy?

---

