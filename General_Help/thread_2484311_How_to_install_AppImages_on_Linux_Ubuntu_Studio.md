---
title: "How to install AppImages on Linux Ubuntu Studio"
date: 2023-02-22
forum: General Help
---

### Post by crecoproject on 2023-02-22
Dear Community,
I will install a AppImage from Oassia Score.
There it is explained that I need libfuse2 to install it.
So I have tried to install libfuse2 but the
Message which I then get explains that libfuse2
is already installed.
But when I call libfuse2 from the Terminal
This Command is not known
So the Problem is:
1.) In which way can I install libfuse2
2.) In which way can test this Installation
3.) In which way can I install the AppImage.
For constructive Ideas thankful
CreCoProject

---

### Post by Rick St. George on 2023-02-22
How did you call it in Terminal ??? The following is what I get;

```

$ sudo apt list libfuse2

Listing... Done
libfuse2/focal,now 2.9.9-3 amd64 [installed,automatic]
libfuse2/focal 2.9.9-3 i386


```

If  it is not listed;

```


sudo apt install libfuse2


```

Personally I like to install with "Synaptic Package Manager" (if you have it installed), but after I checked the file has no dependencies and the Pkg contains the shared library.
Hope this  helps!

Peace 
Rick

---

### Post by Holger_Gehrke on 2023-02-22
Appimages are the closest thing to Windows 'portable apps' you'll find on Linux. You just put them in some directory in your PATH (for a single user I recommend ~/bin or ~/.local/bin), mark them as executable, and perhaps set up a .desktop file so your GUI knows about it and you're done.

libfuse2 isn't a program you can call directly, it's a library that programs can load, comparable to a DLL on Windows. From 'apt show libfuse2'
> 
Description: Filesystem in Userspace (library)
 Filesystem in Userspace (FUSE) is a simple interface for userspace programs to
 export a virtual filesystem to the Linux kernel. It also aims to provide a
 secure method for non privileged users to create and mount their own filesystem
 implementations.
 .
 This package contains the shared library.

If libfuse2 is installed correctly, you should have a file libfuse.so.2.x.y (x and y are minor version and patch level; on 22.04 it's libfuse.so.2.9.9) in /lib/x86_64-linux-gnu/ and a symbolic link named libfuse.so.2 in the same directory.

Holger

---

### Post by mIk3_08 on 2023-02-22
I do have Appimage application that runs in my system.
What I did is that, I just make it executable via a terminal window with the command below:
```
chmod +x application-name.AppImage
```
Then I run the AppImage by just double clicking or you can just run via command below in your terminal: 
```
./application-name.AppImage
```
Regards and cheers.

---

### Post by crecoproject on 2023-02-23
Thanks a lot Commuity,
I have made the Installation File executable.
And it seams to work.
But I have now another Problematic Fact.
The File will nothing install.
Rather it starts the Program directly.
I think just I read a little bit of the Oasis Manual.
So I would express my thanks to you.

---

