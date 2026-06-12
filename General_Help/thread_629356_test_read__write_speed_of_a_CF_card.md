---
title: "test read / write speed of a CF card"
date: 2007-12-02
forum: General Help
---

### Post by markp1989 on 2007-12-02
i brought a CF card on ebay it was sold as a 150X  Cf card, i was wondering if there is any software available to test the read/write speed of the CF card?

---

### Post by fjgaude on 2007-12-02
You see the card as a drive and it has a label. Use this:

```
sudo hdparm -tT /dev/label
```

The card should show something around 25 MB/sec read throughput.

Let us know what you get.

---

### Post by markp1989 on 2007-12-02
Thanks for the fast reply, here is the out put:


```
mark@mark-desktop:~$ sudo hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   728 MB in  2.00 seconds = 363.67 MB/sec
 Timing buffered disk reads:    4 MB in  4.51 seconds = 908.71 kB/sec

```

what do these mean?

this is currently using a usb card reader, il do another test when i get my CF to ide adapter, i ordered it over 3 weeks ago, and its taking for ever!!

---

### Post by markp1989 on 2008-05-11
does any one know why my usb hard drive is so slow?

mark@eee:~$ sudo hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:   664 MB in  2.00 seconds = 331.65 MB/sec
 Timing buffered disk reads:    4 MB in  4.54 seconds = 902.31 kB/sec

never mind , had my eee set to usb 1 by mistake

---

