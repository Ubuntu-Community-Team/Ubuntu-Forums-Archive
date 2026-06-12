---
title: "HowTo Extract .run files?"
date: 2007-02-25
forum: General Help
---

### Post by fejimush on 2007-02-25
How do you extract the contents of a .run file?  (i.e. like the ati/nvidia closed source drivers)

Thanks,
fej

Update:  Problem solved...see my reply below.

---

### Post by Mike'sHardLinux on 2007-02-25
Hi fejimush!

You don't extract .run files. They are actually scripts that you run on the command-line. You probably need to make it executable ( chmod +x filename.run ), and then type something like ./filename.run

I believe those drivers to which you are referring need to be run them as root, but I'm not sure.

Also, if you want to see what's in the script, open it in a text editor.

---

### Post by Maestro23 on 2007-02-25
> **fejimush said:**
> How do you extract the contents of a .run file?  (i.e. like the ati/nvidia closed source drivers)

Thanks,
fej

Open a terminal:

> sudo chmod +x filename.run
./filename.run


*Edit: Sorry, thought you wanted to run the script.

---

### Post by fejimush on 2007-02-25
Just like this:

> sh ./some-run-package --extract target_directory

some use this instead:

> sh ./some-run-package --extract-only target_directory

turned out to be easier than I thought.

Thanks for the replies though,
fej

---

### Post by Mike'sHardLinux on 2007-02-25
That is curious. I always thought .run files were simply scripts that did something, like install UT2004, or install drivers. I didn't realize there was anything to extract. What exactly was contained in that file?

---

### Post by fejimush on 2007-02-25
All kinds of good stuff...usually a bunch of script files that do something useful and lib files and etc...(pretty much whatever they stuff in there).  A tool called Makeself is used for this.  (Just learned all this).

thanks,
fej

---

### Post by ~LoKe on 2007-02-25
The nVidia drivers had some problems recently where you'd need to correct a line in some of the files.

```
sh *run --extract-only
cd NV*
gksudo gedit usr/src/nv/nv-linux.h
## make the modification
cd ../../../ && ./nvidia-installer
```

---

### Post by fejimush on 2007-02-25
> **~LoKe said:**
> The nVidia drivers had some problems recently where you'd need to correct a line in some of the files.

```
sh *run --extract-only
cd NV*
gksudo gedit usr/src/nv/nv-linux.h
## make the modification
cd ../../../ && ./nvidia-installer
```

That doesn't look like valid C.   Do you have the right file?  Is that supposed to go in a script file and not a header file?

thanks,
fej

---

