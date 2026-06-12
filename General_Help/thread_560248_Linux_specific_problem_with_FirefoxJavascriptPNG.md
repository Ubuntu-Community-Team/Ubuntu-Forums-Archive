---
title: "Linux specific problem with Firefox/Javascript/PNG"
date: 2007-09-26
forum: General Help
---

### Post by notamonopoly on 2007-09-26
I wasn't sure what the best category would be for this problem.

I am building a website that allows objects to be dragged around the screen, widgets I guess. I just added an absolute positioned div that takes up 100% of the screen and has a semi-transparent PNG image repeated in the background. With a lower z-index than the dragable element this acts as an overlay. So far so good.

I noticed that as soon as I added the overlay the dragging became extremely choppy, to the point of not being usable. This only occurs in Firefox under Linux (Ubuntu). 

Works fine in Opera (Ubuntu and Windows), Internet Explorer, Netscape and oddly, Firefox under Windows.

So the problem is restricted to this single browser and only on Ubuntu. To make the problem even more confusing, it only happens when the background is semi-transparent. If I edit the image and make it 100% transparent or 0% transparent (100% Opac), it works perfectly.

I'm using:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty)

I don't have a live site to point to and the code is far too involved to take any one piece and have it mean anything so I can't paste it here. Not that it would help really, as the issue is definitely with the browser and not the code.

Does anyone have any suggestions? I would hate to have Firefox on Ubuntu be the only browser/platform that I can't support.

Thanks

---

