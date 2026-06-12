---
title: "Issue with ia32-lib and new Ubuntu 13.10"
date: 2013-10-21
forum: General Help
---

### Post by geemac2 on 2013-10-21
Hello,

I do support and testing of a virtual world viewer package which is cross platform, but only written for 32 bit systems.
Please excuse the long winded post.  I wanted to be detailed as much as possible in this matter.

Our viewer has been running for some time now without any issues on various Linux distros including 64bit systems.
The issue we have is that the new 13.10 64bit system will not run until you install the 32bit libs.  I have tested this with a fresh install of 13.10 and this wreaks havoc with 13.10 after the libraries have been added.   I have reinstalled 13.10 and repeated this at least four times to see if it was just an issue with the install.  A updated install of a previous Ubuntu did not seem to have any issues. 

The issues are as follows:
13.10 would start to run slow.  The viewer would now run, but unusable due to the very low frame rate to the point of locking up. I did not check the CPU usage but I am thinking that this could be the issue and or a memory issue.  The latency was so high to the point that typing or movement is behind 3-5 seconds or better.
Another odd issue which I was able to repeat; with a fresh install, after installing the ia32-lib and after a reboot the system stated that there were new updates available.  All the updates were checked twice before this and were up to date.  This new update went on for roughly an hour.  This was  with a fiber high speed connection of 25x25 so the time was not due to the connection speed.  So this should rule out any delay on this odd update.
As I watched this update it seemed to be installing a new system and items that I feel should not have to be installed.
After this situation I rebooted the system and there was no activity after grub.  I also tried the recovery at the grub menu and it produced a very long list of errors followed on the next reboot. Of course I had to reinstall again since 13.10 was trashed.  As stated above I was able to repeat this.
I have been researching various methods of updating or lets say back-dating to add 32bit libraries for this type of situation.  What I have found is that the below steps using the outdated ia32-lib is the issue.
Should the installation of the 32bit libs been done as ia32-lib-multiarch?  If yes, can someone please correct the below steps so we do not run into this issue for the users that are using a fresh Install of 13.10.

Thank you for your time and patience with this long post.  Any help would be greatly appreciated.

TC
--------------------------------------
```
[SIZE=1]
[/SIZE]
[LIST=1]
[*][SIZE=1] Install Synaptic from terminal window ( Ctrl+Alt+T )  if you have not done so already.
[/SIZE] 
[*][SIZE=1] Type or copy this in the terminal minus the quotes " sudo apt-get install synaptic "
[/SIZE] 
[*][SIZE=1] Launch synaptic and goto “Settings then Repositories”
[/SIZE] 
[*][SIZE=1] Click “other software  then add”
[/SIZE] 
[*][SIZE=1] Insert this line in the box   "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring main restricted universe multiverse"
[/SIZE] 
[*][SIZE=1] click ok and close synaptic
[/SIZE] 
[*][SIZE=1] Type or copy minus the quotes  in the terminal “sudo apt-get update” Wait until the listing stops and you are at the prompt.
[/SIZE] 
[*][SIZE=1] Then type or copy minus the quotes “sudo apt-get install ia32-libs”  Wait  until install is finished then reboot your computer.[/SIZE] 
[*][SIZE=1]Run viewer per the readme text provided. [/SIZE] 
[/LIST]

```

---

### Post by scouser73 on 2013-10-22
Do you mean TeamViewer?, if so there is a solution.

[**[COLOR="#FF0000"]TeamViewer On Ubuntu[/COLOR]**]("http://www.teamviewer.com/en/help/363-How-do-I-install-TeamViewer-on-my-Linux-distribution.aspx")

[I]On newer 64-bit DEB-systems with Multiarch-support (Debian 7) teamviewer_linux_x64.deb cannot be installed because the package ia32-libs is not available anymore on these systems. In this case you can use teamviewer_linux.deb instead.

In case you get the error “wrong architecture i386” you have to execute the following command lines:

dpkg --add-architecture i386

apt-get update

For further information: [http://wiki.debian.org/Multiarch/HOWTO](http://wiki.debian.org/Multiarch/HOWTO)[/I]

---

### Post by geemac2 on 2013-10-22
Hello Scouser73,

Thanks for the quick responce  to my long post. 
This is not team viewer, but is good to know there is a fix for that.  This is a Viewer for a virtual world.  Some call it  a game, but it is actually a social network with avatars and such.  No  points or capture the flag.  Just folks hanging out.   [http://secondlife.com/](http://secondlife.com/)  We are a third party viewer for SL.  It is just a 32 bit program trying to make it in a new 13.10 64bit world. 
Your suggestion looks interesting though.  I'll give it a go here. 

Thanks again

TC

---

### Post by scouser73 on 2013-10-22
Hi geemac2,

I've done a bit of googling and found this.

[**[COLOR="#FF0000"]http://wiki.phoenixviewer.com/ia32-libs-in-ubuntu-13-10[/COLOR]**]("http://wiki.phoenixviewer.com/ia32-libs-in-ubuntu-13-10")

*Canonical has decided to end support for the transitional package of ia32-libs. This will not allow 64 bit versions of this distribution (13.10) to access Secondlife. Here is a workaround using ia32-libs from a previous distribution (13.04). This has been tested with the release candidate of 13.10 and all is well and functional.*

*Install Synaptic from terminal window*

```
sudo apt-get install synaptic
```

*Launch synaptic and goto “settings > Repositories”*

click “other software > add”

insert this line in the box ```
deb http://archive.ubuntu.com/ubuntu/ raring main restricted universe multiverse
```

click ok and close synaptic

in terminal ```
sudo apt-get update
```

in terminal ```
sudo apt-get install ia32-libs
```

---

### Post by geemac2 on 2013-10-22
Hello again.
LOL  yep I know that post well.... I know who wrote the original steps.  That is the group I do the support for.  I suggested that they put the warning on that post in the Wiki.
  That does not work since that is an old ia32-lib.  That lib will wreak havoc with 13.10.

 I'm just getting ready to try your earlier suggestion.

Thanks again

TC

---

### Post by simon5 on 2013-10-24
> **geemac2 said:**
> Hello again.
LOL  yep I know that post well.... I know who wrote the original steps.  That is the group I do the support for.  I suggested that they put the warning on that post in the Wiki.
  That does not work since that is an old ia32-lib.  That lib will wreak havoc with 13.10.

 I'm just getting ready to try your earlier suggestion.

Thanks again

TC

did you find a solution? I need ia32-lib too

---

### Post by geemac2 on 2013-10-26
Hello Simon.
I did find a fix here but it may only pertain to my system.  It is quite involved, but it worked for me.  If it works for you _Please_ let me know along with your system setup so I can post the info to our Dev team for the viewer.  This way I can keep an eye on what systems these steps worked with.
  
The below information is what I posted to our JIRA for our viewer.  The older ia32-lib did not properly work in 13.10 with our viewer, but the steps below did.  If any of the Ubuntu 13.10 experts see anything wrong in these steps or a much shorter way to get the proper 32 bit libraries installed for the 32 bit programs that used to work under 13.04 with the old ia32-lib _Please_ let me know.
Thank you...

 I would follow steps 4 and on.  

> 1. Download Firestorm Linux
  
2. Un-archive the package folder to your Home Directory.  Make sure  it is just the folder not all the contents.  That would be a bit messy.   Rename the folder to firestorm or a name of your choice.  Placing the  Firestorm folder in your Home Directory will make the next steps easier.  


3. Now for the fun part,  Fasten your seatbelt.  Now we will install the missing 32 Bit libraries.
  
4. Install these library packages first by opening the *Terminal  window using Ctrl+Alt+T. You can Copy and Paste (C/P) the below line or  type it, whichever is easier for you.
  sudo apt-get install libgtk2.0-0:i386 libpangox-1.0-0:i386 libpangoxft-1.0-0:i386 libidn11:i386
  
5. Next we are going to add some small applications which contain extra 32 Bit libraries.
Type or C/P the following line in the terminal window.
  sudo apt-get install gstreamer0.10-pulseaudio:i386  gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386  gstreamer0.10-ffmpeg:i386
  These are mainly audio/sound applications, but we just need the  libraries that are included.  You can also combine the last two step in  this fashion, but I strongly would not recommend this method.
  sudo apt-get install libgtk2.0-0:i386 libpangox-1.0-0:i386  libpangoxft-1.0-0:i386 libidn11:i386 gstreamer0.10-pulseaudio:i386  gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386  gstreamer0.10-ffmpeg:i386
  
6. After this is all complete reboot the system via terminal, sudo reboot or via the normal method.
  
7. After the system is running and settled open your terminal and type cd firestorm or the name you gave the folder.
  
8. Now type ./firestorm and sit back and watch the flow of text in the terminal window.
Firestorm Viewer should be up and running at this point.  If it is  taking too much time to go through its paces or unresponsive, look at  the terminal and see if the flow of text is repeating lines in reference  to QPainter.  If so follow steps 9-10 if not and the Viewer is running  fine for you then skip the next steps and you should be on your way.
  
9. If the Viewer seems to be unresponsive or slow,stop the operation  by shutting down Firestorm or close the terminal.  You may also have to  reboot the system if the terminal and the viewer are unresponsive.
  
10. Reopen the terminal if you had shut it down or rebooted the  system in the previous step. Once in the terminal C/P or type this line.   You can also install via **Synaptic or Ubuntu Software Center.  After  searching for qpainter it will be shown as libqtexengine1  .
  sudo apt-get install libqtexengine1 then enter.
  
11. Once this application is installed, reboot via the terminal or the usual method.
  
12. After your computer has rebooted and settled, reopen the terminal  and go to the firestorm directory and type ./firestorm  Firestorm  should now be running smooth.
  Have Fun

  *Terminal
I would suggest that you also install a small little terminal package  called Guake. Once installed and running you can access the terminal,  now a drop down by pressing F12.  This is a great method to accessing  the terminal without the fuss of pressing three keys.  Also Guake will  also move out of the way if you set it up to do so.  It will also retain  where you left off so you do not have to keep retyping your commands.   Guake can be installed by two methods. One being the Ubuntu Software  Center and the other is via Synaptic.  I have not tried via the terminal  using sudo apt-get install guake. The latter may work.

  **Synaptic
I would strongly suggest that you install this application above all  applications.  Open the terminal via F12 if you installed Guake or  Ctrl+Alt+T and run this line
sudo apt-get install synaptic
No reboot is needed for either the Guake terminal or Synaptic. 



---

### Post by shamstaj on 2013-11-24
I HAD MY FIRESTORM RUNNING OK BUT SINCE I INSTALLED NEW CUDA 5.5 IT STOP WORKING, WHEN I TRY TO UPDATE OR INSTALL ia32-libs IT GIVES ME THE FOLLOWING MESSAGE.
MY Ubuntu IS 12.04
RUNNING ON 
I7 PROCESSOR 
GE-FORCE 640 NVIDIA


ANY IDEA 
THANKS

shams@ubuntu:~$ sudo apt-get install ia32-libs
[sudo] password for shams: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  libcublas4 libnpp4 libvdpau-dev gir1.2-ubuntuoneui-3.0 libcudart4 g++-4.4
  libcurand4 nvidia-opencl-dev nvidia-cuda-dev nvidia-cuda-doc nvidia-cuda-gdb
  libqtassistantclient4 opencl-headers libubuntuoneui-3.0-1
  thunderbird-globalmenu libcusparse4 nvidia-compute-profiler libthrust-dev
  libcufft4 libstdc++6-4.4-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1704 not upgraded.

---

### Post by shamstaj on 2013-11-24
Oh God, I cant take anymore, i spent 8 days, not one hour a day but 14-15 hours a day just to solve my Ubuntu Issues optimize it and get it running and now when it was up and running i made the foolish step to ask for a help about lib32, If i knew i am going to end up  with a blue screen or there was a slightest chance to get into this ,  i would never had done this, 
as some one suggested i upgraded and now my screen is completely blue, nothing but mouse cursor.  

Please somebody help.

---

### Post by Bashing-om on 2013-11-24
@ shamstaj; Hey;

That is not the operating system at fault, scream at the hardware manufactures who do not support linux and ubuntu in particular !
Now see what the open source developers are trying to do to help your situation:
[http://test.ubuntu-discourse.org/t/hybrid-graphics-with-amd-and-nvidia-in-ubuntu-13-10-and-12-04-3/1144](http://test.ubuntu-discourse.org/t/hybrid-graphics-with-amd-and-nvidia-in-ubuntu-13-10-and-12-04-3/1144)
> 
we have worked to officially support Hybrid graphics in Ubuntu 13.10 and in 12.04.3 LTS.

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Linux now supports Hybrid Graphics Systems with Ubuntu 13.10
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

Not that this helps your situation, may not apply to "cudda" ; but anything that requires installation of 32 bit libraries/compatiblities is not part of the ubuntu support system. That is 3rd party software, let the installer be ware and as the disclaimer says .. not for the soft at heart, breakage can and does occur.

Situation that is at hand> Why do you need "ia32-libs" available on your system? Knowing that maybe we can see about what it will take to do that.
Are you still on version 12.04 or  have you upgraded to a later version ?

Now the good stuff, Developers are working very hard on multi-arch support.
Take a look in 13.10 repositories and see if the application you want is available as <package_name>.i386. If it is maintained, just "sudo apt-get install" and it is a done deal ! But, got to be running version 13.10 to do this the easy way ! 

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by wblalok on 2013-12-06
For what it is worth geemac2, my Kubuntu 13.10 does NOT have any of those packages, nor anything that looks "close enough"

I have been unable to get firestorm running at all, no matter what search results I have tried. :(

edited because I forgot to paste my ldd output

will>ldd bin/do-not-directly-run-firestorm-bin 
        linux-gate.so.1 =>  (0xf779a000)
        libopenal.so.1 => /usr/lib/i386-linux-gnu/libopenal.so.1 (0xf7711000)
        libalut.so => not found
        libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf76f5000)
        libcollada14dom.so => not found
        libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0xf7656000)
        librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf764d000)
        libhunspell-1.3.so.0 => not found
        libboost_program_options-mt.so.1.52.0 => not found
        libboost_regex-mt.so.1.52.0 => not found
        libboost_context-mt.so.1.52.0 => not found
        libboost_wave-mt.so.1.52.0 => not found
        libboost_thread-mt.so.1.52.0 => not found
        libgobject-2.0.so.0 => /usr/lib/i386-linux-gnu/libgobject-2.0.so.0 (0xf75f9000)
        libglib-2.0.so.0 => /lib/i386-linux-gnu/libglib-2.0.so.0 (0xf74f5000)
        libGLU.so.1 => /usr/lib/i386-linux-gnu/libGLU.so.1 (0xf746f000)
        libGL.so.1 => /usr/lib/i386-linux-gnu/mesa/libGL.so.1 (0xf7415000)
        libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf72e0000)
        libfmodex.so => not found
        libGLOD.so => not found
        libSDL-1.2.so.0 => not found
        libgdk-x11-2.0.so.0 => not found
        libgthread-2.0.so.0 => /usr/lib/i386-linux-gnu/libgthread-2.0.so.0 (0xf72dc000)
        libgtk-x11-2.0.so.0 => not found
        libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0xf72b2000)
        libssl.so.1.0.0 => /lib/i386-linux-gnu/libssl.so.1.0.0 (0xf725b000)
        libcrypto.so.1.0.0 => /lib/i386-linux-gnu/libcrypto.so.1.0.0 (0xf70ae000)
        libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf70a9000)
        libpng15.so.15 => not found
        libfontconfig.so.1 => /usr/lib/i386-linux-gnu/libfontconfig.so.1 (0xf706e000)
        libboost_filesystem-mt.so.1.52.0 => not found
        libaprutil-1.so.0 => not found
        libapr-1.so.0 => not found
        libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf6f84000)
        libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf6f41000)
        libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf6f24000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf6d70000)
        /lib/ld-linux.so.2 (0xf779b000)
        libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf6d56000)
        libffi.so.6 => /usr/lib/i386-linux-gnu/libffi.so.6 (0xf6d4e000)
        libpcre.so.3 => /lib/i386-linux-gnu/libpcre.so.3 (0xf6d0d000)
        libglapi.so.0 => /usr/lib/i386-linux-gnu/libglapi.so.0 (0xf6cf6000)
        libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf6ce3000)
        libXdamage.so.1 => /usr/lib/i386-linux-gnu/libXdamage.so.1 (0xf6cdf000)
        libXfixes.so.3 => /usr/lib/i386-linux-gnu/libXfixes.so.3 (0xf6cd8000)
        libX11-xcb.so.1 => /usr/lib/i386-linux-gnu/libX11-xcb.so.1 (0xf6cd5000)
        libxcb-glx.so.0 => /usr/lib/i386-linux-gnu/libxcb-glx.so.0 (0xf6cbd000)
        libxcb-dri2.so.0 => /usr/lib/i386-linux-gnu/libxcb-dri2.so.0 (0xf6cb7000)
        libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf6c96000)
        libXxf86vm.so.1 => /usr/lib/i386-linux-gnu/libXxf86vm.so.1 (0xf6c8f000)
        libdrm.so.2 => /usr/lib/i386-linux-gnu/libdrm.so.2 (0xf6c82000)
        libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf6c7e000)
        libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf6c77000)

Many of the libraries listed as not found are present, but much newer.  For example the libboost* oldest version I have is 1.53*

libalut is present, not in a form that firestorm recognizes.

lib GLOD and fmodex are not found at all, any version or architecture.

---

### Post by s-stefanov on 2014-01-09
Tried installing sopcast-player (which has the same dependency on ia32-libs) with the package provided here - no joy:

[http://chucktalk.com/2013/11/05/webex-multiarch-support-in-saucy/](http://chucktalk.com/2013/11/05/webex-multiarch-support-in-saucy/)

---

### Post by noteleks on 2014-01-12
Yes, I did everything this post said to do and I still cannot connect to the Internet. My WIFI shows that it is working but when I run FireFox nothing is happening. It takes awhile and then says it cannot connect. I hate that I have to redo it to some other Linux OS.

---

### Post by dave2001 on 2014-02-18
marking this thread as solved is very innapropriate...

---

### Post by s-stefanov on 2014-02-18
> **dave2001 said:**
> marking this thread as solved is very inappropriate...

Agreed. There are problems with ia32-libs on 64-bit Ubuntu probably since 12.04 and they have been a continuous source of frustration for many users. Truth is the only workarounds are manually compiling from source and removing dependencies from the config file (not always working) and getting developers to update their applications (almost impossible, it's probably a significant amount of work).

---

### Post by gunsnrails on 2014-03-16
Ha, deja vu. Year after year I keep trying Linux distros just to end up at the same place. Missing libraries, missing packages and non working applications. Now this one. Seems like Linux will always be a OS for nerds or people with huge patience or time. Though I have to agree that this time the wifi card was detected from scratch. I'll reinstall a 32bit version of Ubuntu tomorrow. I just wanted to install Veetle and use a box for that. :(

---

### Post by anmg on 2014-05-11
I have done all as described in a first post of the thread.
As youi can see only few packages were downloaded from old repository, all other from new

> 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main gcc-4.9-base i386 4.9-20140406-0ubuntu1 [13,9 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:2 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgcc1 i386 1:4.9-20140406-0ubuntu1 [47,8 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main libgd2-xpm i386 2.0.36~rc1~dfsg-6.1ubuntu1 [201 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:4 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libc6 i386 2.19-0ubuntu6 [4.017 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main libgphoto2-port0 i386 2.4.14-2 [43,5 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main libgphoto2-2 i386 2.4.14-2 [970 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:7 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libexpat1 i386 2.1.0-4ubuntu1 [71,4 kB]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:8 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libffi6 i386 3.1~rc1+r3.0.13-12 [14,4 kB]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:9 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgpg-error0 i386 1.12-0.2ubuntu1 [10,9 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:10 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgcrypt11 i386 1.5.3-2ubuntu4 [237 kB]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:11 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgdbm3 i386 1.8.3-12build1 [33,3 kB]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:12 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libp11-kit0 i386 0.20.2-2ubuntu2 [71,4 kB]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:13 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libtasn1-6 i386 3.4-3 [42,5 kB]                                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:14 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main zlib1g i386 1:1.2.8.dfsg-1ubuntu1 [57,5 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:15 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgnutls26 i386 2.12.23-12ubuntu2 [374 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:16 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/universe ia32-libs-multiarch i386 20090808ubuntu36 [4.682 B]                    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:17 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/universe ia32-libs amd64 20090808ubuntu36 [4.570 B]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:18 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libtinfo5 i386 5.9+20140118-1ubuntu1 [70,8 kB]                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:19 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libreadline6 i386 6.3-4ubuntu2 [111 kB]                                 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:20 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libsqlite3-0 i386 3.8.2-1ubuntu2 [344 kB]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:21 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty-updates/main libssl1.0.0 i386 1.0.1f-1ubuntu2.1 [779 kB]                     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:22 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main gcc-4.8-base i386 4.8.2-19ubuntu1 [15,5 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:23 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libstdc++6 i386 4.8.2-19ubuntu1 [262 kB]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:24 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libusb-0.1-4 i386 2:0.1.12-23.3ubuntu1 [15,2 kB]                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:25 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libattr1 i386 1:2.4.47-1ubuntu1 [9.414 B]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:26 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libacl1 i386 2.2.52-1 [18,1 kB]                                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:27 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libbz2-1.0 i386 1.0.6-5 [33,9 kB]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:28 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcap2 i386 1:2.24-0ubuntu2 [10,8 kB]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:29 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcomerr2 i386 1.42.9-3ubuntu1 [62,6 kB]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:30 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libdb5.3 i386 5.3.28-3ubuntu3 [651 kB]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:31 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libdbus-1-3 i386 1.6.18-0ubuntu4 [132 kB]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:32 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libdrm2 i386 2.4.52-1 [23,2 kB]                                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:33 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libjson-c2 i386 0.11-3ubuntu1 [24,3 kB]                                 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:34 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main liblzma5 i386 5.1.1alpha+20120614-2ubuntu2 [84,2 kB]                    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:35 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libncurses5 i386 5.9+20140118-1ubuntu1 [93,8 kB]                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:36 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libncursesw5 i386 5.9+20140118-1ubuntu1 [122 kB]                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:37 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libnih1 i386 1.0.3-4ubuntu25 [46,3 kB]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:38 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libnih-dbus1 i386 1.0.3-4ubuntu25 [13,6 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:39 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libpcre3 i386 1:8.31-2ubuntu2 [140 kB]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:40 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libpng12-0 i386 1.2.50-1ubuntu2 [118 kB]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:41 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty-updates/main libselinux1 i386 2.2.2-1ubuntu0.1 [57,5 kB]                     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:42 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libslang2 i386 2.2.4-15ubuntu1 [460 kB]                                 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:43 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcgmanager0 i386 0.24-0ubuntu5 [24,0 kB]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:44 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libudev1 i386 204-5ubuntu20 [34,3 kB]                                   
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:45 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libuuid1 i386 2.20.1-5.1ubuntu20 [11,7 kB]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:46 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libroken18-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [40,9 kB]         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:47 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libasn1-8-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [169 kB]           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:48 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libglib2.0-0 i386 2.40.0-2 [1.031 kB]                                   
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:49 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libdbus-glib-1-2 i386 0.100.2-1 [74,2 kB]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:50 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty-updates/main libelf1 i386 0.158-0ubuntu5.1 [42,7 kB]                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:51 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libkrb5support0 i386 1.12+dfsg-2ubuntu4 [29,8 kB]                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:52 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libk5crypto3 i386 1.12+dfsg-2ubuntu4 [77,6 kB]                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:53 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libkeyutils1 i386 1.5.6-1 [7.266 B]                                     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:54 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libkrb5-3 i386 1.12+dfsg-2ubuntu4 [260 kB]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:55 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgssapi-krb5-2 i386 1.12+dfsg-2ubuntu4 [111 kB]                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:56 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libhcrypto4-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [82,3 kB]        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:57 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libheimbase1-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [28,9 kB]       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:58 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libwind0-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [48,2 kB]           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:59 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libhx509-5-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [103 kB]          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:60 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libkrb5-26-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [198 kB]          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:61 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libheimntlm0-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [15,5 kB]       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:62 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgssapi3-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [89,5 kB]         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:63 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libidn11 i386 1.28-1ubuntu2 [92,3 kB]                                   
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:64 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libsasl2-modules-db i386 2.1.25.dfsg1-17build1 [14,7 kB]                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:65 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libsasl2-2 i386 2.1.25.dfsg1-17build1 [55,0 kB]                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:66 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libldap-2.4-2 i386 2.4.31-1+nmu2ubuntu8 [150 kB]                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:67 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main librtmp0 i386 2.4+20121230.gitdf6c518-1 [57,2 kB]                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:68 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libusb-1.0-0 i386 2:1.0.17-1ubuntu2 [39,3 kB]                           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:69 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxau6 i386 1:1.0.8-1 [8.352 B]                                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:70 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxdmcp6 i386 1:1.1.1-1 [13,1 kB]                                      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:71 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxcb1 i386 1.10-2ubuntu1 [40,6 kB]                                    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:72 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libx11-6 i386 2:1.6.2-1ubuntu2 [557 kB]                                 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:73 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxext6 i386 2:1.3.2-1 [33,9 kB]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:74 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxml2 i386 2.9.1+dfsg1-3ubuntu4 [555 kB]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:75 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgpm2 i386 1.20.4-6.1 [16,0 kB]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:76 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libaa1 i386 1.4p5-41 [53,5 kB]                                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:77 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libraw1394-11 i386 2.1.0-1ubuntu1 [32,4 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:78 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libavc1394-0 i386 0.5.4-2 [20,3 kB]                                     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:79 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcaca0 i386 0.99.beta18-1ubuntu5 [202 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:80 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libfreetype6 i386 2.5.2-1ubuntu2 [300 kB]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:81 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libfontconfig1 i386 2.11.0-0ubuntu4 [123 kB]                            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:82 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libpixman-1-0 i386 0.30.2-2ubuntu1 [216 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:83 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxcb-render0 i386 1.10-2ubuntu1 [11,9 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:84 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxcb-shm0 i386 1.10-2ubuntu1 [5.622 B]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:85 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxrender1 i386 1:0.9.8-1 [20,3 kB]                                    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:86 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcairo2 i386 1.13.0~20140204-0ubuntu1 [550 kB]                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:87 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcairo-gobject2 i386 1.13.0~20140204-0ubuntu1 [16,5 kB]               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:88 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libdv4 i386 1.0.0-6 [65,2 kB]                                           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:89 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libogg0 i386 1.3.1-1ubuntu1 [16,1 kB]                                   
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:90 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libflac8 i386 1.3.0-2 [98,1 kB]                                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:91 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libjpeg-turbo8 i386 1.3.0-0ubuntu2 [107 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:92 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libjpeg8 i386 8c-2ubuntu8 [2.188 B]                                     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:93 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libjasper1 i386 1.900.1-14ubuntu3 [126 kB]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:94 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty-updates/main libjbig0 i386 2.0-2ubuntu4.1 [25,1 kB]                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:95 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty-updates/main libtiff5 i386 4.0.3-7ubuntu0.1 [142 kB]                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:96 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgdk-pixbuf2.0-0 i386 2.30.7-0ubuntu1 [155 kB]                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:97 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgstreamer0.10-0 i386 0.10.36-1.2ubuntu3 [617 kB]                     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:98 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main liborc-0.4-0 i386 1:0.4.18-1ubuntu1 [139 kB]                            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:99 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgstreamer-plugins-base0.10-0 i386 0.10.36-1.1ubuntu2 [419 kB]        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:100 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgudev-1.0-0 i386 1:204-5ubuntu20 [13,7 kB]                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:101 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libiec61883-0 i386 1.2.0-0.1ubuntu3 [24,3 kB]                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:102 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libsamplerate0 i386 0.1.8-7 [938 kB]                                   
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:103 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libjack-jackd2-0 i386 1.9.9.5+20130622git7de15e7a-1ubuntu1 [180 kB]    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:104 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libspeex1 i386 1.2~rc1.1-1ubuntu1 [87,4 kB]                            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:105 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libtheora0 i386 1.1.1+dfsg.1-3.2 [156 kB]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:106 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libvorbis0a i386 1.3.2-1.3ubuntu1 [83,1 kB]                            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:107 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libshout3 i386 2.3.1-3 [39,6 kB]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:108 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libproxy1 i386 0.4.11-0ubuntu4 [55,3 kB]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:109 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main glib-networking i386 2.40.0-1 [39,2 kB]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:110 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libsoup2.4-1 i386 2.44.2-1ubuntu2 [226 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:111 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libsoup-gnome2.4-1 i386 2.44.2-1ubuntu2 [4.972 B]                      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:112 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libtag1-vanilla i386 1.9.1-2 [350 kB]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:113 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libtag1c2a i386 1.9.1-2 [11,3 kB]                                      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:114 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libv4lconvert0 i386 1.0.1-1 [73,0 kB]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:115 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libv4l-0 i386 1.0.1-1 [36,5 kB]                                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:116 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libwavpack1 i386 4.70.0-1 [84,4 kB]                                    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:117 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxdamage1 i386 1:1.1.4-1ubuntu1 [7.406 B]                            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:118 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxfixes3 i386 1:5.0.1-1ubuntu1 [11,5 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:119 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxv1 i386 2:1.0.10-1 [10,2 kB]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:120 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcdparanoia0 i386 3.10.2+debian-11 [62,8 kB]                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:121 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libvisual-0.4-0 i386 0.4.0-5 [110 kB]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:122 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libvorbisenc2 i386 1.3.2-1.3ubuntu1 [66,9 kB]                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:123 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main gstreamer0.10-plugins-base i386 0.10.36-1.1ubuntu2 [530 kB]            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:124 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main gstreamer0.10-plugins-good i386 0.10.31-3+nmu1ubuntu5 [1.344 kB]       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:125 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libdatrie1 i386 0.2.8-1 [17,3 kB]                                      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:126 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libthai0 i386 0.1.20-3 [17,1 kB]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:127 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libpango-1.0-0 i386 1.36.3-1ubuntu1 [148 kB]                           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:128 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgraphite2-3 i386 1.2.4-1ubuntu1 [54,4 kB]                           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:129 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libharfbuzz0b i386 0.9.27-1 [125 kB]                                   
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:130 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libpangoft2-1.0-0 i386 1.36.3-1ubuntu1 [32,6 kB]                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:131 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libpangocairo-1.0-0 i386 1.36.3-1ubuntu1 [20,0 kB]                     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:132 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe gtk2-engines-oxygen i386 1.4.5-0ubuntu1 [369 kB]                   
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:133 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libaio1 i386 0.3.109-4 [6.578 B]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:134 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libao-common all 1.1.0-2ubuntu2 [6.278 B]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:135 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libao4 i386 1.1.0-2ubuntu2 [30,7 kB]                                   
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:136 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libasound2 i386 1.0.27.2-3ubuntu7 [324 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:137 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libasyncns0 i386 0.8-4ubuntu2 [11,6 kB]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:138 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libsndfile1 i386 1.0.25-7ubuntu2 [143 kB]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:139 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libwrap0 i386 7.6.q-25 [45,8 kB]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:140 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libpulse0 i386 1:4.0-0ubuntu11 [211 kB]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:141 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libspeexdsp1 i386 1.2~rc1.1-1ubuntu1 [69,2 kB]                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:142 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libasound2-plugins i386 1.0.27-2ubuntu2 [62,4 kB]                      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:143 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libatk1.0-0 i386 2.10.0-2ubuntu2 [49,5 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:144 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libice6 i386 2:1.0.8-2 [45,9 kB]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:145 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libsm6 i386 2:1.2.1-2 [17,3 kB]                                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:146 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxt6 i386 1:1.1.4-1 [176 kB]                                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:147 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libaudio2 i386 1.9.4-1 [57,0 kB]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:148 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libaudiofile1 i386 0.3.6-2 [115 kB]                                    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:149 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libavahi-common-data i386 0.6.31-4ubuntu1 [21,3 kB]                    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:150 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libavahi-common3 i386 0.6.31-4ubuntu1 [22,2 kB]                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:151 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libavahi-client3 i386 0.6.31-4ubuntu1 [24,5 kB]                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:152 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libltdl7 i386 2.4.2-1.7ubuntu1 [35,2 kB]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:153 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libtdb1 i386 1.2.12-1 [38,6 kB]                                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:154 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libvorbisfile3 i386 1.3.2-1.3ubuntu1 [17,5 kB]                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:155 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcanberra0 i386 0.30-0ubuntu3 [35,0 kB]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:156 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcups2 i386 1.7.2-0ubuntu1 [175 kB]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:157 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxcomposite1 i386 1:0.4.4-1 [7.594 B]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:158 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxcursor1 i386 1:1.1.14-1 [22,8 kB]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:159 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxi6 i386 2:1.7.1.901-1ubuntu1 [32,0 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:160 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxinerama1 i386 2:1.1.3-1 [7.900 B]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:161 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxrandr2 i386 2:1.4.2-1 [16,1 kB]                                    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:162 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgtk2.0-0 i386 2.24.23-0ubuntu1 [1.694 kB]                           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:163 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcanberra-gtk0 i386 0.30-0ubuntu3 [7.584 B]                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:164 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcroco3 i386 0.6.8-2ubuntu1 [81,1 kB]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:165 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty-updates/main libcupsfilters1 i386 1.0.52-0ubuntu1.1 [74,0 kB]               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:166 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcupsimage2 i386 1.7.2-0ubuntu1 [15,2 kB]                            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:167 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcurl3 i386 7.35.0-1ubuntu2 [174 kB]                                 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:168 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libpciaccess0 i386 0.13.2-1 [21,9 kB]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:169 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libdrm-intel1 i386 2.4.52-1 [54,2 kB]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:170 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libdrm-nouveau2 i386 2.4.52-1 [14,2 kB]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:171 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libdrm-radeon1 i386 2.4.52-1 [24,6 kB]                                 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:172 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main esound-common all 0.2.41-11 [9.558 B]                                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:173 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libesd0 i386 0.2.41-11 [16,3 kB]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:174 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libexif12 i386 0.6.21-1ubuntu1 [71,3 kB]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:175 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe libfluidsynth1 i386 1.1.6-2 [185 kB]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:176 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgail18 i386 2.24.23-0ubuntu1 [13,9 kB]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:177 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgconf-2-4 i386 3.2.6-0ubuntu2 [77,3 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:178 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxpm4 i386 1:3.5.10-1 [38,2 kB]                                      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:179 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libvpx1 i386 1.3.0-2 [518 kB]                                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:180 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgd3 i386 2.1.0-3 [142 kB]                                           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:181 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libunistring0 i386 0.9.3-5ubuntu3 [272 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:182 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty-updates/main libgettextpo0 i386 0.18.3.1-1ubuntu3 [104 kB]                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:183 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libllvm3.4 i386 1:3.4-1ubuntu3 [6.849 kB]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:184 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgl1-mesa-dri i386 10.1.0-4ubuntu5 [4.987 kB]                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:185 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libglapi-mesa i386 10.1.0-4ubuntu5 [21,4 kB]                           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:186 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libx11-xcb1 i386 2:1.6.2-1ubuntu2 [9.396 B]                            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:187 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxcb-dri2-0 i386 1.10-2ubuntu1 [7.150 B]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:188 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxcb-dri3-0 i386 1.10-2ubuntu1 [5.292 B]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:189 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxcb-glx0 i386 1.10-2ubuntu1 [21,6 kB]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:190 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxcb-present0 i386 1.10-2ubuntu1 [5.412 B]                           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:191 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxcb-sync1 i386 1.10-2ubuntu1 [8.418 B]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:192 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxshmfence1 i386 1.1-2 [4.700 B]                                     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:193 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxxf86vm1 i386 1:1.1.3-1 [11,8 kB]                                   
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:194 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgl1-mesa-glx i386 10.1.0-4ubuntu5 [112 kB]                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:195 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgphoto2-port10 i386 2.5.3.1-1ubuntu2 [39,7 kB]                      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:196 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgphoto2-6 i386 2.5.3.1-1ubuntu2 [710 kB]                            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:197 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgstreamer1.0-0 i386 1.2.3-1 [586 kB]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:198 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgstreamer-plugins-base1.0-0 i386 1.2.3-1 [430 kB]                   
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:199 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libibus-1.0-5 i386 1.5.5-1ubuntu3 [109 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:200 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libieee1284-3 i386 0.2.11-12 [23,7 kB]                                 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:201 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe libmad0 i386 0.15.1b-8ubuntu1 [72,7 kB]                            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:202 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe libmikmod2 i386 3.1.16-1 [99,5 kB]                                 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:203 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe libmpg123-0 i386 1.16.0-1ubuntu1 [114 kB]                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:204 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty-updates/main mysql-common all 5.5.37-0ubuntu0.14.04.1 [14,2 kB]             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:205 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty-updates/main libmysqlclient18 i386 5.5.37-0ubuntu0.14.04.1 [592 kB]         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:206 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libnspr4 i386 2:4.10.2-1ubuntu1 [111 kB]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:207 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libnss3 i386 2:3.15.4-1ubuntu7 [1.046 kB]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:208 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libodbc1 i386 2.2.14p2-5ubuntu5 [172 kB]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:209 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxft2 i386 2.3.1-2 [35,6 kB]                                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:210 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libpangoxft-1.0-0 i386 1.36.3-1ubuntu1 [14,9 kB]                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:211 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libpulse-mainloop-glib0 i386 1:4.0-0ubuntu11 [11,5 kB]                 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:212 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libpulsedsp i386 1:4.0-0ubuntu11 [20,6 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:213 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqtcore4 i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [1.557 kB]       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:214 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-xml i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [97,1 kB]        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:215 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqtdbus4 i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [182 kB]         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:216 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-network i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [551 kB]     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:217 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-script i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [793 kB]      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:218 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-sql i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [98,5 kB]        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:219 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-xmlpatterns i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [1.022 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:220 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqtgui4 i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [4.185 kB]        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:221 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-declarative i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [1.081 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:222 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-designer i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [3.613 kB]  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:223 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-opengl i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [300 kB]      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:224 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-qt3support i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [1.040 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:225 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-scripttools i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [225 kB] 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:226 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-sql-mysql i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [30,3 kB]  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:227 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-svg i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [137 kB]         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:228 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-test i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [60,5 kB]       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:229 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxslt1.1 i386 1.1.28-2build1 [140 kB]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:230 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqtwebkit4 i386 2.3.2-0ubuntu7 [8.989 kB]                            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:231 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main librsvg2-2 i386 2.40.2-1 [90,0 kB]                                     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:232 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libsane i386 1.0.23-3ubuntu3 [1.858 kB]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:233 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libsdl1.2debian i386 1.2.15-8ubuntu1 [166 kB]                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:234 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libwebp5 i386 0.4.0-4 [133 kB]                                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:235 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe libsdl-image1.2 i386 1.2.12-5build2 [27,5 kB]                      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:236 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe libsdl-mixer1.2 i386 1.2.12-10 [71,8 kB]                           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:237 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe libsdl-net1.2 i386 1.2.8-4 [11,7 kB]                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:238 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe libsdl-ttf2.0-0 i386 2.0.11-3 [14,9 kB]                            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:239 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libsecret-1-0 i386 0.16-0ubuntu1 [86,9 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:240 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe libssl0.9.8 i386 0.9.8o-7ubuntu3.1 [868 kB]                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:241 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe libstdc++5 i386 1:3.3.6-25ubuntu4 [259 kB]                         
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:242 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxmu6 i386 2:1.1.1-1 [52,9 kB]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:243 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxaw7 i386 2:1.0.12-1 [164 kB]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:244 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxp6 i386 1:1.0.2-1ubuntu1 [15,5 kB]                                 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:245 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxss1 i386 1:1.2.2-1 [8.566 B]                                       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:246 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libxtst6 i386 2:1.2.2-1 [13,8 kB]                                      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:247 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main odbcinst amd64 2.2.14p2-5ubuntu5 [12,6 kB]                             
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:248 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main odbcinst1debian2 amd64 2.2.14p2-5ubuntu5 [40,6 kB]                     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:249 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main odbcinst1debian2 i386 2.2.14p2-5ubuntu5 [39,6 kB]                      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:250 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main xaw3dg i386 1.5+E-18.2 [173 kB]                                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:251 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe libcapi20-3 i386 1:3.25+dfsg1-3.3ubuntu2 [31,9 kB]                 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:252 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libglu1-mesa i386 9.0.0-2 [195 kB]                                     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:253 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe libopenal1 i386 1:1.14-4ubuntu1 [180 kB]                           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:254 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libpangox-1.0-0 i386 0.0.2-4ubuntu1 [40,8 kB]                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:255 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libtxc-dxtn-s2tc0 i386 0~git20131104-1.1 [48,1 kB]                     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:256 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libsasl2-modules i386 2.1.25.dfsg1-17build1 [59,3 kB]                  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:257 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main bluez-alsa i386 4.101-0ubuntu13 [80,4 kB]                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:258 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main gstreamer0.10-x i386 0.10.36-1.1ubuntu2 [57,7 kB]                      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:259 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main gtk2-engines i386 1:2.20.2-3ubuntu1 [208 kB]                           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:260 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libpango1.0-0 i386 1.36.3-1ubuntu1 [3.476 B]                           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:261 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main gtk2-engines-murrine i386 0.98.2-0ubuntu2 [105 kB]                     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:262 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe gtk2-engines-pixbuf i386 2.24.23-0ubuntu1 [17,8 kB]                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:263 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main gvfs-libs i386 1.20.1-1ubuntu1 [103 kB]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:264 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main gvfs i386 1.20.1-1ubuntu1 [89,4 kB]                                    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:265 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main ibus-gtk i386 1.5.5-1ubuntu3 [13,0 kB]                                 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:266 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libcanberra-gtk-module i386 0.30-0ubuntu3 [8.868 B]                    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:267 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libgail-common i386 2.24.23-0ubuntu1 [112 kB]                          
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:268 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libqt4-dbus i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 [6.432 B]       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:269 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main librsvg2-common i386 2.40.2-1 [4.962 B]                                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:270 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/main libvisual-0.4-plugins i386 0.4.0.dfsg.1-7build1 [126 kB]               


---

### Post by geemac2 on 2014-09-26
**Solved**
Not sure who marked this solved, but I am now marking it solved. 
Thanks to all that responded to this old issue.

GEE


OK....  It's been quite some time after I made the original post almost one year ago, short a month. 
Here is just a short update...

At the time of the original post we were all scratching our heads with the issues with newley released 3.10 Ubuntu.
As of late this seems not to be an issue running Firestorm viewer for Second life under Linux.  There have been many Firestorm updates and Ubuntu updates since this post.  Apparently Multiarch is now part of Trusty 14.04.
I haven't tried 13.10 since the release Trusty 14.04 release so I am not sure if there has been an update for 13.10 with Multiarch.  
Those of you that are still having issues with Firestorm viewer, you can check here for more information  *[http://www.firestormviewer.org](http://www.firestormviewer.org)*  There is a good staff of support people that are well versed in Linux.


Thanks Again all

---

### Post by Bashing-om on 2014-09-26
geemac2; Thanks

For returning and providing your update. All to the good.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

