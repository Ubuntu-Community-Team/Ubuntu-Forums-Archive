---
title: "The only reason I got to boot into windows..."
date: 2008-01-13
forum: General Help
---

### Post by dracker on 2008-01-13
My webcam... 
I want to make this work since it's the only reason I have atm to boot into windows... please help!; when I plug the camera in I have nothing.. when I put lsusb on the console I get this:

```

Bus 001 Device 002: ID 093a:2608 Pixart Imaging, Inc. 

```

And when I try camorama it says "Could not  connect to video device (/dev/video0). Please check connection".
Can you give me a detailed guide.. I'm still kind of new in Ubuntu.
Thank you :)

---

### Post by Nexusx6 on 2008-01-14
Try this guide:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by articpenguin on 2008-01-14
firewire webcams usually have better hardware support than webcam support. I cant get my panasonic DV camera to work on USB but it works on firewire.

---

### Post by linuxwizard on 2008-01-14
That webcam is supported > 10 up from bottom shows your cam > [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) > Try using Ekiga see if it detects your webcam

---

### Post by dracker on 2008-01-20
I followed the instructions but I have a question... how do I load the gspcav1 driver into memory to plug my cam? I can't find that :S... thank you

---

### Post by onidlo on 2008-01-22
Hi, 

I think I have the same webcam and I got it to work;-). Although, the quality of the image is very poor.

So, first of all, check if you have exactly the same webcam, by typing lsusb to console:

Bus 003 Device 006: ID 093a:2608 Pixart Imaging, Inc.

Then download the latest source code of GSPCA from:
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Unpack them somewhere and go to the directory with source code and type:

```
make
sudo make install

```

Then load the module:

```
sudo modprobe gspca

```

If the module loads correctly, you should get something like:

```
lsmod | grep spca
gspca                 681168  0
videodev               29312  1 gspca
usbcore               138632  8 gspca,snd_usb_audio,snd_usb_lib,usbserial,hci_usb,ehci_hcd,uhci_hcd

```

And now you can plug-in the webcam. To test, if it works, try:

```
ls /dev/video*
or
dmesg|tail -30

```

---

### Post by onidlo on 2008-01-22
If you want to improve the quality of the image, go to:

[http://www.kaiser-linux.li/index.php/PAC7311](http://www.kaiser-linux.li/index.php/PAC7311)

and apply "2008-01-10" patch...:lolflag:

---

### Post by dracker on 2008-01-23
@onidlo: Thank you for your guide! I feel I'm close now, but 
```

ls /dev/video*

```
returns
```

ls: /dev/video*: No existe el fichero ó directorio
(there's no such directory in english)

```
And
```

dmesg|tail -30

```
returns
```

[  484.488000] Linux video capture interface: v2.00
[  484.520000] usbcore: registered new interface driver gspca
[  484.520000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered


```

I guess the last part is ok.. since it identifies my camera, but there is no /dev/video... can you please help me? I haven't try the patch jet.

---

### Post by p221072 on 2008-03-04
Hi,
I followed all the steps.
This is what I've got [trust wp3300p]:

```
paolo@Moon:~/gspcav1-20071224$ lsusb
Bus 004 Device 002: ID 0766:0001 Jess-Link Products Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 093a:2608 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000 

```
...at the end of all the instructions...

```
paolo@Moon:~/gspcav1-20071224$ lsmod | grep gspca
gspca                 608336  0 
videodev               29312  1 gspca
usbcore               138632  8 gspca,snd_usb_audio,snd_usb_lib,usb_storage,libusual,ehci_hcd,uhci_hcd

```
but still:
```
paolo@Moon:~/gspcav1-20071224$ ls /dev/vid*
ls: /dev/vid*: No such file or directory
```

this is the end of a dmesg:

```
[ 8310.368000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 8310.604000] usb 1-1: configuration #1 chosen from 1 choice
```

and I cannot find any device with any application, ie Ekiga or Skype 2

any help?
Thanks,
Paolo

---

### Post by p221072 on 2008-03-05
Update:
changing **usb** port the webcam started working!
The quality is very low compared to the win driver.
Any suggestion to increase luminosity and quality?
Thanks,
Paolo

---

### Post by linuxwizard on 2008-03-05
Which apps. have you tried with your webcam ? Some may work better than other apps.

---

### Post by p221072 on 2008-03-06
Hi,
I've tryed:

[LIST]
Skype 2 - I know it's not the best application for a test but it is what I would use more. In the options there are no settings for the webcam;[/LIST]
[LIST]Cheese - Also here the quality is below aspectations and I couldn't find any settings;
[/LIST]

Is there any software to make some general changes to the video device settings?
Or a better driver than gspca?
Thanks for the support,
Paolo

---

### Post by linuxwizard on 2008-03-06
Try using Ekiga & Camorama. In Kubuntu I use Kopete. They are the only ones I use. Their are setting adjustments in them so you can work with color & brightness.  IMO Cheese is a waste of time nothing you can adjust. My cam looks bad in Cheese. I don't use Skype so I don't know much about it but I saw a post that stated that their were no adjustments for the webcam. Some cams works better than other with gspca that's all their is for your cam.

---

### Post by p221072 on 2008-03-07
Thank you for the support, I will try Ekiga.
Anyway as from the subject of the thread, this will keep me booting into Windows :(
All my friends and relatives use Skype, so I don't have much of a choice.
Cheers,
Paolo

---

### Post by p221072 on 2008-03-13
I've tried Ekiga, the quality is still very bad.
Now I can adjust the settings, but the image is flickering and colours are terrible.
Is there any chance to find better drivers or I'd better change webcam? ( The one I have is very cheap, though working good under win)

---

### Post by linuxwizard on 2008-03-13
Some cams works better than others in Linux just because of the drivers.Just like a webcam will work better in one program better than another. I would say their is no other driver you can use for your webcam. Buying another webcam is going to be up to you. Can you live with the quality of the picture you have in Linux? Where do you use your cam the most Linux or M$ ?

---

### Post by kegie on 2008-05-23
Does anyone have that "2008-01-10" patch from [http://www.kaiser-linux.li/index.php/PAC7311](http://www.kaiser-linux.li/index.php/PAC7311) ? The site is down :(

---

