---
title: "&quot;Could not write bytes: broken pipe&quot; error in Lubuntu 12.04"
date: 2013-03-10
forum: General Help
---

### Post by AncientCows7 on 2013-03-10
Hello, I have a Dell Inspiron 600m and wanted to start using Lubuntu because it will work better seeing as it is an older system, and here is what happened:

-Tried installing Lubuntu 12.10, get 'PAE' error
-Found solution online, needed to install Lubuntu 12.04 then update with some modifications
-Installed L 12.04 alongside WinXP

-But when I try to boot into it, it briefly displays the Lubuntu logo, then goes into code.
-The first line is: "Could not write bytes: broken pipe" 
-There are other lines after it, and I can list them here if they are relevant
-There is no place for me to write anything to get any sort of error/message log, the only place that I can type anything is on the same screen where the error message is displayed.

-Is there any work around for this problem? Any help is appreciated :)

---

### Post by mörgæs on 2013-03-11
Hi, welcome to the fora.

The general advice when these problems appear is trying the [alternate ISO]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/"). 

Did you have wired internet access while installing?

---

### Post by AncientCows7 on 2013-03-12
[COLOR=#000000]How will the alternate ISO help? It installed completely, and my hard drive is smaller when I use WinXP, meaning that it has already been partioned.

And no I did not have a wired internet connection, but I have WiFi and I filled out the details (password, etc.) while installing.[/COLOR]

---

### Post by mörgæs on 2013-03-12
First of all, am I correct that the message is "Could not *write* bytes: broken pipe"?

---

### Post by AncientCows7 on 2013-03-12
[COLOR=#000000]Whoops yes, it is indeed "Could not [/COLOR]*write *bytes: Broken pipe"

Also, I tried restarting a couple of times to see if the message would change, and it did:

1st restart: [COLOR=#000000]Could not [/COLOR]*write *[I]bytes: Broken pipe
[/I]
2nd restart: 

* Stopping cold plug devices                            [OK]
* Stopping log initial device creation                  [OK]
* Starting configure virtual network devices        [OK]
* Stopping configure virtual network devices       [OK]
* Stopping save kernel messages                      [OK]
* Stopping System V runlevel compatibility          [OK]

3rd restart:

* Starting Bridge socket events into upstart        [OK]
* Starting AppArmor profiles                             [OK]
Skipping profile in /etc/apparmorid/disables
                                                                   [OK]
* Starting NTP Server ntpd                               [OK]

4th restart: nothing

---

### Post by mörgæs on 2013-03-13
OK, I edit the posts so Google will not be confused.

The bug has been a problem for some time for 12.04 and earlier versions. I have not seen reports for 12.10, so I guess it is fixed here, but as your computer doesn't have PAE it won't help you much.

I doubt that any effort will be put into fixing the bug(s) for 12.04. Have you considered another distro? For example, Precise Puppy Retro will give you access to all Buntu 12.04 packages on a non-PAE platform.


Another option is installing Lubuntu through the [minimal]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") (or the alternate) ISO, as I mentioned above. Though the same packages are being installed there could be configuration differences, and sometimes it does solve the problem, though it might sound illogical.

---

### Post by AncientCows7 on 2013-03-18
Ok thanks for the options but I think I'll leave Linux for a while, at least until I get a newer laptop. 

So can you please direct me to a link/page that helps in uninstalling Lubuntu without booting into it first?

Thanks for all of your help :)

---

### Post by sudodus on 2013-03-18
> **AncientCows7 said:**
> Ok thanks for the options but I think I'll leave Linux for a while, at least until I get a newer laptop. 

So can you please direct me to a link/page that helps in uninstalling Lubuntu without booting into it first?

Thanks for all of your help :)
Don't give up so easily! Try the ***Puppy linux ***version suggested by *mörgæs,* or try ***Knoppix*** if you have at least 512 MB RAM.

I'm writing this message on an old IBM Thinkpad T42 with a non-pae kernel and Lubuntu 12.04. I have no bug in Lubuntu, and those other distros are working well too on this machine as well as on many other aging computers.

Good luck :-)
--
You can remove the installed Lubuntu system when booted the Lubuntu install CD/USB drive, but beware, if you remove the /boot directory, you need to rewrite the master boot record to point to the windows again.

---

### Post by mörgæs on 2013-03-18
+1 to sudodus. Giving up after one installation attempt, really?

---

### Post by AncientCows7 on 2013-03-30
Well, you see, I'm sure that the options that both of you have suggested will work, but now the fact that it is not working is not the only problem I am experiencing. The other problem that I am facing is that my hard drive is not big enough to support 2 OS's (The max size is 60 GB, but windows takes up 10-15, and Lubuntu takes 10, and the rest are my files).
 
In the future if I am to buy a hard drive for this computer, I can always refer back to this thread. So for now, can you please tell me how to remove Lubuntu? Thanks :)

---

### Post by kurt18947 on 2013-03-30
I hesitate to give advice on how to remove things without breaking other  things.  May I suggest something for your consideration?  Does your  current machine have USB 2, as opposed to USB 1.1?  2 GB. RAM? If so, you could run  other distros as a live USB or I've done 'real' installs on USB drives  formatted as ext2.  I didn't create a swap partition and writes are  pretty slow but you can install and update a full system on a larger -   8 GB. works, 16 GB is maybe better - USB flash drive.  You could create a swap partition on a flash drive but I'm not sure how long the flash drive would last -  it may live long and prosper, it may not.  I guess it depends on how frequently the swap partition is written to.

A downside to the live USB installs  with persistence for me is that I was unable to install updates.  A live  USB with persistence would remember data files and settings but after  an update or two, the system would be broken.  As to the O.P.s original question,  I've had similar problems if I didn't have a wired internet connection.  The install process looks for a live network connection, doesn't find it and hangs.

---

### Post by sudodus on 2013-03-30
If you have a dual boot system it uses grub to boot, which is installed into the MBR (at the head of the drive) and in /boot (in the linux partition). So if you remove linux the computer will not boot. You must install the windows code into the MBR again (as it was before you installed linux (Lubuntu)). See > #7: Fix a corrupt master boot record at this link
[[COLOR=#ff0000]http://www.techrepublic.com/article/10-things-you-can-do-when-windows-xp-wont-boot/6031733[/COLOR]]("http://www.techrepublic.com/article/10-things-you-can-do-when-windows-xp-wont-boot/6031733")

or watch this video about EasyBCD (that you run in Windows before deleting Ubuntu)
[[COLOR=#ff0000]https://www.youtube.com/watch?v=uUgf84bdYvg[/COLOR]]("https://www.youtube.com/watch?v=uUgf84bdYvg")

---

