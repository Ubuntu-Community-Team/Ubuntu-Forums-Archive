---
title: "Major, major problems with MonoDevelop"
date: 2005-10-15
forum: General Help
---

### Post by Hikaru79 on 2005-10-15
This happened in Breezy's beta too, but I was hoping it would be fixed by the official release -- it hasn't been.

It's very simple. I open MonoDevelop, I open a solution, it crashes. Here's the stack trace:```
hikaru79@ubuntu:~$ monodevelop
2005-10-15 13:40:59,773 [-1208846112] INFO  MonoDevelop.Services.ILoggingService [(null)] - Reading /home/hikaru79/.config/MonoDevelop/CodeCompletionData/mscorlib_1.0.5000.0_b77a5c561934e089.pidb
2005-10-15 13:41:00,017 [-1208846112] INFO  MonoDevelop.Services.ILoggingService [(null)] - WARNING Could not find stock Icons.16x16.FindPrevIcon
2005-10-15 13:41:00,050 [-1208846112] INFO  MonoDevelop.Services.ILoggingService [(null)] - WARNING Could not find stock gtk-stop
2005-10-15 13:41:00,114 [-1208846112] INFO  MonoDevelop.Services.ILoggingService [(null)] - Creating DefaultWorkbench
Socket already in use
2005-10-15 13:41:07,246 [-1208846112] INFO  MonoDevelop.Services.ILoggingService [(null)] - WARNING Could not find stock gtk-open
2005-10-15 13:41:07,986 [-1227904080] INFO  MonoDevelop.Services.ILoggingService [(null)] - Reading /home/hikaru79/.config/MonoDevelop/CodeCompletionData/gtk-sharp_1.0.0.0_35e10195dab3c99f.pidb
2005-10-15 13:41:08,012 [-1227904080] INFO  MonoDevelop.Services.ILoggingService [(null)] - Reading /home/hikaru79/.config/MonoDevelop/CodeCompletionData/glib-sharp_1.0.0.0_35e10195dab3c99f.pidb
2005-10-15 13:41:08,060 [-1227904080] INFO  MonoDevelop.Services.ILoggingService [(null)] - Reading /home/hikaru79/.config/MonoDevelop/CodeCompletionData/System_1.0.5000.0_b77a5c561934e089.pidb
2005-10-15 13:41:08,128 [-1227904080] INFO  MonoDevelop.Services.ILoggingService [(null)] - Reading /home/hikaru79/.config/MonoDevelop/CodeCompletionData/System.Xml_1.0.5000.0_b77a5c561934e089.pidb
2005-10-15 13:41:08,142 [-1227904080] INFO  MonoDevelop.Services.ILoggingService [(null)] - Reading /home/hikaru79/.config/MonoDevelop/CodeCompletionData/gdk-sharp_1.0.0.0_35e10195dab3c99f.pidb
2005-10-15 13:41:08,152 [-1227904080] INFO  MonoDevelop.Services.ILoggingService [(null)] - Reading /home/hikaru79/.config/MonoDevelop/CodeCompletionData/pango-sharp_1.0.0.0_35e10195dab3c99f.pidb
2005-10-15 13:41:08,162 [-1227904080] INFO  MonoDevelop.Services.ILoggingService [(null)] - Reading /home/hikaru79/.config/MonoDevelop/CodeCompletionData/atk-sharp_1.0.0.0_35e10195dab3c99f.pidb
2005-10-15 13:41:08,169 [-1227904080] INFO  MonoDevelop.Services.ILoggingService [(null)] - Reading /home/hikaru79/.config/MonoDevelop/CodeCompletionData/glade-sharp_1.0.0.0_35e10195dab3c99f.pidb
2005-10-15 13:41:08,240 [-1208846112] INFO  MonoDevelop.Services.ILoggingService [(null)] - WARNING Could not find stock gtk-save

(MonoDevelop:16439): Gdk-CRITICAL **: gdk_cursor_new_for_display: assertion `GDK_IS_DISPLAY (display)' failed

(MonoDevelop:16439): Gdk-CRITICAL **: gdk_cursor_new_for_display: assertion `GDK_IS_DISPLAY (display)' failed
2005-10-15 13:41:22,293 [-1208846112] INFO  MonoDevelop.Services.ILoggingService [(null)] - WARNING Could not find stock gtk-open

** (MonoDevelop:16439): WARNING **: Cannot load type 'Pango.UnderlineGType, pango-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'

** (MonoDevelop:16439): WARNING **: Cannot load type 'Pango.UnderlineGType, pango-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'
Error while loading System.NullReferenceException: Object reference not set to an instance of an object
in <0x00164> GLib.GType:op_Explicit (System.Type type)
in <0x0005c> GLib.Value:.ctor (System.Object obj)
in <0x00033> Gtk.TextTag:set_Underline (Underline value)
in <0x0020d> MonoDevelop.SourceEditor.Gui.SourceEditorBuffer:.ctor ()
in <0x00039> MonoDevelop.SourceEditor.Gui.SourceEditor:.ctor (MonoDevelop.SourceEditor.Gui.SourceEditorDisplayBindingWrapper bind)
in <0x00139> MonoDevelop.SourceEditor.Gui.SourceEditorDisplayBindingWrapper:.ctor ()
in <0x00019> MonoDevelop.SourceEditor.Gui.SourceEditorDisplayBinding:CreateContentForFile (System.String fileName)
in <0x00023> MonoDevelop.Services.DefaultFileService+LoadFileWrapper:Invoke (System.String fileName)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_string (string)
in <0x00014> MonoDevelop.Core.Services.FileUtilityService+LoadWrapper:Invoke ()
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
in <0x00018> MonoDevelop.Core.Services.FileUtilityService:ObservedLoad (MonoDevelop.Core.Services.FileOperationDelegate saveFile, System.String fileName, System.String message, FileErrorPolicy policy)
2005-10-15 13:41:28,169 [-1208846112] INFO  MonoDevelop.Services.ILoggingService [(null)] - WARNING Could not find stock gtk-open

** (MonoDevelop:16439): WARNING **: Cannot load type 'Pango.UnderlineGType, pango-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'

** (MonoDevelop:16439): WARNING **: Cannot load type 'Pango.UnderlineGType, pango-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'
Error while loading System.NullReferenceException: Object reference not set to an instance of an object
in <0x00164> GLib.GType:op_Explicit (System.Type type)
in <0x0005c> GLib.Value:.ctor (System.Object obj)
in <0x00033> Gtk.TextTag:set_Underline (Underline value)
in <0x0020d> MonoDevelop.SourceEditor.Gui.SourceEditorBuffer:.ctor ()
in <0x00039> MonoDevelop.SourceEditor.Gui.SourceEditor:.ctor (MonoDevelop.SourceEditor.Gui.SourceEditorDisplayBindingWrapper bind)
in <0x00139> MonoDevelop.SourceEditor.Gui.SourceEditorDisplayBindingWrapper:.ctor ()
in <0x00019> MonoDevelop.SourceEditor.Gui.SourceEditorDisplayBinding:CreateContentForFile (System.String fileName)
in <0x00023> MonoDevelop.Services.DefaultFileService+LoadFileWrapper:Invoke (System.String fileName)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_string (string)
in <0x00014> MonoDevelop.Core.Services.FileUtilityService+LoadWrapper:Invoke ()
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
in <0x00018> MonoDevelop.Core.Services.FileUtilityService:ObservedLoad (MonoDevelop.Core.Services.FileOperationDelegate saveFile, System.String fileName, System.String message, FileErrorPolicy policy)

(MonoDevelop:16439): Gdk-CRITICAL **: gdk_cursor_new_for_display: assertion `GDK_IS_DISPLAY (display)' failed

** (MonoDevelop:16439): WARNING **: Cannot load type 'Gtk.ToolbarStyleGType, gtk-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'

** (MonoDevelop:16439): WARNING **: Cannot load type 'Gtk.ToolbarStyleGType, gtk-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'

(MonoDevelop:16439): Gtk-WARNING **: Failed to set label from markup due to error parsing markup: Error on line 16: Character ')' is not valid at the start of an entity name; the & character begins an entity; if this ampersand is not supposed to be an entity, escape it as &amp;

(MonoDevelop:16439): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(MonoDevelop:16439): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(MonoDevelop:16439): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(MonoDevelop:16439): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(MonoDevelop:16439): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in (unmanaged) 0x47864783
in <0x00004> (wrapper managed-to-native) GLib.Object:g_object_unref (intptr)
in <0x00119> GLib.Object:PerformQueuedUnrefs ()
in <0x00048> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x00036> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0x4787874f
in <0x00004> (wrapper managed-to-native) Gtk.Dialog:gtk_dialog_run (intptr)
in <0x0001d> Gtk.Dialog:Run ()
in <0x000a8> MonoDevelop.Commands.CommandManager:ReportError (string,System.Exception)
in <0x0037a> MonoDevelop.Commands.CommandManager:DispatchCommand (object,object)
in <0x00024> MonoDevelop.Commands.CommandMenuItem:OnActivated ()
in <0x00047> Gtk.MenuItem:activated_cb (intptr)
in <0x00032> (wrapper native-to-managed) Gtk.MenuItem:activated_cb (intptr)
in (unmanaged) 0x4790dab2
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x0048a> MonoDevelop.Commands.StartWorkbenchCommand:Run ()
in <0x00a66> MonoDevelop.SharpDevelopMain:Main (string[])

Killed
```
That's about ten distinct errors in about one minute of running the program. How on earth did MonoDevelop make it into Breezy this way?

---

### Post by CapnCook on 2005-10-15
I'm pretty new to linux so I don't have any suggestions on fixing MonoDevelop, except to reinstall it. MonoDevelop works fine on Breezy here.

---

### Post by Hikaru79 on 2005-10-15
[QUOTE=CapnCook]I'm pretty new to linux so I don't have any suggestions on fixing MonoDevelop, except to reinstall it. MonoDevelop works fine on Breezy here.[/QUOTE]
Hm, I've tried that, of course. Can you try something really quick for me? Create a new Glade#2 project, and try to execute the default code that is given. (Glade#2, not Glade#, please!). Let me know if any crashes occur.

---

### Post by Txukie on 2005-10-15
Works fine for me.......I tried to create a Glade#2 proyect and no problem at all......

---

### Post by CapnCook on 2005-10-15
I created a Glade 2 solution, compiled and ran it. No problems at all.

---

### Post by Hikaru79 on 2005-10-16
Hmm... must be just me, then, but I have no idea what could be wrong, since I've tried reinstalling every single mono and glade-related package. Any ideas? :(

---

### Post by nehalem on 2005-10-16
Monodevelop is junk for me too.  I don't understand what's wrong but it will randomly just die with the following error when run from the console:

(MonoDevelop:8791): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: asserti on `G_TYPE_CHECK_INSTANCE (instance)' failed
*** glibc detected *** corrupted double-linked list: 0x092e1550 ***
2005-10-16 11:30:57,061 [-1266951248] INFO  MonoDevelop.Services.ILoggingService  [(null)] - Reading /home/xxxxxxxxx/.config/MonoDevelop/CodeCompletionData/Syste m_1.0.5000.0_b77a5c561934e089.pidb

Any idea what could cause this?  All my other mono apps, so far, have worked great.  I was so excited to use this version of MD too since it has some nice improvments.

I too have tried reinstalling, deleting all config files, etc.  No idea why it's so buggy.

---

### Post by nehalem on 2005-10-17
Hikaru79,
After looking at things closer it appears that while getting the error above I am also getting similar errors to yours too.  I would love to know if you have found a solution.

I noticed when I try and install gtk-sharp package that it errors out on accont of perl-xml configuration not working.  I installed the google mail notification thing as was shown here:
[http://www.ubuntuforums.org/showthread.php?t=74539](http://www.ubuntuforums.org/showthread.php?t=74539)

It has a part wherer you install some perl xml stuff and I am curious if that might have something to do with it. 

Have you by chance installed the same things?

Furthermore I have gcc 4 and 3.4 installed.  I thought they used different names but had to install 3.4 because of vmware.  I'm curious, could this be the problem.

If anyone could help I would really appreciate it.

Thanks!

---

### Post by Hikaru79 on 2005-10-17
[QUOTE=nehalem]Furthermore I have gcc 4 and 3.4 installed.  I thought they used different names but had to install 3.4 because of vmware.  I'm curious, could this be the problem.

If anyone could help I would really appreciate it.

Thanks![/QUOTE]
Hm. Me too. I'm thinking this is possible. Next time I'm on my computer, I'll try removing gcc 3.4 and seeing if that helps.

Thanks for pointing that out :D

---

### Post by nehalem on 2005-10-17
Well didn't work here.  But then I didn't pursue it far.  I'm going to try another computer and not install vmware and check the performance (assuming it's not HW related).  That would suck if it is vmware, since  it's far too important for me.

---

### Post by Hikaru79 on 2005-10-17
I don't have VMWare installed, yet the problem still exists, so luckily I do not think VMWare is the problem :)

Of course, I don't know what the problem really *is* :(

---

### Post by CapnCook on 2005-10-17
I didn't install monodevelop from the repos, I downloaded mono-1.1.9.2_1-installer.bin from go-mono.com. Did a chmod +x mono-1.1.9.2_1-installer.bin then sudo ./mono-1.1.9.2_1-installer.bin. It was installed to /opt/mono-1.1.9.2 directory. I had tried without success to compile the source code but this install works flawlessly.

You might completely nuke mono from your system and give that a try. I had to do a dpkg -l mono* to find all of the packages that were installed and then dpkg --remove package to get rid of all of them.

Hope that helps

---

### Post by tuxtail on 2005-10-21
I'm in debian, but have somewhat the same issues... :confused: 

Have you come up with a solution? 

/tuxtail

---

### Post by Hikaru79 on 2005-10-21
[QUOTE=tuxtail]I'm in debian, but have somewhat the same issues... :confused: 

Have you come up with a solution? 

/tuxtail[/QUOTE]
No, no solution yet =( Anyone else?

---

### Post by nosami on 2005-10-22
Monodevelop is working fine for me and I have vmware 5.5 installed.

---

### Post by MrRoot on 2005-10-23
my monodevelop (and monodoc) was unusable, it would freeze when I simply closed a source window.. I removed all mono packages and used the binary installer from go-mono, and the crashes are mostly gone.

---

### Post by lgoss007 on 2005-10-26
I had this problem a few weeks back and posted a bug report here:
[https://launchpad.net/distros/ubuntu/+source/monodevelop/+bug/2870]("https://launchpad.net/distros/ubuntu/+source/monodevelop/+bug/2870")

It is said to be fixed there, but I have had this problem come up again. The way to fix this is to remove ~/.config/MonoDevelop/

---

### Post by klaatu on 2005-11-17
Just wondering if a solution has been found to this problem.
Breezy seems to hate Monodevelop.
This has severely affected my development scedule.
Am thinking of returning to Hoary. But I want to develop for GMCS. :confused: 

What's happening is,
  When I open or create a Solution and want to view the source from the Solution pane, nothing happens until after about a minute the pane blanks and Monodevelop freezes.
  Yet Help browsing works ok, to a point.

I had no problems with Monodevelop in Hoary. It was beutiful.



Kyle.

---

### Post by klaatu on 2005-11-24
What's this!
I wiped Breezy and re-installed Hoary, but to my horror Monodevelop is still not playing the game. :???:
It doesn't play up as much, but will hickup at the wrong times.
I can't import past projects. And integration with Glade has disapeared.
And I thought Monodevelop had a good future.
Not to mention my now overtime development scedule! 
Sorry Breezy for ever doubting you.

---

### Post by Othersider on 2005-11-25
Like CapnCook, I installed by the installer mono proviides from their site.  Installation goes well, but it won't run normally.
```

me@localhost:/opt/mono-1.1.10/bin$ sudo ./monodevelop
System.TypeInitializationException: An exception was thrown by the type initializer for Gnome.ModuleInfo ---> System.DllNotFoundException: gnomesharpglue-2
in (wrapper managed-to-native) Gnome.ModuleInfo:gnomesharp_gnome_moduleinfo_get_name_offset ()
in <0x00008> Gnome.ModuleInfo:.cctor ()--- End of inner exception stack trace ---

in <0x00000> <unknown method>
in <0x00025> Gnome.Modules:get_UI ()
in <0x00440> MonoDevelop.Ide.Gui.IdeStartup:Run (System.String[] args)
in <0x00169> MonoDevelop.Core.AddIns.AddInService:StartApplication (System.String addinId, System.String[] parameters)

```

MonoDevelop opens and runs perfectly, if I try:
```

me@localhost:/opt/mono-1.1.10/bin$ su
Password:
root@localhost:/opt/mono-1.1.10/bin# ./monodevelop

``` 
This becomes a problem because I can't launch it directly from any shortcuts or icons.  Any ideas?

---

### Post by SickBoy on 2005-11-26
I had that problems and I had to purge (not only uninstalling) everything related to mono, delete my $HOME/.config/MonoDevelop and reinstall. Anyway monodevelop does not import old projects correctly. Importing must be handmade.

---

### Post by klaatu on 2005-11-27
Thanks guys, that was very helpfull.

If you wish to run Monodevelop from a shortcut using your proceedure Otherside, just create a script, run a shortcut to your script.
I'm going to give that a try as well.  :)

---

### Post by klaatu on 2005-11-28
Just a follow up from my last post.
I still wanted to do things the easy Debian/Ubuntu way, so I used the package manager, but I took a leaf out of the Monodevelop team's suggestion on how to load the dependancies. ie One at a time.
The result was mostly successful.
So using the package manager, install these dependancies one at a time.
Of course, make sure any previous existance of the following are removed first. Or do as I did and start with a fresh install of Breezy.

Mono1
Libgdiplus
Cli-Common (I actualy did this one last)
Xsp (only if wanted)
Mod_Mono (only if wanted, for Apache)
Gtk-Sharp1
Gtk-Sharp2
GtkSourceView-Sharp2 (I didn't actually do this one)
MonoDoc1
Gecko#2
Monodevelop
GMCS (I added this as a last thought to support .Net2)

To help, restart your machine after every major package installed. I know it is slow, but better to be safe than sorry.

Monodevelop now works. Though, will not close properly. So I save often. :)
I am now able to use old projects(though some conversion is automaticaly done :confused: ) and I have Glade support, though only Glade2.

Doing things the professional way is probebly better. The above rules still aply.
I just wanted to show that it can be done the Ubuntu way. :)

Kyle.

---

### Post by pchr on 2006-02-26
Hello.  This is my first post (Yipee, the Ubuntu's on me!)

I was very keen to have a play with Mono, (I bought "A Developer's Notebook" yesterday) and I'm having the same problems running monodevelop as many others.  Load or create a gtk# project, solution window does not let you open anything, goes blank and program dies.

I haven't tried the above suggestion of installing each package one at a time with a reboot inbetween each (purleeeze!) but I wondered if there's been any more progress with this (or is everyone crossing their fingers waiting for Dapper :D)

EDIT:
I've just added the repository mentioned here ([http://apt.filefind.net/](http://apt.filefind.net/)) and reinstalled and things work much better, if I try to run a new GTK# solution it compiles and opens up a blank window, if I do the same with gtk#2 I get an error along the lines of:

[Task:File=/home/pchr/Projects/Mono/Training/test/MyWindow.cs, Line=2, Column=7, Type=Error, Description=The type or namespace name `Gtk' could not be found. Are you missing a using directive or an assembly reference?(CS0246)

But at least I can start playing with Mono now.  Perhaps I might go for installing from source at some point?

---

### Post by abhaysahai on 2006-03-17
Hi pchr,
The error that "The type or namespace name `Gtk' could not be found" arises only in monodevelop and not when you use mcs from command line. 
The error is becoz, monodevelop uses gtk version 2.4 where as you might have upgraded to GTK version 2.8.. Please correct em if I am wrong. 
To resolve this, in the solution explorer, right click on references and click Edit References.  Add the version of gtk, gnome ( 2.8 in my case) etc, as required. 
And if you want a clean interface delete all hte old references. 

Hope this helps. 
Abhay

---

### Post by pchr on 2006-03-17
Thanks abhaysahai, you are spot on!  I should have probably done a bit of research into that.  I'd noticed that mcs works.  That seems a little odd as (off the top of my head) I'd expect them to behave the same.

I'd actually started using the version included in the Mono Installer (quite an odd experience seeing the sort of setup dialogues I'm more used to in windows) but as I think's been mentioned the icons that are placed on the desktop don't work, in fact you have to start monodevelop from command line.

I'm sure there's a simple enough solution for that but I'm happier using the install from the repository I mentioned in my previous post.

Cheers.

---

### Post by abhaysahai on 2006-03-19
Nice to know that I could be of some help. 
As for experience in windows, well I don't see any IDE here, which can even remotely provide the ease and features/functionality of even the Free version of C# Express.  Even the java IDEs like netbeans and Eclise cannot come close to J# Express. So please do not compare the environment.

---

### Post by pchr on 2006-03-19
[QUOTE=abhaysahai]As for experience in windows, well I don't see any IDE here, which can even remotely provide the ease and features/functionality of even the Free version of C# Express.  Even the java IDEs like netbeans and Eclise cannot come close to J# Express. So please do not compare the environment.[/QUOTE]

I was comparing the installation :confused: 

I'd not seen a graphical install in Linux until I installed mono using the Linux setup from their site.

Cheers any who.

---

### Post by klaatu on 2006-03-28
Yi ya pchr.
Good to see your having some success.
As far as my own instalation of Monodevelop, I haven't changed it since my last post and am still putting up with the minor hicups.
Which leads me to ask if anyone has any idea of any comming upgrades of Monodevelop for Breezy.
I like Breezy, but have noticed that many package upgrades occur slowly, much more than with Hoary.
I prefer to upgrade things the Ubuntu way, and why not it's so simple and reliable.
I've been tempted to go back to Hoary(Monodevelop was more reliable) but am being patient.(trying to anyway) :)

---

### Post by pchr on 2006-03-29
Yi ya Klaatu! :-D 

Is that a typo or an australiaism?

I have only been using Ubuntu since the start of this year, so I have no experience prior to Breezy.  Did they release changes to Monodevelop during Hoary's lifetime or was it just that version was more stable?

I think adding unofficial repositories is pretty cool, allowing you to still tie everything together through Synaptic.  I use mono and OpenOffice repositories and those versions are more recent (and they're stable).

When Dapper comes out I'm going to probably go for a fresh install using only the official repositories (and universe and multiverse of course :-) and run with that for a little while, hopefully the version of monodevelop that's included will be more stable, but there's always the option of other repositories, the official mono setup or installing from source!

---

### Post by klaatu on 2006-03-30
>Yi ya Klaatu!
>
>Is that a typo or an australiaism?

lol  
Klaatu is the main character from the sci-fi movie, The Day The Earth Stood Still (1951).
It's an old classic with a powerful message that is still current today. DVD is available.
Also it is the name of a Canadian Electro-Rock band from the eighties. They got their name from said movie and used the movies message as a theme throughout their music.

As far as Monodevelop goes, even though there has been a recent upgrade for Mono in Breezy, nothing for Monodevelop. I guess the upgrade will appear for Dapper. Meaning yet another OS install. I have been around a long time in the computer world and am getting very 'install weary'.
The good thing about linux is that transfering personal data to a new install is dead easy and reliable.

Monodevelop on Hoary was very nice but no GMCS. Though i am sure there were a couple of upgrades.
But upgrades in general for Breezy packages are few at best. So I guess an upgrade to Dapper may be required. :/

Breezy is a lot better than Hoary, and I guess it can be expected that Dapper will be an improvement as well.
Either way, after all the many flavours of Linux I have tried over the years, Ubuntu is definately the way. Very high on the productivity scale. It may be made for newbies but you can still get 'geeky with it' if you want. 

Cheers.

---

### Post by klaatu on 2006-05-02
Just another follow up...

I have solved some of my development issues by simply using Perl and GTK2 with a simple text editor and Glade2 as a sudo IDE. :p 
Go figure.

But don't get me wrong, I still believe the Mono project has a good future.  :cool: 
It just has a lot of competition.  :mrgreen: 

Cheers.

---

### Post by gunfu on 2006-09-09
Ok...I have gotten something to work...Here is what I did. Downloaded the MonoDevelop package via 'Add/Remove Packages' and it seemed to work find for command line stuff (non-gui). Got Gtk-Sharp the same way, but it wouldn't work on the basic 'hello world' program (have it listed below). I FINALLY got it to work and work it does. On the command line I used:

mcs -pkg:gtk-sharp-2.0 gtk_helloWorld.cs -r:System.Drawing
...then....
mono gtk_helloWorld.exe
...and it works.

The way I ran accross this was simple, but I could not find a whole lot about it on the web. It seems that there is a directory that includes all the '.pc' package config files...for instance, Gtk-Sharp is in there as 'gtk-sharp.pc' and v2.0 is 'gtk-sharp-2.0.pc'. There are misc other ones in there too that you can browse. They are in text so you can pull them up in a xterm/vim to view. So I figured if I was getting the error message:

error CS0246: The type or namespace name `Gtk' could not be found.

maybe the issue was with gtk-sharp.pc ... so i used gtk-sharp-2.0.pc and it worked like a champ.

Here is the code for the gtk_helloWorld.cs:
// helloworld.cs - Gtk# Tutorial example
 
using Gtk;
using GtkSharp;
using System;
using System.Drawing;
 
public class HelloWorld {
	// This is a callback function. The data arguments are ignored
	// in this example. More on callbacks below.
	static void hello (object obj, EventArgs args)
	{
		Console.WriteLine("Hello World");
		Application.Quit ();
	}
 
	static void delete_event (object obj, DeleteEventArgs args)
	{
		// If you return FALSE in the "delete_event" signal handler,
		// GTK will emit the "destroy" signal. Returning TRUE means
		// you don't want the window to be destroyed.
		// This is useful for popping up 'are you sure you want to quit?'
		// type dialogs.
 
		    Console.WriteLine ("delete event occurred\n");
		    Application.Quit ();
	}
 
	public static void Main(string[] args)
	{
		// This is called in all GTK applications. Arguments are parsed
		// from the command line and are returned to the application. */
		Application.Init ();
 
		// create a new window
		Window window = new Window ("helloworld");
 
		// When the window is given the "delete_event" signal (this is given
		// by the window manager, usually by the "close" option, or on the
		// titlebar), we ask it to call the delete_event () function
		// as defined above. The data passed to the callback
		// function is NULL and is ignored in the callback function.
 
		window.DeleteEvent += new DeleteEventHandler (delete_event);
    
		// Sets the border width of the window.
		window.BorderWidth = 10;
    
		// Creates a new button with the label "Hello World".
		Button btn = new Button ("Hello World");
    
		// When the button receives the "clicked" signal, it will call the
		// function hello() passing it null as its argument.  The hello()
		// function is defined above.
		btn.Clicked += new EventHandler (hello);
 
		// This packs the button into the window (a gtk container).
		window.Add (btn);
 
		// The final step is to display this newly created 
		window.ShowAll ();
 
		// All GTK applications must call the main loop: Application.Run
		// Events are processed and dispatched here.
 
		Application.Run ();
	}
}

Enjoy,
George

---

### Post by klaatu on 2006-11-30
Good job gunfu, well done. 8) 

I recently returned to MonoDevelop after trying version 0.10 which came with Knoppix 5.

This is a fantastic distro(sorry Ubuntu). The DVD version is packed. :o 

MonoDevelop in this distro seems to be rock solid, a joy to use. And with GMCS it comes dotNet2 ready.:D 

As a Perl programmer this disturbs me, lol, but at least now I can get a good handle on MonoDevelop. :rolleyes: 

Cheers. ;)

---

