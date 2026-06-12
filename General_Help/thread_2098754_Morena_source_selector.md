---
title: "Morena source selector"
date: 2012-12-27
forum: General Help
---

### Post by cigtoxdoc on 2012-12-27
PDF Studio Pro 8 by Qoppas Software uses Morena source selector to select the scanner to use.  My scanner is part of a Brother MFC-9440CN.  It works with xsane, gscan2pdf, etc., but everything (for example, Bus 002 Device 005: ID 04f9:01ca Brother Industries, Ltd MFC-9440CN Remote Setup Port)
I enter into the Morena source selector causes an error.  The technical support person apparently does not know either as she sent me to [http://penguin-breeder.org/sane/saned](http://penguin-breeder.org/sane/saned),  That website assumes you are a Linux guru.

sane-find-scanner gives, "found USB scanner (vendor=0x04f9, product=0x01ca) at libusb:002:005"

lsusb gives, "Bus 002 Device 005: ID 04f9:01ca Brother Industries, Ltd MFC-9440CN Remote Setup Port"

What is the magic line of code that the Morena source selector is looking for?

Thank you,

John

---

