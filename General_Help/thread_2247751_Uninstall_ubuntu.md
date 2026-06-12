---
title: "Uninstall ubuntu"
date: 2014-10-10
forum: General Help
---

### Post by josh98 on 2014-10-10
Heyya! So For the past 5 hours i have been trying to get rid of ubuntu.... yes i'm sorry but my son can't play one of his favourite games and it kills me to not let him play it. I need to reinstall windows again. I have tried using winusb but it doesnt let me for some reason. I have tried so much stuff. I have the windows 7 iso file ready to install. I have tested it and it works in a virtual machiene. I just want to get windows back as my main os. Would someone be able to help me as I am not very computer savvy. I can download team viewer or a program alike if you are able to help me. Please please help me i am so frustruated.

---

### Post by mörgæs on 2014-10-10
Did you ask in the gaming forum for advice about getting the game running?

---

### Post by sudodus on 2014-10-10
Too bad that you cannot continue with Ubuntu.

Anyway, you need not uninstall it. Just let Windows grab the whole drive, when you start installing it! Then Windows will overwrite Ubuntu's bootloader, partition table and replace the partitions with Windows partitions (also known as drives in the Windows jargon).

---

### Post by mikewhatever on 2014-10-10
What do you mean by "it doesn't let me"? Why not? What happens? Were you able to boot from USB?

---

### Post by josh98 on 2014-10-10
> **mikewhatever said:**
> What do you mean by "it doesn't let me"? Why not? What happens? Were you able to boot from USB?

Here is what the usb looks likes after using winusb [[IMG]http://s27.postimg.org/ov3jeth8z/Screenshot_from_2014_10_10_20_14_29.png[/IMG]]("http://postimg.org/image/mdrs7jxcf/full/")

Apparently it had something on it, so I went onto my wifes laptop and was able to erase everything then i was able to install windows on it (i think)

after using winusb i got this message

Installation failed !
Exit code: 512
Log:
Formating device...
Mounting...
mount: block device /media/josh/HP SimpleSave/aaaa.iso is write-protected, mounting read-only
Copying...
cp: error reading &#8216;./efi/microsoft/boot/bcd&#8217;: Input/output error
cp: failed to extend &#8216;/media/winusb_target_1412932114_2696/./efi/microsoft/boot/bcd&#8217;: Input/output error
Error occured !
Syncing...
Cleaning...
/usr/bin/winusb: line 78:  3065 Terminated              while true; do
    sleep 0.05; echo 'pulse';
done
Umounting and removing '/media/winusb_iso_1412932114_2696'...
Umounting and removing '/media/winusb_target_1412932114_2696'...

EDIT: 

tried booting from usb and got a windows screen telling me to insert my windows installation disk...

EDIT:

this iso file works on virtual box... i love ubuntu and would hate to see it go. but also another problem was not being able to acces my usb drives whilst on the virtual box, if someone can help me with that then i can keep ubuntu and let my son play his games.

---

### Post by ian-weisser on 2014-10-10
> **josh98 said:**
> not being able to acces my usb drives whilst on the virtual box

Hmmmm. I can access USB from Virtualbox in 14.04 without problem.
That feature was added years ago.
Have you enabled USB in the VB settings?

---

### Post by mikewhatever on 2014-10-10
Well, I am not familiar with winusb, but if it doesn't work for you, burn the ISO to a DVD, or ask on a Windows forums how to make an installation media properly.

---

### Post by yancek on 2014-10-10
Googling winusb I get this definition:  WinUSB is a generic USB driver provided by Microsoft, so I don't think it does what you want but I've never used it.  The microsoft site below goes into detail:

[http://msdn.microsoft.com/en-us/library/windows/hardware/ff540174(v=vs.85).aspx](http://msdn.microsoft.com/en-us/library/windows/hardware/ff540174(v=vs.85).aspx)

---

