---
title: "How to fulfill the page when printing via cups?"
date: 2015-05-18
forum: General Help
---

### Post by xiyu on 2015-05-18
Hi there):P! I'm new here and any advise would be greatly appreciated.
I'm using cups-1.2.12 to do a printing job with command-line. I followed this tutorial  ([https://www.cs.utexas.edu/facilities/documentation/printing-options](https://www.cs.utexas.edu/facilities/documentation/printing-options)) to configure my printer and everything goes well. But for some reason, I want the printer to print a page fulfilled with the image, even distortion might occur.
For instance, there's a bit-map image whose original size is 4,200*2,100 pixels. This image aspect ratio is 2.0 but the standard A4 page (210mm*297mm) is  1.414.
With the option "fitplot"(means scaling to fit the page as the image aspect ratio allows), the printer's output is fairly satisfied but there's still a large blank area which is not used looks not comfortable. I want the image to be printed on the whole page without large blank areas.
Is there any possibility to achieve this feature?
Thanks in advance.:p

p.s. printing job with command-line 
```
lpoptions -p HP-LaserJet1010 -o PageSize=A4 -o fitplot
lp -d HP-LaserJet1010 testfile.bmp
```

---

### Post by Frogs Hair on 2015-05-18
Support question, moved to general help.

---

### Post by dino99 on 2015-05-18
with a gui the printing settings are shown with a dialog box; but without gui you need the lpr command:
 [http://www.computerhope.com/unix/ulpr.htm](http://www.computerhope.com/unix/ulpr.htm)
[http://www.thegeekstuff.com/2015/01/lpadmin-examples/](http://www.thegeekstuff.com/2015/01/lpadmin-examples/)

---

### Post by xiyu on 2015-05-18
Sorry to trouble you. Thanks.

---

### Post by xiyu on 2015-05-18
Thanks for your reply.
I'm using cups-1.2.12 without GUI. With the CUPS command-line manual from the site you attached, I cannot find anymore printing options of my printer except these:
```
# lpoptions -p HP-LaserJet1010 -l
PageSize/Media Size: Card3x5 Hagaki A6 Card5x8 Oufuku A5 B5 JB5 Executive 16k Letter *A4 ExecutiveJIS FLSA Legal EnvA2 EnvC6 EnvChou4 EnvMonarch EnvDL Env10 EnvChou3 EnvC5 EnvB5 Custom
PageRegion/Media Size: Card3x5 Hagaki A6 Card5x8 Oufuku A5 B5 JB5 Executive 16k Letter A4 ExecutiveJIS FLSA Legal EnvA2 EnvC6 EnvChou4 EnvMonarch EnvDL Env10 EnvChou3 EnvC5 EnvB5 Custom
Duplex/Double-Sided Printing: DuplexNoTumble DuplexTumble *None
InputSlot/Media Source: *Auto PhotoTray Upper Lower Envelope LargeCapacity Manual MPTray
ColorModel/Output Mode: *Gray
MediaType/Media Type: *Plain
OutputMode/Print Quality: *Normal Draft
OptionDuplex/Duplexer Installed: *False True

```
But I found that there are some extra printing options seem to be useful when I checked the source code of CUPS. As the printing options in the source code, they are testified to be available. Here are some segments for illustration(the color of options is changed to red):
```
  if ((val = cupsGetOption("[COLOR=#ff0000]scaling[/COLOR]", num_options, options)) != NULL)
	  zoom = atoi(val) * 0.01;	
  else if (cupsGetOption("[COLOR=#ff0000]fitplot[/COLOR]", num_options, options))
    zoom = 1.0;


  if ((val = cupsGetOption("[COLOR=#ff0000]ppi[/COLOR]", num_options, options)) != NULL)
    if (sscanf(val, "%dx%d", &xppi, &yppi) < 2)
      yppi = xppi;


```
Unfortunately, there's no printing option which is related to "fulfilling the page". Does this feature depend on printer or printing options? Is there any possibility to program a piece of code by ourselves and insert it to the CUPS source code for this feature? I'm confused now. 
I'm newbie here and my English is poor:p. There must be some mistakes in my description. Sorry for that.
Thanks, buddy.
yu xi.

---

