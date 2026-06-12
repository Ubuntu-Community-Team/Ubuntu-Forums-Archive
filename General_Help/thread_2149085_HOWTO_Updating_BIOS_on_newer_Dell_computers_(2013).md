---
title: "HOWTO: Updating BIOS on newer Dell computers (2013)"
date: 2013-05-27
forum: General Help
---

### Post by deruberhanyok on 2013-05-27
Hi all,

I recently purchased myself a new Inpsiron 15R laptop during a sale because I knew it would be a perfect Linux system - Intel wifi, Intel video, etc. Unfortunately I discovered that the BIOS that it shipped with was a little bit out of date, and one of the fixes in the newer version was for a fan speed problem I was having (I was on A05, and A06 listed "improved fan speed algorithm" as an update, and A07 later came out). When I went to download the BIOS I was disappointed to see that it was a Windows/DOS executable that couldn't easily be unpacked. Having replaced the hard drive with an SSD for Ubuntu, I considered just booting the laptop's original Windows 8 hard drive, but I wanted to keep that unused in case I ever sell the laptop. I figured there must be a way to do this without having to install/boot Windows on the system.

I read through a large number of guides on various websites, including the Ubuntu wiki, to figure out how to do it. I tried pulling a ".hdr" file out of it with wine and the "writehdrfile" option ("invalid winflash parameters"), I also tried the (now deprecated, as I learned) Dell Linux BIOS servers. I tried using unetbootin to make a FreeDOS boot USB device, only to find that running the executable in FreeDOS gave me the extremely useful output of "Test." whatever that means, and I tried a few other things, eventually stumbling on a fairly easy way to run the BIOS update. I wanted to share in case anyone else was having similar problems

This definitely worked on my new Inspiron 15R (5521) and will possibly also work with other newer Dell systems where the previous methods fail. You'll need a few things:

- VirtualBox (from [http://www.virtualbox.org](http://www.virtualbox.org), or from the Ubuntu Software Center)
- a 32 bit Windows 7 Home Premium install ISO (I downloaded one from Linux Lab Library on this page: [https://sites.google.com/site/linuxlablibrary/windows-iso](https://sites.google.com/site/linuxlablibrary/windows-iso), if the links no longer work you the filename is X17-24208.iso and MD5 is c5bb99b2f1a9e7a5b4fbc6e3eff70882) (I'll explain why 32 bit below)
- a blank CD (and a CD writer, obviously)
- a FAT formatted flash drive
- the BIOS EXE file from Dell (for this example, the filename is 5521A07.exe)

If you know anything about Windows and Virtualbox you can probably guess where this is going. The Windows CD will let you install without entering a product key and gives you a 30 day trial period for using the OS. Since we only need it for a few minutes, this'll do just fine. :)

1) Using Virtualbox and the Windows 7 32 bit ISO, create a Windows 7 VM. The install will be fairly quick reading from an ISO file. Once it is done, shut down the VM.
2) In the VM settings, go to the CD drive and make sure it is set for "host drive" and click the "passthrough" checkbox (this is required to burn a CD from inside the VM).
3) Now start the VM, click the start "pearl", go to the control panel, select "system and security" and then "backup and restore".
4) On the backup page, there should be a link for "create a system repair disc" - click on that and follow the prompts.
5) Once the disc is created, you can shut down the VM - you don't need it anymore.

The next part is a bit finicky. I was running Ubuntu 64 bit, and my SSD has a GPT on it, not the older MBR method. This is, I think, standard for a 64 bit Ubuntu install on a system with UEFI booting (which this laptop, and all newer Dell machines that I know of, uses by default). I originally found that the 32 bit repair disc would spit out this error message and not proceed to any useful menus:

"This version of System Recovery Options is not compatible with the version of Windows you are trying to repair. Try using a recovery disc that is compatible with this version of Windows."

My best guess as to why is because it saw the GPT scheme on my SSD and, if I remember correctly, only the 64 bit versions of Windows support GPT on the boot drive on UEFI systems. So I tried repeating the process with a 64 bit repair disc. This worked, but attempting to run the BIOS executable gave me this error:

"The subsystem needed to support the image type is not present."

From what I could find, it turns out that Dell just hasn't got around to supporting the 64 bit mini-windows environment (I've seen it called "WinPE") for running the BIOS update. It works fine from within the full 64 bit OS, but obviously we can't flash BIOS from inside a virtual machine. My solution was as follows:

6) copy the BIOS file to the flash drive
7) shut down the laptop and disconnect the hard drive (I couldn't find an option for disabling it so I had to physically disconnect; if you can find a way to shut off access to it in the BIOS then do that and save yourself the trouble)
8) connect the flash drive to the system
9) boot to the 32 bit Windows repair disc (may need to enter the boot menu, via F12, if it doesn't automatically boot to the CD)
10) the Windows repair environment will scan your system for a Windows install. Let it finish and then select the top option ("Use recovery tools that can help fix problems Starting Windows.")
11) on the list of recovery tools, pick "command prompt"

Final steps here:

12) At the command prompt, type "C:" and press enter.
13) type "dir" and press enter.
14) If you see the BIOS flash file, then type the filename, press enter, and follow the prompts. 

If you don't see the BIOS flash file, try other drive letters ("D:", "E:", etc) until you find it.

15) When the system reboots for the last time and tries to load the Windows repair disc again, shut it down, reconnect your drive and then go back to whatever you were doing.

I was disappointed to see that Dell didn't have a simple bootable image that could be burned to a CD or flash drive for the BIOS update (or, for that matter, that they haven't integrating updating capabilities directly into the BIOS, as some motherboard manufacturers have) but this is a relatively painless process.

Hopefully someone will find this useful and skip all of the frustration I experienced going through the various older documented methods.

Matt

---

### Post by Ilya_Greenworld on 2013-09-27
Thank you a lot for so detailed instructions

This is the ONLY way i was able to update my BIOS without removing Ubuntu and installing Windows (i think it's too much if i need update BIOS only)

---

### Post by SantaFe on 2013-09-27
Glad you got it updated, but there is this Package in Synaptic: firmware-addon-dell

```
The firmware-addon-dell package provides plugins to firmware-tools which enable
BIOS updates for Dell system, plus pulls in standard inventory modules
applicable to most Dell systems.
```

Now I'll admit I haven't tried it, as I dual boot (although sometimes it feels like Duel-Boot ;) ) with Windows 7, but it might be a slightly easier route.

---

