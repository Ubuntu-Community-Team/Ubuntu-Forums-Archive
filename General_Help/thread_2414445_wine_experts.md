---
title: "wine experts?"
date: 2019-03-10
forum: General Help
---

### Post by oilyfish on 2019-03-10
I have Turbocad  for windows  It's a CAD engineering  design  package.
I can still run it in windows  on another hard disk. Means I gotta swap hard discs in a front bay (First world  modern problems I know) 
I have not  tried to install my Win 7  in Ubuntu with wine

What I did was install the Turbocad in wine.  It installed like a champ and even put the Icon on my desktop. 
But when I run it, it crashes. 
Should I uninstall it and install windows under Wine and try again? 
What do you think?

---

### Post by QIII on 2019-03-10
Hello!

You can't install Windows under Wine.  Wine provides a compatibility layer that provides *nix libraries in an attempt (sometimes not very successful) to have them work in the place of Windows libraries so that some Windows software can run (perhaps not well) on Linux.

Wine does not provide an environment under which to install Windows.

If your desired software does not work well with Wine, there isn't really much to be done about it.

You have a couple of options if you must run Windows to use your software:

- Dual-booting (this can be a pain since you have to reboot your machine).
- Virtualization (VirtualBox, KVM, etc)

---

### Post by DuckHook on 2019-03-10
Another option might be to drop TurboCAD and run a native Linux app instead: [https://alternativeto.net/software/turbocad/?platform=linux](https://alternativeto.net/software/turbocad/?platform=linux)

In fact, this is the usual methodology for people trying to wean themselves off Windows: move to a native Linux app.

---

### Post by oilyfish on 2019-03-10
> **DuckHook said:**
> Another option might be to drop TurboCAD and run a native Linux app instead: [https://alternativeto.net/software/turbocad/?platform=linux](https://alternativeto.net/software/turbocad/?platform=linux)



Yah I suppose I  could.  The odd thing about all these different platforms is that  once you learn one ( I'm talking about the  higher end softeware not sketchup and the like)  You become  very much a victim of its intricacies.   IT takes a long time to learn how to loft a helix or a thread in a part  stairs   meshing gears  these things in a 3D environment are very hard to master in the various different platforms and  it's like going  for a root canal every time  you open the program when  trying to  learn a new one.  

That was AutoDesk's trick.  Other platforms used Dongles and keys to prevent piracy but not  Autodesk, they  left themselves wide open to it and  as they planned,  young engineering students all flocked to it  exactly because they could pirate it.  So that's what they demanded when they got in the working world.   Because learning something else is  a horror. 


There's a French company  Dasault with a system that works in linux  Dunno if it's full 3D  it's actually damn cheap at $300   that's just a little more than I paid for Turbocad platinum pro .

---

### Post by HermanAB on 2019-03-11
Try FreeCAD:
[https://www.aeronetworks.ca/2014/12/freecad.html](https://www.aeronetworks.ca/2014/12/freecad.html)

Otherwise, try Code Weavers:
[https://www.codeweavers.com/](https://www.codeweavers.com/)

---

### Post by sbnwl on 2019-03-11
> **oilyfish said:**
> Yah I suppose I  could.  The odd thing about all these different platforms is that  once you learn one ( I'm talking about the  higher end softeware not sketchup and the like)  You become  very much a victim of its intricacies.   IT takes a long time to learn how to loft a helix or a thread in a part  stairs   meshing gears  these things in a 3D environment are very hard to master in the various different platforms and  it's like going  for a root canal every time  you open the program when  trying to  learn a new one.  

That was AutoDesk's trick.  Other platforms used Dongles and keys to prevent piracy but not  Autodesk, they  left themselves wide open to it and  as they planned,  young engineering students all flocked to it  exactly because they could pirate it.  So that's what they demanded when they got in the working world.   Because learning something else is  a horror. 


There's a French company  Dasault with a system that works in linux  Dunno if it's full 3D  it's actually damn cheap at $300   that's just a little more than I paid for Turbocad platinum pro .

Agree with what you said, AUTODESK trick worked.


My two cents on the Drafting software are as follows.

I don't know whether you are talking of DraftSight from Dassault Systemes..? But DraftSight is free and also available on Linux platform.



I have another alternative. I myself run SolidWorks in a Windows 10 Guest inside [VMWare Player for Linux.]("https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/15_0")
Oracle VM VirtualBox is also an option but It didn't provide sufficient acceleration to SolidWorks.

If you really want to use a 3D CAD tool on Linux then I would say, install VMWare Player.
Then use a Windows 10 (or whatever Windows version you have) ISO file in VMWare to install Windows as a guest operating system.
Then install Turbocad in the guest Windows OS.

I am sure TurboCAD will work great if you have a recent hardware..

---

### Post by mastablasta on 2019-03-11
> **oilyfish said:**
> IT takes a long time to learn how to loft a helix or a thread in a part  stairs   meshing gears  these things in a 3D environment are very hard to master in the various different platforms and  it's like going  for a root canal every time  you open the program when  trying to  learn a new one.  

i used to use MS word 2000 and 2003 for a really long time, so switching to LO Writer shouldn't be an issue (interfaces are rather similar). but for the past couple of years i've been mostly using word 2007 and later which all come with ribbon interface. the other day i had to do some really light editing in LO (setup the edges in writer, insert photos, change some borders... then add a few animation to impress slides). anyway i was surprised how i couldn't find anything. and how complicated it was to find what i needed. sure if you know the shortcuts it is easy, but if you don't you spend a lot of time clicking around menus where you think the settings are. in ribbon once i got used to it i can quickly find the needed icon and i realised i am much faster because of that. 

anyway it is difficult to just change the interface and menus. i can't even imagine the time i would use if there was even more stuff i would need to do.

---

