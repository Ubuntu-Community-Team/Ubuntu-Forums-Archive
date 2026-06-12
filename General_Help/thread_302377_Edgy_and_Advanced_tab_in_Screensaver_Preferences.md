---
title: "Edgy and Advanced tab in Screensaver Preferences"
date: 2006-11-18
forum: General Help
---

### Post by Piviul on 2006-11-18
Hi all, I've install edgy and I find it fantastic but (I'm very sorry but I find a "but" in everything I use...) I can't find the advanced tab in screen saver preferences. 
I don't need it; I would only configure GLSlideShow to display a personal images directory. Now I've solved the problem creating a symbolic link of my personal images directory in /usr/share/backgrounds. The problem now is that I don't want to see ubuntu default images but nevertheless I don't want to delete them...

So the question: there is a way to configure glslideshow to use a custom directory instead of his default one?

Thank you very much

Piviul

---

### Post by Piviul on 2006-11-23
In four days none answered me. I have to guess that in your ubuntu edgy you have the advanced tab in screen saver preferences?

Thank you very much

Piviul

---

### Post by thepizzaking on 2006-11-23
> **Piviul said:**
> In four days none answered me. I have to guess that in your ubuntu edgy you have the advanced tab in screen saver preferences?

Thank you very much

Piviul

There is no advanced tab with the GNOME Screensaver.  GNOME is intended to be simple, but unfortunately this means that some options are unavailable.  If you really need to change the settings your best option is to probably use 'xscreensaver' instead, luckily for me I do not need it as I use the blank screen option.
If anyone has a better solution I'd also like to hear it.

---

### Post by Piviul on 2006-11-23
> **thepizzaking said:**
> There is no advanced tab with the GNOME Screensaver.  GNOME is intended to be simple, but unfortunately this means that some options are unavailable.  If you really need to change the settings your best option is to probably use 'xscreensaver' instead, luckily for me I do not need it as I use the blank screen option.
If anyone has a better solution I'd also like to hear it.

There was no advanced tab in ubuntu 6.06 screensaver preferences too?
So there is no way to set the screensaver default images directory!

I hope someone knows a workaround...

Thank you very much

Piviul

---

### Post by n00bWillingToLearn on 2006-12-10
There is a thread on changing screen saver prefs here:
[http://ubuntuforums.org/showthread.php?t=198809](http://ubuntuforums.org/showthread.php?t=198809)

---

### Post by Piviul on 2007-10-23
I've found a way to have a default images directory for gnome-screensaver: it is sufficient to create a directory named Pictures under the user's home. :)

Bye

Piviul

---

### Post by potentia on 2007-10-24
So they consider it great usability and keep Gnome simple by removing a SETTINGS option? Great, so now I have to follow *another* HOW-TO to get something very simple done.

---

### Post by bl1rt on 2007-11-06
Yeah, this is a quite persistent problem with the gnome-screensaver. As far as I know it is like potentia said that the gnome developers fancy the idea of having a very simple interface without overloading the user with options. If this problem here (that has been going on up to gutsy and probably will go on forever) is a good place to insist on this principle might be questioned.
But who knows, maybe it's all different and the people behind gnome are simply waiting for a new version of the xscreensaver with better integration capabilities (gnome-screensaver is just a wrapper for xscreensaver).


However, there is a rather easy way to configure GLSlideshow; lookie here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/GettingStarted#How_to_configure_GLSlideshow](http://ubuntuguide.org/wiki/Ubuntu:Feisty/GettingStarted#How_to_configure_GLSlideshow)



And I just saw on Launchpad ([https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/22007](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/22007)), that there seems to be some guy working to include the all-wanted settings button in gnome-screensaver. It all seems to be great work and he even created a .deb file, but I have not tried it out! So dont't hold me responsible when it doesn't work! You can get it from here: [http://software.xfx.net/ftp/screensaver-settings_0.2.2-1_i386.deb]("http://software.xfx.net/ftp/screensaver-settings_0.2.2-1_i386.deb")
Would be great if someone who tries that would report on it whether it works or not, because maybe that really is the end of all moaning

---

### Post by BCtom on 2007-11-08
Hello all, I thought I would give xFX Screensaver-settings a try.... It is in the distros, just typ XFX or Screensaver-settings in Synaptic, it is there. Also, I'm on 7.10,  so.......

It worked great while it first loaded it up. I was able to us it, change settings and screensavers, just like the good old day in Gnome, but then I tried the Screensaver from:    System-->Preferences-->Screensaver,    and looked at it, then I went beck to XFX, and XFX would not start. XfX would just shut down right away.

I started it up in terminal and got this: 

[INDENT]tom@tom-desktop:~$ screensaver-settings
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentException: An element with the same key already exists in the dictionary.
  at System.Collections.Generic.Dictionary`2[System.String,System.String].Add (System.String , System.String ) [0x00000] 
  at ScreenSaver.UpdateCurrentValues () [0x00000] 
  at ScreenSaver.GetCurrentValues () [0x00000] 
  at ScreenSaver..ctor (System.IO.FileInfo file) [0x00000] 
  at MainWindow.LoadScreenSavers () [0x00000] 
  at MainWindow.Init (System.Object sender, System.EventArgs e) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr gch) [0x00000] 

   at GLib.ExceptionManager.RaiseUnhandledException ()
   at GLib.Signal.voidObjectCallback ()
   at GLib.Signal.voidObjectCallback ()
   at Gtk.Application.gtk_main ()
   at Gtk.Application.gtk_main ()
   at Gtk.Application.Run ()
   at MainClass.Main ()
 [/INDENT]

So now I'm wondering if it is possible that the old Gnome Screensaver needs to be removed for the XFX Screensaver-settings to run? 

But it did work. I still kept the settings I made during the first attempted. I've only had it on my machine for a few minutes, so I may find out what's going on with? But yes, I wish Gnome would put back the "settings," and give more options and choices like it did before?

---

