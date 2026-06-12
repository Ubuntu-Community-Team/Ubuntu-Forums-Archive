---
title: "[SOLVED] Print alignment problem with Brother DCP-135C"
date: 2007-12-14
forum: General Help
---

### Post by blueturtl on 2007-12-14
Hello.

I succesfully installed the a newly purchased Brother DCP-135C.

I followed the instructions on Brother's Linux support page and the both the printer and scanner are working. However, printing anything but the test page from the CUPS configuration I observe that the printed information appears a little too much on the right side of a page.

I have set the page size to A4, but it doesn't work.
Does anybody have a solution?

Thanks and merry [your religious holiday here] to you!

---

### Post by Frodo232 on 2007-12-14
I get exactly the same thing with my DCP-115c, the whole page is shifted towards the right, is it a common problem?

---

### Post by blueturtl on 2007-12-14
Bump.

Guess it is since there's you and me now. I'll be posting here if I come up with a solution so you'll benefit too.

Hope someone who knows how to deal with this reads the problem description.

---

### Post by blueturtl on 2007-12-15
I sent Brother the following message:

> Hello.

I just bought this printer and I have problem with printout alignment. It looks like everything that gets printed is shifted towards the right side of the page. A rough estimate would be that the right-side margin is about 1/2 of the left. I have set the paper size to A4, but this does not seem to fix the problem. Interestingly the CUPS test page prints just fine. I run Ubuntu Linux 7.10 and I have set the printer up according to your instructions at solutions.brother.com. Thank you for your support in advance and happy holidays!

Now awaiting their response.

---

### Post by blueturtl on 2008-01-31
Nothing sensible has come out of the Brother tech support (they want me to replace the printer, even though the test pages are printed correctly).

Filed a [bug report]("https://bugs.launchpad.net/ubuntu/+bug/187598") on this today.

---

### Post by Frodo232 on 2008-01-31
That just shows the tech support guys know nothing about linux, its definatly a driver fault not the printer, I have since also had mine connected to a friends windows machine and it prints fine. Why can't people start taking us linux users serously

---

### Post by blueturtl on 2008-02-20
A little progress has been made, new packages are available for Ubuntu Gutsy at

[http://upload.leservicetechnique.com/brother/gutsy/](http://upload.leservicetechnique.com/brother/gutsy/)

See [this page]("https://wiki.ubuntu.com/BrotherDriverPackaging") for which packages to try.

Unfortunately the package for my printer has not yet been uploaded so I can't confirm if these bring about improvement, but those of you with other models with the same problem go ahead and see.

---

### Post by blueturtl on 2008-04-22
A solution finally!

I stumbled on this page via launchpad bug reports:
[http://solutions.brother.com/linux/sol/printer/linux/printsetlpr.html](http://solutions.brother.com/linux/sol/printer/linux/printsetlpr.html)

It appears the CUPS settings do not apply with Brother's own LPR driver so you have to use their special utility to set the paper size correctly.

I logged in as root using sudo -s and then entered the following command:

```
brprintconf_dcp135c -pt A4
```

This fixed print alignment for me.
Apparently command can be printer spesific as I had to use brdprintconf_dcp135c instead of the reference brdprintconf.

This is using the official drivers from Brother, not the included Gutsy/Hardy drivers.

Hope this helps someone.

---

