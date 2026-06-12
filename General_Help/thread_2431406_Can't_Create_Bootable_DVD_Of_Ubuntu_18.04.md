---
title: "Can't Create Bootable DVD Of Ubuntu 18.04"
date: 2019-11-16
forum: General Help
---

### Post by John_Patrick_Mason on 2019-11-16
Hi everyone,

Not sure if this is a case of a failing CD/DVD  drive, but for some reason, I can't seem to be able to create a bootable  DVD of Ubuntu 18.04.

Usually, when I want to create a bootable DVD, I  use K3b as I've heard that Brasero can be quite buggy, but, for whatever  reason, now, when I choose to check "verify written data" before burning  the ISO file to the DVD, the burning fails.

I've already tried three  consecutive times to create a live DVD using a blank DVD+R disc, and  every time, at least when I made sure to check the "verify written data"  box, the burning fails midway, and I get an error pop-up that says,  "Found medium. No medium information. Please insert a suitable medium  into drive." I've successfully managed to create bootable live DVDs of  Ubuntu in the past, using these same blank DVD+Rs, so I don't think it's  a problem with the blank DVDs.

When the burning of the ISO fails, after  I've checked the "verify written data box," K3b will also show a  message saying, "Writing successfully completed. Retrieving all CSS  keys. This might take a while. Failed to retrieve all CSS keys. Video  DVD decryption failed." If I don't check the "verify written data" box,  burning seems to work fine. However, when I try to boot from the live  DVD after changing to boot order in the BIOS, my computer won't boot  from the DVD, and will go directly to GRUB and Ubuntu.

I should also say that I'm under Ubuntu 16.04.

---

### Post by scdbackup on 2019-11-16
Hi,

i fail to find the message text
  "Found medium. No medium information. Please insert a suitable medium into drive."
in
  [https://sources.debian.org/src/brasero/3.12.2-6/](https://sources.debian.org/src/brasero/3.12.2-6/)
In the middle of the burn run, this is a strange text.

What kind of burner drive do you have ? Is it perhaps a USB laptop drive
which pulls its power from the USB cable and thus has no separate power
supply ? If so, plug it into a USB 3 port for better voltage stability.

If not, what do you get from these terminal commands while a blank DVD+R
is inserted:
```

xorriso -devices
xorriso -outdev /dev/sr0 -toc

```

For more tangible error messages, consider to do this burn run:
```

xorriso -as cdrecord -v dev=/dev/sr0 -eject ...file.path.of.ISO...

```
where "...file.path.of.ISO..." is the path by which the program can find
your ISO image file.

Checkreading on media level:
```

xorriso -indev /dev/sr0 -check_media --

```

You may verify the burnt DVD by the SHA256 checksum from Ubuntu which
you obtain as described in
  [https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

The decisive point is to restrict the checksumming to the size of the
ISO image, because else you get trailing garbage from the end of the DVD.

  [https://www.debian.org/CD/faq/#verify](https://www.debian.org/CD/faq/#verify)
proposes to learn the sector count by
```

/sbin/isosize -x /dev/sr0

```
and to use it as parameter of program "dd" to read exactly the right number
of bytes from DVD. Let's assume you see as result
```

sector count: 1024000, sector size: 2048

```
Then run this
```

dd if=/dev/sr0 count=1024000 bs=2048 | sha256sum

```
and compare the resulting hex string with the downloaded Ubuntu SHA256.

Have a nice day :)

Thomas

---

### Post by John_Patrick_Mason on 2019-11-16
[QUOTE=scdbackup]Hi,

i fail to find the message text
  "Found medium. No medium information. Please insert a suitable medium into drive."
in
  [https://sources.debian.org/src/brasero/3.12.2-6/](https://sources.debian.org/src/brasero/3.12.2-6/)
In the middle of the burn run, this is a strange text.[/QUOTE]

Uhmm, just to be clear. If you reread my post, you'll notice that I used K3b, instead of Brasero.

I'll have to try out the rest of the instructions in your post, tomorrow, as it's getting really late here.

---

### Post by scdbackup on 2019-11-16
Hi,

> Uhmm, just to be clear. If you reread my post, you'll notice that
> I used K3b, instead of Brasero.

Oops. Sorry. 
  [https://codesearch.debian.net/search?q=package%3Ak3b+No+medium+information](https://codesearch.debian.net/search?q=package%3Ak3b+No+medium+information).
yields
  [https://sources.debian.org/src/k3b/18.08.1-1/libk3b/tools/k3bmedium.cpp/?hl=354#L354](https://sources.debian.org/src/k3b/18.08.1-1/libk3b/tools/k3bmedium.cpp/?hl=354#L354)

This is where K3B reports about the medium in the drive. It should not do
it in the middle of a burn run. The medium state is unknown, although this
should have been examined already before the burn run begins.

Internally the trigger for the message is the evaluation
Device::STATE_UNKNOWN. Possible reasons are:

- Inability to open the device file:
  [https://sources.debian.org/src/k3b/18.08.1-1/libk3bdevice/k3bdevice.cpp/?hl=741#L744](https://sources.debian.org/src/k3b/18.08.1-1/libk3bdevice/k3bdevice.cpp/?hl=741#L744)

- Unknown inf->status after execution of the SCSI command READ DISC
  INFORMATION.
  [https://sources.debian.org/src/k3b/18.08.1-1/libk3bdevice/k3bdevice.cpp/?hl=761#L761](https://sources.debian.org/src/k3b/18.08.1-1/libk3bdevice/k3bdevice.cpp/?hl=761#L761)
  [https://sources.debian.org/src/k3b/18.08.1-1/libk3bdevice/k3bdevice.cpp/?hl=1934#L1934](https://sources.debian.org/src/k3b/18.08.1-1/libk3bdevice/k3bdevice.cpp/?hl=1934#L1934)
  Here we learn that STATE_EMPTY, STATE_INCOMPLETE, STATE_COMPLETE, and
  STATE_UNKNOWN is about the content state of the medium: Blank, Appendable,
  Closed, and Other.
  MMC-5 specifies: "Empty Disc", "Incomplete Disc", "Finalized", and "Others"
  "Others" means:
    "The currently mounted disc supports only random access writing and
     is not recordable serially in multiple sessions."
  That's not a valid state for a DVD+R. It could be appropriate for DVD+RW,
  formatted DVD-RW, and DVD-RAM.

This looks as if your drive had lost its knowledge of the medium.
If this happens after the burn run began, then it is a hardware problem.
Maybe something about power supply of the drive.

It would be interesting to see xorriso's assessment of a misburned DVD+R medium:
```

xorriso -outdev /dev/sr0 -toc

```

Have a nice day :)

Thomas

---

### Post by John_Patrick_Mason on 2019-11-16
[QUOTE=scdbackup]What kind of burner drive do you have ? Is it perhaps a USB laptop drive
which pulls its power from the USB cable and thus has no separate power
supply ?[/QUOTE]

It's not a USB CD/DVD drive. It's a laptop with  an embedded CD/DVD drive. The battery on the laptop is dead, so the  laptop is running directly from current, but that shouldn't matter as I  have successfully created live CDs without the battery using the same  DVD+Rs. So, it used to work.

```
xorriso -devices
```

and

```

xorriso -outdev /dev/sr0 -toc

```

both yield:

```
xorriso 1.4.2 : RockRidge filesystem manipulator, libburnia project.

Beginning to scan for devices ...
Full drive scan done
-----------------------------------------------------------------------------
0  -dev '/dev/sr0' rwrw-- :  'TSSTcorp' 'DVD+-RW TS-L633J' 
-----------------------------------------------------------------------------

```

and 

```

xorriso 1.4.2 : RockRidge filesystem manipulator, libburnia project.

xorriso : NOTE : Disc status unsuitable for writing
Drive current: -outdev '/dev/sr0'
Media current: is not recognizable
Media status : is not present
Drive current: -outdev '/dev/sr0'
Drive type   : vendor 'TSSTcorp' product 'DVD+-RW TS-L633J' revision 'D400'
Drive id     : 'R8126GNB467326  '
Media current: is not recognizable
Media status : is not present

```

respectively.

```

xorriso -as cdrecord -v dev=/dev/sr0 -eject /home/mason/Downloads/ubuntu-18.04.3-desktop-amd64.iso

```

doesn't seem to yield any errors, but I'll post the output anyway because I don't usually use the CLI to create my live CDs:

```

xorriso 1.4.2 : RockRidge filesystem manipulator, libburnia project.

Drive current: -outdev '/dev/sr0'
Media current: DVD+R
Media status : is blank
Media summary: 0 sessions, 0 data blocks, 0 data, 4483m free
Beginning to write data track.
xorriso : UPDATE : Thank you for being patient. Working since 0 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 1 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 2 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 3 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 4 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 5 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 6 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 7 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 8 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 9 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 10 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 11 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 12 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 13 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 14 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 15 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 16 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 17 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 18 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 19 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 20 seconds.
xorriso : UPDATE : Thank you for being patient. Working since 21 seconds.
xorriso : UPDATE :    0 of 1986 MB written (fifo 99%) [buf 100%]   0.0x.
xorriso : UPDATE :    0 of 1986 MB written (fifo 99%) [buf 100%]   0.7x.
xorriso : UPDATE :    0 of 1986 MB written (fifo 99%) [buf 100%]   0.0x.
xorriso : UPDATE :    1 of 1986 MB written (fifo 95%) [buf 100%]   0.2x.
xorriso : UPDATE :    2 of 1986 MB written (fifo 93%) [buf  87%]   0.8x.
xorriso : UPDATE :    6 of 1986 MB written (fifo 97%) [buf  99%]   3.5x.
xorriso : UPDATE :   11 of 1986 MB written (fifo 95%) [buf  99%]   3.4x.
xorriso : UPDATE :   16 of 1986 MB written (fifo 96%) [buf  99%]   3.5x.
xorriso : UPDATE :   20 of 1986 MB written (fifo 97%) [buf  99%]   3.5x.
xorriso : UPDATE :   25 of 1986 MB written (fifo 98%) [buf 100%]   3.5x.
xorriso : UPDATE :   29 of 1986 MB written (fifo 94%) [buf  99%]   3.5x.
xorriso : UPDATE :   34 of 1986 MB written (fifo 96%) [buf  99%]   3.5x.
xorriso : UPDATE :   39 of 1986 MB written (fifo 98%) [buf  99%]   3.5x.
xorriso : UPDATE :   43 of 1986 MB written (fifo 94%) [buf  99%]   3.5x.
xorriso : UPDATE :   48 of 1986 MB written (fifo 94%) [buf  99%]   3.5x.
xorriso : UPDATE :   53 of 1986 MB written (fifo 96%) [buf  99%]   3.5x.
xorriso : UPDATE :   57 of 1986 MB written (fifo 97%) [buf  99%]   3.5x.
xorriso : UPDATE :   62 of 1986 MB written (fifo 96%) [buf  99%]   3.6x.
xorriso : UPDATE :   67 of 1986 MB written (fifo 98%) [buf  99%]   3.6x.
xorriso : UPDATE :   72 of 1986 MB written (fifo 93%) [buf  99%]   3.6x.
xorriso : UPDATE :   76 of 1986 MB written (fifo 99%) [buf  99%]   3.6x.
xorriso : UPDATE :   81 of 1986 MB written (fifo 94%) [buf  99%]   3.6x.
xorriso : UPDATE :   86 of 1986 MB written (fifo 97%) [buf  99%]   3.6x.
xorriso : UPDATE :   91 of 1986 MB written (fifo 95%) [buf  99%]   3.6x.
xorriso : UPDATE :   95 of 1986 MB written (fifo 94%) [buf  99%]   3.6x.
xorriso : UPDATE :  100 of 1986 MB written (fifo 95%) [buf  99%]   3.6x.
xorriso : UPDATE :  105 of 1986 MB written (fifo 96%) [buf  99%]   3.6x.
xorriso : UPDATE :  110 of 1986 MB written (fifo 96%) [buf  99%]   3.6x.
xorriso : UPDATE :  115 of 1986 MB written (fifo 92%) [buf  99%]   3.7x.
xorriso : UPDATE :  120 of 1986 MB written (fifo 94%) [buf  99%]   3.7x.
xorriso : UPDATE :  124 of 1986 MB written (fifo 95%) [buf  99%]   3.7x.
xorriso : UPDATE :  129 of 1986 MB written (fifo 97%) [buf  99%]   3.7x.
xorriso : UPDATE :  131 of 1986 MB written (fifo 93%) [buf  80%]   1.2x.
xorriso : UPDATE :  136 of 1986 MB written (fifo 96%) [buf  99%]   3.7x.
xorriso : UPDATE :  141 of 1986 MB written (fifo 94%) [buf  99%]   3.7x.
xorriso : UPDATE :  146 of 1986 MB written (fifo 96%) [buf  99%]   3.7x.
xorriso : UPDATE :  150 of 1986 MB written (fifo 93%) [buf  99%]   3.7x.
xorriso : UPDATE :  155 of 1986 MB written (fifo 95%) [buf  99%]   3.7x.
xorriso : UPDATE :  160 of 1986 MB written (fifo 98%) [buf  99%]   3.7x.
xorriso : UPDATE :  162 of 1986 MB written (fifo 99%) [buf  99%]   1.7x.
xorriso : UPDATE :  166 of 1986 MB written (fifo 93%) [buf  99%]   3.1x.
xorriso : UPDATE :  171 of 1986 MB written (fifo 96%) [buf  99%]   3.8x.
xorriso : UPDATE :  176 of 1986 MB written (fifo 93%) [buf  99%]   3.8x.
xorriso : UPDATE :  181 of 1986 MB written (fifo 92%) [buf  99%]   3.8x.
xorriso : UPDATE :  186 of 1986 MB written (fifo 98%) [buf  99%]   3.8x.
xorriso : UPDATE :  191 of 1986 MB written (fifo 94%) [buf  99%]   3.8x.
xorriso : UPDATE :  196 of 1986 MB written (fifo 92%) [buf  99%]   3.8x.
xorriso : UPDATE :  201 of 1986 MB written (fifo 96%) [buf  99%]   3.8x.
xorriso : UPDATE :  206 of 1986 MB written (fifo 98%) [buf  99%]   3.8x.
xorriso : UPDATE :  212 of 1986 MB written (fifo 95%) [buf  99%]   3.8x.
xorriso : UPDATE :  217 of 1986 MB written (fifo 98%) [buf  99%]   3.8x.
xorriso : UPDATE :  222 of 1986 MB written (fifo 94%) [buf  99%]   3.8x.
xorriso : UPDATE :  227 of 1986 MB written (fifo 98%) [buf  99%]   3.9x.
xorriso : UPDATE :  232 of 1986 MB written (fifo 94%) [buf  99%]   3.8x.
xorriso : UPDATE :  237 of 1986 MB written (fifo 98%) [buf  99%]   3.9x.
xorriso : UPDATE :  242 of 1986 MB written (fifo 94%) [buf  99%]   3.9x.
xorriso : UPDATE :  247 of 1986 MB written (fifo 96%) [buf  99%]   3.9x.
xorriso : UPDATE :  252 of 1986 MB written (fifo 97%) [buf  99%]   3.9x.
xorriso : UPDATE :  258 of 1986 MB written (fifo 95%) [buf  99%]   3.9x.
xorriso : UPDATE :  263 of 1986 MB written (fifo 96%) [buf  99%]   3.9x.
xorriso : UPDATE :  268 of 1986 MB written (fifo 94%) [buf  99%]   3.9x.
xorriso : UPDATE :  273 of 1986 MB written (fifo 94%) [buf  99%]   3.9x.
xorriso : UPDATE :  278 of 1986 MB written (fifo 96%) [buf  99%]   3.9x.
xorriso : UPDATE :  283 of 1986 MB written (fifo 92%) [buf  99%]   3.9x.
xorriso : UPDATE :  289 of 1986 MB written (fifo 92%) [buf  99%]   3.9x.
xorriso : UPDATE :  294 of 1986 MB written (fifo 96%) [buf  99%]   3.9x.
xorriso : UPDATE :  299 of 1986 MB written (fifo 93%) [buf  99%]   4.0x.
xorriso : UPDATE :  304 of 1986 MB written (fifo 96%) [buf  99%]   4.0x.
xorriso : UPDATE :  310 of 1986 MB written (fifo 92%) [buf  99%]   4.0x.
xorriso : UPDATE :  315 of 1986 MB written (fifo 96%) [buf  99%]   4.0x.
xorriso : UPDATE :  320 of 1986 MB written (fifo 92%) [buf  99%]   4.0x.
xorriso : UPDATE :  326 of 1986 MB written (fifo 97%) [buf  99%]   4.0x.
xorriso : UPDATE :  331 of 1986 MB written (fifo 93%) [buf  99%]   4.0x.
xorriso : UPDATE :  336 of 1986 MB written (fifo 94%) [buf  99%]   4.0x.
xorriso : UPDATE :  342 of 1986 MB written (fifo 96%) [buf  99%]   4.0x.
xorriso : UPDATE :  347 of 1986 MB written (fifo 98%) [buf  99%]   4.0x.
xorriso : UPDATE :  352 of 1986 MB written (fifo 95%) [buf  99%]   4.0x.
xorriso : UPDATE :  358 of 1986 MB written (fifo 93%) [buf  99%]   4.1x.
xorriso : UPDATE :  363 of 1986 MB written (fifo 96%) [buf  99%]   4.1x.
xorriso : UPDATE :  368 of 1986 MB written (fifo 96%) [buf  99%]   4.1x.
xorriso : UPDATE :  374 of 1986 MB written (fifo 92%) [buf  99%]   4.1x.
xorriso : UPDATE :  379 of 1986 MB written (fifo 97%) [buf  99%]   4.1x.
xorriso : UPDATE :  385 of 1986 MB written (fifo 95%) [buf  99%]   4.1x.
xorriso : UPDATE :  390 of 1986 MB written (fifo 92%) [buf  99%]   4.1x.
xorriso : UPDATE :  396 of 1986 MB written (fifo 97%) [buf  99%]   4.1x.
xorriso : UPDATE :  401 of 1986 MB written (fifo 93%) [buf  99%]   4.1x.
xorriso : UPDATE :  406 of 1986 MB written (fifo 98%) [buf  99%]   4.1x.
xorriso : UPDATE :  412 of 1986 MB written (fifo 96%) [buf  99%]   4.1x.
xorriso : UPDATE :  417 of 1986 MB written (fifo 98%) [buf  99%]   4.2x.
xorriso : UPDATE :  423 of 1986 MB written (fifo 92%) [buf  99%]   4.2x.
xorriso : UPDATE :  428 of 1986 MB written (fifo 96%) [buf  99%]   4.2x.
xorriso : UPDATE :  430 of 1986 MB written (fifo 94%) [buf  99%]   1.4x.
xorriso : UPDATE :  436 of 1986 MB written (fifo 94%) [buf  99%]   4.2x.
xorriso : UPDATE :  441 of 1986 MB written (fifo 92%) [buf  99%]   4.2x.
xorriso : UPDATE :  447 of 1986 MB written (fifo 95%) [buf  99%]   4.2x.
xorriso : UPDATE :  452 of 1986 MB written (fifo 98%) [buf  99%]   4.2x.
xorriso : UPDATE :  458 of 1986 MB written (fifo 96%) [buf  99%]   4.2x.
xorriso : UPDATE :  462 of 1986 MB written (fifo 99%) [buf  99%]   3.0x.
xorriso : UPDATE :  465 of 1986 MB written (fifo 94%) [buf  99%]   2.8x.
xorriso : UPDATE :  471 of 1986 MB written (fifo 92%) [buf  99%]   4.3x.
xorriso : UPDATE :  476 of 1986 MB written (fifo 98%) [buf  99%]   4.2x.
xorriso : UPDATE :  482 of 1986 MB written (fifo 96%) [buf  99%]   4.3x.
xorriso : UPDATE :  488 of 1986 MB written (fifo 93%) [buf  99%]   4.3x.
xorriso : UPDATE :  493 of 1986 MB written (fifo 96%) [buf  99%]   4.3x.
xorriso : UPDATE :  496 of 1986 MB written (fifo 96%) [buf  99%]   1.6x.
xorriso : UPDATE :  501 of 1986 MB written (fifo 92%) [buf  99%]   4.3x.
xorriso : UPDATE :  507 of 1986 MB written (fifo 96%) [buf  99%]   4.3x.
xorriso : UPDATE :  513 of 1986 MB written (fifo 99%) [buf  99%]   4.3x.
xorriso : UPDATE :  518 of 1986 MB written (fifo 94%) [buf  99%]   4.3x.
xorriso : UPDATE :  524 of 1986 MB written (fifo 93%) [buf  99%]   4.3x.
xorriso : UPDATE :  530 of 1986 MB written (fifo 95%) [buf  99%]   4.3x.
xorriso : UPDATE :  535 of 1986 MB written (fifo 98%) [buf  99%]   4.3x.
xorriso : UPDATE :  541 of 1986 MB written (fifo 95%) [buf  99%]   4.3x.
xorriso : UPDATE :  547 of 1986 MB written (fifo 93%) [buf  99%]   4.3x.
xorriso : UPDATE :  553 of 1986 MB written (fifo 91%) [buf  99%]   4.4x.
xorriso : UPDATE :  558 of 1986 MB written (fifo 97%) [buf  99%]   4.4x.
xorriso : UPDATE :  564 of 1986 MB written (fifo 96%) [buf  99%]   4.4x.
xorriso : UPDATE :  570 of 1986 MB written (fifo 93%) [buf  99%]   4.4x.
xorriso : UPDATE :  576 of 1986 MB written (fifo 96%) [buf  99%]   4.4x.
xorriso : UPDATE :  582 of 1986 MB written (fifo 96%) [buf  99%]   4.4x.
xorriso : UPDATE :  587 of 1986 MB written (fifo 92%) [buf  99%]   4.4x.
xorriso : UPDATE :  593 of 1986 MB written (fifo 98%) [buf  99%]   4.4x.
xorriso : UPDATE :  599 of 1986 MB written (fifo 92%) [buf  99%]   4.4x.
xorriso : UPDATE :  605 of 1986 MB written (fifo 94%) [buf  99%]   4.4x.
xorriso : UPDATE :  611 of 1986 MB written (fifo 96%) [buf  99%]   4.4x.
xorriso : UPDATE :  617 of 1986 MB written (fifo 91%) [buf  99%]   4.5x.
xorriso : UPDATE :  623 of 1986 MB written (fifo 97%) [buf  99%]   4.5x.
xorriso : UPDATE :  629 of 1986 MB written (fifo 96%) [buf  99%]   4.5x.
xorriso : UPDATE :  635 of 1986 MB written (fifo 95%) [buf  99%]   4.5x.
xorriso : UPDATE :  640 of 1986 MB written (fifo 92%) [buf  99%]   4.5x.
xorriso : UPDATE :  646 of 1986 MB written (fifo 99%) [buf  99%]   4.5x.
xorriso : UPDATE :  652 of 1986 MB written (fifo 98%) [buf  99%]   4.5x.
xorriso : UPDATE :  658 of 1986 MB written (fifo 96%) [buf  99%]   4.5x.
xorriso : UPDATE :  664 of 1986 MB written (fifo 96%) [buf  99%]   4.5x.
xorriso : UPDATE :  670 of 1986 MB written (fifo 93%) [buf  99%]   4.5x.
xorriso : UPDATE :  676 of 1986 MB written (fifo 98%) [buf  99%]   4.5x.
xorriso : UPDATE :  682 of 1986 MB written (fifo 97%) [buf  99%]   4.5x.
xorriso : UPDATE :  688 of 1986 MB written (fifo 96%) [buf  99%]   4.6x.
xorriso : UPDATE :  694 of 1986 MB written (fifo 96%) [buf  99%]   4.6x.
xorriso : UPDATE :  700 of 1986 MB written (fifo 92%) [buf  99%]   4.6x.
xorriso : UPDATE :  706 of 1986 MB written (fifo 92%) [buf  99%]   4.6x.
xorriso : UPDATE :  713 of 1986 MB written (fifo 92%) [buf  99%]   4.6x.
xorriso : UPDATE :  719 of 1986 MB written (fifo 99%) [buf  99%]   4.6x.
xorriso : UPDATE :  725 of 1986 MB written (fifo 92%) [buf  99%]   4.6x.
xorriso : UPDATE :  731 of 1986 MB written (fifo 92%) [buf  99%]   4.6x.
xorriso : UPDATE :  737 of 1986 MB written (fifo 92%) [buf  99%]   4.6x.
xorriso : UPDATE :  743 of 1986 MB written (fifo 97%) [buf  99%]   4.6x.
xorriso : UPDATE :  749 of 1986 MB written (fifo 97%) [buf  99%]   4.7x.
xorriso : UPDATE :  755 of 1986 MB written (fifo 97%) [buf  99%]   4.6x.
xorriso : UPDATE :  762 of 1986 MB written (fifo 98%) [buf  99%]   4.7x.
xorriso : UPDATE :  768 of 1986 MB written (fifo 96%) [buf  99%]   4.7x.
xorriso : UPDATE :  773 of 1986 MB written (fifo 94%) [buf  99%]   4.7x.
xorriso : UPDATE :  779 of 1986 MB written (fifo 92%) [buf  99%]   4.7x.
xorriso : UPDATE :  786 of 1986 MB written (fifo 93%) [buf  99%]   4.7x.
xorriso : UPDATE :  792 of 1986 MB written (fifo 98%) [buf  99%]   4.7x.
xorriso : UPDATE :  798 of 1986 MB written (fifo 96%) [buf  99%]   4.7x.
xorriso : UPDATE :  804 of 1986 MB written (fifo 96%) [buf  99%]   4.7x.
xorriso : UPDATE :  811 of 1986 MB written (fifo 97%) [buf  99%]   4.7x.
xorriso : UPDATE :  817 of 1986 MB written (fifo 98%) [buf  99%]   4.7x.
xorriso : UPDATE :  823 of 1986 MB written (fifo 98%) [buf  99%]   4.7x.
xorriso : UPDATE :  829 of 1986 MB written (fifo 98%) [buf  99%]   4.7x.
xorriso : UPDATE :  836 of 1986 MB written (fifo 98%) [buf  99%]   4.8x.
xorriso : UPDATE :  842 of 1986 MB written (fifo 97%) [buf  99%]   4.8x.
xorriso : UPDATE :  848 of 1986 MB written (fifo 91%) [buf  99%]   4.8x.
xorriso : UPDATE :  855 of 1986 MB written (fifo 92%) [buf  99%]   4.8x.
xorriso : UPDATE :  861 of 1986 MB written (fifo 91%) [buf  99%]   4.8x.
xorriso : UPDATE :  867 of 1986 MB written (fifo 92%) [buf  99%]   4.8x.
xorriso : UPDATE :  874 of 1986 MB written (fifo 92%) [buf  99%]   4.8x.
xorriso : UPDATE :  880 of 1986 MB written (fifo 92%) [buf  99%]   4.8x.
xorriso : UPDATE :  886 of 1986 MB written (fifo 92%) [buf  99%]   4.8x.
xorriso : UPDATE :  893 of 1986 MB written (fifo 93%) [buf  99%]   4.8x.
xorriso : UPDATE :  899 of 1986 MB written (fifo 98%) [buf  99%]   4.8x.
xorriso : UPDATE :  906 of 1986 MB written (fifo 94%) [buf  99%]   4.9x.
xorriso : UPDATE :  912 of 1986 MB written (fifo 96%) [buf  99%]   4.9x.
xorriso : UPDATE :  919 of 1986 MB written (fifo 96%) [buf  99%]   4.9x.
xorriso : UPDATE :  925 of 1986 MB written (fifo 92%) [buf  99%]   4.9x.
xorriso : UPDATE :  931 of 1986 MB written (fifo 98%) [buf  99%]   4.9x.
xorriso : UPDATE :  938 of 1986 MB written (fifo 96%) [buf  99%]   4.9x.
xorriso : UPDATE :  944 of 1986 MB written (fifo 97%) [buf  99%]   4.9x.
xorriso : UPDATE :  951 of 1986 MB written (fifo 96%) [buf  99%]   4.9x.
xorriso : UPDATE :  957 of 1986 MB written (fifo 92%) [buf  99%]   4.9x.
xorriso : UPDATE :  964 of 1986 MB written (fifo 99%) [buf  99%]   4.9x.
xorriso : UPDATE :  970 of 1986 MB written (fifo 96%) [buf  99%]   4.9x.
xorriso : UPDATE :  977 of 1986 MB written (fifo 90%) [buf  99%]   5.0x.
xorriso : UPDATE :  984 of 1986 MB written (fifo 92%) [buf  99%]   4.9x.
xorriso : UPDATE :  990 of 1986 MB written (fifo 95%) [buf  99%]   5.0x.
xorriso : UPDATE :  997 of 1986 MB written (fifo 94%) [buf  99%]   5.0x.
xorriso : UPDATE : 1001 of 1986 MB written (fifo 99%) [buf  99%]   3.2x.
xorriso : UPDATE : 1006 of 1986 MB written (fifo 96%) [buf  99%]   3.7x.
xorriso : UPDATE : 1012 of 1986 MB written (fifo 95%) [buf  99%]   5.0x.
xorriso : UPDATE : 1019 of 1986 MB written (fifo 97%) [buf  99%]   5.0x.
xorriso : UPDATE : 1026 of 1986 MB written (fifo 96%) [buf  99%]   5.0x.
xorriso : UPDATE : 1032 of 1986 MB written (fifo 90%) [buf  99%]   5.0x.
xorriso : UPDATE : 1035 of 1986 MB written (fifo 92%) [buf  99%]   1.9x.
xorriso : UPDATE : 1041 of 1986 MB written (fifo 99%) [buf  99%]   5.0x.
xorriso : UPDATE : 1048 of 1986 MB written (fifo 91%) [buf  99%]   5.1x.
xorriso : UPDATE : 1055 of 1986 MB written (fifo 93%) [buf  99%]   5.0x.
xorriso : UPDATE : 1062 of 1986 MB written (fifo 93%) [buf  99%]   5.1x.
xorriso : UPDATE : 1067 of 1986 MB written (fifo 99%) [buf  99%]   4.0x.
xorriso : UPDATE : 1071 of 1986 MB written (fifo 96%) [buf  99%]   3.0x.
xorriso : UPDATE : 1078 of 1986 MB written (fifo 95%) [buf  99%]   5.1x.
xorriso : UPDATE : 1084 of 1986 MB written (fifo 91%) [buf  99%]   5.1x.
xorriso : UPDATE : 1091 of 1986 MB written (fifo 95%) [buf  99%]   5.1x.
xorriso : UPDATE : 1098 of 1986 MB written (fifo 99%) [buf  99%]   5.1x.
xorriso : UPDATE : 1104 of 1986 MB written (fifo 95%) [buf  99%]   5.1x.
xorriso : UPDATE : 1111 of 1986 MB written (fifo 91%) [buf  99%]   5.1x.
xorriso : UPDATE : 1117 of 1986 MB written (fifo 93%) [buf  99%]   5.1x.
xorriso : UPDATE : 1124 of 1986 MB written (fifo 91%) [buf  99%]   5.1x.
xorriso : UPDATE : 1131 of 1986 MB written (fifo 91%) [buf  99%]   5.1x.
xorriso : UPDATE : 1138 of 1986 MB written (fifo 92%) [buf  99%]   5.2x.
xorriso : UPDATE : 1145 of 1986 MB written (fifo 95%) [buf  99%]   5.1x.
xorriso : UPDATE : 1151 of 1986 MB written (fifo 96%) [buf  99%]   5.2x.
xorriso : UPDATE : 1158 of 1986 MB written (fifo 97%) [buf  99%]   5.2x.
xorriso : UPDATE : 1165 of 1986 MB written (fifo 96%) [buf  99%]   5.2x.
xorriso : UPDATE : 1172 of 1986 MB written (fifo 92%) [buf  99%]   5.2x.
xorriso : UPDATE : 1179 of 1986 MB written (fifo 97%) [buf  99%]   5.2x.
xorriso : UPDATE : 1186 of 1986 MB written (fifo 92%) [buf  99%]   5.2x.
xorriso : UPDATE : 1193 of 1986 MB written (fifo 96%) [buf  99%]   5.2x.
xorriso : UPDATE : 1200 of 1986 MB written (fifo 96%) [buf  99%]   5.2x.
xorriso : UPDATE : 1207 of 1986 MB written (fifo 94%) [buf  99%]   5.2x.
xorriso : UPDATE : 1213 of 1986 MB written (fifo 95%) [buf  99%]   5.2x.
xorriso : UPDATE : 1220 of 1986 MB written (fifo 96%) [buf  99%]   5.2x.
xorriso : UPDATE : 1227 of 1986 MB written (fifo 96%) [buf  99%]   5.3x.
xorriso : UPDATE : 1234 of 1986 MB written (fifo 97%) [buf  99%]   5.3x.
xorriso : UPDATE : 1241 of 1986 MB written (fifo 96%) [buf  99%]   5.3x.
xorriso : UPDATE : 1248 of 1986 MB written (fifo 97%) [buf  99%]   5.3x.
xorriso : UPDATE : 1255 of 1986 MB written (fifo 97%) [buf  99%]   5.3x.
xorriso : UPDATE : 1262 of 1986 MB written (fifo 97%) [buf  99%]   5.3x.
xorriso : UPDATE : 1269 of 1986 MB written (fifo 91%) [buf  99%]   5.3x.
xorriso : UPDATE : 1276 of 1986 MB written (fifo 93%) [buf  99%]   5.3x.
xorriso : UPDATE : 1283 of 1986 MB written (fifo 96%) [buf  99%]   5.3x.
xorriso : UPDATE : 1291 of 1986 MB written (fifo 98%) [buf  99%]   5.3x.
xorriso : UPDATE : 1298 of 1986 MB written (fifo 98%) [buf  99%]   5.4x.
xorriso : UPDATE : 1305 of 1986 MB written (fifo 91%) [buf  99%]   5.3x.
xorriso : UPDATE : 1312 of 1986 MB written (fifo 92%) [buf  99%]   5.4x.
xorriso : UPDATE : 1319 of 1986 MB written (fifo 92%) [buf  99%]   5.4x.
xorriso : UPDATE : 1326 of 1986 MB written (fifo 92%) [buf  99%]   5.4x.
xorriso : UPDATE : 1333 of 1986 MB written (fifo 94%) [buf  99%]   5.4x.
xorriso : UPDATE : 1340 of 1986 MB written (fifo 97%) [buf  99%]   5.4x.
xorriso : UPDATE : 1347 of 1986 MB written (fifo 98%) [buf  99%]   5.4x.
xorriso : UPDATE : 1355 of 1986 MB written (fifo 96%) [buf  99%]   5.4x.
xorriso : UPDATE : 1362 of 1986 MB written (fifo 91%) [buf  99%]   5.4x.
xorriso : UPDATE : 1369 of 1986 MB written (fifo 90%) [buf  99%]   5.4x.
xorriso : UPDATE : 1376 of 1986 MB written (fifo 93%) [buf  99%]   5.4x.
xorriso : UPDATE : 1383 of 1986 MB written (fifo 96%) [buf  99%]   5.5x.
xorriso : UPDATE : 1391 of 1986 MB written (fifo 97%) [buf  99%]   5.5x.
xorriso : UPDATE : 1398 of 1986 MB written (fifo 94%) [buf  99%]   5.5x.
xorriso : UPDATE : 1405 of 1986 MB written (fifo 95%) [buf  99%]   5.5x.
xorriso : UPDATE : 1412 of 1986 MB written (fifo 98%) [buf  99%]   5.5x.
xorriso : UPDATE : 1420 of 1986 MB written (fifo 89%) [buf  99%]   5.5x.
xorriso : UPDATE : 1427 of 1986 MB written (fifo 92%) [buf  99%]   5.5x.
xorriso : UPDATE : 1434 of 1986 MB written (fifo 96%) [buf  99%]   5.5x.
xorriso : UPDATE : 1441 of 1986 MB written (fifo 95%) [buf  99%]   5.5x.
xorriso : UPDATE : 1449 of 1986 MB written (fifo 98%) [buf  99%]   5.5x.
xorriso : UPDATE : 1456 of 1986 MB written (fifo 92%) [buf  99%]   5.5x.
xorriso : UPDATE : 1463 of 1986 MB written (fifo 92%) [buf  99%]   5.6x.
xorriso : UPDATE : 1471 of 1986 MB written (fifo 94%) [buf  99%]   5.6x.
xorriso : UPDATE : 1478 of 1986 MB written (fifo 93%) [buf  99%]   5.6x.
xorriso : UPDATE : 1485 of 1986 MB written (fifo 97%) [buf  99%]   5.6x.
xorriso : UPDATE : 1493 of 1986 MB written (fifo 99%) [buf  99%]   5.6x.
xorriso : UPDATE : 1500 of 1986 MB written (fifo 92%) [buf  99%]   5.6x.
xorriso : UPDATE : 1508 of 1986 MB written (fifo 91%) [buf  99%]   5.6x.
xorriso : UPDATE : 1515 of 1986 MB written (fifo 91%) [buf  99%]   5.6x.
xorriso : UPDATE : 1522 of 1986 MB written (fifo 92%) [buf  99%]   5.6x.
xorriso : UPDATE : 1530 of 1986 MB written (fifo 94%) [buf  99%]   5.6x.
xorriso : UPDATE : 1537 of 1986 MB written (fifo 96%) [buf  99%]   5.6x.
xorriso : UPDATE : 1545 of 1986 MB written (fifo 98%) [buf  99%]   5.6x.
xorriso : UPDATE : 1551 of 1986 MB written (fifo 92%) [buf  99%]   5.6x.
xorriso : UPDATE : 1559 of 1986 MB written (fifo 96%) [buf  99%]   5.7x.
xorriso : UPDATE : 1566 of 1986 MB written (fifo 92%) [buf  99%]   5.6x.
xorriso : UPDATE : 1574 of 1986 MB written (fifo 96%) [buf  99%]   5.7x.
xorriso : UPDATE : 1581 of 1986 MB written (fifo 92%) [buf  99%]   5.7x.
xorriso : UPDATE : 1589 of 1986 MB written (fifo 99%) [buf  99%]   5.7x.
xorriso : UPDATE : 1597 of 1986 MB written (fifo 93%) [buf  99%]   5.7x.
xorriso : UPDATE : 1604 of 1986 MB written (fifo 91%) [buf  99%]   5.7x.
xorriso : UPDATE : 1612 of 1986 MB written (fifo 93%) [buf  99%]   5.7x.
xorriso : UPDATE : 1619 of 1986 MB written (fifo 98%) [buf  99%]   5.7x.
xorriso : UPDATE : 1627 of 1986 MB written (fifo 92%) [buf  99%]   5.7x.
xorriso : UPDATE : 1634 of 1986 MB written (fifo 98%) [buf  99%]   5.7x.
xorriso : UPDATE : 1642 of 1986 MB written (fifo 92%) [buf  99%]   5.7x.
xorriso : UPDATE : 1650 of 1986 MB written (fifo 89%) [buf  99%]   5.8x.
xorriso : UPDATE : 1657 of 1986 MB written (fifo 93%) [buf  99%]   5.8x.
xorriso : UPDATE : 1665 of 1986 MB written (fifo 96%) [buf  99%]   5.8x.
xorriso : UPDATE : 1673 of 1986 MB written (fifo 91%) [buf  99%]   5.8x.
xorriso : UPDATE : 1676 of 1986 MB written (fifo 93%) [buf  99%]   2.3x.
xorriso : UPDATE : 1683 of 1986 MB written (fifo 96%) [buf  99%]   5.8x.
xorriso : UPDATE : 1691 of 1986 MB written (fifo 89%) [buf  99%]   5.8x.
xorriso : UPDATE : 1699 of 1986 MB written (fifo 92%) [buf  99%]   5.8x.
xorriso : UPDATE : 1706 of 1986 MB written (fifo 92%) [buf  99%]   5.8x.
xorriso : UPDATE : 1709 of 1986 MB written (fifo 98%) [buf  99%]   2.4x.
xorriso : UPDATE : 1717 of 1986 MB written (fifo 90%) [buf  99%]   5.8x.
xorriso : UPDATE : 1725 of 1986 MB written (fifo 92%) [buf  99%]   5.8x.
xorriso : UPDATE : 1733 of 1986 MB written (fifo 96%) [buf  99%]   5.8x.
xorriso : UPDATE : 1740 of 1986 MB written (fifo 99%) [buf  99%]   5.3x.
xorriso : UPDATE : 1744 of 1986 MB written (fifo 90%) [buf  99%]   3.0x.
xorriso : UPDATE : 1751 of 1986 MB written (fifo 92%) [buf  99%]   5.9x.
xorriso : UPDATE : 1759 of 1986 MB written (fifo 90%) [buf  99%]   5.9x.
xorriso : UPDATE : 1767 of 1986 MB written (fifo 92%) [buf  99%]   5.9x.
xorriso : UPDATE : 1775 of 1986 MB written (fifo 92%) [buf  99%]   5.9x.
xorriso : UPDATE : 1783 of 1986 MB written (fifo 92%) [buf  99%]   5.9x.
xorriso : UPDATE : 1790 of 1986 MB written (fifo 99%) [buf  99%]   5.9x.
xorriso : UPDATE : 1798 of 1986 MB written (fifo 94%) [buf  99%]   5.9x.
xorriso : UPDATE : 1806 of 1986 MB written (fifo 92%) [buf  99%]   5.9x.
xorriso : UPDATE : 1814 of 1986 MB written (fifo 97%) [buf  99%]   5.9x.
xorriso : UPDATE : 1822 of 1986 MB written (fifo 92%) [buf  99%]   6.0x.
xorriso : UPDATE : 1830 of 1986 MB written (fifo 96%) [buf  99%]   6.0x.
xorriso : UPDATE : 1837 of 1986 MB written (fifo 89%) [buf  99%]   6.0x.
xorriso : UPDATE : 1845 of 1986 MB written (fifo 92%) [buf  99%]   6.0x.
xorriso : UPDATE : 1853 of 1986 MB written (fifo 95%) [buf  99%]   6.0x.
xorriso : UPDATE : 1861 of 1986 MB written (fifo 89%) [buf  99%]   6.0x.
xorriso : UPDATE : 1869 of 1986 MB written (fifo 96%) [buf  99%]   6.0x.
xorriso : UPDATE : 1877 of 1986 MB written (fifo 89%) [buf  99%]   6.0x.
xorriso : UPDATE : 1885 of 1986 MB written (fifo 96%) [buf  99%]   6.0x.
xorriso : UPDATE : 1893 of 1986 MB written (fifo 98%) [buf  99%]   6.0x.
xorriso : UPDATE : 1901 of 1986 MB written (fifo 93%) [buf  99%]   6.0x.
xorriso : UPDATE : 1909 of 1986 MB written (fifo 96%) [buf  99%]   6.0x.
xorriso : UPDATE : 1917 of 1986 MB written (fifo 90%) [buf  99%]   6.0x.
xorriso : UPDATE : 1925 of 1986 MB written (fifo 92%) [buf  99%]   6.0x.
xorriso : UPDATE : 1933 of 1986 MB written (fifo 99%) [buf  99%]   6.1x.
xorriso : UPDATE : 1941 of 1986 MB written (fifo 96%) [buf  99%]   6.1x.
xorriso : UPDATE : 1949 of 1986 MB written (fifo 92%) [buf  99%]   6.1x.
xorriso : UPDATE : 1957 of 1986 MB written (fifo 90%) [buf  99%]   6.1x.
xorriso : UPDATE : 1965 of 1986 MB written (fifo 92%) [buf  99%]   6.1x.
xorriso : UPDATE : 1973 of 1986 MB written (fifo 96%) [buf  99%]   6.1x.
xorriso : UPDATE : 1981 of 1986 MB written (fifo 89%) [buf  99%]   6.1x.
xorriso : UPDATE : 1986 of 1986 MB written (fifo  0%) [buf  99%]   3.6x.
xorriso : UPDATE : 1986 of 1986 MB written (fifo  0%) [buf  99%]   0.0x.
xorriso : UPDATE : 1986 of 1986 MB written (fifo  0%) [buf  99%]   0.0x.
xorriso : UPDATE : Closing track/session. Working since 350 seconds
xorriso : UPDATE : Closing track/session. Working since 351 seconds
xorriso : UPDATE : Closing track/session. Working since 352 seconds
xorriso : UPDATE : Closing track/session. Working since 353 seconds
xorriso : UPDATE : Closing track/session. Working since 354 seconds
xorriso : UPDATE : Closing track/session. Working since 355 seconds
xorriso : UPDATE : Closing track/session. Working since 356 seconds
xorriso : UPDATE : Closing track/session. Working since 357 seconds
xorriso : UPDATE : Closing track/session. Working since 358 seconds
xorriso : UPDATE : Closing track/session. Working since 359 seconds
xorriso : UPDATE : Closing track/session. Working since 360 seconds
xorriso : UPDATE : Closing track/session. Working since 361 seconds
xorriso : UPDATE : Closing track/session. Working since 362 seconds
xorriso : UPDATE : Closing track/session. Working since 363 seconds
xorriso : UPDATE : Closing track/session. Working since 364 seconds
xorriso : UPDATE : Closing track/session. Working since 365 seconds
xorriso : UPDATE : Closing track/session. Working since 366 seconds
xorriso : UPDATE : Closing track/session. Working since 367 seconds
xorriso : UPDATE : Closing track/session. Working since 368 seconds
xorriso : UPDATE : Closing track/session. Working since 369 seconds
xorriso : UPDATE : Closing track/session. Working since 370 seconds
xorriso : UPDATE : Closing track/session. Working since 371 seconds
xorriso : UPDATE : Closing track/session. Working since 372 seconds
xorriso : UPDATE : Closing track/session. Working since 373 seconds
xorriso : UPDATE : Closing track/session. Working since 374 seconds
xorriso : UPDATE : Closing track/session. Working since 375 seconds
xorriso : UPDATE : Closing track/session. Working since 376 seconds
Writing to '/dev/sr0' completed successfully.

xorriso : NOTE : Re-assessing -outdev '/dev/sr0'
xorriso : NOTE : Disc status unsuitable for writing
Drive current: -outdev '/dev/sr0'
Media current: DVD+R
Media status : is written , is closed
Media summary: 1 session, 1017152 data blocks, 1987m data,     0 free

```

I'm also having trouble verifying that the DVD was burned correctly. When I type:

```

/sbin/isosize -x /dev/sr0

```

I get an error message that says:

```

isosize: /dev/sr0: might not be an ISO filesystem
isosize: seek error on /dev/sr0: Invalid argument

```

and I'm not sure how to proceed.

---

### Post by CatKiller on 2019-11-16
> **John_Patrick_Mason said:**
> 
I'm also having trouble verifying that the DVD was burned correctly. 

The disc has a file, called md5sum.txt, containing the MD5 hashes of every file on the disc. You can check that list against the files you've burned with ```
md5sum -c md5sum.txt
```

---

### Post by John_Patrick_Mason on 2019-11-16
> **CatKiller said:**
> The disc has a file, called md5sum.txt, containing the MD5 hashes of every file on the disc. You can check that list against the files you've burned with ```
md5sum -c md5sum.txt
```

I'd like to do that, but for some reason, I can't seem to be able to find the mount point of the CD/DVD drive. It's been awhile since I've created a live DVD, but, in the past, I've used the **mount** command prior to inserting the DVD into the tray, and then compared the results once the DVD is in the tray to figure out what is the mount point of the DVD's filesystem.

Now, for whatever reason, when I insert the burned DVD that I created using **scdbackup**'s **xorriso** command, I get a pop-up error message from the GUI with **two **DVD+R icons in the launcher with one of them saying, "Unable to mount Blank DVD+R Disc. Location is already mounted."

Also, I thought people were moving away from **md5sum** to **sha256sum** for verifying the integrity of files, not that I suspect my system to be compromised.

---

### Post by scdbackup on 2019-11-17
Hi,

during the run with xorriso command "-toc", the drive believed to have no
medium at all.

Later, during the run with command "-as cdrecord" it recognized a DVD+R.
The re-assessment after the burning shows the expected medium status.
(So K3B would have no reason to complain about "No medium information"
 at that moment.)

Nevertheless the block device driver of the Linux kernel throws a seek
error, when /sbin/isosize tries to read the superblock of the burnt
ISO filesystem. This info is located in block 16 of the DVD.
Obviously the kernel cannot address it.
This also explains why it cannot be mounted.
The consequential confusion of the desktop is not flattering to its
developers.

So we have to rely on libburn as device driver.
What do you get when the xorriso DVD+R is in the drive and you do again
```

xorriso -outdev /dev/sr0 -toc

```
If it complains "Device or resource busy", then do:
```

sudo umount /dev/sr0
xorriso -outdev /dev/sr0 -toc

```

If it still recognizes the medium as DVD+R and says
"Media status : is written , is closed", then run:
```

xorriso -outdev /dev/sr0 -check_media use=outdev --

```
which will test the DVD for accessability and read errors. (We have to
expect to see some.)

If xorriso shows that the drive recognizes the DVD+R as closed, and if
it can read all its blocks, then the behavior of /sbin/isosize can only
be explained by a data damage of the ISO on the DVD.
First verify your ISO image file and determine its block count:
```

sha256sum /home/mason/Downloads/ubuntu-18.04.3-desktop-amd64.iso
/sbin/isosize -x /home/mason/Downloads/ubuntu-18.04.3-desktop-amd64.iso

```
Then let xorriso copy the ISO image (plus some trailing garbage) from 
the DVD to a disk file and compute the checksum:
```

xorriso -outdev /dev/sr0 -check_media use=outdev data_to=/home/mason/Downloads/from_dvd.iso  --
dd if=/home/mason/Downloads/from_dvd.iso count=1017000 bs=2048 | sha256sum

```
(The number 1017000 is the isosize of ubuntu-18.04.3-desktop-amd64.iso)

MD5 would suffice for verification. But Debian makes great effort to
eradicate it in order to keep people from using it in security checks.
So we can as well practice with the longer checksum.

Have a nice day :)

Thomas

---

### Post by John_Patrick_Mason on 2019-11-17
> **scdbackup said:**
> 
What do you get when the xorriso DVD+R is in the drive and you do again
```

xorriso -outdev /dev/sr0 -toc

```


When I insert the burned DVD and run the above command I get:

```

xorriso 1.4.2 : RockRidge filesystem manipulator, libburnia project.

Drive current: -outdev '/dev/sr0'
Media current: DVD+R
Media status : is blank
Media summary: 0 sessions, 0 data blocks, 0 data, 4483m free
Drive current: -outdev '/dev/sr0'
Drive type   : vendor 'TSSTcorp' product 'DVD+-RW TS-L633J' revision 'D400'
Drive id     : 'R8126GNB467326  '
Media current: DVD+R
Media product: AML/003/48 , UML
Media status : is blank
Media blocks : 0 readable , 2295104 writable , 2295104 overall
Media summary: 0 sessions, 0 data blocks, 0 data, 4483m free

```

It's not even saying the "device or resource [is] busy," or even that the DVD is "written," it's saying the DVD is blank. WTH.

What should I do next?

---

### Post by scdbackup on 2019-11-17
Hi,

> It's not even saying the "device or resource [is] busy,"

That would have been if the DVD was in some way readable and had been
mounted by some filesystem driver.

But when the drive says it is blank, then it most probably failed to
burn it properly. This might be a problem with the overall recordable
surface, or only with the table-of-contents part of the DVD.
Does the surface look like there is a reflectivity change about
two-thirds on the way from middle to rim ?

If you have a different DVD drive in reach, try what the software on
that system says about it.

> What should I do next? 

Assumed that no other drive says that the DVD+R is readable, contains
about 2 GB of files, and can read these files:

Get other media, for example DVD-R. (Both types should work well, if there
is no individual glitch in either drive or batch of media.)

If possible try whether a different drive can properly burn your remaining
DVD+R media.

If nothing helps: get a new drive.

After extracting the old one, shake it, put it upside down, give it a
strong air blow, and then put it back in. Try whether it works.

(No joke. I had a Blu-ray drive idle in a card box for 4 years after it
lost its capability to recognize BD media. It got some kicks and was used
for a few weeks as DVD burner. Recently i needed a drop-in for another
dead DVD burner. Surprise: It does BD-RE again.)

But be ready to buy a new drive.

-------------------------------------------------------------------------

If booting from an USB stick is an option, consider to do make a backup from
its current content:
```

dd if=/dev/sdX bs=1M | gzip >/my/big/filesystem/stick_sdX.img.gz

```
where "sdX" is the base device file address of the USB stick, like /dev/sdc,
not like /dev/sdc1. All its partitions (sdc1 ... sdcN) should be unmounted
before you make the copy image.

Then put the ISO image plainly onto the USB stick, which will forget about
everything it knew about its old content. (Thus the backup in advance):
```

dd if=/home/mason/Downloads/ubuntu-18.04.3-desktop-amd64.iso bs=1M of=/dev/sdX

```
This USB stick is supposed to boot via PC-BIOS and EFI like from DVD.
Do not let partition editors fiddle with it before you use it for booting.

To later restore the old content to the USB stick, do:
```

gunzip </my/big/filesystem/stick_sdX.img.gz | dd bs=1M of=/dev/sdX

```
Plug out and in. Then the system should show the old partitions and
filesystems.

Have a nice day :)

Thomas

---

### Post by John_Patrick_Mason on 2019-11-18
It sucks because I'm doing this for a friend; he uses a desktop with Windows 7 that's going to reach EOL on January 14, 2020. Being less-than-tech-literate, I gave him three options: either upgrade to Windows 10 for $139, buy a cheap Chromebook for under $300, or have me install Ubuntu/Lubuntu for free. I created a bootable USB stick with Ubuntu, but his desktop wouldn't boot, even after changing the boot order in the BIOS. Hence, the reason I need a live CD.

I'm probably going to get an external USB CD/DVD drive with a separate power source on Amazon. Check back in a few days. The thing is I'm going to have to get it soon, to give him enough time to try a Linux-based OS, so that he can make his final decision on Black Friday, when everything is on sale, *if* he decides to buy a Chromebook, instead.

Also, I can't help but notice that you had me use **xorriso** to create the bootable DVD, would you know by any chance if **xorriso** is OS agnostic? I usually like to stick to utilities that are OS agnostic, like xdg-open to open files. In the past, when I was first learning how to use the command line, I've used **wodim** to burn image files to DVDs.

---

### Post by scdbackup on 2019-11-18
Hi,

> I created a bootable USB stick with Ubuntu, but his desktop wouldn't
> boot,

Did you use a plain copy method (dd, cp, ...) ?
There are old howtos around which propose unpacking the ISO and installing
the files in the filesystem of the USB stick.
Those might not work any more, because they rely much on the way how
the kernel is supposed to start the operating system after having been
started itself by the bootloader.

But if the machine boots normally from its normal disk instead of
complaining or being stuck in boot process, then it is most likely the
firmware which does not work with the USB stick. Try all USB ports
of the machine. Some BIOSes inspect not all of them.


> I'm probably going to get an external USB CD/DVD drive with a separate power
> source on Amazon.

An alternative would be buying an Ubuntu DVD. Like
  [https://www.amazon.com/Ubuntu-Linux-18-04-DVD-OFFICIAL/dp/B07CWLKBDY](https://www.amazon.com/Ubuntu-Linux-18-04-DVD-OFFICIAL/dp/B07CWLKBDY)
  [https://www.osdisc.com/products/linux/ubuntu](https://www.osdisc.com/products/linux/ubuntu)

(But of course, everybody should have a working DVD burner.)


> Also, I can't help but notice that you had me use xorriso to create
> the bootable DVD, would you know by any chance if xorriso is OS agnostic?

When it comes to burning a bootable ISO image by GNU/Linux: Surely yes.

That's because the bytes in the ISO image constitute the bootability.
The burn program only has to put those bytes 1:1 onto the medium.
(Same with USB stick, of course.)
xorriso burns via libburn, which has OS adapters for Linux, FreeBSD,
NetBSD, and Solaris.

When it comes to making a bootable ISO: Quite yes.

It is mainly in use within the GNU/Linux world. The other larger free OSes
take pride in having their own ISO production software. But the really small
ones are again users of grub-mkrescue and thus xorriso.

Your Ubuntu ISO was made by xorriso. Very old xorriso, but still good enough.
```

Preparer Id  : XORRISO-1.2.4 2012.07.20.130001, ...

```
xorriso only packs up what the distro developers have prepared.
Ubuntu ISOs boot on legacy PC-BIOS by ISOLINUX and on EFI by GRUB.
Both boot loaders then start a Linux kernel which pulls up a GNU/Linux
system.
This aspect of xorriso runs on any X/Open compliant system. X/Open includes
MS-Windows with e.g. Cygwin as X/Open layer and contemporary MacOS.
A portability problem might arise if it gets the task to prepare an
ISO using a yet unknown bootloader system.

Have a nice day :)

Thomas

---

### Post by John_Patrick_Mason on 2019-11-18
[QUOTE=scdbackup]
Did you use a plain copy method (dd, cp, ...) ?
[/QUOTE]

Nope. I used Startup Disk Creator, through the GUI, to create the bootable USB stick, since I'm more used to creating live DVDs, at least, that's what I've done in the past.

[QUOTE=scdbackup]
But if the machine boots normally from its normal disk instead of
complaining or being stuck in boot process, then it is most likely the
firmware which does not work with the USB stick. Try all USB ports
of the machine. Some BIOSes inspect not all of them.
[/QUOTE]

Huh, I didn't even think of that. I tested the USB stick, at home, to see if it would boot, and sure enough it did, but I only tested the front-facing USB ports on my friend's desktop. Maybe next time try the ones in the back? Also, which firmware are we talking about? The firmware of the USB stick itself, or the firmware of my friend's front-facing USB port?

[QUOTE=scdbackup]
An alternative would be buying an Ubuntu DVD. Like
  [https://www.amazon.com/Ubuntu-Linux-18-04-DVD-OFFICIAL/dp/B07CWLKBDY](https://www.amazon.com/Ubuntu-Linux-18-04-DVD-OFFICIAL/dp/B07CWLKBDY)
  [https://www.osdisc.com/products/linux/ubuntu](https://www.osdisc.com/products/linux/ubuntu)
[/QUOTE]

Yeah, but, now, I have all these blank spare DVDs laying around, and if I'm going to install Ubuntu -- or one of its flavors -- on somebody's computer, I'd rather give them a physical installation disc, since those are cheap, rather than give them a brand new USB stick for free.

[QUOTE=scdbackup]
When it comes to burning a bootable ISO image by GNU/Linux: Surely yes.
[/QUOTE]

How does it compare to wodim for creating live CDs? Is there a clear winner/standard in the Linux world?

---

### Post by scdbackup on 2019-11-18
Hi,

> which firmware are we talking about? 

The mainboard firmware. In case of x86 processors the two candidates
are commonly known as BIOS and EFI. This firmware shall inspect the
attached storage media for boot sectors. In case it finds some, it shall
start the program to which the boot sector points.

In case of BIOS and USB stick, this is the MBR x86 machine code.
In case of EFI and USB stick, it is the EFI System Partition, which holds
a FAT filesystem containing a start program with a name which is defined
by UEFI specs for each processor type. (E.g. \EFI\BOOT\BOOTX64.EFI for
64 bit x86 processors.)
Ubuntu 18.04.03 ISO offers both, so that it is supposed to boot on BIOS
and EFI alike. (The boot menus look different because they are shown by
different boot loaders ISOLINUX and GRUB, respectively.)


> I'd rather give them a physical installation disc, since those are cheap,
> rather than give them a brand new USB stick for free.

The links i gave offer Ubuntu desktop DVDs. 6 to 10 USD.
But yeah. If the drive is dead you should get a new one anyway.


> How does it compare to wodim for creating live CDs? Is there a clear
> winner/standard in the Linux world? 

wodim is a burn program. Not advised for DVD, though. Its last maintainer
stated in [https://lists.debian.org/debian-user/2018/09/msg01078.html](https://lists.debian.org/debian-user/2018/09/msg01078.html)
> 
cdrkit [the package containing wodim and genisoimage] is definitely now EOL,
and I don't use it myself for writing DVD or BD media. You can quote me
on that.

We have growisofs and the libburn based programs. No need to play with a
mummy like wodim, unless you need its capability to create exotic CD formats.
If you really want to run a program from this code base, you should compile
cdrtools in order to get Joerg Schilling's cdrecord, from which wodim was
forked in 2006.
Being biased, i state that Andy Polyakov's growisofs and my libburn are
more compliant to MMC specs for DVD and BD, than cdrecord is. Joerg does
not agree to this assessment, of course.

Have a nice day :)

Thomas

---

### Post by westie457 on 2019-11-18
Any chance that you could use your friends machine to create the bootable media?

If yes I suggest [https://cdburnerxp.se/en/home](https://cdburnerxp.se/en/home) this for creating the DVD
and this for creating the USB [https://rufus.ie/](https://rufus.ie/)

Both are Windows only apps.

On your own machine have you tried this to create a bootable USB? [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

There is another tool to use. [https://www.balena.io/etcher/](https://www.balena.io/etcher/)
This one is cross-platform. I do not know if it will write to a DVD because I have never tried that aspect.

---

### Post by scdbackup on 2019-11-18
Hi,

westie457 wrote:
> [https://rufus.ie/](https://rufus.ie/)

This is indeed a suitable tool to put any USB stick bootable GNU/Linux ISO
onto an USB stick. Use its "dd" mode in order to get the boot equipment
which is prepared in the ISO, not the equipment which Rufus would install.


> [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

This looks like a more user-safe tool which acts like our GNU dd or cp.
> 
mkusb will 'use the whole device', actually only the head end (size of the
iso file), but the rest of the device is not available. mkusb simply clones
the ISO 9660 file system with its content from the iso file. This ISO 9660
file system works from CD/DVD disks, and also from USB drives. After using
a USB pendrive like this, you make a new partition table and file system,
if you want to use it for another purpose. 
[...]
The crucial task of mkusb was and is to help selecting the correct device
and avoid overwriting other devices.

It shall be praised for that !

So (assumed that mkusb works ok) i revoke my proposal
```

dd if=/home/mason/Downloads/ubuntu-18.04.3-desktop-amd64.iso bs=1M of=/dev/sdX

```
in favor of this tool. I keep up the proposal to make a backup by dd and
gzip. The backup restore step could become more safe by
```

gunzip </my/big/filesystem/stick_sdX.img.gz >/my/big/filesystem/stick_sdX.fake.iso
mkusb /my/big/filesystem/stick_sdX.fake.iso

```

Have a nice day :)

Thomas

---

### Post by sudodus on 2019-11-18
@scdbackup,

**mkusb version 12** alias **dus** can extract directly from a gzip or xz compressed image file, so
```

dus /my/big/filesystem/stick_sdX.img.gz

```
will do the job, to help you identify and select the correct target device and extract from the compressed image :-)

This is described when you use the option -h,
```

$ dus -h
dus 12.3.8
Usage:
---- Make USB or memory card install drive from ISO or image file ---
dus
dus file.iso
dus "quote file name (1) with special characters.iso"
dus file.img
dus file.img.gz
dus file.img.xz
dus file.tar       # if an mkusb tarfile for Windows
---- Clone a device (typically a CD drive or USB drive) -------------
dus /dev/sr0       # example of CD drive
---- Wipe or restore a USB drive or memory card ---------------------
dus
---- Options --------------------------------------------------------
dus -d [file.iso]  # dialog (text mode menus)
dus -t [file.iso]  # plain text mode interface
dus -h             # usage text
dus -v             # version

```

> 
mkusb will 'use the whole device', actually only the head end (size of the
iso file), but the rest of the device is not available.

This used to be true, but starting with Ubuntu 19.10, the drive space behind the cloned image of the iso file can be used for persistence. A partition with label 'casper-rw' can be created there and you can save installed programs, tweaks and personal data files. See [this link](https://askubuntu.com/questions/1181854/how-is-it-easier-to-make-a-persistent-live-drive-with-ubuntu-19-10).

---

### Post by scdbackup on 2019-11-18
Hi,

sudodus wrote:
> mkusb version 12 alias dus can extract directly from a gzip or xz 
> compressed image file

Is there a reason known why this tool is not available as Debian
package ?
[https://www.debian.org/CD/faq/#write-usb](https://www.debian.org/CD/faq/#write-usb) could really need safer advise
than leaving alone the user with "Be careful to make sure you have the 
right device name".

With DVDs we have the lucky situation that /dev/sr0 cannot be easily 
confused with the hard disk /dev/sda. Further the usual distros allow 
the desktop user rw-access to /dev/sr* (often via ACL). So even the burn
programs need no special privileges.
But with USB stick it is always a lengthy warning story to tell the users.

Have a nice day :)

Thomas

---

### Post by sudodus on 2019-11-18
@scdbackup,

I have tried, but the Debian gurus that are managing the repositories are not interested. So I have failed to get it into a repository. The best I can do is to maintain the PPA, 'ppa:mkusb/ppa'

---

### Post by scdbackup on 2019-11-18
Hi,

yes, Debian can be quite a closed clam. But debian-cd and debian-live
should be interested in such a tool. I myself am upstream programmer and
"sponsored" uploader of my own software. So i cannot decide nor am i fully
skilled as Debian packager.

Where can i learn about the dependencies at compile time and run time ?
Is everything that's needed already provided by Debian in the necessary
versions ? Any idea why it was not accepted ?

(My mail address is [EMAIL="scdbackup@gmx.net"]scdbackup@gmx.net[/EMAIL])

Have a nice day :)

Thomas

---

### Post by sudodus on 2019-11-18
> **scdbackup said:**
> Where can i learn about the dependencies at compile time and run time ?
Is everything that's needed already provided by Debian in the necessary
versions ? Any idea why it was not accepted ?


mkusb consists of **bash shellscripts**, that call standard tools, most of them already bundled with Ubuntu and Debian, the rest of them readily available from the standard repositories.

So there is no compiling. Please tell me which files you would like to see (debian files, that configure the packaging), and I can send them to you so that you can check the dependencies.

The help package usb-pack-efi might upset the debian gurus, but mkusb works without it for cloning, and when making persistent live drives for Ubuntu (but not Debian). If necessary, I can make it work for Debian too, or simply remove that feature and rely on mkusb-minp for Debian persistent live drives.

---

### Post by scdbackup on 2019-11-19
Hi,

just to avoid the impression that i bailed out of this thread:
sudodus and i are discussing the mkusb/Debian issue in private mails now.

Have a nice day :)

Thomas

---

### Post by John_Patrick_Mason on 2019-11-20
[QUOTE=scdbackup]
Ubuntu ISOs boot on legacy PC-BIOS by ISOLINUX and on EFI by GRUB.
[/QUOTE]

I'm  not sure if I understand this part. The computer I'm on uses BIOS as  its firmware, but uses GRUB as its bootloader. At least, I think it uses  GRUB as its bootloader. Here's what my bootloader looks like -- not  from my computer:

[IMG]https://kbimg.dell.com/library/KB/DELL_ORGANIZATIONAL_GROUPS/DELL_GLOBAL/REC/nomodeset_Linux_HC_ASM_01.png[/IMG]

Also,  both the Master Boot Record (MBR) and the EFI System Partition for EFI  systems are located on the HDD/SSD or, in this case, USB stick, correct?  I just want to make sure I understand how firmware is able to boot a  Linux distribution.

[QUOTE=westie457]
On your own machine have you tried this to create a bootable USB? [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[/QUOTE]

Since,  I'm more used to creating live DVDs, I didn't use a utility like mkusb  to create the bootable USB, I just used Startup Disk Creator. And, I  know I was successful in my endeavor, because I ended up testing it on  my home computer, first, to see if it would boot. So, I was successful  in creating a bootable USB stick, it just wouldn't boot on my friend's  front-facing USB port; I haven't tried the back ones, though. That's why I need a functional DVD drive as backup, in case the USB stick fails to boot in the back. As for the DVD burner itself, it should arrive on Thursday. So, be ready to check back then.

Also, I tried popping in two DVDs into my CD/DVD drive, and it's weird, one of the DVDs worked, but the drive failed to even respond to the other DVD. Is this another sign of a failing CD/DVD drive, when one DVD works, but the other doesn't? It's weird, though, because the same DVD that my drive wouldn't recognize on Ubuntu, worked just fine on my Windows 7 partition (I dual-boot).

---

### Post by scdbackup on 2019-11-20
Hi,

about Ubuntu ISOs and its bootloaders.

It is of course possible and usual to install GRUB on your hard disk as
boot loader for being started by PC-BIOS firmware. It is also possible to
use GRUB as bootloader of an ISO image for being started by PC-BIOS.
This can be seen with the ISOs from program grub-mkrescue or of the Guix
project.

Nevertheless it is a long standing tradition to boot ISOs via PC-BIOS by
the bootloader ISOLINUX from the SYSLINUX project. When Matthew Garrett
added EFI booting to the Fedora ISOs, he decided for hard technical reasons
not to use SYSLINUX for that task. Its EFI code simply fails with CD-ROM.
See [http://mjg59.dreamwidth.org/11285.html](http://mjg59.dreamwidth.org/11285.html) for Matthew's success report.
So GRUB got into Fedora ISOs. Debian and Ubuntu followed a while later,
using the same combination of boot loaders.

The typical "mjg" ISO has two El Torito boot images. Inspection by xorriso
yields:
```

$ xorriso -indev ubuntu-18.04.3-desktop-amd64.iso -report_system_area plain -report_el_torito plain
...
El Torito images   :   N  Pltf  B   Emul  Ld_seg  Hdpt  Ldsiz         LBA
El Torito boot img :   1  BIOS  y   none  0x0000  0x00      4      995658
El Torito boot img :   2  UEFI  y   none  0x0000  0x00   4928      997283

```
These images are also exposed by the ISO as data files
```

El Torito img path :   1  /isolinux/isolinux.bin
El Torito img path :   2  /boot/grub/efi.img

```
The one is a 16-bit x86 program and the other is a FAT filesystem image,
as specified in UEFI. As the names already suggest, they stem from ISOLINUX
and GRUB, respectively.

So far for booting from CD/DVD/BD media. For booting from USB stick, there
is ISOLINUX x86 code in the MBR of the ISO image. If started by PC-BIOS it
immediately executes the El Torito boot program isolinux.bin.
This is indicated in the xorriso report by the word "isohybrid" in 
```

System area summary: MBR isohybrid cyl-align-on GPT APM

```
For booting from USB stick via EFI, there is an MBR partition of type EF.
```

MBR partition table:   N Status  Type        Start       Blocks
MBR partition      :   1   0x80  0x00            0      4068000
MBR partition      :   2   0x00  0xef      3989132         4928
MBR partition path :   2  /boot/grub/efi.img

```
UEFI specifies that the firmware shall look into the FAT filesystem of this
partition for the EFI start program. That's \EFI\BOOT\BOOTX64.EFI for
64 bit x86 processors. The partition start block 3989132 in 512-byte units
matches the start block of the EFI El Torito image 997283 in 2048-byte
units. So both are the same byte range. (El Torito addresses in 2048 but
counts size in 512. Shrug.)

ISOs can have an MBR and partition tables, because the ISO 9660 specs
reserve the first 32 KB of the filesystem range for arbitrary "System Use".

-------------------------------------------------------------------------

It is indeed a bad sign if the drive sometimes recognizes a particular 
medium and sometimes does not. It is not plausible that it would work
reproducibly better with MS-Windows than with GNU/Linux. The recognition
happens in the drive by its own firmware. Operating systems and burn
programs inquire the recognized status by standardized SCSI commands.
There is few room for artsy variations with this task.

But statistics can be a bitch. It might need a lot of tries until you
get similar success/failure rates in both groups of experiments.

Have a nice day :)

Thomas

---

### Post by John_Patrick_Mason on 2019-11-22
Just received the DVD burner, but I'm a bit nervous; when I opened the box from Amazon, and looked at the back of the box from the manufacturer (inside the Amazon box), it only said DVD**-**RW. That's weird, because on the [product page on Amazon]("https://www.amazon.com/gp/product/B07FD4YCV2/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1"), it specifically says, "DVD**+/-**RW." I'm really worried now that there's a chance the drive may not be compatible with both formats. Now that I think of it, this reminds me of an article I read in Ars Technica, a while back, about how many third-party sellers on Amazon intentionally mislabel their products in order to get more people to buy them. I thought almost all DVD drives sold today were compatible with both formats, so maybe the drive is still compatible with both formats.

Anyway, I did a

```

sudo tail -f /var/log/syslog

```

to get the device name of the external drive, and repeated the instructions from before using the same xorriso-burned DVD from earlier by typing:

```

xorriso -outdev /dev/sr1 -toc

```

which gave me:

```

xorriso 1.4.2 : RockRidge filesystem manipulator, libburnia project.

xorriso : NOTE : Disc status unsuitable for writing
Drive current: -outdev '/dev/sr1'
Media current: DVD+R
Media status : is written , is closed
Drive current: -outdev '/dev/sr1'
Drive type   : vendor 'HL-DT-ST' product 'DVDRAM GT80N' revision '1.01'
Drive id     : 'KZ5D9H24934 '
Media current: DVD+R
Media product: AML/003/48 , UML
Media status : is written , is closed
Media blocks : 0 readable , 0 writable , 0 overall
TOC layout   : Idx ,  sbsector ,       Size , Volume Id
xorriso : SORRY : Cannot obtain Table Of Content
xorriso : NOTE : Tolerated problem event of severity 'SORRY'
xorriso : NOTE : -return_with SORRY 32 triggered by problem severity SORRY

```

and, then, proceeded to type:

```

xorriso -outdev /dev/sr1 -check_media use=outdev --

```

which gave:

```

xorriso 1.4.2 : RockRidge filesystem manipulator, libburnia project.

xorriso : NOTE : Disc status unsuitable for writing
Drive current: -outdev '/dev/sr1'
Media current: DVD+R
Media status : is written , is closed
xorriso : FAILURE : No content detected on media
xorriso : aborting : -abort_on 'FAILURE' encountered 'FAILURE'

```

Edit: I just looked up the model and manufacturer with the help of the above information to check if the drive is compatible with both formats. At first, it's not at all obvious what the model and manufacturer of the drive is, but it looks like the drive is compatible with my DVD+Rs. I think Roofull is one of those white-label companies that rebrands drives that are sold to multiple companies.

---

### Post by scdbackup on 2019-11-22
Hi,

> using the same xorriso-burned DVD from earlier 
```

Drive type   : vendor 'HL-DT-ST' product 'DVDRAM GT80N' revision '1.01'
Drive id     : 'KZ5D9H24934 '
Media current: DVD+R
Media product: AML/003/48 , UML
Media status : is written , is closed
Media blocks : 0 readable , 0 writable , 0 overall
TOC layout   : Idx ,  sbsector ,       Size , Volume Id
xorriso : SORRY : Cannot obtain Table Of Content
xorriso : NOTE : Tolerated problem event of severity 'SORRY'
xorriso : NOTE : -return_with SORRY 32 triggered by problem severity SORRY

```
Well, that medium is dead. Closed and 0 bytes.

> it only said DVD-RW. 

They simply do all DVD types, nowadays.
You can inquire its list of supported media by:
```

xorriso -outdev /dev/sr1 -list_profiles

```
which with a typical DVD burner should look like:
```

Profile      : 0x0015 (DVD-R/DL sequential recording)
Profile      : 0x0016 (DVD-R/DL layer jump recording)
Profile      : 0x002B (DVD+R/DL)
Profile      : 0x001B (DVD+R)
Profile      : 0x001A (DVD+RW)
Profile      : 0x0014 (DVD-RW sequential recording)
Profile      : 0x0013 (DVD-RW restricted overwrite)
Profile      : 0x0012 (DVD-RAM)
Profile      : 0x0011 (DVD-R sequential recording)
Profile      : 0x0010 (DVD-ROM)
Profile      : 0x000A (CD-RW)
Profile      : 0x0009 (CD-R)
Profile      : 0x0008 (CD-ROM)
Profile      : 0x0002 (Removable disk)

```
An SCSI profile is a set of SCSI features which bundle sets of SCSI commands
and parameters. Sometimes one medium type can be burned according to more
than one profile. (DVD-ROM, CD-ROM, Removable disk are read-only profiles.)
But roughly you can tell that if it says "DVD+R" then it believes to
be able to burn DVD+R according to the good habits described in MMC-6.


> I think Roofull is one of those white-label companies that rebrands
> drives that are sold to multiple companies

It is made by LG. "HL-DT-ST" = Hitachi-LG Data Storage.
  [https://en.wikipedia.org/wiki/Hitachi-LG_Data_Storage](https://en.wikipedia.org/wiki/Hitachi-LG_Data_Storage)
  [https://www.lg.com/us/burners-drives/lg-GT80N-internal-dvd-writer](https://www.lg.com/us/burners-drives/lg-GT80N-internal-dvd-writer)

Now try whether it burns a yet unused DVD+R with your favorite burn program.

Have a nice day :)

Thomas

---

### Post by John_Patrick_Mason on 2019-11-22
I used K3b to burn and verify the disc, and was able to successfully  boot from the resulting burned DVD. So, what do you think the problem was, a  malfunctioning CD/DVD drive?

Also, when you write:

[QUOTE=scdbackup]
Well, that medium is dead. Closed and 0 bytes.
[/QUOTE]

by closed, you mean the xorriso-burned DVD can no longer be written to, correct?

Lastly, I'm having trouble verifying the md5sums using CatKiller's method with:

```

md5sum -c /media/mason/"Ubuntu 18.04.3 LTS amd64"/md5sum.txt

```

This is what I get if I type the above command:

```

md5sum: ./pics/red-upperleft.png: No such file or directory
./pics/red-upperleft.png: FAILED open or read
md5sum: ./pics/red-lowerleft.png: No such file or directory
./pics/red-lowerleft.png: FAILED open or read
md5sum: ./pics/blue-lowerleft.png: No such file or directory
./pics/blue-lowerleft.png: FAILED open or read
md5sum: ./pics/logo-50.jpg: No such file or directory
./pics/logo-50.jpg: FAILED open or read
md5sum: ./pics/blue-upperright.png: No such file or directory
./pics/blue-upperright.png: FAILED open or read
md5sum: ./pics/blue-lowerright.png: No such file or directory
./pics/blue-lowerright.png: FAILED open or read
md5sum: ./pics/red-lowerright.png: No such file or directory
./pics/red-lowerright.png: FAILED open or read
md5sum: ./pics/blue-upperleft.png: No such file or directory
./pics/blue-upperleft.png: FAILED open or read
md5sum: ./pics/debian.jpg: No such file or directory
./pics/debian.jpg: FAILED open or read
md5sum: ./pics/red-upperright.png: No such file or directory
./pics/red-upperright.png: FAILED open or read
md5sum: ./preseed/ubuntu.seed: No such file or directory
./preseed/ubuntu.seed: FAILED open or read
md5sum: ./preseed/ltsp.seed: No such file or directory
./preseed/ltsp.seed: FAILED open or read
md5sum: ./preseed/cli.seed: No such file or directory
./preseed/cli.seed: FAILED open or read
md5sum: ./pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb: No such file or directory
./pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb: FAILED open or read
md5sum: ./pool/main/m/mouseemu/mouseemu_0.16-0ubuntu10_amd64.deb: No such file or directory
./pool/main/m/mouseemu/mouseemu_0.16-0ubuntu10_amd64.deb: FAILED open or read
md5sum: ./pool/main/m/manpages/manpages-dev_4.15-1_all.deb: No such file or directory
./pool/main/m/manpages/manpages-dev_4.15-1_all.deb: FAILED open or read
md5sum: ./pool/main/m/make-dfsg/make_4.1-9.1ubuntu1_amd64.deb: No such file or directory
./pool/main/m/make-dfsg/make_4.1-9.1ubuntu1_amd64.deb: FAILED open or read
md5sum: ./pool/main/l/linux/linux-libc-dev_4.15.0-55.60_amd64.deb: No such file or directory
./pool/main/l/linux/linux-libc-dev_4.15.0-55.60_amd64.deb: FAILED open or read
md5sum: ./pool/main/l/lupin/lupin-support_0.57build1_amd64.deb: No such file or directory
./pool/main/l/lupin/lupin-support_0.57build1_amd64.deb: FAILED open or read
md5sum: ./pool/main/s/shim-signed/shim-signed_1.37~18.04.3+15+1533136590.3beb971-0ubuntu1_amd64.deb: No such file or directory
./pool/main/s/shim-signed/shim-signed_1.37~18.04.3+15+1533136590.3beb971-0ubuntu1_amd64.deb: FAILED open or read
md5sum: ./pool/main/s/shim/shim_15+1533136590.3beb971-0ubuntu1_amd64.deb: No such file or directory
./pool/main/s/shim/shim_15+1533136590.3beb971-0ubuntu1_amd64.deb: FAILED open or read
md5sum: ./pool/main/s/setserial/setserial_2.17-50_amd64.deb: No such file or directory
./pool/main/s/setserial/setserial_2.17-50_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-7/libstdc++-7-dev_7.4.0-1ubuntu1~18.04.1_amd64.deb: No such file or directory
./pool/main/g/gcc-7/libstdc++-7-dev_7.4.0-1ubuntu1~18.04.1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-7/libasan4_7.4.0-1ubuntu1~18.04.1_amd64.deb: No such file or directory
./pool/main/g/gcc-7/libasan4_7.4.0-1ubuntu1~18.04.1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-7/libubsan0_7.4.0-1ubuntu1~18.04.1_amd64.deb: No such file or directory
./pool/main/g/gcc-7/libubsan0_7.4.0-1ubuntu1~18.04.1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-7/libgcc-7-dev_7.4.0-1ubuntu1~18.04.1_amd64.deb: No such file or directory
./pool/main/g/gcc-7/libgcc-7-dev_7.4.0-1ubuntu1~18.04.1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-7/g++-7_7.4.0-1ubuntu1~18.04.1_amd64.deb: No such file or directory
./pool/main/g/gcc-7/g++-7_7.4.0-1ubuntu1~18.04.1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-7/libcilkrts5_7.4.0-1ubuntu1~18.04.1_amd64.deb: No such file or directory
./pool/main/g/gcc-7/libcilkrts5_7.4.0-1ubuntu1~18.04.1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-7/gcc-7_7.4.0-1ubuntu1~18.04.1_amd64.deb: No such file or directory
./pool/main/g/gcc-7/gcc-7_7.4.0-1ubuntu1~18.04.1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-defaults/g++_7.4.0-1ubuntu2.3_amd64.deb: No such file or directory
./pool/main/g/gcc-defaults/g++_7.4.0-1ubuntu2.3_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-defaults/gcc_7.4.0-1ubuntu2.3_amd64.deb: No such file or directory
./pool/main/g/gcc-defaults/gcc_7.4.0-1ubuntu2.3_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/grub2/grub-efi-amd64-bin_2.02-2ubuntu8.13_amd64.deb: No such file or directory
./pool/main/g/grub2/grub-efi-amd64-bin_2.02-2ubuntu8.13_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/grub2/grub-efi-amd64_2.02-2ubuntu8.13_amd64.deb: No such file or directory
./pool/main/g/grub2/grub-efi-amd64_2.02-2ubuntu8.13_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/grub2/grub-efi_2.02-2ubuntu8.13_amd64.deb: No such file or directory
./pool/main/g/grub2/grub-efi_2.02-2ubuntu8.13_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/glibc/libc-dev-bin_2.27-3ubuntu1_amd64.deb: No such file or directory
./pool/main/g/glibc/libc-dev-bin_2.27-3ubuntu1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/glibc/libc6-dev_2.27-3ubuntu1_amd64.deb: No such file or directory
./pool/main/g/glibc/libc6-dev_2.27-3ubuntu1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/grub2-signed/grub-efi-amd64-signed_1.93.14+2.02-2ubuntu8.13_amd64.deb: No such file or directory
./pool/main/g/grub2-signed/grub-efi-amd64-signed_1.93.14+2.02-2ubuntu8.13_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-8/libtsan0_8.3.0-6ubuntu1~18.04.1_amd64.deb: No such file or directory
./pool/main/g/gcc-8/libtsan0_8.3.0-6ubuntu1~18.04.1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-8/libmpx2_8.3.0-6ubuntu1~18.04.1_amd64.deb: No such file or directory
./pool/main/g/gcc-8/libmpx2_8.3.0-6ubuntu1~18.04.1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-8/libatomic1_8.3.0-6ubuntu1~18.04.1_amd64.deb: No such file or directory
./pool/main/g/gcc-8/libatomic1_8.3.0-6ubuntu1~18.04.1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-8/liblsan0_8.3.0-6ubuntu1~18.04.1_amd64.deb: No such file or directory
./pool/main/g/gcc-8/liblsan0_8.3.0-6ubuntu1~18.04.1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-8/libquadmath0_8.3.0-6ubuntu1~18.04.1_amd64.deb: No such file or directory
./pool/main/g/gcc-8/libquadmath0_8.3.0-6ubuntu1~18.04.1_amd64.deb: FAILED open or read
md5sum: ./pool/main/g/gcc-8/libitm1_8.3.0-6ubuntu1~18.04.1_amd64.deb: No such file or directory
./pool/main/g/gcc-8/libitm1_8.3.0-6ubuntu1~18.04.1_amd64.deb: FAILED open or read
md5sum: ./pool/main/b/build-essential/build-essential_12.4ubuntu1_amd64.deb: No such file or directory
./pool/main/b/build-essential/build-essential_12.4ubuntu1_amd64.deb: FAILED open or read
md5sum: ./pool/main/b/b43-fwcutter/b43-fwcutter_019-3_amd64.deb: No such file or directory
./pool/main/b/b43-fwcutter/b43-fwcutter_019-3_amd64.deb: FAILED open or read
md5sum: ./pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-5_amd64.deb: No such file or directory
./pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-5_amd64.deb: FAILED open or read
md5sum: ./pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-3_all.deb: No such file or directory
./pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-3_all.deb: FAILED open or read
md5sum: ./pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.03-1_all.deb: No such file or directory
./pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.03-1_all.deb: FAILED open or read
md5sum: ./pool/main/u/user-setup/user-setup_1.63ubuntu5_all.deb: No such file or directory
./pool/main/u/user-setup/user-setup_1.63ubuntu5_all.deb: FAILED open or read
md5sum: ./pool/main/u/ubiquity/oem-config_18.04.14.12_all.deb: No such file or directory
./pool/main/u/ubiquity/oem-config_18.04.14.12_all.deb: FAILED open or read
md5sum: ./pool/main/u/ubiquity/oem-config-gtk_18.04.14.12_all.deb: No such file or directory
./pool/main/u/ubiquity/oem-config-gtk_18.04.14.12_all.deb: FAILED open or read
md5sum: ./pool/main/u/ubiquity-slideshow-ubuntu/oem-config-slideshow-ubuntu_138_all.deb: No such file or directory
./pool/main/u/ubiquity-slideshow-ubuntu/oem-config-slideshow-ubuntu_138_all.deb: FAILED open or read
md5sum: ./pool/main/d/dkms/dkms_2.3-3ubuntu9.5_all.deb: No such file or directory
./pool/main/d/dkms/dkms_2.3-3ubuntu9.5_all.deb: FAILED open or read
md5sum: ./pool/main/d/dpkg/dpkg-dev_1.19.0.5ubuntu2.1_all.deb: No such file or directory
./pool/main/d/dpkg/dpkg-dev_1.19.0.5ubuntu2.1_all.deb: FAILED open or read
md5sum: ./pool/main/f/fakeroot/fakeroot_1.22-2ubuntu1_amd64.deb: No such file or directory
./pool/main/f/fakeroot/fakeroot_1.22-2ubuntu1_amd64.deb: FAILED open or read
md5sum: ./pool/main/f/fakeroot/libfakeroot_1.22-2ubuntu1_amd64.deb: No such file or directory
./pool/main/f/fakeroot/libfakeroot_1.22-2ubuntu1_amd64.deb: FAILED open or read
md5sum: ./.disk/info: No such file or directory
./.disk/info: FAILED open or read
md5sum: ./.disk/base_installable: No such file or directory
./.disk/base_installable: FAILED open or read
md5sum: ./.disk/casper-uuid-generic: No such file or directory
./.disk/casper-uuid-generic: FAILED open or read
md5sum: ./.disk/cd_type: No such file or directory
./.disk/cd_type: FAILED open or read
md5sum: ./.disk/release_notes_url: No such file or directory
./.disk/release_notes_url: FAILED open or read
md5sum: ./EFI/BOOT/BOOTx64.EFI: No such file or directory
./EFI/BOOT/BOOTx64.EFI: FAILED open or read
md5sum: ./EFI/BOOT/grubx64.efi: No such file or directory
./EFI/BOOT/grubx64.efi: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/chain.mod: No such file or directory
./boot/grub/x86_64-efi/chain.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/blocklist.mod: No such file or directory
./boot/grub/x86_64-efi/blocklist.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/spkmodem.mod: No such file or directory
./boot/grub/x86_64-efi/spkmodem.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/loopback.mod: No such file or directory
./boot/grub/x86_64-efi/loopback.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/pata.mod: No such file or directory
./boot/grub/x86_64-efi/pata.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/echo.mod: No such file or directory
./boot/grub/x86_64-efi/echo.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/lsacpi.mod: No such file or directory
./boot/grub/x86_64-efi/lsacpi.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_sha256.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_sha256.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cbls.mod: No such file or directory
./boot/grub/x86_64-efi/cbls.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/part_acorn.mod: No such file or directory
./boot/grub/x86_64-efi/part_acorn.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/ctz_test.mod: No such file or directory
./boot/grub/x86_64-efi/ctz_test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/videotest.mod: No such file or directory
./boot/grub/x86_64-efi/videotest.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gettext.mod: No such file or directory
./boot/grub/x86_64-efi/gettext.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/iorw.mod: No such file or directory
./boot/grub/x86_64-efi/iorw.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/acpi.mod: No such file or directory
./boot/grub/x86_64-efi/acpi.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/part_sun.mod: No such file or directory
./boot/grub/x86_64-efi/part_sun.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/terminfo.mod: No such file or directory
./boot/grub/x86_64-efi/terminfo.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/minix3_be.mod: No such file or directory
./boot/grub/x86_64-efi/minix3_be.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/ohci.mod: No such file or directory
./boot/grub/x86_64-efi/ohci.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_arcfour.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_arcfour.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/raid6rec.mod: No such file or directory
./boot/grub/x86_64-efi/raid6rec.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gfxmenu.mod: No such file or directory
./boot/grub/x86_64-efi/gfxmenu.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/xnu_uuid_test.mod: No such file or directory
./boot/grub/x86_64-efi/xnu_uuid_test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/morse.mod: No such file or directory
./boot/grub/x86_64-efi/morse.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/efi_uga.mod: No such file or directory
./boot/grub/x86_64-efi/efi_uga.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/part_apple.mod: No such file or directory
./boot/grub/x86_64-efi/part_apple.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/video_bochs.mod: No such file or directory
./boot/grub/x86_64-efi/video_bochs.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/dm_nv.mod: No such file or directory
./boot/grub/x86_64-efi/dm_nv.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_camellia.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_camellia.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/multiboot2.mod: No such file or directory
./boot/grub/x86_64-efi/multiboot2.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/bitmap.mod: No such file or directory
./boot/grub/x86_64-efi/bitmap.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/part_plan.mod: No such file or directory
./boot/grub/x86_64-efi/part_plan.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/usb_keyboard.mod: No such file or directory
./boot/grub/x86_64-efi/usb_keyboard.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/efifwsetup.mod: No such file or directory
./boot/grub/x86_64-efi/efifwsetup.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/part_amiga.mod: No such file or directory
./boot/grub/x86_64-efi/part_amiga.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/parttool.lst: No such file or directory
./boot/grub/x86_64-efi/parttool.lst: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/boot.mod: No such file or directory
./boot/grub/x86_64-efi/boot.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/hfs.mod: No such file or directory
./boot/grub/x86_64-efi/hfs.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/eval.mod: No such file or directory
./boot/grub/x86_64-efi/eval.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/partmap.lst: No such file or directory
./boot/grub/x86_64-efi/partmap.lst: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/adler32.mod: No such file or directory
./boot/grub/x86_64-efi/adler32.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/div.mod: No such file or directory
./boot/grub/x86_64-efi/div.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/btrfs.mod: No such file or directory
./boot/grub/x86_64-efi/btrfs.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_serpent.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_serpent.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/setjmp_test.mod: No such file or directory
./boot/grub/x86_64-efi/setjmp_test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cpio_be.mod: No such file or directory
./boot/grub/x86_64-efi/cpio_be.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/tftp.mod: No such file or directory
./boot/grub/x86_64-efi/tftp.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/lsefi.mod: No such file or directory
./boot/grub/x86_64-efi/lsefi.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/xnu_uuid.mod: No such file or directory
./boot/grub/x86_64-efi/xnu_uuid.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/test.mod: No such file or directory
./boot/grub/x86_64-efi/test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/syslinuxcfg.mod: No such file or directory
./boot/grub/x86_64-efi/syslinuxcfg.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/test_blockarg.mod: No such file or directory
./boot/grub/x86_64-efi/test_blockarg.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/mul_test.mod: No such file or directory
./boot/grub/x86_64-efi/mul_test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/part_msdos.mod: No such file or directory
./boot/grub/x86_64-efi/part_msdos.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/datetime.mod: No such file or directory
./boot/grub/x86_64-efi/datetime.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/keystatus.mod: No such file or directory
./boot/grub/x86_64-efi/keystatus.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/password.mod: No such file or directory
./boot/grub/x86_64-efi/password.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/lsefimmap.mod: No such file or directory
./boot/grub/x86_64-efi/lsefimmap.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/halt.mod: No such file or directory
./boot/grub/x86_64-efi/halt.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/luks.mod: No such file or directory
./boot/grub/x86_64-efi/luks.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/video.lst: No such file or directory
./boot/grub/x86_64-efi/video.lst: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/macbless.mod: No such file or directory
./boot/grub/x86_64-efi/macbless.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/geli.mod: No such file or directory
./boot/grub/x86_64-efi/geli.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_tiger.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_tiger.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_rmd160.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_rmd160.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/part_sunpc.mod: No such file or directory
./boot/grub/x86_64-efi/part_sunpc.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/raid5rec.mod: No such file or directory
./boot/grub/x86_64-efi/raid5rec.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/lspci.mod: No such file or directory
./boot/grub/x86_64-efi/lspci.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/terminal.lst: No such file or directory
./boot/grub/x86_64-efi/terminal.lst: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/crypto.lst: No such file or directory
./boot/grub/x86_64-efi/crypto.lst: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/jpeg.mod: No such file or directory
./boot/grub/x86_64-efi/jpeg.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/video_fb.mod: No such file or directory
./boot/grub/x86_64-efi/video_fb.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/datehook.mod: No such file or directory
./boot/grub/x86_64-efi/datehook.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cbtable.mod: No such file or directory
./boot/grub/x86_64-efi/cbtable.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/mpi.mod: No such file or directory
./boot/grub/x86_64-efi/mpi.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_rijndael.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_rijndael.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/videoinfo.mod: No such file or directory
./boot/grub/x86_64-efi/videoinfo.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/file.mod: No such file or directory
./boot/grub/x86_64-efi/file.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/testload.mod: No such file or directory
./boot/grub/x86_64-efi/testload.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_twofish.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_twofish.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/lsefisystab.mod: No such file or directory
./boot/grub/x86_64-efi/lsefisystab.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/usbserial_usbdebug.mod: No such file or directory
./boot/grub/x86_64-efi/usbserial_usbdebug.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/xfs.mod: No such file or directory
./boot/grub/x86_64-efi/xfs.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/minix3.mod: No such file or directory
./boot/grub/x86_64-efi/minix3.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/ntfscomp.mod: No such file or directory
./boot/grub/x86_64-efi/ntfscomp.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/minix2.mod: No such file or directory
./boot/grub/x86_64-efi/minix2.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/uhci.mod: No such file or directory
./boot/grub/x86_64-efi/uhci.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/testspeed.mod: No such file or directory
./boot/grub/x86_64-efi/testspeed.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/jfs.mod: No such file or directory
./boot/grub/x86_64-efi/jfs.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/help.mod: No such file or directory
./boot/grub/x86_64-efi/help.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/offsetio.mod: No such file or directory
./boot/grub/x86_64-efi/offsetio.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/videotest_checksum.mod: No such file or directory
./boot/grub/x86_64-efi/videotest_checksum.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/video_colors.mod: No such file or directory
./boot/grub/x86_64-efi/video_colors.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/usb.mod: No such file or directory
./boot/grub/x86_64-efi/usb.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/zfscrypt.mod: No such file or directory
./boot/grub/x86_64-efi/zfscrypt.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/setpci.mod: No such file or directory
./boot/grub/x86_64-efi/setpci.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/bswap_test.mod: No such file or directory
./boot/grub/x86_64-efi/bswap_test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/diskfilter.mod: No such file or directory
./boot/grub/x86_64-efi/diskfilter.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cat.mod: No such file or directory
./boot/grub/x86_64-efi/cat.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/minicmd.mod: No such file or directory
./boot/grub/x86_64-efi/minicmd.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/msdospart.mod: No such file or directory
./boot/grub/x86_64-efi/msdospart.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/part_bsd.mod: No such file or directory
./boot/grub/x86_64-efi/part_bsd.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_rsa.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_rsa.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/exfctest.mod: No such file or directory
./boot/grub/x86_64-efi/exfctest.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/lvm.mod: No such file or directory
./boot/grub/x86_64-efi/lvm.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/progress.mod: No such file or directory
./boot/grub/x86_64-efi/progress.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_sha512.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_sha512.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/romfs.mod: No such file or directory
./boot/grub/x86_64-efi/romfs.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gfxterm_menu.mod: No such file or directory
./boot/grub/x86_64-efi/gfxterm_menu.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/ufs1_be.mod: No such file or directory
./boot/grub/x86_64-efi/ufs1_be.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/newc.mod: No such file or directory
./boot/grub/x86_64-efi/newc.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/true.mod: No such file or directory
./boot/grub/x86_64-efi/true.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/aout.mod: No such file or directory
./boot/grub/x86_64-efi/aout.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gfxterm_background.mod: No such file or directory
./boot/grub/x86_64-efi/gfxterm_background.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_md4.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_md4.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/shift_test.mod: No such file or directory
./boot/grub/x86_64-efi/shift_test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/verify.mod: No such file or directory
./boot/grub/x86_64-efi/verify.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/ehci.mod: No such file or directory
./boot/grub/x86_64-efi/ehci.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/video.mod: No such file or directory
./boot/grub/x86_64-efi/video.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/http.mod: No such file or directory
./boot/grub/x86_64-efi/http.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_des.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_des.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cryptodisk.mod: No such file or directory
./boot/grub/x86_64-efi/cryptodisk.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/usbserial_common.mod: No such file or directory
./boot/grub/x86_64-efi/usbserial_common.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/backtrace.mod: No such file or directory
./boot/grub/x86_64-efi/backtrace.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/fat.mod: No such file or directory
./boot/grub/x86_64-efi/fat.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/xnu.mod: No such file or directory
./boot/grub/x86_64-efi/xnu.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/lssal.mod: No such file or directory
./boot/grub/x86_64-efi/lssal.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/efinet.mod: No such file or directory
./boot/grub/x86_64-efi/efinet.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/div_test.mod: No such file or directory
./boot/grub/x86_64-efi/div_test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/grub.cfg: No such file or directory
./boot/grub/x86_64-efi/grub.cfg: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/crc64.mod: No such file or directory
./boot/grub/x86_64-efi/crc64.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/pcidump.mod: No such file or directory
./boot/grub/x86_64-efi/pcidump.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/date.mod: No such file or directory
./boot/grub/x86_64-efi/date.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/parttool.mod: No such file or directory
./boot/grub/x86_64-efi/parttool.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/ldm.mod: No such file or directory
./boot/grub/x86_64-efi/ldm.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_sha1.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_sha1.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/memrw.mod: No such file or directory
./boot/grub/x86_64-efi/memrw.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_crc.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_crc.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/png.mod: No such file or directory
./boot/grub/x86_64-efi/png.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/hfspluscomp.mod: No such file or directory
./boot/grub/x86_64-efi/hfspluscomp.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/hexdump.mod: No such file or directory
./boot/grub/x86_64-efi/hexdump.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/ntfs.mod: No such file or directory
./boot/grub/x86_64-efi/ntfs.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/keylayouts.mod: No such file or directory
./boot/grub/x86_64-efi/keylayouts.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_md5.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_md5.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_dsa.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_dsa.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/bfs.mod: No such file or directory
./boot/grub/x86_64-efi/bfs.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/usbserial_ftdi.mod: No such file or directory
./boot/grub/x86_64-efi/usbserial_ftdi.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/sleep_test.mod: No such file or directory
./boot/grub/x86_64-efi/sleep_test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/efi_gop.mod: No such file or directory
./boot/grub/x86_64-efi/efi_gop.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_whirlpool.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_whirlpool.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/lzopio.mod: No such file or directory
./boot/grub/x86_64-efi/lzopio.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/at_keyboard.mod: No such file or directory
./boot/grub/x86_64-efi/at_keyboard.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gptsync.mod: No such file or directory
./boot/grub/x86_64-efi/gptsync.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/minix2_be.mod: No such file or directory
./boot/grub/x86_64-efi/minix2_be.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/relocator.mod: No such file or directory
./boot/grub/x86_64-efi/relocator.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/hashsum.mod: No such file or directory
./boot/grub/x86_64-efi/hashsum.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/usbserial_pl2303.mod: No such file or directory
./boot/grub/x86_64-efi/usbserial_pl2303.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/mdraid09.mod: No such file or directory
./boot/grub/x86_64-efi/mdraid09.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/ata.mod: No such file or directory
./boot/grub/x86_64-efi/ata.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/ufs1.mod: No such file or directory
./boot/grub/x86_64-efi/ufs1.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/procfs.mod: No such file or directory
./boot/grub/x86_64-efi/procfs.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/elf.mod: No such file or directory
./boot/grub/x86_64-efi/elf.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gfxterm.mod: No such file or directory
./boot/grub/x86_64-efi/gfxterm.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cpio.mod: No such file or directory
./boot/grub/x86_64-efi/cpio.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/ls.mod: No such file or directory
./boot/grub/x86_64-efi/ls.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/mmap.mod: No such file or directory
./boot/grub/x86_64-efi/mmap.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/odc.mod: No such file or directory
./boot/grub/x86_64-efi/odc.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/hfsplus.mod: No such file or directory
./boot/grub/x86_64-efi/hfsplus.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/crypto.mod: No such file or directory
./boot/grub/x86_64-efi/crypto.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_idea.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_idea.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/net.mod: No such file or directory
./boot/grub/x86_64-efi/net.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_rfc2268.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_rfc2268.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/legacycfg.mod: No such file or directory
./boot/grub/x86_64-efi/legacycfg.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/pbkdf2_test.mod: No such file or directory
./boot/grub/x86_64-efi/pbkdf2_test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cpuid.mod: No such file or directory
./boot/grub/x86_64-efi/cpuid.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/bsd.mod: No such file or directory
./boot/grub/x86_64-efi/bsd.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/part_dvh.mod: No such file or directory
./boot/grub/x86_64-efi/part_dvh.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/sleep.mod: No such file or directory
./boot/grub/x86_64-efi/sleep.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/fixvideo.mod: No such file or directory
./boot/grub/x86_64-efi/fixvideo.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/setjmp.mod: No such file or directory
./boot/grub/x86_64-efi/setjmp.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/read.mod: No such file or directory
./boot/grub/x86_64-efi/read.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/random.mod: No such file or directory
./boot/grub/x86_64-efi/random.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/macho.mod: No such file or directory
./boot/grub/x86_64-efi/macho.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_blowfish.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_blowfish.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/squash4.mod: No such file or directory
./boot/grub/x86_64-efi/squash4.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/multiboot.mod: No such file or directory
./boot/grub/x86_64-efi/multiboot.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/password_pbkdf2.mod: No such file or directory
./boot/grub/x86_64-efi/password_pbkdf2.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/ext2.mod: No such file or directory
./boot/grub/x86_64-efi/ext2.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/bitmap_scale.mod: No such file or directory
./boot/grub/x86_64-efi/bitmap_scale.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cmp_test.mod: No such file or directory
./boot/grub/x86_64-efi/cmp_test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/archelp.mod: No such file or directory
./boot/grub/x86_64-efi/archelp.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/moddep.lst: No such file or directory
./boot/grub/x86_64-efi/moddep.lst: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/mdraid1x.mod: No such file or directory
./boot/grub/x86_64-efi/mdraid1x.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/reiserfs.mod: No such file or directory
./boot/grub/x86_64-efi/reiserfs.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cmp.mod: No such file or directory
./boot/grub/x86_64-efi/cmp.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/fs.lst: No such file or directory
./boot/grub/x86_64-efi/fs.lst: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/loadbios.mod: No such file or directory
./boot/grub/x86_64-efi/loadbios.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/linuxefi.mod: No such file or directory
./boot/grub/x86_64-efi/linuxefi.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/hdparm.mod: No such file or directory
./boot/grub/x86_64-efi/hdparm.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/signature_test.mod: No such file or directory
./boot/grub/x86_64-efi/signature_test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cbtime.mod: No such file or directory
./boot/grub/x86_64-efi/cbtime.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cbmemc.mod: No such file or directory
./boot/grub/x86_64-efi/cbmemc.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/command.lst: No such file or directory
./boot/grub/x86_64-efi/command.lst: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/scsi.mod: No such file or directory
./boot/grub/x86_64-efi/scsi.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/tr.mod: No such file or directory
./boot/grub/x86_64-efi/tr.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/play.mod: No such file or directory
./boot/grub/x86_64-efi/play.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/ufs2.mod: No such file or directory
./boot/grub/x86_64-efi/ufs2.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/mdraid09_be.mod: No such file or directory
./boot/grub/x86_64-efi/mdraid09_be.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/loadenv.mod: No such file or directory
./boot/grub/x86_64-efi/loadenv.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/all_video.mod: No such file or directory
./boot/grub/x86_64-efi/all_video.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/linux16.mod: No such file or directory
./boot/grub/x86_64-efi/linux16.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/xzio.mod: No such file or directory
./boot/grub/x86_64-efi/xzio.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/font.mod: No such file or directory
./boot/grub/x86_64-efi/font.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/ahci.mod: No such file or directory
./boot/grub/x86_64-efi/ahci.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/time.mod: No such file or directory
./boot/grub/x86_64-efi/time.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/part_dfly.mod: No such file or directory
./boot/grub/x86_64-efi/part_dfly.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/appleldr.mod: No such file or directory
./boot/grub/x86_64-efi/appleldr.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cs5536.mod: No such file or directory
./boot/grub/x86_64-efi/cs5536.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/linux.mod: No such file or directory
./boot/grub/x86_64-efi/linux.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_cast5.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_cast5.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/reboot.mod: No such file or directory
./boot/grub/x86_64-efi/reboot.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/lsmmap.mod: No such file or directory
./boot/grub/x86_64-efi/lsmmap.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gzio.mod: No such file or directory
./boot/grub/x86_64-efi/gzio.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/usbtest.mod: No such file or directory
./boot/grub/x86_64-efi/usbtest.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/legacy_password_test.mod: No such file or directory
./boot/grub/x86_64-efi/legacy_password_test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/bufio.mod: No such file or directory
./boot/grub/x86_64-efi/bufio.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/udf.mod: No such file or directory
./boot/grub/x86_64-efi/udf.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/pbkdf2.mod: No such file or directory
./boot/grub/x86_64-efi/pbkdf2.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/video_cirrus.mod: No such file or directory
./boot/grub/x86_64-efi/video_cirrus.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/nativedisk.mod: No such file or directory
./boot/grub/x86_64-efi/nativedisk.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/disk.mod: No such file or directory
./boot/grub/x86_64-efi/disk.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cbfs.mod: No such file or directory
./boot/grub/x86_64-efi/cbfs.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/cmdline_cat_test.mod: No such file or directory
./boot/grub/x86_64-efi/cmdline_cat_test.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/regexp.mod: No such file or directory
./boot/grub/x86_64-efi/regexp.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/minix_be.mod: No such file or directory
./boot/grub/x86_64-efi/minix_be.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/priority_queue.mod: No such file or directory
./boot/grub/x86_64-efi/priority_queue.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/trig.mod: No such file or directory
./boot/grub/x86_64-efi/trig.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/tga.mod: No such file or directory
./boot/grub/x86_64-efi/tga.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/usbms.mod: No such file or directory
./boot/grub/x86_64-efi/usbms.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/terminal.mod: No such file or directory
./boot/grub/x86_64-efi/terminal.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/gcry_seed.mod: No such file or directory
./boot/grub/x86_64-efi/gcry_seed.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/exfat.mod: No such file or directory
./boot/grub/x86_64-efi/exfat.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/serial.mod: No such file or directory
./boot/grub/x86_64-efi/serial.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/probe.mod: No such file or directory
./boot/grub/x86_64-efi/probe.mod: FAILED open or read
md5sum: ./boot/grub/x86_64-efi/part_gpt.mod: No such file or directory
./boot/grub/x86_64-efi/part_gpt.mod: FAILED open or read
md5sum: ./boot/grub/efi.img: No such file or directory
./boot/grub/efi.img: FAILED open or read
md5sum: ./boot/grub/grub.cfg: No such file or directory
./boot/grub/grub.cfg: FAILED open or read
md5sum: ./boot/grub/loopback.cfg: No such file or directory
./boot/grub/loopback.cfg: FAILED open or read
md5sum: ./boot/grub/font.pf2: No such file or directory
./boot/grub/font.pf2: FAILED open or read
md5sum: ./casper/filesystem.size: No such file or directory
./casper/filesystem.size: FAILED open or read
md5sum: ./casper/filesystem.manifest: No such file or directory
./casper/filesystem.manifest: FAILED open or read
md5sum: ./casper/filesystem.squashfs: No such file or directory
./casper/filesystem.squashfs: FAILED open or read
md5sum: ./casper/filesystem.squashfs.gpg: No such file or directory
./casper/filesystem.squashfs.gpg: FAILED open or read
md5sum: ./casper/initrd: No such file or directory
./casper/initrd: FAILED open or read
md5sum: ./casper/filesystem.manifest-minimal-remove: No such file or directory
./casper/filesystem.manifest-minimal-remove: FAILED open or read
md5sum: ./casper/filesystem.manifest-remove: No such file or directory
./casper/filesystem.manifest-remove: FAILED open or read
md5sum: ./casper/vmlinuz: No such file or directory
./casper/vmlinuz: FAILED open or read
md5sum: ./README.diskdefines: No such file or directory
./README.diskdefines: FAILED open or read
md5sum: ./dists/bionic/restricted/binary-i386/Release: No such file or directory
./dists/bionic/restricted/binary-i386/Release: FAILED open or read
md5sum: ./dists/bionic/restricted/binary-i386/Packages.gz: No such file or directory
./dists/bionic/restricted/binary-i386/Packages.gz: FAILED open or read
md5sum: ./dists/bionic/restricted/binary-amd64/Release: No such file or directory
./dists/bionic/restricted/binary-amd64/Release: FAILED open or read
md5sum: ./dists/bionic/restricted/binary-amd64/Packages.gz: No such file or directory
./dists/bionic/restricted/binary-amd64/Packages.gz: FAILED open or read
md5sum: ./dists/bionic/Release: No such file or directory
./dists/bionic/Release: FAILED open or read
md5sum: ./dists/bionic/Release.gpg: No such file or directory
./dists/bionic/Release.gpg: FAILED open or read
md5sum: ./dists/bionic/main/binary-i386/Release: No such file or directory
./dists/bionic/main/binary-i386/Release: FAILED open or read
md5sum: ./dists/bionic/main/binary-i386/Packages.gz: No such file or directory
./dists/bionic/main/binary-i386/Packages.gz: FAILED open or read
md5sum: ./dists/bionic/main/binary-amd64/Release: No such file or directory
./dists/bionic/main/binary-amd64/Release: FAILED open or read
md5sum: ./dists/bionic/main/binary-amd64/Packages.gz: No such file or directory
./dists/bionic/main/binary-amd64/Packages.gz: FAILED open or read
md5sum: ./install/mt86plus: No such file or directory
./install/mt86plus: FAILED open or read
md5sum: WARNING: 332 listed files could not be read

```

---

### Post by CatKiller on 2019-11-22
> **John_Patrick_Mason said:**
> Lastly, I'm having trouble verifying the md5sums using CatKiller's method with:

```

md5sum -c /media/mason/"Ubuntu 18.04.3 LTS amd64"/md5sum.txt

```

With that command you're checking the md5 hashes listed in the text file against the files that are in whichever directory you're in (likely ~/).

Something like ```
cd /media/mason/"Ubuntu 18.04.3 LTS amd64"/
md5sum -c md5sum.txt
```
is what you're after.

If you're able to boot from it, there's a "check for errors" option that does the same thing.

---

### Post by John_Patrick_Mason on 2019-11-22
> **CatKiller said:**
> With that command you're checking the md5 hashes listed in the text file against the files that are in whichever directory you're in (likely ~/).

Something like ```
cd /media/mason/"Ubuntu 18.04.3 LTS amd64"/
md5sum -c md5sum.txt
```
is what you're after.

If you're able to boot from it, there's a "check for errors" option that does the same thing.

@CatKiller
That makes much more sense.

I think I will do this from now on, instead of using K3b to verify the disc for me. Is md5sum capable of highlighting files whose md5sums don't match, or do I have to use a utility such as grep to find any files that haven't been burned properly? If so, it would help if I knew what I was looking for, i.e. something like:

```

md5sum -c md5sum.txt | grep 'NOT OKAY'

```

That's just an example, of course. I don't know what a non-matching md5sum looks like.

---

### Post by CatKiller on 2019-11-22
> **John_Patrick_Mason said:**
> I don't know what a non-matching md5sum looks like.

Actually, nor do I. I think that if any individual line has a problem that is also listed at the end of the output, though. 

Having the list of MD5 sums is something that the distros do specifically so that they can embed a utility to check the disc for errors as part of the installation process. It wouldn't be there on an arbitrary burned disc.

---

### Post by John_Patrick_Mason on 2019-11-22
@CatKiller-AKA-DogLover

[QUOTE=CatKiller]
If you're able to boot from it, there's a "check for errors" option that does the same thing.
[/QUOTE]

It's been awhile since I've installed from a live DVD -- I'm still on Ubuntu 16.04 -- but I vaguely remember seeing that option somewhere in the past, but I couldn't find it when I tried to boot from the bootable DVD that I just created. Do I need to click on "Try Ubuntu" first, or is it before that?

Edit: Nevermind, I found the option by holding any key down. I usually check the integrity of any live CD I create through K3b, rather than using that method.

---

### Post by CatKiller on 2019-11-22
> **John_Patrick_Mason said:**
> It's been awhile since I've installed from a live DVD -- I'm still on Ubuntu 16.04 -- but I vaguely remember seeing that option somewhere in the past, but I couldn't find it when I tried to boot from the bootable DVD that I just created. Do I need to click on "Try Ubuntu" first, or is it before that?

Even longer for me: almost all of my machines have no optical drive. I'm pretty sure it's on the very first menu that you see; if the disc's dodgy you don't want to have to load a bunch of (potentially broken) stuff before you get to check. I think they also went through a phase of some menus being hidden behind a keypress, but I don't know if that's still the case.

---

### Post by John_Patrick_Mason on 2019-11-23
> **CatKiller said:**
> Even longer for me: almost all of my machines have no optical drive. I'm pretty sure it's on the very first menu that you see; if the disc's dodgy you don't want to have to load a bunch of (potentially broken) stuff before you get to check. I think they also went through a phase of some menus being hidden behind a keypress, but I don't know if that's still the case.

You're right. I just tested the bootable DVD that I successfully created. The "check CD for defects" option is hidden by default, unless you press a key -- I think, any key will do -- soon after the boot screen. I had almost forgot about it, since that's not usually how I verify the integrity of my live CDs. And that's true for Ubuntu 16.04, as well; I kept my Ubuntu 16.04 installation disc, in case I rendered my Ubuntu partition unbootable -- it happened to me once, while making changes to system files. Ubuntu 14.04 might have been different, but it's no longer supported, anyway.

I should say that the reason I've stuck to DVDs for so long is because when I did try to create a bootable USB stick with Ubuntu 16.04 on it, it wouldn't boot. Ubuntu 18.04 works fine, though -- on a USB stick.

---

### Post by scdbackup on 2019-11-23
Hi,

> by closed, you mean the xorriso-burned DVD can no longer be written to,
> correct?

Yes. A DVD+R can have three states: Blank, Appendable, Closed.
Blank means it is yet unused. Appendable means that it contains data and
still can take another burn run ("session"). Closed means that it cannot
be written any more.

CD-RW and unformatted DVD-RW can be blanked to become writable from scratch
again. CD-R, DVD-R, DVD+R, BD-R stay closed forever. DVD-RAM, DVD+RW, BD-RE,
formatted DVD-RW, formatted CD-RW can be overwritten without blanking,
because they are in the fourth possible state: Overwritable.

> So, what do you think the problem was, a malfunctioning CD/DVD drive?

Obviously. Now the question is: Does it just have some dust on the lense
or is it entirely dead. A good blow with pressured air into the open
drive might work wonders.

--------------------------------------------------------------------------

As for checkreading, i would propose to read the plain DVD+R content instead
of mounting it and checking its files. If the overall image is ok, the files
can hardly be damaged. (libmath says 0 if i try to estimate the probability.
Well, numerical math is always a bit optimistic.)

It is important to read only as many blocks from the DVD as the original
ISO image has. Else the checksum will hardly match.
```

blocks=$(expr $(stat -c '%s' ubuntu-18.04.3-desktop-amd64.iso) / 2048)
dd if=/dev/sr1 bs=2048 count=$blocks | md5sum

```
Compare the resultiing hex number with the hex number in line
```

72491db7ef6f3cd4b085b9fe1f232345 *ubuntu-18.04.3-desktop-amd64.iso

```
of [http://releases.ubuntu.com/18.04/MD5SUMS](http://releases.ubuntu.com/18.04/MD5SUMS)


> I don't know what a non-matching md5sum looks like.

It will be just some string of 32 hex digits [0-9a-f] which is not the same
as the one you expect. E.g. "hallo\n" has this MD5:
```

$ echo hallo | md5sum
aee97cb3ad288ef0add6c6b5b5fae48a  -

```
If you are insecure about comparing 32 digits, let the shell do it for you:
```

$ test 72491db7ef6f3cd4b085b9fe1f232345 = 72491db7ef6f3cd4b085b9fe1f232345 && echo OK
OK
$ test 72491db7ef6f3cd4b085b9fe1f232345 = 72491db7ef6f3cd4b085b9fe1f232340 && echo OK
$

```
(I.e. chirping crickets are a negative outcome.)

Have a nice day :)

Thomas

---

### Post by John_Patrick_Mason on 2019-11-23
```

blocks=$(expr $(stat -c '%s' ubuntu-18.04.3-desktop-amd64.iso) / 2048)
dd if=/dev/sr1 bs=2048 count=$blocks | md5sum

```

OK, I've used **stat** for other purposes, mainly to check access times, which I would think would be useful in a server environment, but, it in this case, **stat -c** fetches the total number of bytes of the ISO file. Then, what?

The book that I learned the command line from didn't cover the **expr** command, but I can see that the **expr** command uses the output of the **stat** command as input (command substitution), and that the output of the **expr** command, ends up getting divided by 2048 in an arithmetic expansion. Is that correct?

---

### Post by scdbackup on 2019-11-24
Hi,

> total number of bytes of the ISO file [...]  divided by 2048
> Is that correct? 

Yes. Ye olde way of doing arithmetics in shell.
```

$ stat -c '%s' ubuntu-18.04.3-desktop-amd64.iso
2082816000
$ expr 2082816000 / 2048
1017000

```
The stat run is put in "$(...)" so that it provides its output as argument
for the expr run. This too is put in "$(...)" to provide its output as content
 for the variable assignment "blocks=".

The kids would save 3 characters of line length by
```

blocks=$(($(stat -c '%s' ubuntu-18.04.3-desktop-amd64.iso) / 2048))

```

Reason for this computation is that dd would be awfully slow if we let
it read and count single bytes (by bs=1). The block size bs=2048 is
the natural granularity of optical data storage and of ISO 9660 filesystems.
So we can safely assume that the division yields an integer result.

The man page of expr can be displaid on a terminal by
```

man expr

```

Have a nice day :)

Thomas

---

