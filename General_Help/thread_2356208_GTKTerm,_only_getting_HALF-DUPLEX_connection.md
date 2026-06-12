---
title: "GTKTerm, only getting HALF-DUPLEX connection?"
date: 2017-03-20
forum: General Help
---

### Post by john_ladasky on 2017-03-20
Hi there,

I'm doing embedded systems development.  My main computer runs Ubuntu 16.04.  A few weeks ago I upgraded to 16.04.2.  This might be relevant to my problem.

My embedded computers (I have more than one) are Nordic nRF52 evaluation boards.  There's a USB/UART chip on board.  My software communicates over that link.  Or at least, it used to.  I've been using GTKTerm as my serial interface.  I have some programs which just transmit from the peripheral to the central computer.  Others receive input characters.  About 80% of the time, I'm not receiving any data from the peripheral.  

However, 100% of the time, I can transmit.  I can type characters into a GTKTerm window that looks like it isn't working, and those characters will be received by embedded system.  Example: I have a program that runs a timer on the embedded computer.  I can adjust the timer frequency up or down by typing the "1" or "2" keys on my desktop machine.  I can watch the timer frequency change when I type.  I'm also supposed to get feedback over the UART: "Frequency = <xxx> kHz."  That doesn't happen.  It used to work.

I have been going round and round all day, looking for bugs in programs I assumed were working, trying different sequences of starting up the embedded computer and GTKTerm, adjusting the baud rate down, inserting long delays into my programs in case I was overrunning a buffer, etc.  Keep in mind that I have multiple embedded computers to try.  I can change devices without correcting the problem.

Is there something that I don't understand about GTKTerm?  Is there a change in the version of GTKTerm that accompanied 16.04.2?  Is there another way that I can troubleshoot my problem?  

Thanks for any suggestions!

---

### Post by alexandari on 2017-03-21
How about using xterm? Did you try that?

---

### Post by john_ladasky on 2017-03-21
Thanks for your suggestion, Alexandari.  I may not have to try it.  Here's a follow-up note, I might have had a hardware problem.  

I had my cell phone plugged into the same USB hub that I use to connect to my peripherals.  Yesterday evening I noticed that my phone failed to charge.  Today I tried plugging my USB hub into a different port on the back of my computer.  My UART seems to be working again, and my phone is charging.  

I will continue to monitor the situation, since the problem was intermittent in nature.

---

### Post by john_ladasky on 2017-03-28
Well, now I have the reverse problem.  My Ubuntu box can now _receive_ dependably from the terminal, but I can no longer _transmit_ over the USB-UART link.  Stranger still, the USB connection to the single-wire debug (SWD) interface on the peripherals is working fine.  I can program the device, because programming is accomplished through the SWD.  But I can't talk to any of my peripheral's applications.

My cell phone is charging from the USB.  That may have been a red herring.

This is driving me crazy.  I have two identical peripherals, so the problem is unlikely to be in the peripheral.  I don't just have a broken UART.  I would have to have two broken UART's, and they would have to break (and unbreak) at the same time and in the same way.

I have tried multiple USB cables.  I thought that solved the problem once.  Then it went back to misbehaving.

I would like to try another computer (I'll get to that tomorrow).  In the mean time, I would like to try Alexandari's suggestion of using another terminal program besides gtkterm.  Does anyone know how to get xterm to talk to a serial port?  I read the help and I think the -S option is what I need, but somehow I don't seem to have the right syntax.

Thanks!

---

### Post by john_ladasky on 2017-07-21
Hello everyone,

I am reviving this thread that I started a few months back.  

As I reported before, my devices connect intermittently using Ubuntu 16.04.  I have another computer running Ubuntu 17.04 Gnome with the same problem.  The problems started between three and six months ago.

I have discovered that my devices are connecting very dependably, using Windows 7 and Windows 10 and putty as my UART interface.  The two computers that I am using for my tests are both dual-boot systems.  One is running Ubuntu 16.04 or Win7; the other is running Ubuntu 17.04 or Win10.  So there is no chance that the host system hardware has any effect.  This is a software problem.

The Nordic nRF52 development boards expose several different services over a single USB wire.  I have only been talking about the UART.  However, the dev boards also have a mass-storage device with some README files, and a service called JLink which is used to program the flash memory on the board.  The mass storage device and the JLink work 100% of the time, on every OS that I try.  

Based on these findings, I believe that I have a UART driver problem on Linux.  I would greatly appreciate any troubleshooting advice you can provide!  Thanks.

---

### Post by vocx on 2017-07-21
> **john_ladasky said:**
> Hello everyone,

I am reviving this thread that I started a few months back.  

I have discovered that my devices are connecting very dependably, using Windows 7 and Windows 10.  As I reported before, my devices connect intermittently using Ubuntu 16.04.  I have another computer running Ubuntu 17.04 Gnome with the same problem.  The problems started between three and six months ago.

The Nordic nRF52 development boards expose several different services over a single USB wire.  I have only been talking about the UART.  However, the dev boards also have a mass-storage device with some README files, and a service called JLink which is used to program the flash memory on the board.  The mass storage device and the JLink work 100% of the time, on every OS that I try.  

Based on these findings, I believe that I have **a UART driver problem on Linux**.  I would greatly appreciate any troubleshooting advice you can provide!  Thanks.
To be entirely honest, your issue sounds too advanced for the level of these forums. You are basically programming some C code, and using GTK+ libraries to communicate via serial port to another board, or something similar? That is a development question which requires experience using GTK+ and Linux. I have not seen any discussions about such topics in this forum. There is also a subforum on development and programming, but not even there have I seen any hardware engineers answering these kinds of questions.

My honest suggestion would be to check the documentation or source code of GTKTerm. You mentioned that the problem occurred as you changed from one version to the other, and that may be totally true. Things change all the time. I remember years ago, I was investigating some source code, I think it was the gtksourceviewer component of GTK+, and then realized that the new version changed the widget and now it behaved differently. So I strongly suggest you check the documentation, their website, mailing list, and even message the developers of the program to see if they have more clues. Also, it is totally possible to get older source code to compile, and compare against the newer version. Maybe in this way you can find where the changes were made that break the functionality that you were using.

That you found a bug in a driver of the actual Linux kernel, I think would be very difficult, as the kernel is worked on by many, many people who know a lot about hardware programming. That they messed up something that was working recently would have a very small chance.

---

### Post by john_ladasky on 2017-07-24
> **vocx said:**
> That you found a bug in a driver of the actual Linux kernel, I think would be very difficult, as the kernel is worked on by many, many people who know a lot about hardware programming. That they messed up something that was working recently would have a very small chance.

Thanks for your reply, vocx.  I will investigate other possibilities as you suggest, and place greater confidence in the kernel for now.

It looks like putty is available on Linux too.  I dislike putty, but I can make it work in Windows.  If putty also works on Linux, I've narrowed down the problem.

---

### Post by john_ladasky on 2017-07-25
Following up: PuTTY is working 100% on Windows 10.  Two or three retries are generally needed to establish a PuTTY connection from Linux.  I am taking care to use the exact same physical USB port on the computer, the same USB cable, and the same peripheral running the same program.  

This is not what I hoped to find.

---

