---
title: "Missing library for Appimages in Ubuntu 24.04"
date: 2024-04-28
forum: General Help
---

### Post by flatdisk on 2024-04-28
Hello, I installed the new LTS Ubuntu release, 24.04 and everything works great. However, I discovered there's a missing library necessary to run Appimages in the repository of Ubuntu 24.04.
If I try to launch an Appimage (Orcaslicer in my case) I get this:

```
/tmp/.mount_OrcaSlGe0RMn/bin/orca-slicer: error while loading shared libraries: libwebkit2gtk-4.0.so.37: cannot open shared object file: No such file or directory

```

Through Synaptic I've seen that the packages libwebkit2gtk-4.1-0 and -6.0-4 are already installed.
What can I do? Is there a way to report this missing library?

Thank you in advance!
[COLOR=#005400][FONT=Monaco]
[/FONT][/COLOR]

---

### Post by TheFu on 2024-04-28
If the issue is for 1 program, contact the AppImage packager.  Often, they forget dependencies.

---

### Post by flatdisk on 2024-04-28
I've checked that and indeed other AppImage apps work well. I'll contact them, thanks for the help!

---

### Post by hong-xu on 2024-04-29
For a quick resolution on your side, you can try to install the dependency and see if it works out: ```
sudo apt install libwebkit2gtk-4.0-37
```

EDIT: The package above is no longer available in Ubuntu 24.04. Looks like you have to contact the author of the AppImage :(

---

### Post by vanadium on 2024-04-30
> **hong-xu said:**
> For a quick resolution on your side, you can try to install the dependency and see if it works out:

That typically will not work, by definition, for containerized applications. These applications have no access to the system directories.

---

### Post by TheFu on 2024-04-30
> **vanadium said:**
> That typically will not work, by definition, for containerized applications. These applications have no access to the system directories.

AppImages aren't containers. They are just 1 packaged file with all dependencies and LD_LIBRARY_PATH set to find the appimage libraries BEFORE any system libraries.  We've been doing this for 40 yrs, just without the good marketing that is AppImages. I'm over-simplifying what the AppImage wrapper does, but not by much. There aren't any constraints and it isn't a "Linux Container" at all.  This is a main reason people like AppImages over Flatpaks and snaps. No constraints.  It can be a liability if the source of the appimage isn't trusted.

---

### Post by Tadaen_Sylvermane on 2024-04-30
I saw a video on this. I think this is the libfuse2 problem. Libfuse2 is old and barely being maintained. They've moved to libfuse3. As such 2 has been dropped from default installations for a number of distros. This has broken the bulk of appimages. The maintainer of AppImage, at least in the video that I saw seems intent on sticking with libfuse2. So this will likely not get solved any time soon. You can install libfuse2 yourself from the repositories although there is no telling how long it will remain available.

[https://www.youtube.com/watch?v=jaYZqc7Luag](https://www.youtube.com/watch?v=jaYZqc7Luag) for those interested. This is the one I watched not long ago when I hit a .so not found on 22.04. It's pretty much failing to self extract.

*edit* I like this guy's videos but he can be a bit obnoxious. Fair warning.

---

### Post by kdmorris303 on 2024-05-06
OrcaSlicer did the same for me... the devs are aware of and addressing it if you can be patient.

Patience isn't my virtue... I added the jammy repositories, apt update, apt install libwebkit2gtk-4.0-37 as described [here]("http://github.com/bambulab/BambuStudio/issues/3973") then removed jammy from sources.

It feels like a bad idea and I take no responsibility for your actions, but it got me running.

---

### Post by TheFu on 2024-05-07
> **kdmorris303 said:**
>  It feels like a bad idea and I take no responsibility for your actions, but it got me running.

Sometimes, we have to do what we have to do.    As long as that library isn't being used by other apps and didn't replace an existing one, then the only issue likely will be with the AppImage AND without it, the AppImage doesn't run, so there is little risk.

I don't know any specifics about AppImage packaging, but I understand the idea - because we would manually do much of what an AppImage does whenever a specific library is needed for specific programs over the last 3+ decades across many Unixen.  My only fear is that the library is listed in the APT DB  and will break other programs.  

If it were me, I'd create a /usr/local/appimage/lib/ directory and create a hard-link to the library in that location (and any other important parts of the libxxxxxxx.deb file would need to go to in similar "correct" locations under /usr/local/appimage/.  Then I'd purge the package from APT, so it doesn't mess with dependencies. All the other items in the deb file and where they belong is a judgement call that most C programmers can make.  

Another option, could be easier or more complex, IDK.  If possible, unpack the AppImage and recreate it with the libxxxxxx.a/.so files where ever the other AppImage libraries in the package are located in the virtual file system of the AppImage creation tool.   [https://spetriuk.github.io/linux/how-to/AppImage%20Repack/](https://spetriuk.github.io/linux/how-to/AppImage%20Repack/)  makes it seem pretty clear and easy to add a library to an AppImage, but I've never done it so I don't really know.  For people unused to dealing with packaging and unfamiliar with the different types of files, this hill will be very steep.

I don't know if this post is clear at all.  Mainly, the goal is to have the correct library, in a location that only the appimage uses, not corrupt the installation with bogus deb packages, so dependency issues don't arise. Sorry if I just confused it more for some.

---

### Post by rva1945 on 2024-07-01
Hi, I'm looking for help regarding running AppImages. I want to run any slicer like Cura, Orca, etc, but to no avail. Went to Properties and enabed Run, installed libfuse2 (it was already installed BTW). 20.04 is my Linux version.
You say that other AppImages work, I'd appreciate any help!

---

