---
title: "Newly installed Xubuntu 20.04.3 seems to hang 10 sec at shutdown"
date: 2021-11-30
forum: General Help
---

### Post by Ralph L on 2021-11-30
I just installed Xubuntu 20.04.3 (formatting the partition during install as is necessary). It completed installation without error. When I booted of the new partition, it asked to install upgraded SW. I clicked yes and it installed a lot of SW. I then selected a complete shutdown off the whiskers menu. The "processing" indicator moved in a circle for a second or two, then the screen blanked for a couple seconds, then came back on with word Xubuntu and the processing indicator frozen for about 10 seconds. Then the computer shutoff.
Is this 10 second freeze normal for Xubuntu shutdown? My old Xubuntu 18.04 did not do that. It seems abnormal to me. Should I be concerned??
Any help appreciated.........

---

### Post by T6&amp;sfpER35% on 2021-12-02
mine does that too , i'm not worried as long as it starts up fine again lol

---

### Post by Impavidus on 2021-12-02
You can hit escape during shutdown (also during startup) to show the messages instead of the splash screen. Maybe it says what it's waiting for. Or dig into the logs. But I wouldn't be bothered.

---

### Post by Ralph L on 2021-12-03
Does anybody know if Ubuntu (rather than Xubuntu) also hangs (freezes) for 10 seconds at shutdown?

Thanks
Ralph

---

### Post by him610 on 2021-12-04
No hang here on two machines both running LTS 20.04.3; however, there are no other processes waiting to terminate. 
Laptop, Acer Aspire V3-572G-543S, shuts down in about one second; Desktop, AsRock H270M-ITX, shuts down in about three seconds.
I have observed some processes taking up to 130 seconds to terminate on some machines before shutting down.
There is probably nothing to be concerned about, as long as it boots as 3nd suggested.

---

### Post by Ralph L on 2021-12-05
him610
Thanks for the response. I really appreciate it. I presume the 20.04.3 you are running is Xubuntu. Could you verify that this is so? I am looking for how your Xubuntu 20.04.3 could be different than mine, since yours seems to shutdown ok. Also, for a test I installed Ubuntu 20.04.3 in a separate partition and it has no problem shutting down.
1. Do you use a swap partition, or do you use a swap file? I am using a swap file.
2. Are you multi-operating systems? I have the original Windows, 18.04 (my current running system and using a swap partition), Xubuntu 20.04.3 downloaded a few days ago and updated, and now for testing Ubuntu 20.04.3 (it shuts down fine).
3. Can you think of anything else that could be different about your Xubuntu system from mine.
Thank you very much..........
Ralph
PS. This is the 3rd bug I have found in Xubuntu 20.04.3 and I haven't even started to use it. Kind of frustrating. Maybe I will stick with Xubuntu 18.04.

---

### Post by him610 on 2021-12-05
Ralph L
Both machines use Xubuntu 20.04.3. The laptop is dual bootable with Win10; the AsRock H270 has only Xubuntu on it. I have another machine, AsRock B450m with only Xubuntu 20.04.3 on it that powers down with little noticeable delay if any.

Post #3 suggests, "You can hit escape during shutdown (also during startup) to show the messages instead of the splash screen...."
You can also get the same messages every startup and shutdown by modifying the line in your grub file to read, [COLOR="#FF0000"]GRUB_CMDLINE_LINUX_DEFAULT="text"[/COLOR]
It is much more informative to watch the messages scroll by than just look at a splash screen.
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

By the way, that ten second delay is not a bug. What are the other two bugs you are referring to?

---

### Post by Ralph L on 2021-12-09
him610:
Again, thank you for responding.
1. I have been able to display the messages, but on shutdown they roll by much too fast to read. And they disappear before the hang takes place. I did use my cell phone to make a video of the screen during shut down and then viewed it frame by frame with vlc. The video wasn't perfect, but it showed the messages fairly well, and I didn't see anything unusual about the shutdown--no error messages or anything like that. 
2. I downloaded, and installed in a spare partition, xubuntu 21.10. It didn't have the shutdown delay, so somebody fixed/changed something. I also downloaded and installed plain Ubuntu 20.04.3 and it did not have the delay either.
3. I agree with you that it probably doesn't make much difference having the delay, but I do like things to work right, especially when I will be using them for a long time.
4. The other 2 bugs I ran into were: 
A. During system install from the memory stick, you get an error if you don't format the install partition after you select "Something else". in the past I have always formatted the install partition with gparted before I started the install, and didn't bother to format it again in the midst of the install. This bug came up relatively easily after several google attempts and is well know by everybody but me. 
B. I have become very dependent on Python Windows Organizer. With a keystroke or 2 you can size and place a window in 11 positions on the screen and they fit together very nicely. Pywo hung during install on Focal. It ran fine under Bionic and all previous OSs. I found that I had to install a symbolic link in /usr/bin to link "python" to "python2.7". This one took me a while, because I started the wrong way looking at python code (which I am unfamiliar with) instead of trying to fix library linkages.
Thanks again for responding........

---

### Post by Ralph L on 2021-12-19
I seem to have fixed the "10 sec hang on shutdown" problem by disabling the Splash screen (the Xubuntu logo and the circular arrow) at boot time. This can be done manually at boot time issuing the "e" command, when selecting the OS to boot, then editing out the "Splash" in the boot command, and pressing F10 to boot. It can be done permanently by editing the file /etc/default/grub to remove the "splash" in line 6 of the commands.
```
sudo mousepad
delete the word "splash" in the 6th command line
Ctl s to save the change
sudo update-grub

```
This worked for me. Of course I don't see the Xubuntu log and progress circle during boot or shutdown.

---

