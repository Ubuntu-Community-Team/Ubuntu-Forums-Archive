---
title: "Cannot use Brother HL5140"
date: 2015-06-29
forum: General Help
---

### Post by CkDGTAT on 2015-06-29
Hi,

Though having properly installed the plugin given on Brother printer website:

[http://support.brother.com/g/b/downloadtop.aspx?c=au&lang=en&prod=hl5140_all](http://support.brother.com/g/b/downloadtop.aspx?c=au&lang=en&prod=hl5140_all)

I am unable to print anything. The status gives "Waiting for printers to become available".

Thank you for your support

---

### Post by plucky on 2015-06-29
> **CkDGTAT said:**
> Hi,

Though having properly installed the plugin given on Brother printer website:

[http://support.brother.com/g/b/downloadtop.aspx?c=au&lang=en&prod=hl5140_all](http://support.brother.com/g/b/downloadtop.aspx?c=au&lang=en&prod=hl5140_all)

I am unable to print anything. The status gives "Waiting for printers to become available".

Thank you for your support

Open a terminal and post output for ```
dpkg -l | grep Brother
``` so we can see what has been installed.

Are you connected by USB connection?

---

