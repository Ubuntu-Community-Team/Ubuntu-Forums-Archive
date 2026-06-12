---
title: "How to extract Ubuntu from a DVD containing also other softwares?"
date: 2016-12-17
forum: General Help
---

### Post by arashk on 2016-12-17
[COLOR=#111111][FONT=Ubuntu]I have a DVD containing many softwares. It has an Ubuntu too, as bootable. I want to extract only Ubuntu and then make its ISO file and then put it on a USB. How can I extract [/FONT][/COLOR]**only Ubuntu**[COLOR=#111111][FONT=Ubuntu] from DVD?

(A picture of the main folder of the DVD is sttached.)[/FONT][/COLOR]

---

### Post by howefield on 2016-12-17
Thread moved to the "*General Help*" forum.

---

### Post by coffeecat on 2016-12-17
What is the DVD, and what is the release number of Ubuntu in it? Looking at the dates of the folders in your screenshot, I would hazard a guess that the version of Ubuntu is 12.10, which is hopelessly out of date now and long past its end-of-life. That is, unsupported.

Apart from extracting a pure Ubuntu ISO from a third-party DVD, what are you trying to achieve? Do you want to acquire an ISO of Ubuntu in order to install it? If so, you would be advised to find a supported version. Tell us what you want in the long run and we can go from there.

Also - your screenshot looks as though it is from Windows. Do you have any experience of installing and using Ubuntu?

---

### Post by arashk on 2016-12-17
> **coffeecat said:**
> What is the DVD, and what is the release number of Ubuntu in it? Looking at the dates of the folders in your screenshot, I would hazard a guess that the version of Ubuntu is 12.10, which is hopelessly out of date now and long past its end-of-life. That is, unsupported.

Apart from extracting a pure Ubuntu ISO from a third-party DVD, what are you trying to achieve? Do you want to acquire an ISO of Ubuntu in order to install it? If so, you would be advised to find a supported version. Tell us what you want in the long run and we can go from there.

Also - your screenshot looks as though it is from Windows. Do you have any experience of installing and using Ubuntu?
The DVD is a pack of softwares. Its bootable part is ubuntu.
Because I only want to use ubuntu for booting from usb, I do not need an up to date version. I cannot download an up to date version. For now, I need ubuntu for a limited use.

I am trying to achieve an ISO of Ubuntu to boot it from USB, not to install on HDD. For now, I cannot find or download a supported version. I am in a hurry.

I have some experience in using Ubuntu.

Now can you tell how to extract the Ubuntu from the DVD?

---

### Post by sudodus on 2016-12-17
I agree with *coffeecat*, that it is a bad idea to run an operating system, that has passed end of life. I would avoid it even as a live system except for testing. But if you have no choice, and cannot download a current version, here is how you can extract it in Ubuntu.

0. You need a target drive of at least the same size as the used part of the DVD disk. An 8 GB drive will be big enough. Maybe a 4 GB drive is big enough, but you must check with the DVD disk inserted, in linux with the command line

```
sudo lsblk -m /dev/sr?
```

1. Boot from the DVD. I hope that the old 12.10 can run dus. I know that 12.04 LTS can do it, so it 'should' work.

2. Install ***guidus*** according to the instructions at this link: [help.ubuntu.com/community/mkusb/gui](https://help.ubuntu.com/community/mkusb/gui) **from phillw.net**.

Download the shell-script file mkusb-installer with the browser or do it directly from a terminal window with

```
wget http://phillw.net/isos/linux-tools/mkusb/mkusb-installer
```

and run it from a terminal window with

```
bash mkusb-installer
...
[sudo] password:
...
Install via ppa or wget, uninstall or quit? (p/w/u/Q) w
...
```

Guidus and ***dus*** can do the job for us. It can extract the system from the same DVD as the computer is booted from.

3. Extract the whole DVD to a USB pendrive or memory card or hard disk drive. Start with the following command line in a terminal window

```
dus /dev/sr0
```

Usually the DVD drive is seen as /dev/sr0. Modify if necessary.

When ***dus*** has started, Select [Install], Clone, the target device, and Go ...

-o-

To do the corresponding thing in Windows, you need a cloning tool, that can write from the DVD disk to a USB drive. It is also possible to do it in two steps. First make an image file from the DVD disk to the internal drive. Then write from the image file to the USB drive. At least the last step can be done with [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb).

---

### Post by arashk on 2016-12-18
> **sudodus said:**
> I agree with *coffeecat*, that it is a bad idea to run an operating system, that has passed end of life. I would avoid it even as a live system except for testing. But if you have no choice, and cannot download a current version, here is how you can extract it in Ubuntu.

0. You need a target drive of at least the same size as the used part of the DVD disk. An 8 GB drive will be big enough. Maybe a 4 GB drive is big enough, but you must check with the DVD disk inserted, in linux with the command line

```
sudo lsblk -m /dev/sr?
```
...
.

Thank you for this tutorial, BUT I do **not** want to Extract the **whole** DVD to a USB (That is a cinch for me.). As I said in the first post, I want to [COLOR=#111111][FONT=Ubuntu]extract [/FONT][/COLOR]**only Ubuntu[COLOR=#111111][FONT=Ubuntu][/FONT][/COLOR]**[COLOR=#111111][FONT=Ubuntu] from DVD[/FONT][/COLOR]**[COLOR=#111111][FONT=Ubuntu].[/FONT][/COLOR]**

---

### Post by sudodus on 2016-12-18
It is difficult to do that. I don't think I can help you.

---

### Post by arashk on 2016-12-18
> **sudodus said:**
> It is difficult to do that. I don't think I can help you.

Is there such a thing as mini ubuntu?

---

### Post by sudodus on 2016-12-18
Yes. See this link,

[mini.iso, minimal install, netboot iso](https://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730)

---

### Post by arashk on 2016-12-19
> **sudodus said:**
> Yes. See this link,

[mini.iso, minimal install, netboot iso]("https://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730")

Thank you.

1. lubuntu ISOs are smaller than ubuntu ISOs. What are the important differences between lubuntu and ubuntu?

2. Apart from support period, which one is better, Ubuntu LTS or Ubuntu standard?

---

### Post by coffeecat on 2016-12-19
> **arashk said:**
> 1. lubuntu ISOs are smaller than ubuntu ISOs. What are the important differences between lubuntu and ubuntu?

2. Apart from support period, which one is better, Ubuntu LTS or Ubuntu standard?

@arashk, these questions have strayed far beyond your original one. If you need answers, please start a new thread in an appropriate sub-forum.

Please be aware that questions about the differences between different flavours of Ubuntu, and the pros and cons of LTS and non-LTS, have been asked on this forum (and in many other places) so often that we have a special place for them and similar topics: [Recurring Discussions](https://ubuntuforums.org/forumdisplay.php?f=302)

You would help yourself and do other members a courtesy by researching both those questions before starting new threads, so that you have a better overview of the subject and are better able to pose focused questions. Members need to know what you need in terms of the functionality of the operating system, available software, and so on, as well as what sort of hardware you intend to run Ubuntu or a variant on.

---

