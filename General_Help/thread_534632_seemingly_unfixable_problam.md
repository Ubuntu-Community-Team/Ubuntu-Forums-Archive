---
title: "seemingly unfixable problam"
date: 2007-08-25
forum: General Help
---

### Post by joeyea on 2007-08-25
ive been using linux for about a year now and ever since i put linux on this pc ive this same problem (this is including other distributions).
i think it happen anytime but it seems it happens most while using a browser. apart from that there is no other common theme. 
now for the problem, what happens is the screen instantaniusly (sorry about spelling) goes the general colour of the window at the time but really stripy with lines of colour going down that are similer to the colour of the window. it looks like someone has dragged the top of the screen downwards.
if anyone wants a pic ill send it 

any help would be appreciated 

thx joeyea

---

### Post by SOULRiDER on 2007-08-25
Have you tried with other browsers? And is it only in sites with  flash? Flash can do some really odd things, at least it does for me....

---

### Post by ddrichardson on 2007-08-25
Post a pic - i'm intrigued.

---

### Post by Scunizi on 2007-08-25
Sounds like your video card isn't set up correctly. Maybe too high of a verticle refresh rate.. Check you settings in /etc/X11/xorg.conf against what refresh rate the monitor should support.

---

### Post by joeyea on 2007-08-26
it happens on all browsers including when browsing files using konquer so i dont think its flash. i will check the xorg file but ive had 2 different screens and its happend on both.

ill post an image next

---

### Post by kerry_s on 2007-08-26
your most likely using the "vesa" driver, you need to set it up with your card driver.

in terminal->

sudo dpkg-reconfigure -phigh xserver-xorg

then log out & press ctrl+alt+backspace to restart the xserver.

---

### Post by joeyea on 2007-08-26
thanks ill try that, here's a picture anyway.

[http://img254.imageshack.us/img254/5454/image00002pn2.jpg](http://img254.imageshack.us/img254/5454/image00002pn2.jpg)

its different every time

---

### Post by joeyea on 2007-08-26
i did what you said and changed the driver to via (my card). but it still does the problem and it messed up my reselution and i dont know how to change it back.

thx

joeyea

---

### Post by joeyea on 2007-08-29
bump

---

### Post by Scunizi on 2007-08-29
Ok.. here's my thoughts on this issue. Your card is still not configured correctly; Your card is exibiting failure problems; Your card is overheating.  If this card is built on the motherboard all of the above could still apply.  If you have a different card available to you and a slot on the motherboard, I suggest doing a swap and see what happens.

---

### Post by Scunizi on 2007-08-29
I totally missread you last post .. so here's an update I hope will address your problem.   You said your card was Via.. unless I'm mistaken, that's usually a chipset on the motherboard and not your video card.  It's usually a nVidia, Ati or Intel i8xx or i9xx.  Intel cards typically built on the motherboard.  What is the actual card emulation name?

---

### Post by joeyea on 2007-08-31
x

---

### Post by kesman on 2007-08-31
are your screen specs added correctly in the xorg.conf ? I mean vertical and horizontal sync rates? Try to find that information from your screens manufactrer website or manual or whatever and edit your xorg.conf -file to correctly use the screen.

---

### Post by joeyea on 2007-08-31
how do i find the emulation name?

i changed the refresh rates so im yet to see if that has made a difference

---

### Post by soxs on 2007-08-31
try ```
lspci
``` and search for something that sounds like via/nVidea/ati/intel

---

### Post by joeyea on 2007-08-31
this is the output of lspci:

```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

```


and unfortunatly although i changed the refresh rates it still does the problem.

thx for the help 
joeyea

---

### Post by joeyea on 2007-09-01
bump

---

### Post by joeyea on 2007-09-03
bumb :(

---

### Post by ddrichardson on 2007-09-03
Just a refresher for me:

Is this problem only in X? Text mode is OK? If you have Windows installed is all OK? Do you at present have a working X at all?

---

### Post by joeyea on 2007-09-04
This is only in x. I only had windows on it for about 5 mins so im not sure but when i had fedora on it it still happened.

I figured out that it happened when i was booted from the ubuntu live cd, so im going to burn suse and see if it still happens. (im pretty it certian it will though)

---

### Post by joeyea on 2007-09-06
I've now installed suse on it but it still happened so now ive got windows and ubuntu dualbooting (have to configure my wireless again :( ).
It dosnt seem to have happened on windows yet which suggests it is software based rather than a problem with the card but im still supsicious of the card.

thx for any futher help

---

### Post by joeyea on 2007-09-08
bumb

---

### Post by joeyea on 2007-09-11
bumb :(

---

### Post by joeyea on 2007-09-12
bump :confused: 

is anyone gonna put anything forward or should i change the name to "unfixable problem"?

---

