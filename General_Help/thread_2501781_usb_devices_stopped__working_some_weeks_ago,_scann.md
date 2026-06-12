---
title: "usb devices stopped  working some weeks ago, scanner and webcam do not work"
date: 2024-10-20
forum: General Help
---

### Post by catastrophix2 on 2024-10-20
My scanner and webcam were working fine some weeks ago and now both of them do not work anymore. Nothing changed in the hardware. I spent many hourse trying to debug them individually. I lost many hours trying to find a fix among the old one that should not work anymore and the new messages but everything I tried change seomthing. . I began to wonder if this is not a security feature that block them  

The devices are detected by the usb low level function and I can see them in applications but cannot use them. The document scanner see the scanner and comeback with an error that it cannot connect to it. the webcam is seen in application but show black screen I have tried different applications for both like zoom and discord for the webcam. Those applications were working before. I have already look ar the rights for foilders like /dev/video0 and nothing changed. I tried uninstalling applications and reinstalling them 

I look in the ubuntu app setting. the apps have the access right slider in the good position to access everything they have listed

lsusb show the devices 
Bus 001 Device 004: ID 04a5:2060 Acer Peripherals Inc. (now BenQ Corp.) Prisa 620U+/640U
Bus 001 Device 005: ID 046d:085c Logitech, Inc. C922 Pro Stream Webcam

lshw see them 

             *-usb:2 NON-RÉCLAMÉ
                   description: Périphérique USB générique
                   produit: FlatbedScanner 13
                   fabricant: Color
                   identifiant matériel: 9
                   information bus: usb@1:9
                   version: 1.00
                   fonctionnalités: usb-1.00
                   configuration : maxpower=100mA speed=12Mbit/s
              *-usb:3
                   description: Vidéo
                   produit: C922 Pro Stream Webcam
                   fabricant: Logitech, Inc.
                   identifiant matériel: a
                   information bus: usb@1:a
                   version: 0.16
                   numéro de série: D055DEEF
                   fonctionnalités: usb-2.00
                   configuration : driver=snd-usb-audio maxpower=500mA speed=480Mbit/s

v4l2-ctl 
Driver Info:
    Driver name      : uvcvideo
    Card type        : C922 Pro Stream Webcam
    Bus info         : usb-0000:00:14.0-10
    Driver version   : 6.8.12
    Capabilities     : 0x84a00001
        Video Capture
        Metadata Capture
        Streaming
        Extended Pix Format
        Device Capabilities
    Device Caps      : 0x04200001
        Video Capture
        Streaming
        Extended Pix Format
Media Driver Info:
    Driver name      : uvcvideo
    Model            : C922 Pro Stream Webcam
    Serial           : D055DEEF
    Bus info         : usb-0000:00:14.0-10
    Media version    : 6.8.12
    Hardware revision: 0x00000016 (22)
    Driver version   : 6.8.12


ffplay  -f v4l2 -i /dev/video1
gave me 
ioctl(VIDIOC_G_INPUT): Inappropriate ioctl for device /dev/video1: Inappropriate ioctl for device



I see hundreds of line or error in the logs  that apparmor block things like 

audit: type=1400 audit(1729451537.752:87323): apparmor="DENIED" operation="ptrace" class="ptrace" profile="snap.discord.discord" pid=9352 comm="Utils" requested_mask="read" denied_mask="read" peer="unconfined"

but I don't see specific one related to usb so I have no reason to think they are related . I don't see anything unusal in dmesg. 

What should I look at ?

---

### Post by Autodave on 2024-10-20
From a hardware viewpoint, are you using any USB hubs?  If so, disconnect them and then try you camera and scanner one at a time.  Also, you may be having a power supply problem with the 5V output.

---

