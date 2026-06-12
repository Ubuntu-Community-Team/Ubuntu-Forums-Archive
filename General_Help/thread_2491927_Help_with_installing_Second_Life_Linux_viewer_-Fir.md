---
title: "Help with installing Second Life Linux viewer -Firestorm (I am a NOB)"
date: 2023-10-25
forum: General Help
---

### Post by mraroid on 2023-10-25
Hello friends...

I need to be able to tell you which version of Ubuntu I have installed.  I clicked on everything but was unable to tell.  I do have have something called Ubuntu Pro (good to 2032) installed, and I also install any updates Ubuntu tells me to install.  So I believe I am up to date.  But I can not find a place to see which version of Ubuntu I have on my system.  Any suggestions on what click on?

Once that is over with, I would like to install a Linux port of a Second Life viewer called Firestorm:

[https://www.firestormviewer.org/linux/](https://www.firestormviewer.org/linux/)

I do not understand how to properly extract it and install it.  I have down loaded it. I made a folder called SL and moved my downloaded file to it.  I clicked on the file and it acted like it was extracting something, but if it did, I am unable to find it on my system.

If someone can direct me to a web page or help page which would help me, I would be happy to do that and not bother anyone.  But as it is now, I do not understand the directions on the above link.

Help appreciated.
Many thanks,

mraroid

---

### Post by #&amp;thj^% on 2023-10-25
Let's see what your runing now:
open a terminal and run:
```
sudo apt install inxi
###Now Run
inxi -F
```
Copy the output from the terminal for the last line only. And please wrap it in Code Tags >>>[noparse][CODE} copied text here[/CODE][/noparse]

---

### Post by TheFu on 2023-10-25
I don't think you want to be called a "NOB", perhaps "noob" is a nicer term?

There are many ways to know what release you are running.  The easiest that I know is this terminal command:

**lsb_release -a**

If you want a short, system overview, use:
**inxi -bz**
You'll probably need to install the inxi package for that to work. It can provide all sorts of specialized information about a system, based on the options.  To install, first update the repo lists:
**sudo apt update**
then install a specific package:
**sudo apt install inxi**
This assumes you know the name of the package with the correct case. Most will be all lowercase, but sometimes a hyphen will be added where we don't expect it.  I supposes there's a GUI to install packages. I find that too slow. Also, the most recent GUI package managers have mixed regular, debian packages and dependencies with the alpha-code for "snap" packages that Canonical decided we all needed (we don't).  Whether to use snap packages is your choice. There are pros and cons, just know they behave differently, have restrictions, and generally load slower. OTOH, in theory, snap constraints provide protection between different programs harming each other, but those protections can get in the way of things "just working", which can be extremely frustrating.  Also, snap packages will self-update which sounds like a good idea, until one of those updates breaks your workflow unexpectedly because it happened in the middle of a workday.

Want "full" information?   **inxi -F**
Want Networking?  **inxi -Nxx**
Want Graphics/GPU?  **inxi -Gxx**
The manpage for inxi will be installed with the program package and explains all the different settings.  As a "noob", manpages are the main way to learn about the commands on your system.  Want to know how to use the manpages?  **man man**

There are 50,000 ways to install different programs on Linux, but there are 3 main ways.  Let me look at that link to see if they are using on of the main ways.  BTW, 99.99% of the time, you should be using the package manager, like APT or Synaptic to install programs.  Going out and downloading a package from some random website is the LAST way you should install software.

Ok, They are providing two files for download:
```
Firestorm Release 6.6.14.69596 64 bit Linux.tar.xz
MD5 Checksum: 46ca48b9db04d7aba8c03b98a00fbd83
```

The first is a tar + xz compressed file. 
The 2nd is the md5sum of that file, as a way to ensure (99.99%) that the tar.xz file is the one the author claimed.  

Validate the download: ```
**cd** into the directory where both files are downloaded.  I don't know where you put them.  You can check your ~/Downloads/ directory and /tmp/ directory to start. If you can't find them, download again, this time keeping track of where the files are placed. **PAY ATTENTION**.

[code]$ md5sum "Firestorm Release 6.6.14.69596 64 bit Linux.tar.xz"
```
The output from the md5sum command will be a filename and long hex number.  I theory, this number should 100% match the "46ca48b9db04d7aba8c03b98a00fbd83" above.
If you are lazy, like me, you can use bash globbing to make the command shorter:
```
$ md5sum Fires*xz
```
Lazy is good and prevents typing too much. Remember, Unix is always case-sensitive.
There might be a GUI way to do these things. I don't know it. Sorry.

Oh, because the person who created the file seems to have been space-happy (they put spaces in the filename), you'll need to always quote that filename, unless you rename it so it doesn't include spaces or other "funny" characters. It will be a pain until you do.

If the md5sum output matches, continue. If it doesn't STOP IMMEDIATELY.

So you have a .tar.gz file and want to uncompress it and expand the tar?  We can do that in 1 command.
```
tar -Jxvf Fires*xz
```
Note how I'm lazy again?  Also, the -j is a switch/option specific to the xz compression used.  Other types of compression like gzip, zip, compress, bz, lzip, lzma, lzop, zstd, ...  each have their own option. There's an option to specify any other compression used with an external "helper" too, if that's needed.

Now you will have a new subdirectory. **cd** into that and look for a README or INSTALL file and follow those instructions.  Destribution of programs with a tar file is so 1990s. Around the mid-1990s, all the major distros changed to a package manager with cryptographic signatures to provide automatic assurances that the team creating the software approved the package.  Using a tar file is very flexible, but too much like a setup.exe in the MSFT ecosystem and doesn't provide the same level of validation that a properly signed .deb package provided through a Canonical repo provides.  Plus, you will need to maintain this package, since it isn't integrated in the OS repository upgrade system like the other 2000 packages in your system are.  It is best to find a package in a Canonical managed repo with a SL client and use that instead, so any needed updates are included with your normal, weekly, patching.

BTW, I did a web search asking the same question you asked.  Found this: [https://askubuntu.com/questions/579806/how-to-install-second-life](https://askubuntu.com/questions/579806/how-to-install-second-life) which has steps.  Also, [https://wiki.secondlife.com/wiki/Linux_Viewer](https://wiki.secondlife.com/wiki/Linux_Viewer) which says that no install is needed.  Looks like there could be some challenges with movie playback and other graphics driver issues, especially if you have an nvidia GPU.

---

