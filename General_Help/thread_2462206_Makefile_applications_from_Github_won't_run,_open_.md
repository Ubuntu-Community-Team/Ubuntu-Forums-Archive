---
title: "Makefile applications from Github won't run, open as text document"
date: 2021-05-16
forum: General Help
---

### Post by michelvandegaer on 2021-05-16
Hello,

I'm a fairly new to Ubuntu and I am trying to run these 'DyanamicFoam' and 'TinyEngine' applications/makefiels that I downloaded from Github and are now located on my Desktop:


[LIST]
[*][https://github.com/weigert/DynamicFoam](https://github.com/weigert/DynamicFoam)
[*][https://github.com/weigert/TinyEngine](https://github.com/weigert/TinyEngine)
[/LIST]

TinyEngine is needed to run the DynamicFoam app, as mentioned in the DynamicFoam Readme:[INDENT][I]
This system was built using TinyEngine. Install TinyEngine and then use the makefile to create an executable:

[/I][/INDENT]
[INDENT]*make all*[/INDENT]


In TinyEngine's Readme it says that it runs on Ubuntu 18 LTS

So what I have done is bought a 2nd hand laptop: 

Lenovo Thinkpad X240 / i5-4300 CPU / 1.90Hz x 4
Graphics Intel HD 4400 
8GB Memory

I did an erase-install of Ubuntu 19.10 from a bootable USB stick, and an upgrade to version 20.04.

Next I have installed via Terminal under Sudo -s all the dependencies listed near the end of TinyEninge's Readme:


[LIST]
[*]OpenGL3: apt-get install libglu1-mesa-dev
[*]SDL2:    apt-get install libsdl2-dev libsdl2-ttf-dev libsdl2-mixer-dev libsdl2-image-dev
[*]GLEW:    apt-get install libglew-dev
[*]Boost:   apt-get install libboost-system-dev libboost-filesystem-dev
[*]GLM:     apt-get install libglm-dev
[*]DearImGUI (already included!)
[*]g++ (compiler)
[/LIST]

I also installed:


[LIST]
[*]Homebrew
[*]Make
[/LIST]
------

Now when I try to run the Makefiles in the *TinyEngine-Master* and *DynamicFoam-main* folders nothing happens, they just open as text-documents.

Don't know how to solve this issue. Is it perhaps a problem with my Permissions, but I am logged in as the Root user, no? Or should I place these documents at an other location, such as 'lib' which I have tried. But I can't drag and drop them over there, and I couldn't find a solution how to move them over there.

Any suggestions ... all help is welcome!

Grtz,
M.


Attached:

 
[LIST]
[*]System Overview
[*]Versions read-out in Terminal of Make, g++ and Homebrew
[*]Permission denied in Terminal when looking for the TinyEngine file
[*]What I get when I click the makefiles that open as text docs.
[/LIST]

[IMG]http://800million.org/Ub/System.png[/IMG]


[IMG]http://800million.org/Ub/Make_G_Brew.png[/IMG]


[IMG]http://800million.org/Ub/Permission_find.png[/IMG]

[IMG]http://800million.org/Ub/Makefile_text.png[/IMG]

---

### Post by mikewhatever on 2021-05-16
...

---

### Post by michelvandegaer on 2021-05-16
Thanks for the reply, not sure what you exactly mean with 'executable' ... the files are downloadable via:

[https://github.com/weigert/DynamicFoam](https://github.com/weigert/DynamicFoam) (600kb)
[https://github.com/weigert/TinyEngine](https://github.com/weigert/TinyEngine) (60Mb)

I think the main problem is that when clicking on them they should 'automatically' run *via* the Terminal.

I previously tried to run these applications on MacOSX using XCode, and there the Makefiles were listed in their map with a Terminal label/icon (see pic). 

But there I had other issues, so I though of doing it all 'native' and getting a smooth run.

[IMG]http://800million.org/Ub/Terminal_icon.png[/IMG]

---

### Post by michelvandegaer on 2021-05-16
Small update. 

A practical problem was that I couldn't do a right-click on the laptop. :oops:
 
So I installed the gnome-tweak-tool, and now I'm able to right-click and change the properties and the Default Application.
 
I changed it to 'Run Software' and tried 'Software Install' (see pic).

But nothing happened except a 'Run Software' wheel that rolled for a moment on the upper left side.

There wasn't a Terminal option, mh.

I also made everything in the map to read/write.

BTW Not sure if I'm here at the right section (General) of the Forum regarding this problem?


[IMG]http://800million.org/Ub/Default.jpg[/IMG]

[IMG]http://800million.org/Ub/Read_Write.jpg[/IMG]

---

### Post by Impavidus on 2021-05-16
Makefiles aren't executable files and you don't run them. Instead, you run make, which will find the makefile and interpret the instructions therein.

---

### Post by michelvandegaer on 2021-05-16
Ok, so I ran 'Make' and got this response: 

[INDENT]*No targets specified and no makefile found. Stop.*[/INDENT]

BTW since the Makefile didn't open in the Terminal I did a copy/paste of whole the Makefile-code into the Terminal, but nothing happened.

Here's the transcript: [http://800million.org/Ub/Terminal_printout.txt](http://800million.org/Ub/Terminal_printout.txt)

Not sure if that made any sense.



[IMG]http://800million.org/Ub/Make.jpg[/IMG]

---

### Post by Holger_Gehrke on 2021-05-16
For various reasons - chief among them the need for elevated privileges for putting the include files in /usr/local/include and the library in /usr/local/lib - this makefile is not a good candidate for running through the GUI. So just open a terminal, change the working directory to the one with the makefile and run 'sudo make all' for TinyEngine.
```

cd ~/Desktop/TinyEngine-master
sudo make all

```

The situation is similar for DynamicFoam, but here there's a simpler solution: the file 'main' is a compiled executable. If you have the same version of Ubuntu as the author and have all the needed libraries installed, you can simply mark this file as executable and run it.

Holger

---

### Post by michelvandegaer on 2021-05-16
Hi Holger, 

Thanks for your feedback!

I ran your code lines for *TinyEngine* Application and got:
[INDENT]
No rule to make target 'all'. Stop.[/INDENT]

I did the similar thing for the *DynamicFoam* Application and I got a bunch of errors, probably related to what you just wrote about needing the extra files from the author (or a library that's downloadable from Brew?), and a fatal error but that's probably related to the *TinyEngine* not being active.

I also opened/ran the Makefile from within the DynamicFoam-main folder with Run Software ... but it didn't do anything, probably again related to the same errors mentioned here above.


[IMG]http://800million.org/Ub/MakeAll.jpg[/IMG]

---

### Post by michelvandegaer on 2021-05-16
Wait. I made a mistake BRB

---

### Post by michelvandegaer on 2021-05-16
I'm back. 

The 'mistake' was that I had renamed the folder *TinyEngine-master* to [I]TinyEngine.
 
[/I]I renamed it back to it's original name and ran the code snipped that used 'TinyEngine-master'.

... and got a fatal error of a file that could not be found (operations.hpp).

I guess that relates to what you were mentioning earlier on regarding the need to have the same files as the author, and this is probably such a file/library. No?


[IMG]http://800million.org/Ub/Correction.jpg[/IMG]

---

### Post by michelvandegaer on 2021-05-16
Ha, I was able to install TinyEngine by installing that missing 'operations.hpp' library:[INDENT]
apt-get install libboost-filesystem-dev[/INDENT]


Something must have gone wrong during the installation of the dependency 'Boost' mentioned in my oringinal post:


[LIST]
[*]*Boost:   apt-get install libboost-system-dev libboost-filesystem-dev*
[/LIST]


[IMG]http://800million.org/Ub/TinyOK.png[/IMG]


---

Running the *DynamicFoam *Application still isn't solved:[INDENT]
compilation terminated due to -Wfatal-errors.[/INDENT]



[IMG]http://800million.org/Ub/DynFoam_err.png[/IMG]

---

### Post by Holger_Gehrke on 2021-05-16
As I said above, there's a pre-compiled binary in the git-repository. Have you tried that ?

I have tried compiling DynamicFoam and ended up with the same error. Seems that the author is not using the main branch of TinyEngine for this program but the newer version in the 'working' branch in the repository. So lets clean out the installed TinyEngine, download the newer branch, compile that and try again:
```

sudo rm -rf /usr/local/include/TinyEngine/
sudo rm /usr/local/lib/libTinyEngine.a
mkdir ~/src/
cd ~/src
git clone -b working https://github.com/weigert/TinyEngine.git
cd TinyEngine
sudo make all
cd ..

```
If the git command fails telling you that you don't have git installed, a quick 'sudo apt install git' should get that part running. Now try compiling DynamicFoam again. For me it complained about not finding 'noise/noise.h'. After 'sudo apt install libnoise-dev' it compiled but wouldn't run giving me 'SDL_Error: Couldn't find matching GLX visual'. Forcing SDL to use another way to look up GLX visuals with 'export SDL_VIDEO_X11_VISUALID=' ended with a window coming up for a fraction of a second and the program crashing. Probably wants something either my hardware or the installed OpenGL can't provide ...

Holger

---

### Post by michelvandegaer on 2021-05-16
Hi Holger,

Thanks for the new tips and progression.

Mh, for I a moment I felt like I was on board but I think that I started to mess things up.


So, I did the 'clean out' and 'new install via git', that went smooth:


[IMG]http://800million.org/Ub/run1.jpg[/IMG]

But as a follow up, fetching the DynamicFoam didn't work:

[IMG]http://800million.org/Ub/run2.jpg[/IMG]


I guess there I was still in the same 'area' as where you winded up, I did an install of the -lnoise stuff, like you did and i think also libboost again.

I also ran the 'Main' file in the DynamicFoam folder that you suggested again.
 
Note, I did't miss that comment the first time, but I misunderstood, and actually overlooked the actual 'main'.

I just did Run Software for the 'makefile' I though you were referring with "main" to that file. 

Anyway, it didn't do much, I got the 'Run Software wheel' and that was that.

[IMG]http://800million.org/Ub/run0.jpg[/IMG]


After the install of those libraries I tried to do again:

cd ~/Desktop/DynamicFoam-main
sudo make all

But that didn't work ... or I made a mistake ... I closed the terminal and tried the process again with the code you gave, but as there was no longer anything old to clean (I think), I started to get into a kind of situation where it only compiled TinyEngine again.

[IMG]http://800million.org/Ub/run3.jpg[/IMG]

--------

Note, I am in touch with Nick McDonald the developer of the programs, he is going to take a look later on.

BTW this is what the Dynamic Foam app does:

[https://vimeo.com/546373165](https://vimeo.com/546373165)

---

### Post by Holger_Gehrke on 2021-05-16
Actually I meant for you to run that 'main' executable in the shell. You get a lot more information that way. In this case, you'd probably get told that you're missing some libraries, specifically the libnoise and libboost_serialization. Install those two with 'sudo apt install libnoise-dev libboost-serialization-dev'. Missing those two libraries is why the compilation / linking failed in the next to last attempt you showed screenshots of. The last one failed because of that 'sudo -s' at the beginning. 'sudo -s' gives you a shell as root. '~/' at the beginning of a path is an abbreviation meaning 'the home directory of the current user'. There is no 'Desktop/DynamicFoam-main' in /root - the home directory of the root user.

And regarding all those screenshots: copy and paste from a terminal might be a bit more difficult (ctrl-c and ctrl-v for copy and paste don't work in a terminal because these keys have a special meaning to the shell, ^c is used to abort a running program, ^v is used to enter characters that normally would be interpreted by the command line editor; you can either use the terminal's menu to copy or use ctrl-shift-c to copy and ctrl-shift-v to paste) but it's worth it for two reasons: you can't quote from a screenshot and text takes up for less space/transmission capacity.

Holger

---

### Post by michelvandegaer on 2021-05-16
Hi Holgre,

Sorry for the screenshots, I'm actually working from two computers, responding here on the forum and doing all the other things on in Ubuntu. The reason is that I don't feel that at home yet, and the other one clickpad of the Thinkpad laptop isn't very precise ... it feels a bit like ice-skating for the first time : )
 
For the moment I'm sending these sreenshots via my gmail to my other computer, I've reduced the size so they shouldn't be too heavy.

I know how to do c/p in the Terminal using Ctrl + Shift but it's so automatic that I still do it sometimes in the terminal with just Ctrl. 

Next time I'll respond straight from Ubuntu.

 -----

So now I launched that main file from the Terminal and got the same issue regarding 'matching GLX' that you mentioned.

I looked it up and found this reference:

[https://stackoverflow.com/questions/41338549/sdl2-cant-create-window-since-it-couldnt-find-matching-glx-visual](https://stackoverflow.com/questions/41338549/sdl2-cant-create-window-since-it-couldnt-find-matching-glx-visual)

Where they said to do:

```
[COLOR=#000000][FONT=monospace]glxinfo[/FONT][/COLOR]
```

And so I did:

[IMG]http://800million.org/Ub/ex0.jpg[/IMG]

They mentioned to look for this:

[IMG]http://800million.org/Ub/ex1.jpg[/IMG]

Not sure why, and suggested to do this before executing:

```
[COLOR=#000000]export SDL_VIDEO_X11_VISUALID=[/COLOR]
```

Which I did ... and for a fraction of a second a black box showed up that disappeared again right away. I guess you had a similar result. Makes me wonder if I need for example a GPU card from Nvidia or so? Donno.

[IMG]http://800million.org/Ub/ex2.jpg[/IMG]

---

### Post by michelvandegaer on 2021-05-16
Mh, I promised not to send an other screenshot but ... 

here's one of that black 'Example Window' that jumped open for fraction of a second. Wondering if you had something similar.

[IMG]http://800million.org/Ub/example.jpg[/IMG]

BTW previous to this I got this reply in the Terminal after doing the execution (no more screenshot):

```
[COLOR=#000000][FONT=Helvetica]chimel@chimel-ThinkPad-X240:~$ ~/Desktop/DynamicFoam-main/main[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]terminate called after throwing an instance of 'std::runtime_error'[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]  what():  not triangulation[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Aborted (core dumped)[/FONT][/COLOR]
```

---

### Post by Holger_Gehrke on 2021-05-16
Yes, that's about the same I got. So I'm guessing this either needs better hardware or a newer OpenGL.

Holger

---

### Post by michelvandegaer on 2021-05-20
I got this feedback from the author today, curious if the advice in the linked-to Ubuntu-post helps in your case:
> 
[COLOR=#000000][FONT=Helvetica]- Makefiles are used by running make with a target (all) from the same directory with privilege, as Holger told you
[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]- Dependencies were missing[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]- The non merged TinyEngine branch is my fault, sorry about that.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]The GLX problem can probably be fixed. What graphics card do you have? I use an Intel integrated GPU, and yours should support Opengl 4.3 as well. I don't think you need to switch out your laptop. Check this thread:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica][https://askubuntu.com/questions/882628/updating-opengl-support-ubuntu-16-04-lts-mesa-12-0-6](https://askubuntu.com/questions/882628/updating-opengl-support-ubuntu-16-04-lts-mesa-12-0-6)
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]and tell me what your version is and try to update it to support 4.3 [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Also the not a triangulation error results from a failed Poisson sampling and can happen randomly in rare exceptions - just ignore and run the program again.[/FONT][/COLOR]

Note, to get some extra info on what the OpenGL my computer runs, I used these lines:
(Ref.: [https://askubuntu.com/questions/850900/why-is-my-opengl-version-stuck-at-3-0-despite-new-hardware-software](https://askubuntu.com/questions/850900/why-is-my-opengl-version-stuck-at-3-0-despite-new-hardware-software))

```
[FONT=var(--ff-mono)]glxinfo|grep OpenGL[/FONT]
```

Which gave the following information:

```
[COLOR=#000000]chimel@chimel-ThinkPad-X240:~$ glxinfo|grep OpenGL[/COLOR]OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 4400 (HSW GT2)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 20.2.6
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 20.2.6
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 20.2.6
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:
chimel@chimel-ThinkPad-X240:~$
```

This brings me to an other point/article about the the OpenGL Mesa 20.2.6, that it can be selective on what parts of its work depending on the driver:
> [COLOR=#404040][FONT=Lato]Mesa 20.2.6 implements the OpenGL 4.6 API, but the version reported by glGetString(GL_VERSION) or glGetIntegerv(GL_MAJOR_VERSION) / glGetIntegerv(GL_MINOR_VERSION) depends on the particular driver being used. Some drivers don&#8217;t support all the features required in OpenGL 4.6. OpenGL 4.6 is [/FONT][/COLOR][COLOR=#404040][FONT=Lato]only[/FONT][/COLOR][COLOR=#404040][FONT=Lato] available if requested at context creation. Compatibility contexts may report a lower version depending on each driver.&#8221;[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica][COLOR=#313131]
[/COLOR][/FONT][/COLOR]
[COLOR=#313131][FONT=Helvetica]Ref. [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica][https://docs.mesa3d.org/relnotes/20.2.6.html](https://docs.mesa3d.org/relnotes/20.2.6.html)[/FONT][/COLOR]

And going back to the readout above where different OpenGL profiles are mentioned:

[LIST]
[*]OpenGL core profile version string: 4.5 (Core Profile) Mesa 20.2.6
[*]OpenGL version string: 3.0 Mesa 20.2.6
[*]OpenGL ES profile version string: OpenGL ES 3.1 Mesa 20.2.6
[/LIST]

Would this mean, as mentioned in the Mesa article, that 4.5 is running but that it only uses 3.0 and 3.1 ... which isn't good enough for the 4.3 version that the author advises?

------

BTW something weird I have noticed is that these lines, seem to remove the 'main' file that's in the extracted 'DynamicFoam-main' folder on the Desktop.

```
[COLOR=#000000][FONT=Helvetica]cd ~/Desktop/DynamicFoam-main[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]sudo make all[/FONT][/COLOR]
```

... and the reason why I get [COLOR=#000000][FONT=Helvetica]"No such file or directory" when I run:
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Helvetica]cd ~/Desktop/DynamicFoam-main/main[/FONT][/COLOR]
```

---

### Post by michelvandegaer on 2021-05-20
Another strange thing I've noticed is that when I run:

```
[COLOR=#000000][FONT=Helvetica]cd ~/Desktop/DynamicFoam-main/main[/FONT][/COLOR]

```

The main file gets locked.


[IMG]http://800million.org/Ub/Lock.jpg[/IMG]

---

### Post by ActionParsnip on 2021-05-20
Instead of screenshots of text. Just copy and paste the text in the forum instead. A forum is a text based system.....

---

### Post by michelvandegaer on 2021-05-20
> **ActionParsnip said:**
> Instead of screenshots of text. Just copy and paste the text in the forum instead. A forum is a text based system.....

Yeah, it was already addressed a few post earlier on, sorry for that.

Any ‘on topic’ suggestions on how to get this application installed would be much appreciated!

---

### Post by Impavidus on 2021-05-20
You ran```
sudo make all
```to compile the program. I wouldn't use sudo for that. You need sudo to install the program system wide, not to compile it. As a general rule, only run the things that really need it with root privileges. As you ran make with sudo, the resulting executable is owned by root and your ordinary user has limited access to it. For example, I don't think you can right now compile it again without sudo, as the tools would attempt to overwrite your executable and have no permission to do so.

You can change ownership of the executable to yourself using chown. You can also delete it, then compile again, but now without the sudo. To delete files, you only need write access to the directory, not to the file itself. But on the other hand, if you want to install it system wide, you can simply move the executable to /usr/local/bin/ or wherever you want it (but that's the suggested location). Stuff there should be owned by root.

I suggest you create a directory to experiment in, maybe create a few more users and groups, and play a bit with permissions. The permission system on Linux is actually really simple.

---

### Post by michelvandegaer on 2021-05-20
Oh man this sucks so hard. 

Isn't there a tool that the author can use that extracts everything related into one install file? 

What a bunch of misery just to run one application. Horror.

I am going to do an erase-install of this laptop ... and start again without the "sudo make all"

To be continued ... brrrr

---

### Post by michelvandegaer on 2021-05-20
Hi Impavidus,

I'm back, sorry for venting some frustration.

I just did a clean-erase install and installed all the dependencies (I hope) and downloaded the two programs [TinyEngine]("https://github.com/weigert/TinyEngine") (not sure if this is now the right version) and [DynamicFoam]("https://github.com/weigert/DynamicFoam").

Now I followed your advice doing the make without the "sudo all" and go this prompt that permission was denied:

```
chimel@chimel-ThinkPad-X240:~$ cd ~/Desktop/TinyEngine-master
chimel@chimel-ThinkPad-X240:~/Desktop/TinyEngine-master$ make
Copying Core Header Files ...
mkdir: cannot create directory ‘/usr/local/include/TinyEngine’: Permission denied
make: *** [makefile:23: setup] Error 1
chimel@chimel-ThinkPad-X240:~/Desktop/TinyEngine-master$ 


```

So I guess I have no other option than to install this under "Sudo -s"?

BTW I didn't really understand your point of *"move the executable to /usr/local/bin/"* do you mean with this to put the whole downloaded applications folders over there instead of just leaving them on the Desktop, and how do I do that, that location seems to be hidden.

----

Edit: This was the code suggested by Holger to download directly from git but it had the Sudo make all:

```
sudo rm -rf /usr/local/include/TinyEngine/
sudo rm /usr/local/lib/libTinyEngine.a
mkdir ~/src/
cd ~/src
git clone -b working https://github.com/weigert/TinyEngine.git
cd TinyEngine
sudo make all
cd ..
```

What should I use?

---

### Post by Holger_Gehrke on 2021-05-20
Better makefiles have separate targets for compiling and installing. The one for TinyEngine doesn't, it's 'install' target compiles the library and copies it to '/usr/local/lib/' and '/usr/local/include/'. The one for DynamicFoam doesn't have a target for installation, it only compiles the program. So use 'sudo make all' for TinyEngine and just 'make' for DynamicFoam.

Holger

---

### Post by michelvandegaer on 2021-05-20
Alright, thanks Holger. I&#8217;m going to give it an other go tomorrow.

BTW have you been able to run it &#8230; have you seen the comments from the author on page 2?

I also got this feedback later today from him:
> Try compiling the TinyEngine example programs. Use the makefiles in the example folder (sudo make all).

The main file should be compiled any way, dont worry if it disappears.

Getting a dedicated server makes no sense.

The standard procedure is to install all dependencies, then clone the repo and then follow the installation instructions.

If there is no folder main, then you can not CD into main. To check the files / directories, use "ls". The dynamicfoam repo should not have a folder main, just an executable. If its missing you can regenerate it using make.

Let me know if the example programs compile. Otherwise I can roll back the GL version to compatibility profiles.

Note, the part about a dedicated server was as an alternative to run it on, would that make sense to you?

&#8212;

You also say &#8216;better makefiles&#8217; is there anything specific that you have in mind / advise that would make it (a whole lot) better?

---

### Post by Impavidus on 2021-05-21
Proper makefiles have separate rules for compiling and installing and only the rules for installing need sudo. It appears that this isn't one of those proper makefiles. In any case, when your file manager shows any file with a lock on it, it means you (as in your ordinary user) have only limited permissions on it. Probably because you're not the owner (root is) and only the owner has write permissions. A proper makefile would avoid this, but it's easy to fix with chown. All files in your home directory (including any subdirectories) should be owned by you, unless you've something special in mind.

Yes, installing software takes quite a bit of knowledge if you don't have a proper installer.

---

### Post by michelvandegaer on 2021-05-31
Hey,

I'm back, good news I got the issue solved last week with the help of the author [Nick McDonald]("https://github.com/weigert").

I thought I pass by with an update:

He removed spurious dependencies and reduced the shader version, the new versions can be downloaded at:

[https://github.com/weigert/TinyEngine](https://github.com/weigert/TinyEngine) (The underlying engine)
[https://github.com/weigert/DynamicFoam](https://github.com/weigert/DynamicFoam) (The actual program)

---

For installation these three steps are needed to get started:

_I. Installing dependencies:_


[LIST]
[*]OpenGL3: apt-get install libglu1-mesa-dev
[*]SDL2: apt-get install libsdl2-dev libsdl2-ttf-dev libsdl2-mixer-dev libsdl2-image-dev
[*]GLEW: apt-get install libglew-dev
[*]Boost: apt-get install libboost-system-dev libboost-filesystem-dev
[*]GLM: apt-get install libglm-dev
[/LIST]

[U]
II. For the TinyEngine:[/U]

```
cd ~sudo rm -rf TinyEngine
git clone https://github.com/weigert/TinyEngine
cd TinyEngine
sudo make all
cd examples/0_Empty
make all
./main
```

It downloads the code and installs it on your computer.


_III. For the DynamicFoam app:_

Download the Zip file and unzip it to your computer:

[https://github.com/weigert/DynamicFoam/archive/refs/heads/main.zip](https://github.com/weigert/DynamicFoam/archive/refs/heads/main.zip)

Next run 

```
cd ~/Desktop/DynamicFoam-main/

./main
```

The first line is to go to the map (I had placed it on my Desktop), and ./main (+Enter) is to run the app.

Note: I had to first delete in the 'Makefile' in the DynamicFoam-folder these two from the linker line:
[LIST]
[*]-lnoise
[*]-lboost_serialization
[/LIST]

---

Once the program runs press 'P' to toggle the paused state of the simulation and 'ESC' to view the simulation control.

Here are two sample-clips with how it looks:

[https://vimeo.com/557182750](https://vimeo.com/557182750)
[https://vimeo.com/557181751](https://vimeo.com/557181751) (inverse colors)

Have fun if you would like to give try it, 
and thanks for all the support!

Best,

M.


p.s. I'm adding below all the communication to get it to work.

> 

The makefile does not perform an "install", therefore that comment is redundant. Installing means copying an executable from the compilation location to a location where the shell looks for executables, e.g. /usr/bin/. This makefile only compiles. And we executed with privilege as a debugging measure since you were having compilation issues. Otherwise it is not necessary to compile as root.

I merged the TinyEngine working branch so you can just clone the main branch to your location of choice (your home folder):

cd ~
git clone [https://github.com/weigert/TinyEngine](https://github.com/weigert/TinyEngine)
cd TinyEngine

It will be cloned into a folder called "TinyEngine". Don't worry about uninstalling it first - if it exists, it will be overwritten. We then use the makefile to perform a build + install. It builds in a folder called TinyEngine/tmp/ which is made and then deleted after install. We run this as privilege so the copy can happen. The file ownership does not matter for the linked libraries.

sudo make all

The files are now installed in the correct locations, which you can read at the top of the makefile.

Finally, we try to compile the example programs (without privilege because without install) and see if we can get a window to open.

cd examples
make all

The executables will remain in the folders of the example programs. We can test example program zero:

cd 0_Empty
./main

This output should then give you the glx error. Don't do anything else, just please confirm that it gives you the "missing glx visual" error. We can then debug from there.

—————

I have removed any spurious dependencies in the main branch (libnoise, boost serialization - they were indeed not required but an artefact in the makefile), so just use the one-liner provided in TinyEngine readme:

sudo apt-get install libglu1-mesa-dev libsdl2-dev libsdl2-ttf-dev libsdl2-mixer-dev libsdl2-image-dev libglew-dev libboost-system-dev libboost-filesystem-dev libglm-dev

On Ubuntu this should be all that you need. If you have installed correctly, this command should also tell you "0 new installed". If not, send me what it tells you is failing.

—————

You were missing the SDL TTF dependency - running the command I sent does exactly what you found in that forum.

Also I JUST fixed the spurious dependencies - so make sure to delete the repo folder, reclone and repeat the steps. Execute the dependency install first / before running the makefile.

—————

It appears you have installed all dependencies correctly as the programs have compiled. This might be an issue with how TinyEngine tries to create a GL context. I will try to reduce to a compatibility version to see if it works, I will update you in a moment.

Also try the following:

glxgears

and tell me if the program runs correctly, and then:

sudo apt-get install libx11-dev

And then recompile install TinyEngine and the example file using the makefiles

cd INSTALLFOLDER
sudo make all
cd examples/0_Empty
make all
./main

—————

Can you please check if you are using Ubuntu / Gnome on X11 or Wayland?

echo $XDG_SESSION_TYPE

Result: X11

————

With INSTALLFOLDER I meant for you to replace it with your install folder, because you told me you were not installing it in your home folder. That's why none of the subsequent commands worked.

When you get the error with "already exists", just type:

sudo rm -rf TinyEngine. 

This removes the folder and its contents recursively. Then you can repeat the steps.

It is interesting that glxgears only ran after you installed something else:

sudo apt install mesa-utils

I suggest cleaning the install (i.e. delete the TinyEngine folder - the additional steps that holger adds are not strictly necessary), recloning the working branch, installing and attempting to run the example.

In other words, while you are running an X11 session:

cd ~
sudo rm -rf TinyEngine
git clone [https://github.com/weigert/TinyEngine](https://github.com/weigert/TinyEngine)
cd TinyEngine
sudo make all
cd examples/0_Empty
make all
./main

——————

Remove the folder again, but this time try cloning the working branch, because I have reduced to a compatibility version.

cd ~
sudo rm -rf TinyEngine
git clone -b working [https://github.com/weigert/TinyEngine](https://github.com/weigert/TinyEngine)
cd TinyEngine
sudo make all
cd examples/0_Empty
make all
./main


Result:

SDL_Error: Couldn't find matching GLX visual

I ran:

export SDL_VIDEO_X11_VISUALID=

This causes SDL to go down a different code path to find the visual. You can also try hardcoding the visual to the visual id from glxinfo:

export SDL_VIDEO_X11_VISUALID=0x022

Ref. [https://stackoverflow.com/questions/41338549/sdl2-cant-create-window-since-it-couldnt-find-matching-glx-visual](https://stackoverflow.com/questions/41338549/sdl2-cant-create-window-since-it-couldnt-find-matching-glx-visual)

——————

Can you please give me the full output of glxinfo?

Apparently your card should support the latest GL: [https://superuser.com/questions/561177/which-version-of-opengl-does-intels-integrated-graphics-card-support](https://superuser.com/questions/561177/which-version-of-opengl-does-intels-integrated-graphics-card-support)

Otherwise I have further reduced the compatibility version. You can try recompiling again just like you did with the working branch to see if anything has changed.

——————

Can you try running:

sudo apt-get install mesa-utils xserver-xorg-video-intel

and confirm that nothing new is installed, then run

sudo ldconfig

——————


I tried:

export MESA_GL_VERSION_OVERRIDE=3.3

via [https://stackoverflow.com/questions/52592309/0110-error-glsl-3-30-is-not-supported-ubuntu-18-04-c](https://stackoverflow.com/questions/52592309/0110-error-glsl-3-30-is-not-supported-ubuntu-18-04-c)

——————

You need to do the following:

sudo nano /etc/modprobe.d/default.conf

Then enter the line:

options snd_hda_intel index=1

then hit ctrl+x, then y and enter (this saves the file), then restart your computer.

To run the julia example go to the julia set example folder:

cd ~/Desktop/TinyEngine-master/examples/4_Julia/

and then compile and run:

make all
./main

(... and Enter)

git clone -b working [https://github.com/weigert/TinyEngine](https://github.com/weigert/TinyEngine)

——————

You should be able to fix this quickly by opening the Makefile and deleting the -lnoise and -lboost_serialization from the linker line.

Then recompile and run. 

The dependencies are deprecated.

——————

There’s a a minor visual bug with the triangles that I haven't fixed yet because of an opengl feature you might be missing on the compatibility version, but everything else should work.

The large triangle is the graphical bug and results from the fact that the compatibility profile of opengl with version 1.3 GLSL shaders does not support shader storage buffer objects. This is the feature I use to render the triangles with properties, which then defaults to that position as it fails. This also causes some irregular segmentation faults - if the program crashes just restart it. This does not happen when the core profile is used (like on my computer).

Your graphics card apparently supports a core profile but some of the tests which I had you do previously apparently failed to load the core profile and resulted in the GLX bug. I am not quite sure why.

——————

Download the updated compatibility version of DynamiFoam.

——————

To generate the executable you simply need to compile. Enter the directory and type "make all".

The main file is definitely generated via compilation


The reason you dont typically ship software with a compiled binary is because of potentially different linked library locations or other compatibility problems, i.e. the binary needs to be compiled on the target platform.

The instructions for compilation are in the makefile, and so typing make all generates the binary on your computer.

---

