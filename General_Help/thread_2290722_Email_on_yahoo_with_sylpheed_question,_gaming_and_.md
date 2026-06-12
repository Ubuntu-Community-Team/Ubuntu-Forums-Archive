---
title: "Email on yahoo with sylpheed question, gaming and other notes, failed hard drive."
date: 2015-08-14
forum: General Help
---

### Post by vanquishedangel on 2015-08-14
Hi, and thank you for reading this. 

System:
HP DC 8200 elite SFF
intel i7 2600 
32 gig ram
AMD power color radeon HD 7750

I will be in college again soon so i need my computer and I recently had to reinstall due to a hard drive failure when my neighbor decided that it was a good idea to flip all the breaker switches for all of the apartments every time he blew a breaker. This was several times because he was trying to install a washer and dryer in an apartment without the proper water or electrical hook ups. This seemed to cause damage to my hard drive, he was doing this about 20 times a day for a month. I was using windows on that hard drive for gaming, it was faster, and had 500 gigs. I only have an ancient hard drive as a backup that is 80 gigs to reinstall on so I installed zram, commented out the swap in fstab, shrunk the swap space from 34 gigs to 1 gig, then expanded the partition with the OS. I then ran badblocks on the bad hard drive, and entered a list of bad sectors in fsck so the operating system will not use the bad sectors. This way I can use it to store my videos, plus I moved the wineprefix folder to the bad hard drive then created a symlink to it in my home folder. I will update this to make it more readable.


**_[SIZE=4]My question about yahoo and imap[/SIZE]_**:

On to my question. I am going back to school again and would like sylpheed to check all my emails using imap. I have my google address working and my college address working (office 365). However yahoo refuses to work with imap. Tutorials I have followed:

[http://email.about.com/od/accessingyahoomail/f/What-Are-The-Yahoo-Mail-Imap-Settings.htm](http://email.about.com/od/accessingyahoomail/f/What-Are-The-Yahoo-Mail-Imap-Settings.htm)

[https://help.yahoo.com/kb/SLN4075.html;_ylt=A0LEViy5Mc5VAc8ACFAnnIlQ;_ylu=X3oDMTByNXQ0NThjBGNvbG8DYmYxBHBvcwM1BHZ0aWQDBHNlYwNzcg--](https://help.yahoo.com/kb/SLN4075.html;_ylt=A0LEViy5Mc5VAc8ACFAnnIlQ;_ylu=X3oDMTByNXQ0NThjBGNvbG8DYmYxBHBvcwM1BHZ0aWQDBHNlYwNzcg--)

None of these work, I got sylpheed to be able to send mail through yahoo but not able to check email, I even tried folder remapping.



**[SIZE=4]_Gaming Notes_[/SIZE]**:

As for the rest of this post, gaming has greatly improved. I run Neverwinter nights (due to AMD graphics, exe had to be renamed) Neverwinter nights 2, Witcher, and the Witcher 2, using Playonlinux.  So notes on these:

**Neverwinter Nights**: This game has tons of player content installed that i collected over many years including, tony k AI, NWshader, PRC pack, and tens of thousands of other files for high resolution graphics updates to models and gameplay. NWshader was installed while using windows. This makes the requirements to run my game higher. I installed using the Playonlinux script, but then installed vcrun 2008 as well. I then discovered wine-staging through playonlinux. I downloaded the newest one through playonlinux and updated the wine prefix for neverwinter nights to use wine-staging 1.7.49. Works like a dream, will post regedit setting later. renamed NWMAIN.exe to NWMAIN2.exe and run the game from there. I zipped my game folder from windows and copied it all to the wine prefix playonlinux made after installing from GOG. 

**Neverwinter Nights 2**: I also have some custom content here but not as much. I zipped this one as well then installed from GOG using playonlinux script. The difference here is I took notes of the programs that the script installed, then deleted the prefix. I then reinstalled without using the playonlinux script, through playonlinux I downloaded two versions of wine, 1.5.31 32 bit and 1.5.31 64 bit. I selected to "install a nonlisted program", then selected the 1.5.31 version for wine, then selected a 64 bit installation (A glitch in Playonlinux makes this required for 64 bit installation). I installed the same programs in the prfix that the script did. Then I installed wine1.7.43-staging-LOL 64 bit. I then clicked confiure in playonlinux and selected wine 1.7.43-staging-LOL. Then the short cut I picked is "nwn2main_amdxp.exe" and then I copied the zipped games files over the existing ones made.

**The Witcher**: Much more straight forward since I have no custom content here, I installed using the playonlinux script. Then selected configure and changed the wine version to 1.7.49-staging.

**The Witcher 2**: Straight forward as well. Installed using the playonlinux script then updated to wine 1.7.49-staging. I also installed xact from playonlinux.


With wine-staging it makes the graphics card do more of the work, and enables threading, among many other things. To enable staging you must configure wine, then click on the staging tab through playonlinux. So far all my games work flawlessly, many even better then they did in windows 7. Here is my reg.reg file for wine (copy and paste, rename file to reg.reg and save it so you can import it through registry editor) (the red part is grahics card specific, can be excluded):

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="opengl"
"Multisampling"="enabled"
"Nonpower2Mode"="repack"
"OffscreenRenderingMode"="fbo"
"RenderTargetModeLock"="readtex"
"StrictDrawOrdering"="enabled"
"UseGLSL"="enabled"
"VertexShaderMode"="hardware"
[COLOR="#FF0000"]"VideoDescription"="ATI Radeon HD 7750"
"VideoDriver"="ati2dvag.dll"
"VideoMemorySize"="1024"
"VideoPCIDeviceID"="dword:0000683f"
"VideoPCIVendorID"="dword:00001002"[/COLOR]

In the witcher 2 the line "StrictDrawOrdering"="enabled" is changed to "StrictDrawOrdering"="disabled" because it makes the game very slow.

---

