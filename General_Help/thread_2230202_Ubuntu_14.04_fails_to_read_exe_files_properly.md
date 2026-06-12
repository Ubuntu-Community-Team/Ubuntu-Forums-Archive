---
title: "Ubuntu 14.04 fails to read exe files properly"
date: 2014-06-17
forum: General Help
---

### Post by jjclonker on 2014-06-17
I saw that someone had posted something similar, but never had it answered properly.

Ok, so here's the problem ,as I understand it.
Some programs that I have installed that are meant for ubuntu 12.04 do not open in 14.04.
Some exe's that are even meant for 14.04 do not open and when I look at there properties it clames that the are DOS/Windows exe's when they are not.
For example: OpenRA Debian package for ubuntu 14.04 reads as a DOS/Windows exe. I know that this information is extremely vague. :P

---

### Post by Bucky Ball on 2014-06-17
DOS/Windows .exe files will not open or run in Linux. You have that part right. If it ends in .exe, forget it. 

Please provide a link to this OpenRA Debian package you've downloaded.

---

### Post by squakie on 2014-06-18
As Bucky Ball pointed out, a .exe file is for Windows/DOS and will NOT run in Linux unless you use something like Wine, and even then it's no guarantee.

I just went to the openra.com site and downloaded the ubuntu/debian package.  I then tried to install it (just double clicking on the deb brings it up in the software center).  The software center issued an error about the package indicating it is not valid and shouldn't be installed.  If this is the error you are getting, it's not ubuntu - it's the package from openra.

A screen capture of the error is attached.

I suspect that at least for openra, you did not click on the debian icon box before going to the download.  Failure to do so would download the Windows version by default.  You *have* to click the debian box, THEN click download.  It will download as type .deb, NOT as type .exe.

---

### Post by jjclonker on 2014-06-18
> I suspect that at least for openra, you did not click on the debian icon  box before going to the download.  Failure to do so would download the  Windows version by default.  You *have* to click the debian box, THEN  click download.  It will download as type .deb, NOT as type .exe. 		

I checked this, and unfortunately this is not the problem. I did download the deb. file, and opened it using ubuntu software center.
After I downloaded it by the software center I unzipped the deb. file to look inside and I found that the OpenRA program was in exe. format.
And the link that is automatically placed on the computer does not work... maybe this is OpenRA's problem, but other people seem to be
running it just fine on ubuntu 14.04. Here is the link [http://www.openra.net/download/](http://www.openra.net/download/).

If you want me to run openra in the terminal to give you the results I could do that.

---

### Post by Karlchen on 2014-06-18
Hello, jjclonker.

The Ubuntu download file [openra_release.20140608_all.deb]("https://github.com/OpenRA/OpenRA/releases/download/release-20140608/openra_release.20140608_all.deb") is a genuine .deb packages meant to be installed by gDebi, Synaptic or Software Manager. It would install fine here, provided I  permitted gDebi to do so, but I won't.
[U]
Note:[/U]
The installed programme needs the software mono in order to execute the .NET framework executables which the .deb package will install.
mono is not included in a default Ubuntu 14.04 installation, but it can be got through the Software Manager or Synaptic.

So chances are you have not agreed to installing the required dependencies, e.g. mono, too. In this case I am sure OpenRA will fail to launch.

Kind regards,
Karl

---

### Post by jjclonker on 2014-06-18
Hello, Karlchen

I will check that out.

Kind regards,
jjclonker

---

### Post by jjclonker on 2014-06-18
Thank you Karl. I will try downloading mono... I think you may be right about that, because I saw that in the dependencies.

hmm... I have mono runtime and mono runtime (terminal).

---

### Post by yancek on 2014-06-18
> I did download the [openra_release.20140608_all.deb]("https://github.com/OpenRA/OpenRA/releases/download/release-20140608/openra_release.20140608_all.deb") not [the Windows download package]("https://github.com/OpenRA/OpenRA/releases/download/release-20140608/OpenRA-release-20140608.exe").
I said this in my above post.

I believe you mis-read the post by Karlchen.  He is saying that you need to install Mono.  Read the section after:  Note in his post.

---

### Post by grahammechanical on 2014-06-18
> [COLOR=#000000]I unzipped the deb. file to look inside and I found that the OpenRA program was in exe. format.[/COLOR]

The software centre might be refusing to install that package because it is flagging the exe file as a possible virus. Is it not a common thing in Windows for a virus to masquerade as an exe file? An exe file inside a deb file. How suspicious is that!

I am curious. The message from software centre says "include the details beneath." What were those details? Do they give a clue why software centre is coming on like a police officer?

---

### Post by jjclonker on 2014-06-18
Yancek, he changed his post... :)

---

### Post by jjclonker on 2014-06-18
> The software centre might be refusing to install that package because it  is flagging the exe file as a possible virus. Is it not a common thing  in Windows for a virus to masquerade as an exe file? An exe file inside a  deb file. How suspicious is that!

I am curious. The message from software centre says "include the details  beneath." What were those details? Do they give a clue why software  centre is coming on like a police officer? 				

Yes, you must have found what I found.

---

### Post by mc4man on 2014-06-18
The deb is failing a lintian check in software-center (openra: arch-independent-package-contains-binary-or-object usr/lib/openra/libSDL232.2.0.2.so, ect.
S-c will give you the option to install anyway "Ignore and Install"

Other option is to remove the lintian package or use gdebi
(openra starts up fine here on 14.04

---

### Post by jjclonker on 2014-06-18
Maybe I will get gdebi, and try that, but I still don't understand why OpenRA has DOS/Windows exe files in it.

---

### Post by mc4man on 2014-06-18
> **jjclonker said:**
> Maybe I will get gdebi, and try that, but I still don't understand why OpenRA has DOS/Windows exe files in it.

As mentioned previously if you are downloading the debian package there are No "DOS/Windows exe files in it"  whatsoever..

---

### Post by whatthefunk on 2014-06-18
> **jjclonker said:**
> Maybe I will get gdebi, and try that, but I still don't understand why OpenRA has DOS/Windows exe files in it.

Because it uses Mono.  Have you installed Mono?

---

### Post by squakie on 2014-06-19
> **grahammechanical said:**
> The software centre might be refusing to install that package because it is flagging the exe file as a possible virus. Is it not a common thing in Windows for a virus to masquerade as an exe file? An exe file inside a deb file. How suspicious is that!

I am curious. The message from software centre says "include the details beneath." What were those details? Do they give a clue why software centre is coming on like a police officer?

First, the OP shouldn't be unzipping and the trying to run the .exe.  They need to use a package manager, and I think that's part of the problem - it needs to be installed, not just unzipped, but I don't really know how to read what's been posted - do you think they installed or just unzipped?

As for the messages from the software center, they are in the attachment.  It's complaining about some object files.  I don't really understand it so I sure hope you can help out!  I was simply trying to install it myself so I could try to help the OP.  That's why I can't believe they installed it unless they allowed the errors and continued.

I see others are trying to help out here as well, but if you could look into the error messages in the attachment, and try to verify the OP actually installed and not just unzipped, I would really appreciate it.  I'm trying more and more to test installing/using packages/programs people have problems with to see if I can duplicate their problem and hopefully help find a fix.

Thanks grahammechanical!!

---

### Post by squakie on 2014-06-19
jjclonker:

I found a bug report on launchpad for problems with the Software Center reporting errors.  While I didn't see this one in particular, I took a chance and overrode it and it installed and shows in the menus.

So:

(1)  You should NOT be attempting to run any of the .exe files
(2)  You *cannot* just use the archive manager to unzip the .deb and try to execute.  This *will not work*.
(3)  Do as I originally posted:
- find the .deb file with a file manager
- right-click on it and select open in software center (*not* archive manager)
- the software center may report the same error as I have shown.  I overrode it - however you do so at your own risk as I have no idea what is in those object files it flags.
- once it finishes, openra is in the menus, as is the openra editor.  I haven't tried, but I assume you can run it from the command line with some sort of options so it knows what it is doing

Again:

- DON'T open with archive manager
- DO open with the software center
- *IF* you get the same error messages I got in the Sofware Center, override at your own risk
- use the command line or the menus to execute openra - *DO NOT* try to run any of the .exe files

---

### Post by jjclonker on 2014-06-19
Ok. Wow! Let me clear some stuff up here...

1st: I did download the deb. file.

2nd: I did try installing the deb. file with software center and gdebi.

3rd: I did unzip the deb. file to see what was in it after I tried the above.

4th: The program OpenRA is not working.

5th: I do have mono runtime and mono runtime terminal. Do I need some other mono thing?

6th: As far as I know I have all the dependencies needed to run OpenRA.

7th: I am posting the terminal results.

```
Platform is Linux
Using SDL 2 with OpenGL renderer
Desktop resolution: 1400x1050
No custom resolution provided, using desktop resolution
Using resolution: 1400x1050
Detected OpenGL version: 1.4
Renderer initialization failed. Fallback in place. Check graphics.log for details.
Using SDL 2 with OpenGL renderer
Desktop resolution: 1400x1050
No custom resolution provided, using desktop resolution
Using resolution: 1400x1050
Detected OpenGL version: 1.4
Renderer initialization failed. Fallback in place. Check graphics.log for details.
Exception of type `System.InvalidOperationException`: No suitable renderers were found. Check graphics.log for details.
  at OpenRA.Game.Initialize (OpenRA.Arguments args) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Run (System.String[] args) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0 
Exception of type `System.NullReferenceException`: Object reference not set to an instance of an object
  at OpenRA.Program.FatalError (System.Exception e) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0 
exception inside UnhandledException handler: Object reference not set to an instance of an object

[ERROR] FATAL UNHANDLED EXCEPTION: System.NullReferenceException: Object reference not set to an instance of an object
  at OpenRA.Program.FatalError (System.Exception e) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0 

```

---

### Post by squakie on 2014-06-19
What's the syntax for running openra?  have you used the openra editor for anything?

Since it gives you this error:

```

[ERROR] FATAL UNHANDLED EXCEPTION: System.NullReferenceException: Object reference not set to an instance of an object
  at OpenRA.Program.FatalError (System.Exception e) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0
```

I would assume, since I've never used it, it's looking for some file to be provided at the time it is invoked - perhaps something like openra <filename>.  What that file would be, and what it would contain, I have no clue.  Perhaps this is what the editor is for?

How did you invoke it to generate the error?

You may want to check [this ]("https://github.com/OpenRA/OpenRA/wiki/FAQ")and follow the very first information about checking the logs.  Given the warning about your display, it's possible that the graphics issue is causing the problems.

EDIT:  You must have some version of OpenGL installed.  To test for this:

- sudo apt-get install mesa-utils
- glxgears

If the gears appear and are spinning I *think* that means OpenGL is installed.

EDIT-EDIT:  The game is apparently downloaded at runtime.  There is mention on the wiki/installation instructions that say you will need to open a port on your firewall.  If you haven't done that you may probably need to.  If it can't download, that may be where the file error is coming from.

---

### Post by jjclonker on 2014-06-19
Ok? I think you want to know how I started the OpenRA game program or its editor...
I never opened the editor, but to open the game I used the terminal and typed openra.
That is what gave me the error/errors.

As for the seccond part of your question(edit #1) the gears do spin.

Your EDIT-EDIT statement I will try that.

---

### Post by jjclonker on 2014-06-19
Ok, I opened the openra-editor in the terminal to see what it would do, and I got the pile of errors.

I am wondering if a viris hasn't hacked into OpenRA's ubuntu download...
I  will continue to take the risk to figure this out, however I warn  anyone that is trying to help me by downloading the OpenRA deb. file,  you are doing this at your own risk.

Here is the error list for the openra-editor.

```
Unhandled Exception:
System.IO.FileNotFoundException: File not found: redalert.mix
File name: 'redalert.mix'
   at OpenRA.FileSystem.GlobalFileSystem.OpenWithExts (System.String  filename, System.String[] exts) [0x00000] in <filename unknown>:0 
  at OpenRA.FileSystem.GlobalFileSystem.Open (System.String filename) [0x00000] in <filename unknown>:0 
   at OpenRA.FileSystem.MixFile..ctor (System.String filename,  PackageHashType type, Int32 priority) [0x00000] in <filename  unknown>:0 
  at OpenRA.FileSystem.GlobalFileSystem.OpenPackage  (System.String filename, System.String annotation, Int32 order)  [0x00000] in <filename unknown>:0 
  at OpenRA.FileSystem.GlobalFileSystem+<Mount>c__AnonStorey29.<>m__7 () [0x00000] in <filename unknown>:0 
   at OpenRA.FileSystem.GlobalFileSystem.Mount (System.String name,  System.String annotation) [0x00000] in <filename unknown>:0 
  at OpenRA.FileSystem.GlobalFileSystem.LoadFromManifest (OpenRA.Manifest manifest) [0x00000] in <filename unknown>:0 
  at OpenRA.Editor.Form1.<Form1>m__1 (System.Object _, System.EventArgs e) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.ToolStripComboBox.OnSelectedIndexChanged (System.EventArgs e) [0x00000] in <filename unknown>:0 
   at System.Windows.Forms.ToolStripComboBox.HandleSelectedIndexChanged  (System.Object sender, System.EventArgs e) [0x00000] in <filename  unknown>:0 
  at System.Windows.Forms.ComboBox.OnSelectedIndexChanged (System.EventArgs e) [0x00000] in <filename unknown>:0 
   at System.Windows.Forms.ComboBox.SetSelectedIndex (Int32 value, Boolean  supressAutoScroll) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.ComboBox.set_SelectedIndex (Int32 value) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.ComboBox.set_SelectedItem (System.Object value) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.ComboBox:set_SelectedItem (object)
  at System.Windows.Forms.ToolStripComboBox.set_SelectedItem (System.Object value) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.ToolStripComboBox:set_SelectedItem (object)
  at OpenRA.Editor.Form1..ctor (System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) OpenRA.Editor.Form1:.ctor (string[])
  at OpenRA.Editor.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.IO.FileNotFoundException: File not found: redalert.mix
File name: 'redalert.mix'
   at OpenRA.FileSystem.GlobalFileSystem.OpenWithExts (System.String  filename, System.String[] exts) [0x00000] in <filename unknown>:0 
  at OpenRA.FileSystem.GlobalFileSystem.Open (System.String filename) [0x00000] in <filename unknown>:0 
   at OpenRA.FileSystem.MixFile..ctor (System.String filename,  PackageHashType type, Int32 priority) [0x00000] in <filename  unknown>:0 
  at OpenRA.FileSystem.GlobalFileSystem.OpenPackage  (System.String filename, System.String annotation, Int32 order)  [0x00000] in <filename unknown>:0 
  at OpenRA.FileSystem.GlobalFileSystem+<Mount>c__AnonStorey29.<>m__7 () [0x00000] in <filename unknown>:0 
   at OpenRA.FileSystem.GlobalFileSystem.Mount (System.String name,  System.String annotation) [0x00000] in <filename unknown>:0 
  at OpenRA.FileSystem.GlobalFileSystem.LoadFromManifest (OpenRA.Manifest manifest) [0x00000] in <filename unknown>:0 
  at OpenRA.Editor.Form1.<Form1>m__1 (System.Object _, System.EventArgs e) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.ToolStripComboBox.OnSelectedIndexChanged (System.EventArgs e) [0x00000] in <filename unknown>:0 
   at System.Windows.Forms.ToolStripComboBox.HandleSelectedIndexChanged  (System.Object sender, System.EventArgs e) [0x00000] in <filename  unknown>:0 
  at System.Windows.Forms.ComboBox.OnSelectedIndexChanged (System.EventArgs e) [0x00000] in <filename unknown>:0 
   at System.Windows.Forms.ComboBox.SetSelectedIndex (Int32 value, Boolean  supressAutoScroll) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.ComboBox.set_SelectedIndex (Int32 value) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.ComboBox.set_SelectedItem (System.Object value) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.ComboBox:set_SelectedItem (object)
  at System.Windows.Forms.ToolStripComboBox.set_SelectedItem (System.Object value) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.ToolStripComboBox:set_SelectedItem (object)
  at OpenRA.Editor.Form1..ctor (System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) OpenRA.Editor.Form1:.ctor (string[])
  at OpenRA.Editor.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0 

```

To run the openra-editor open the terminal and type openra-editor.

I would also like to thank everyone that has helped so far. :KS

---

### Post by QIII on 2014-06-19
Why would you jump to a conclusion like a virus "hacked into" it?

From the stack trace, it looks like a file expected can't be found.

---

### Post by squakie on 2014-06-19
It does appear that the game isn't being downloaded - most likely because of the firewall settings - as the openra log shows the file not found error at program initialization (which one has to assume means at the time of download).

I need to try some things here and see if I have any luck.

EDIT:  my openra graphics log also shows that while I have OpenGL, it wants a version newer than what I have.  Since this involves video adapter drivers, I'm sure I can do much on that account.

The log in question is he geio (?) log in your .openra folder.  Right there it looks like it wants to retrieve a file, doesn't, then it causes the file not found error the rest of the way out.

---

### Post by jjclonker on 2014-06-19
[**[COLOR=#C61919][B]QIII**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=628170"), I may be jumping to conclusions, but an DOS/Windows exe file in a deb. packaged is suspicious to say the least.

squakie, I am having some difficulty finding ubutnu's firewall... could you give me some advice on that, please?

---

### Post by mc4man on 2014-06-19
> **jjclonker said:**
> [**[COLOR=#C61919][B]QIII**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=628170"), I may be jumping to conclusions, but an DOS/Windows exe file in a deb. packaged is suspicious to say the least.

squakie, I am having some difficulty finding ubutnu's firewall... could you give me some advice on that, please?

Could you post the name of this "DOS/Windows exe file"?

As far as running the red alert mod no issue here on 14.04 -  (using the dl content
> $ openra
Platform is Linux
Using SDL 2 with OpenGL renderer
Desktop resolution: 1920x1080
No custom resolution provided, using desktop resolution
Using resolution: 1920x1080
Detected OpenGL version: 3.0
Using OpenAL sound engine
Using default device
Available mods:
	cnc: Tiberian Dawn (release-20140608)
	d2k: Dune 2000 (release-20140608)
	modchooser: Mod Chooser (release-20140608)
	ra: Red Alert (release-20140608)
Loading mod: modchooser
Loading mod: d2k
Loading mod: modchooser
Loading mod: ra


---

### Post by jjclonker on 2014-06-19
The name's are (OpenRA.Game.exe) and (OpenRA.Editor.exe).

I noticed you have a different screen size or resolution whatever you would call that 1920x 1080.
I have a 1400x 1050 resolution.

Could OpenRA be crashing from trying to adjust to screen size? OpenRA does try to start at first and then crashes...

EDIT:

OpenGL is version 1.4 for on my computer and 3.0 on yours.

Should I try updating OpenGL?

---

### Post by mc4man on 2014-06-19
1.4 is likely the glx string - 
> $ glxinfo |grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.1.3
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:

> $ glxinfo |grep glx
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:


Do you have a populated ~/.openra/Content/ra folder?

> :~/.openra/Content/ra$ ls
allies.mix   general.mix   mirrors.txt   russian.mix  snow.mix    temperat.mix
conquer.mix  interior.mix  redalert.mix  scores.mix   sounds.mix


---

### Post by squakie on 2014-06-19
Just a note:  first, I'm glad that someone who actually uses this is replying - thanks!  second, the .deb I downloaded from openra also contains those same 2 exe files.  third - at least for me - after the installation and attempt at running, the only thing in the .openra folder is the logs folder.  Nothing else.  Personally, I couldn't find anything that said for the newcomer "here's what is going on, what you need to do, and how to run this".  fourth - did you have to allow the 1234 port on your firewall (assuming the router as well?) as per the wiki?

I'll just be following this now since I was only trying to help in my very limited way.  Thanks for coming to the rescue here! ;)

jjconker - I'm sorry I wasn't able to help here - gave it my best shot for now.  I hope I haven't distracted the thread any.  Best of luck! ;)

---

### Post by lisati on 2014-06-20
Jumping in late with a side note which might turn out to be largely irrelevant to the "EXE files are DOS/Windows files" observations..... 

In the past I've noticed installers pulling in .EXE files as part of installing MS fonts, most likely a [self-extracting archive]("http://en.wikipedia.org/wiki/Self-extracting_archive") that can be handled with a tool such as UNZIP.

---

### Post by jjclonker on 2014-06-20
> Do you have a populated ~/.openra/Content/ra folder?

I searched my computer for allies.mix and looked in my OpenRA unzipped deb. folder and could not find anything labeled Content.
So my guess would be no.

---

### Post by jjclonker on 2014-06-20
Ok, I found out what the problem is for OpenRA... developers told me that I need openGL 2.0 at least and I have 1.4.

Ubuntu forums has some of the most respectable and kind people.
I would like to thank everyone that helped and/or commented for their valuable time and resources. :KS
I consider this [SOLVED]!!! ):P

---

### Post by Bucky Ball on 2014-06-20
Excellent news. Good on you for persistence. We like that around here! Enjoy! ;)

---

