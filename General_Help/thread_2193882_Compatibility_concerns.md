---
title: "Compatibility concerns"
date: 2013-12-15
forum: General Help
---

### Post by zaibatsu2 on 2013-12-15
Hi,
I'm considering abandoning Windows altogether in favour of Ubuntu, but before I do I have concerns about compatibility of certain programs. I don't use the internet on my laptop at all, I use it for the following;


[LIST]
[*]Microsoft Office 2013
[*]BibleWorks 8
[*]Algebrator
[*]Bagatrix (Math software pack)
[*]Wordpad (.rtf)
[*]Foxit Reader
[*]VLC
[/LIST]

Is there a way for me to get all of these programs working on Ubuntu? With regards Wordpad, is there a program on Ubuntu that can ably replace it? 

Marcus

---

### Post by buzzingrobot on 2013-12-15
Because of the inherent incompatibility of programs across different  software platforms, you're probably better off trying to determine if  Linux provides the functionality you need rather than if specific  programs will work.

Windows programs do not run on Linux, just as Linux programs do not run on Windows. And, of course, neither run on OS X, or vice versa.

That said...

1. VLC is widely available for Linux.

2. Linux offers the Libreoffice suite, which is essentially an Office clone. You need to be certain that it is compatible with the latest Office file formats before you switch. 

3.  I'm sure there are Linux editors than handle rtf files.  I don't know if there is one that duplicates WordPad.

4. I'm not familiar with the other programs.  If the vendors offer Linux versions, they will note that on their sites.

5. A program suite called "Wine" is available in Linux that creates an artificial Windows environment, allowing some Windows programs to run, in effect, inside it.  How well that works depends on a number of things.

---

### Post by zaibatsu2 on 2013-12-15
I'll make note of all of those things, thanks for the reply. Only a  moment ago I saw the option to install from within Windows, so that you  can sort of test Ubuntu 12.4. From this would I be able to attempt to  open programs already on Windows? Sorry for these simple questions,  these computer issues are not my area of expertise.

---

### Post by BlinkinCat on 2013-12-15
Hi,

This may be of assistance to you -

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Cheers - :)

---

### Post by grahammechanical on 2013-12-15
> **zaibatsu2 said:**
> I'll make note of all of those things, thanks for the reply. Only a  moment ago I saw the option to install from within Windows, so that you  can sort of test Ubuntu 12.4. From this would I be able to attempt to  open programs already on Windows? Sorry for these simple questions,  these computer issues are not my area of expertise.

No. It will still not be possible to run Windows programs in Ubuntu. But you will be able to install Linux programs that might compare favourably with the applications that you are already using. You will be able to access the documents that are in Windows to see if they open in the Linux applications and keep their formatting. And you will be able to install wine in Ubuntu and with that you can try to install Windows programs inside wine.

Once wine is installed (it is in the Ubuntu software Centre) look for something called Uninstall Wine Software. That utility will give you an option to install a Windows application. It present a Windows type dialog. Just browse to the location of the application's setup exe file and click on it and Intellishield will run just like in Windows.

Regards.

---

### Post by sgage on 2013-12-15
I believe you meant "look for something called Install Windows Software"?

---

### Post by grahammechanical on 2013-12-15
> **sgage said:**
> I believe you meant "look for something called Install Windows Software"?

Ok. To test this out I have just installed wine 1.4 from the software centre in Trusty Tahr. And the utility is called Uninstall Wine Software. Run that utility and we get a Windows type Add/Remove programs dialog with an "Install" button. Click the Install button and we can browse to the location of the setup or install exe file just like installing in Windows.

One thing to note. The installation process of wine will give an option to install Microsoft true type core fonts. The installation of wine will pause until we either click to accept the Microsoft EULA or click to move forward without installing the Microsoft true type core fonts installer. The dialog to do this will be hidden behind the software centre window. So, minimize the software centre window because the install of wine will hang unless we take action on a couple of hidden dialog boxes.

By the way, these Microsoft true type core fonts might be expected by some Windows applications. Without these core fonts the Windows program may not run under wine.

Regards.

---

