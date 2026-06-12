---
title: "Can't make bootable Windows ISO in Linux"
date: 2020-05-05
forum: General Help
---

### Post by paeschli on 2020-05-05
I'm trying to make a bootable Windows USB-drive in Linux. I've heard  online about unetbootin and woeusb; but it's impossible to install  either of those two. They need dependencies that can't be installed.

paeschli@paeschli-pc:~$ sudo apt-get install unetbootin
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De statusinformatie wordt gelezen... Klaar
Sommige pakketten konden niet geïnstalleerd worden. Dit kan betekenen
dat u om een onmogelijke situatie gevraagd heeft, of, indien u
de distributie 'unstable' gebruikt, dat sommige benodigde pakketten nog gemaakt moeten worden of uit 'Incoming' verwijderd werden.
De volgende informatie kan misschien helpen de situatie op te lossen:

De volgende pakketten hebben niet-voldane vereisten:
 unetbootin : Vereisten: libqt4-network (>= 4:4.5.3) maar het is niet installeerbaar
              Vereisten: libqtcore4 (>= 4:4.7.0~beta1) maar het is niet installeerbaar
              Vereisten: libqtgui4 (>= 4:4.5.3) maar het is niet installeerbaar
              Aanbevelingen: extlinux maar het zal niet geïnstalleerd worden
              Aanbevelingen: unetbootin-translations maar het zal niet geïnstalleerd worden
              Aanbevelingen: gksu maar het is niet installeerbaar of
                             kdesudo maar het is niet installeerbaar
E: Kan problemen niet verhelpen, u houdt defecte pakketten vast.
paeschli@paeschli-pc:~$ sudo apt-get install woeusb
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De statusinformatie wordt gelezen... Klaar
Sommige pakketten konden niet geïnstalleerd worden. Dit kan betekenen
dat u om een onmogelijke situatie gevraagd heeft, of, indien u
de distributie 'unstable' gebruikt, dat sommige benodigde pakketten nog gemaakt moeten worden of uit 'Incoming' verwijderd werden.
De volgende informatie kan misschien helpen de situatie op te lossen:

De volgende pakketten hebben niet-voldane vereisten:
 woeusb : Vereisten: libwxgtk3.0-0v5 (>= 3.0.4+dfsg) maar het is niet installeerbaar
E: Kan problemen niet verhelpen, u houdt defecte pakketten vast.
paeschli@paeschli-pc:~$

---

### Post by CelticWarrior on 2020-05-05
WoeUSB works. I've tested it with the latest Microsoft ISOs successfully.
Unetbootin? Probably not. Microsoft for some time now is publishing non-standard ISOs that rendered many tools unusable for the purpose and, on top of that, the very latest ones contains at least one huge file that requires special settings (NTFS, in a nutshell).

Here are the instructions: [https://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu](https://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu) . But that's not all. [B]You need to select NTFS or it will fail.
[/B]
PS - Except in the LoCo subsection this forum is English only. So, even when posting some terminal output please do so in English: Use "LANG=C" before issuing other commands in order to have the output in English for everything until the end of that terminal session.

---

### Post by ActionParsnip on 2020-05-05
What is the output of:

```

lsb_release -a; uname -a; apt-cache policy unetbootin

```

Thanks

---

### Post by yancek on 2020-05-05
Unetbootin is designed specifically to create bootable Linux systems on a usb and was never meant to use another OS, quote below directly from their home page.  If woeusb doesn't work for you the method described in the link in post2 works, used it with no problems.

> UNetbootin allows you to create bootable Live USB drives for Ubuntu and other Linux distributions .   ISO files for non-Linux operating systems have a different boot mechanism, so don't expect them to work either. 

---

### Post by sudodus on 2020-05-05
**woeusb** has been quite reliable, but recently there is a problem. See [**this link to AskUbuntu**](https://askubuntu.com/questions/1097560/woeusb-error-code-256-with-ntfs-formatted-usb/1098185#1098185)

and scroll down to

> Edit 3:

There is a problem in Ubuntu 20.04 LTS

...

Until this problem with woeusb is solved, you can use mkusb-plug according to this link:

[**help.ubuntu.com/community/mkusb/plug**](https://help.ubuntu.com/community/mkusb/plug)


or [**do it yourself according to this link**](https://help.ubuntu.com/community/Installation/iso2usb/diy/windows-installer-for-big-files)

---

### Post by kurt18947 on 2020-05-06
I think when I downloaded Windows some months ago I used Microsoft's online tool. It seemed to work fine. When I first experimented with Linux distros I used Unetbootin and it worked fine. Then it quit working for some period of time so I quit using it in Linux. I think Unetbootin worked okay in Windows.

---

### Post by kurt18947 on 2020-05-06
> **CelticWarrior said:**
> WoeUSB works. I've tested it with the latest Microsoft ISOs successfully.
Unetbootin? Probably not. Microsoft for some time now **is publishing non-standard ISOs **that rendered many tools unusable for the purpose and, on top of that, the very latest ones contains at least one huge file that requires special settings (NTFS, in a nutshell).
<snip>


Microsoft publishing something non-standard?!!! Say it ain't so!

---

### Post by guiverc on 2020-05-06
> **paeschli said:**
> De volgende pakketten hebben niet-voldane vereisten:
 woeusb : Vereisten: libwxgtk3.0-0v5 (>= 3.0.4+dfsg) maar het is niet installeerbaar
E: Kan problemen niet verhelpen, u houdt defecte pakketten vast.
paeschli@paeschli-pc:~$


You didn't saw what release you are using, however the wanted file is available for 19.10 (eoan)

[https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=ibwxgtk3.0-0v5](https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=ibwxgtk3.0-0v5)


I also note what appears to be a held broken packages, possible from prior commands, so `sudo apt -f install` fixes, or if it doesn't fix the issue usually provides clue as to fix.  Your release though is the starting point

---

