---
title: "Trying to install Ubuntu getting error I think it's about my SAS card..."
date: 2024-04-19
forum: General Help
---

### Post by fin7452 on 2024-04-19
My setup is a i7-13700k with a 3070

Mobo is a MSI MAG Z790 Tomahawk WiFi

I do have an SAS 9211-8i RAID Controller Card

The error happens when I hit try or install Ubuntu. At this point I'm just wanting to see if I can get to the desktop lol

UBSAN: array-index-out-of-bounds in ^(build/linux-hwe-6.5-Zv1Qen/1) index 1 is out of range for type 'MPI2\_SAS\_IO\_UNITO\_PHY\_DATA \[1\]'


This the error i'm seeing on my screen.

I'm very new to pretty much to everything lol

Thanks for any help.

---

### Post by Rubi1200 on 2024-04-20
Which version of Ubuntu are you trying to install?

Please post all the specs. for the computer.

---

### Post by fin7452 on 2024-04-20
Ubuntu 22.04.4 Desktop . I'm not sure what you mean by all. The post does list them all.

---

### Post by ajgreeny on 2024-04-20
Is that 3070 you mention in post #1 your nvidia graphics card?

If so you may need to try running with boot option **nomodeset**.
From the grub screen hit e for edit go to the line starting Linux and ending "quiet splash" and replace those two words with **nomodeset**
Now hit Ctrl+x to boot.
This may get you to a low resolution GUI from which you can then install the correct nvidia driver after installation of the OS.
You could also try enabling the option to install third party drivers during the install process,  something I've never needed to do.

NB:
I have never had an nvidia graphic card and therefore I might be out of date with current needs.
Also check whether you have secure boot enabled and if so disable it Iin the BIOS/UEFI settings.

---

### Post by fin7452 on 2024-04-20
Sorry yes the 3070 is my graphics card. I'll give that a try when I get the next chance. 

Thanks for the help.

---

### Post by MAFoElffen on 2024-04-20
You need to include the "nomodeset" boot option for your NVidia graphics driver until you get your NVidia Drivers loaded... But that is not what that error is about.

First, on your LSI Logic SAS 9211-8i RAID Controller Card...
1) Have you updated it's firmware to it's latest version?
2) Are you using a RAID mode or passing the drives through in HBA mode?
3) Did the drives show through in the installer?
4) which version and edition of the Ubuntu Installer did you use?

Next, from an Ubuntu LiveCD > "Try" option, run the UbuntuForums 'system-info' Script, but instead of running it with standard startup, run it in details mode... From a terminal:
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
[COLOR=#ff0000]./system-info --details[/COLOR]

```
At the end, choose to upload the report to a pastebin, and post the URL in a post. We want to see how the controller is being recognized, and "which driver" is being loaded.

That LSI SAS controller is one I recommend to people for their storage solutions. It is very common, dependable, and usually just works. We'll see if it is having some kind of challenge with that specific kernel version(?)

---

### Post by fin7452 on 2024-04-20
I don't even know where to start with that lol I just put it in my computer and let Windows do the rest. 

Just passing the drives through and setting up as a JBOD with windows.

I haven't even get that far it's literally at the first screen. 

Ubuntu 22.04.4 Desktop..is what what you're asking? I used Rufus to create the USB key.

---

### Post by MAFoElffen on 2024-04-20
Okay...

FYI: "UBSAN: Index Out Of Range" Warnings are usually harmless. They mean, in the underlying code, a range was declared, because the extent of the range values was unknown. The warning like that is that it was more than expected... But it usually goes on from there, meaning it just continues along (not a fatal error).

Does the installer continue on from there?

---

### Post by fin7452 on 2024-04-20
No, I've let it set for 5 minutes just to be sure and it never goes to the next screen. Just a black screen with that error

---

### Post by MAFoElffen on 2024-04-20
Further, in the installer, since you have NVidia, use the "safe Graphics" option to start it up. When it gets to a panel where the last checkbox says "install 3rd party drivers"... check that checkbox, so that it see's your NVidia GPU, and lets it try to install your graphics drivers.

Tell me if it see's all your drives, by going to the "Other/Manual" on the installation method/partitioner screen.

---

### Post by fin7452 on 2024-04-20
Ok will do thanks

---

### Post by fin7452 on 2024-04-20
So an update. I just removed the GPU and after that every went smoothly. 

From my understanding with Plex the iGPU is enough for it with my CPU since I'm not for the most part using Plex outside my home.

The thing is I wanted to dual boot, but when I select the option it never gave me my WD black NVME to do so. 

So I just created a partition in windows and had Ubuntu use that and after that everything went perfectly. 

Thanks everyone for the help.

---

### Post by MAFoElffen on 2024-04-20
So, you ignored everyone's recommendations to either use "nomodeset" boot parameter, or starting the installer with the "Safe Graphics" option. That was verified when you pulled your NVidia card and it just worked.

Okay. LOL. You do not think that is a problem, so this is solved then.

Please use the "Thread Tools" link at the upper right of the page to mark your thread as "Solved".

---

### Post by fin7452 on 2024-04-20
> **MAFoElffen said:**
> So, you ignored everyone's recommendations to either use "nomodeset" boot parameter, or starting the installer with the "Safe Graphics" option. That was verified when you pulled your NVidia card and it just worked.

Okay. LOL. You do not think that is a problem, so this is solved then.

Please use the "Thread Tools" link at the upper right of the page to mark your thread as "Solved".Or you know what I took the advice to look at my GPU that might be causing the issue and confirm that with the removal of my GPU and looking more into it decided that including MY GPU with MY setup no longer made sense so I removed it. Why is that a problem? it's my setup, I was told to look at my GPU as a cause of the issue I confirmed with it's removal and decided to not put it back in... it's odd whenever I i sought help with my windows install everyone was more then willing to help even if I didn't follow advice to the letter, but here no you can't go against advice! wtf! &#128580;

---

