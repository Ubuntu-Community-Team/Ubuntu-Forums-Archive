---
title: "bluetooth keyboard - no encryption"
date: 2008-01-10
forum: General Help
---

### Post by erpo on 2008-01-10
I just connected my new bluetooth wireless keyboard and mouse to my Ubuntu 7.10 laptop using the included bluetooth adapter that plugs into a USB port. It's this one: [http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=033](http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=033)

I am using the Input service, not hidd. Both devices are marked as trusted.

The problem is that the connection between the keyboard and the laptop is not encrypted. I know it's not encrypted because /var/lib/bluetooth/ADAPTER_ADDR/linkkeys is not present. So my keyboard is broadcasting my unencrypted keystrokes to the entire neighborhood.

How can I fix this?

---

