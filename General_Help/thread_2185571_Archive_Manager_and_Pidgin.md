---
title: "Archive Manager? and Pidgin"
date: 2013-11-03
forum: General Help
---

### Post by tomsubt on 2013-11-03
Hi,   Where is the Archive Manager location or do I have to install it if so how and also do i choose archive manager when asked where to install applications? Thanks

---

### Post by tomsubt on 2013-11-03
Hi,   Where is the Archive Manager location or do I have to install it if so how and also do i choose archive manager when asked where to install applications? Thanks

PS: never mind I found the archive manager. the problem i am having is I cannot get a downloaded app to go into it, do I have to install a zip extracter first, if so is there one
that you can direct me to and will I be then able to send and open an app from there? Thanks, sorry new at this!!

---

### Post by grahammechanical on 2013-11-03
I do not know which version of Ubuntu you are using. But in my version (Trusty Tahr) I type Archive in the dash and in a few seconds I get an icon that will let me launch the Archive Manager that was formally know as File Roller, I believe.

I have never been asked where to install applications. Ubuntu Software Centre takes care of that. Perhaps you are thinking about compressed packages that you have downloaded such as those with the .tar.gz extension.

These downloads usually go into the Downloads folder by default. I use File Manager to copy and paste them to a folder of my choice and I use file Manager to open the folder and I right click on the .tar.gz file and select Open with Archive Manager.

Regards.

---

### Post by Impavidus on 2013-11-03
It's not exactly clear what you want.

If the archive manager doesn't open when you double-click an archive, you can open it with the command **file-roller**. It's located in /usr/bin/file-roller. It should be installed by default, but if it isn't, install the package **file-roller**. Use the software centre or the terminal.

If you're really sure you want to install something manually (that is, it's not in the repositories, there's no ppa and not even a .deb), I recommend you try to be smart and install it in /usr/local, with different parts going into /usr/local/bin, /usr/local/share, etc.

---

### Post by grahammechanical on 2013-11-03
You certainly are new to this. You have created two threads on the same subject. I have just replied to your earlier thread. We need a moderator to combine both threads. 

You need to Open and browse to the folder where the .tar.gz file is and select the file to get it into Archive Manager. Which does a lot more than you think.

[https://apps.ubuntu.com/cat/applications/file-roller/](https://apps.ubuntu.com/cat/applications/file-roller/)

[https://help.ubuntu.com/community/File%20Roller](https://help.ubuntu.com/community/File%20Roller)

[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

Regards.

---

### Post by Frogs Hair on 2013-11-03
Merged

---

### Post by tomsubt on 2013-11-03
Sorry about the duplicate thread,  I am using 12.04  and the archive manager is empty,. it seems no matter what I want to install it ask me what do I want to open it with and i dont know what to say?  Right now I want to download yahoo messenger for linuix but the same window came up asking what to open it with, what should I say? Thank You

---

### Post by Iowan on 2013-11-03
Merged.

---

### Post by Impavidus on 2013-11-03
The archive manager can open any archive you tell it to open and then shows what's inside – as long as it has a reasonably common format. It doesn't know anything about installing, however. The only thing it can do is unpack the archive where you instruct it to unpack.

What kind of file are you downloading? Are installation instructions included?

---

### Post by tomsubt on 2013-11-03
I am trying to install this exe>>>    /home/tomsubt/Downloads/msgr11us.exe  so I can use yahoo messenger on Pludgin

---

### Post by tomsubt on 2013-11-04
> **tomsubt said:**
> I am trying to install this exe>>>    /home/tomsubt/Downloads/msgr11us.exe  so I can use yahoo messenger on Pludgin

Well? Does anyone know how to get yahoo messenger on ubuntu, I thought you had to use Pidgin if so how?  Or can I call a yahoo messenger user directly from pidgin? Thanks

---

### Post by Impavidus on 2013-11-04
Eh, I think so (calling directly from pidgin). I don't really know, I never really use messenger programs myself (yes, I know how non-standard I am). Anyway, I don't think you'll get that .exe working on Ubuntu, as it's a Windows executable. Linux executables rarely have an extension, although the whole concept of extensions is quite meaningless to Linux. The reason why the archive manager came up is that some windows executables are self-extracting archives, which can be handled by the archive manager.

---

### Post by philinux on 2013-11-04
In pidgin you need Linux plugins not windows ones.

[https://developer.pidgin.im/wiki/ThirdPartyPlugins](https://developer.pidgin.im/wiki/ThirdPartyPlugins)

---

### Post by tomsubt on 2013-11-04
Impavidus, Thanks for the info,  Do you or anyone know what messenger service I can use to talk to my friend who has yahoo messenger, or is there a talk set up we can both
install and talk with?
Also, I will be looking into the link Philinux sent me on the plugins, Thank You

---

### Post by philinux on 2013-11-05
> **tomsubt said:**
> Impavidus, Thanks for the info,  Do you or anyone know what messenger service I can use to talk to my friend who has yahoo messenger, or is there a talk set up we can both
install and talk with?
Also, I will be looking into the link Philinux sent me on the plugins, Thank You

I think you may have missed a lot of info. [http://www.pidgin.im/](http://www.pidgin.im/)

It's a **_universal_** chat client. You don't need to download from the above link as the same version is in ubuntu software center.
> Pidgin is a graphical, modular instant messaging client capable of using
multiple networks at once. Currently supported are: AIM/ICQ, Yahoo!, MSN,
IRC, Jabber/XMPP/Google Talk, Napster, Zephyr, Gadu-Gadu, Bonjour,
Groupwise, Sametime, SIMPLE, MySpaceIM, and MXit.

---

### Post by christopher-lees on 2013-11-05
> **tomsubt said:**
> Impavidus, Thanks for the info,  Do you or anyone know what messenger service I can use to talk to my friend who has yahoo messenger, or is there a talk set up we can both
install and talk with?
Also, I will be looking into the link Philinux sent me on the plugins, Thank You

If you want to actually talk with microphones or webcams (like a phone call or video call) you should use Skype. It's cross-platform and works well. Yahoo Messenger's basic messenging functionality works cross-platform but it doesn't support voice on Linux. Use Skype instead.

---

### Post by tomsubt on 2013-11-05
Yeah, Thanks  I went back to the link and if im not mistaken it states I can use it with yahoo messenger and google talk but when I bring up the buddy list on pidgin screen it tries to connect to the yahoo messenger ID i gave it but it always comes back as Disconnected and will not connect, it keeps saying it Timed out,  Any idea's on what could be wrong? Thanks

---

### Post by tomsubt on 2013-11-05
Thanks, I just got this message from pidgin about yahoo messenger>>>No Address Associated with the Hostname? what does that mean? Also Google will not connect either. I thought google would work, it states it can with pidgon. bit still will not connect? Any ideas on google not connecting?

---

