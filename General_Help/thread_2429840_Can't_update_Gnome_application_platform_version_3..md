---
title: "Can't update Gnome application platform version 3.34 because needs later flatpak"
date: 2019-10-24
forum: General Help
---

### Post by dora5 on 2019-10-24
I am running Ubuntu 18.04.   

I keep getting told to update Gnome Application Platform version 3.34.  

When I update it I get "Unable to update "GNOME Application Platform version 3.34": Error deploying: runtime/org.freedomdesktop.Platform.openh264/x86_64/19.08 needs a later flatpak version (1.4.2; 1.2.5; 1.0.9);  


Per instructions on another forum I tried;   [COLOR=#1C1C1C][FONT=&amp]flatpak install flathub org.freedesktop.Platform/x86_64/19.08,
and it told me that software and version is already installed.

I tried flatpak update and it installed the flatpak that is already installed. 
Or seemed to.   
But then it said 

[/FONT][/COLOR]Installing: org.freedesktop.Platform.openh264/x86_64/19.08 from flathub
Warning: Failed to install org.freedesktop.Platform.openh264/x86_64/19.08: runtime/org.freedesktop.Platform.openh264/x86_64/19.08 needs a later flatpak version (1.4.2;1.2.5;1.0.9; )

Then I tried flatpak update --system, and it said,

Installing: org.freedesktop.Platform.openh264/x86_64/19.08 from flathub
Warning: Failed to install org.freedesktop.Platform.openh264/x86_64/19.08: runtime/org.freedesktop.Platform.openh264/x86_64/19.08 needs a later flatpak version (1.4.2;1.2.5;1.0.9; )

This seems to be a common question online but noone ever comes up with the answer, or if they do it's not in English.  

One discussion got off on whether one is allowed to use a codec provided by Cisco, which may be one of the things it's beefing about, and evidently one is, but they never said how to actually install this codec we're allowed to use it's beefing we don't have, which has something to do with openh264.  Not I know what the bleep they're talking about! 

  Here are the Flatpaks I have installed, after removing unused flatpaks.

Ref                                               Options       
com.abisource.AbiWord/x86_64/stable               system,current
com.adobe.Flash-Player-Projector/x86_64/stable    system,current
org.freedesktop.Platform.VAAPI.Intel/x86_64/19.08 system,runtime
org.freedesktop.Platform/x86_64/19.08             system,runtime
org.gnome.Platform/x86_64/3.34                    system,runtime
org.gtk.Gtk3theme.Greybird/x86_64/3.22            system,runtime



How, please, do I solve this problem.   En Anglais, por favor.   

I really don't understand how Flatpak was ever needed to install Gnome, especially since it was something I installed after installing Ubuntu, which would have installed Gnome.  Flatpak and Snapwhatever are both notorious bloody nuisances I avoid using like the plague.  Can I get RID of flatpak without trashing my system from under Gnome?   

Nobody can update Gnome until we do solve this problem, so we won't be waiting months for whoever to fix the bug.  

Thanks!



[COLOR=#1C1C1C][FONT=&amp]


[/FONT][/COLOR]

---

### Post by deadflowr on 2019-10-24
post back the results from
```
apt policy flatpak
```

---

### Post by dora5 on 2019-10-24
It MIGHT be fixed.   The message to update Flash and Gnome is intermittent, and evidently they're both flatpacks.

I ran flatpak repair, and got

dora@dora-desktop-ubuntu:~$ flatpak repair
Verifying flathub:runtime/org.freedesktop.Platform/x86_64/19.08...
Verifying flathub:runtime/org.gtk.Gtk3theme.Greybird/x86_64/3.22...
Verifying flathub:app/com.adobe.Flash-Player-Projector/x86_64/stable...
Verifying flathub:runtime/com.abisource.AbiWord.Locale/x86_64/stable...
Verifying flathub:runtime/org.freedesktop.Platform.Locale/x86_64/19.08...
Verifying flathub:appstream2/x86_64...
Verifying flathub:runtime/org.freedesktop.Platform.VAAPI.Intel/x86_64/19.08...
Verifying flathub:app/com.abisource.AbiWord/x86_64/stable...
Removing non-deployed ref flathub:runtime/org.freedesktop.Platform.openh264/x86_64/19.08...
Verifying flathub:runtime/org.gnome.Platform/x86_64/3.34...
Verifying flathub:runtime/com.adobe.Flash_Player_Projector.Locale/x86_64/stable...
Verifying flathub:runtime/org.freedesktop.Platform.GL.default/x86_64/19.08...
Verifying flathub:runtime/org.gnome.Platform.Locale/x86_64/3.34...
Pruning objects


Notice that it specifically removed the freedesktop.Plaform.openh264/86whatever that it kept insisting had to be updated that it kept insisting was up to date.    

Now it isn't telling me I need to update Gnome.   I don't know if that message is gone permanently or it will be back.

---

### Post by totedati on 2019-11-26
Look like is a loong standig problem with that ghost > org.freedesktop.Platform.openh264 package. See here the full fun: [Warning: org.freedesktop.Platform.openh264 not installed]("https://gitlab.com/freedesktop-sdk/freedesktop-sdk/issues/886#note_245154958"). Look like is a need to force upgrade flatpak to escape org.freedesktop.Platform.openh264 endless failed upgrades with this commands:

```
flatpak install org.freedesktop.Platform/x86_64/19.08
flatpak uninstall --unused
flatpak update
```

Problem solved ... At least for me, and is no need to reboot. Now you escaped from that ghost org.freedesktop.Platform.openh264 failed install package error, and proceed with your other flatpak apps installs as usual

---

### Post by hrscr on 2019-11-28
Thank you, works for me too ;)

---

