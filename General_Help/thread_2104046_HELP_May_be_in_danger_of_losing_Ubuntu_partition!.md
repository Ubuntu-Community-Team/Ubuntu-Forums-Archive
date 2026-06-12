---
title: "HELP May be in danger of losing Ubuntu partition!"
date: 2013-01-11
forum: General Help
---

### Post by Enoch Dew on 2013-01-11
I have a Lenovo Z575 that was hit by a nasty peice of ransomeware known as the DOJ virus. I went into my Ubuntu partition and ran ClamAV to remove it. It did ALONG WITH A BUNCH OF IMPORTANT SYSTEM FILES. When I boot into Windows  7 I can log in, but the screen is black with the cusor and I can get into task manager. So my real question is can I use Lenovo's one key recovery feature to save my Windows partition or will it format my Ubuntu and shared data partitions away? Any help would be very appriciated.

---

### Post by cafejunkie on 2013-01-11
If I remember correctly, most recovery partitions on OEM machines will completely wipe any existing partition configuration to restore to factory state.

If you have a windows install disk, you can boot from it and choose the "repair your computer" option and check to see if there are any restore points available to use system restore and roll it back to before you got the infection.

That DoJ malware is a nasty little bugger. Usually it replaces your default login shell with the virus. It's possible you just need to change that registry key back to the proper value.

If you can boot into safemode to open up regedit, check the
HKLM\Software\Microsoft\Windows NT\CurrentVersion key
Look for the "userinit" value and make sure it is set to C:\Windows\System32\userinit.exe

--edit--
you said you can get to task manager. When in normal mode, open up task manager and you can get to regedit from there.  If I remember, it hsouldbe under "file->new task" and you can type in "regedit.exe"
I hope that helps.

---

### Post by Enoch Dew on 2013-01-11
My computer has the "repair your computer" option when you go to the safe mode screen, but I don't have any restore points. I got to the CurrentVersion key, but do not see userinit at all. P.S. Thank you so much for the quick reply.

---

### Post by cafejunkie on 2013-01-11
> **Enoch Dew said:**
> My computer has the "repair your computer" option when you go to the safe mode screen, but I don't have any restore points. I got to the CurrentVersion key, but do not see userinit at all. P.S. Thank you so much for the quick reply.

That was my fault, there's an extra subkey that contains the userinit value (I don't have my windows VM running atm, I'll fire it up if this dones't work)

The userinit value is unter that CurrentVersion key but the subkey is "winlogon"
so the whole thing should be
HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon

---

### Post by Enoch Dew on 2013-01-11
That value is as it should be unless a comma at the end of userinit.exe is significant.

---

### Post by cafejunkie on 2013-01-11
> **Enoch Dew said:**
> That value is as it should be unless a comma at the end of userinit.exe is significant.

Hmm, darn. Was hoping this would be simple :P
The comma is supposed to be there.

I'm afraid there's not much more that I can do to help get it repaired without actually replacing the system files that ClamAV removed. If you happen to have the log of files, you can actually extract a windows service pack (say if you're running 7 you can Download and extract SP1 and you'll be able to unpack the .sy_ and dl_ files and copy those to their respective locations) and that might get you up and running again.
It's a pretty time consuming process but it has worked for me in the past.

Other than that, I think the only other option is to get a hold of windows install media so you can do an "in place upgrade." There is a certain location on the internet that's a Microsoft partner that offers legitimate downloads of Windows 7 install media for this, you'll just have to use your product key on the PC. Unfortunately, I'm sure it's against forum policy for me to link to the particular site but lets just say if you do some googling along the lines of "digital river" or "mydigitallife" and "windows iso" you'll find it ;) (this is where during the install, you choose your current partition with windows on it WITHOUT erasing/deleting it). This will move your current installation along with all of your programs and files to "Windows.old" folder and perform a clean install, at which point you can copy stuff back over).
It will overwrite grub so you'd have to reinstall grub but at least you get to keep your Ubuntu partition.

Last resort option would be to boot off of a live USB/DVD and backup all of your files to an external HDD if you have one and reinstall :(

Good luck! And backup anything you can before you delve too far in to trying to repair windows :)

---

### Post by Enoch Dew on 2013-01-11
Another significant piece of information. On login, a window pops up telling me I'm missing the wgsdgsdgds.dll module.

---

### Post by cafejunkie on 2013-01-11
> **Enoch Dew said:**
> Another significant piece of information. On login, a window pops up telling me I'm missing the wgsdgsdgds.dll module.

That sounds like a dll related to the malware, there's likely still a start up item looking to start the malware program (incomplete removals are very common when using virus scanners as opposed to manually removing infections).

If you can successfully get into safe mode (hit F8 before the windows loading screen comes up) you can download the Sysinternals tools [http://technet.microsoft.com/en-us/sysinternals](http://technet.microsoft.com/en-us/sysinternals)

There is a utility in that set called "autoruns" that will list every start up item on your PC. You can sift through the applications and uncheck anything that looks malicious, as well as enable the default windows services that the malware likely disabled.

---

### Post by Enoch Dew on 2013-01-11
I'll try that when I get the time tomorrow. Thanks again. I'll be sure to let you know how it goes.

---

### Post by cafejunkie on 2013-01-11
> **Enoch Dew said:**
> I'll try that when I get the time tomorrow. Thanks again. I'll be sure to let you know how it goes.

No problem :)
Hopefully it goes well for you. Good luck!

---

### Post by Enoch Dew on 2013-01-13
Thank you so very much! =D I got on safemode, downloaded autoruns, saw and deleted the batch file that started for the virus, ran a utility for windows that repaired system files. When I rebooted everything was back to normal.

---

### Post by cafejunkie on 2013-01-13
> **Enoch Dew said:**
> Thank you so very much! =D I got on safemode, downloaded autoruns, saw and deleted the batch file that started for the virus, ran a utility for windows that repaired system files. When I rebooted everything was back to normal.

Awesome! I'm glad to hear it worked :)

---

