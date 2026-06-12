---
title: "Problem with glabels (using dymo labelwriter duo)"
date: 2024-05-29
forum: General Help
---

### Post by jgw on 2024-05-29
I am trying to setup glabels to print using a dymo labelwriter duo.  This one is strange.  Here is the template file for it:

<?xml version="1.0"?>
<Glabels-templates xmlns="http://glabels.org/xmlns/3.0/">
  <Template brand="Dymo" part="30336" size="Other" width="2.125in" height="2.750in" description="Big Label">
    <Label-rectangle id="0" width="2.125in" height="2.75in" round=".025in" x_waste="0in" y_waste="0in">
      <Markup-margin size="0.125in"/>
      <Layout nx="1" ny="1" x0="0in" y0="0in" dx="2.125in" dy="2.75in"/>
    </Label-rectangle>
  </Template>
</Glabels-templates>

My problem is that the resulting print uses approximately half of the 2 1/8in x 2.75in and I do not know why.  Every thing that I print is shrunk down.  The size is "other" which should be enough to make the 2.125in x 2.75in and I cannot figure out what I have done wrong.  I have not used the dymo for quite a while and everything used to work just fine.  I had to reconstruct the above as I had lost the other one. I also tried to find out what version of glabels I have but Ubuntu doesn't think there is such a program on my machine (there is).  I will try and send a picture of what I have now.  The picture is just a test of stuff to see if anything changed anything.

---

### Post by jgw on 2024-06-01
I am using the "Dymo Label Printer" as my Driver.  There was another offered at drv:///sample.drv/dymo.ppd but I have no idea how to find or download it so I can install it.  It may be able to fix my problem.

Thoughts?

---

### Post by him610 on 2024-06-01
Does this help? [https://packages.ubuntu.com/search?keywords=printer-driver-dymo]("https://packages.ubuntu.com/search?keywords=printer-driver-dymo")

---

### Post by jgw on 2024-06-02
Thank you for the reply!
I got:
Exact hits
Package printer-driver-dymo

    focal (20.04LTS) (text): printer driver for DYMO label printers [universe]
    1.4.0-9build1: amd64 arm64 armhf ppc64el riscv64 s390x
    jammy (22.04LTS) (text): printer driver for DYMO label printers [universe]
    1.4.0-11: amd64 arm64 armhf ppc64el riscv64 s390x
    mantic (23.10) (text): printer driver for DYMO label printers [universe]
    1.4.0-12: amd64 arm64 armhf ppc64el riscv64 s390x
    noble (24.04LTS) (text): printer driver for DYMO label printers [universe]
    1.4.0-12build2: amd64 arm64 armhf ppc64el riscv64 s390x
    oracular (text): printer driver for DYMO label printers [universe]
    1.4.0-12build2: amd64 arm64 armhf ppc64el riscv64 s390x

I also tried:
[https://packages.ubuntu.com/search?keywords=printer-dymo](https://packages.ubuntu.com/search?keywords=printer-dymo)   and a couple of others.  Haven't tried any of the above but thought I would let you know.

Now all I have to do is figure out what to do with it.

---

### Post by jgw on 2024-06-10
I solved my problem.  I just started doing stuff I found on the net.  I found this one:
[https://installati.one/install-printer-driver-dymo-ubuntu-22-04/](https://installati.one/install-printer-driver-dymo-ubuntu-22-04/)

It worked!  Amazing and wonderful.

thank you for the responses..............

---

