---
title: "how to add long bond paper size in Canon PPD?"
date: 2018-07-07
forum: General Help
---

### Post by ardouronerous on 2018-07-07
This line is from the PPD
```
*PageSize Legal/Legal [8.50"x14.00" 215.9x355.6mm]: "<</CNPageSizeName(Legal)/PageSize[612 1008]/ImagingBBox null>>setpagedevice"
```

From this, I was able to make this, but I'm not sure about the PageSize.

```
*PageSize Long/Long [8.50"x13.00" 215.9x330.2mm]: "<</CNPageSizeName(Long)/PageSize[??? ???]/ImagingBBox null>>setpagedevice"
```

Please help.

---

### Post by Impavidus on 2018-07-07
It seems that the PageSize is expressed in typographic points, which are equal to 1/72 inch. So that will be  [612 936].

---

### Post by ardouronerous on 2018-07-07
Thanks.
So I got this:
```
*PageSize Long/Long [8.50"x13.00" 215.9x330.2mm]: "<</CNPageSizeName(Long)/PageSize[612 936]/ImagingBBox null>>setpagedevice"
```

However, when I tried to print a PDF with this size, I got a blank page.

---

### Post by ardouronerous on 2018-07-07
I managed to fix the problem, here's my PPD:
[URL="https://paste.ubuntu.com/p/Yr8rGDXswJ/"]https://paste.ubuntu.com/p/Yr8rGDXswJ/
[/URL]
The found the solution here: [URL="https://github.com/endlessm/cnijfilter2/blob/master/ppd/canonmb2700.ppd"]https://github.com/endlessm/cnijfilter2/blob/master/ppd/canonmb2700.ppd
[/URL]
Here are the additions I made:

```
*DefaultImageableArea: A4
*ImageableArea foolscap: "18.14 14.18 594.14 927.50"
*PaperDimension foolscap: "612 936"
*%CNSizeToPrintArea foolscap 4800 7611

*OpenUI *PageSize/Page Size: PickOne
*DefaultPageSize: A4
*PageSize foolscap/Foolscap [8.5"x13" 215.9x330.2mm]: "<</CNPageSizeName(foolscap)/PageSize[612 936]/ImagingBBox null>>setpagedevice"
*de.PageSize foolscap/Foolscap [215.9x330.2mm 8.5"x13"]: "<</CNPageSizeName(foolscap)/PageSize[612 936]/ImagingBBox null>>setpagedevice": ""
*fr.PageSize foolscap/Papier ministre [215.9x330.2mm 8.5"x13"]: "<</CNPageSizeName(foolscap)/PageSize[612 936]/ImagingBBox null>>setpagedevice": ""
*zh.PageSize foolscap/Foolscap [8.5"x13" 215.9x330.2mm]: "<</CNPageSizeName(foolscap)/PageSize[612 936]/ImagingBBox null>>setpagedevice": ""
*ja.PageSize foolscap/Foolscap [215.9x330.2mm 8.5"x13"]: "<</CNPageSizeName(foolscap)/PageSize[612 936]/ImagingBBox null>>setpagedevice": ""
*CloseUI: *PageSize

*OpenUI *PageRegion: PickOne
*DefaultPageRegion: A4
*PageRegion foolscap/Foolscap [8.5"x13" 215.9x330.2mm]: "<</CNPageSizeName(foolscap)/PageSize[612 936]/ImagingBBox null>>setpagedevice"
*de.PageRegion foolscap/Foolscap [215.9x330.2mm 8.5"x13"]: "<</CNPageSizeName(foolscap)/PageSize[612 936]/ImagingBBox null>>setpagedevice": ""
*fr.PageRegion foolscap/Papier ministre [215.9x330.2mm 8.5"x13"]: "<</CNPageSizeName(foolscap)/PageSize[612 936]/ImagingBBox null>>setpagedevice": ""
*zh.PageRegion foolscap/Foolscap [8.5"x13" 215.9x330.2mm]: "<</CNPageSizeName(foolscap)/PageSize[612 936]/ImagingBBox null>>setpagedevice": ""
*ja.PageRegion foolscap/Foolscap [215.9x330.2mm 8.5"x13"]: "<</CNPageSizeName(foolscap)/PageSize[612 936]/ImagingBBox null>>setpagedevice": ""
*CloseUI: *PageRegion

*CloseGroup: *CNGeneral


*UIConstraints: *PageSize foolscap *Duplex DuplexNoTumble
*UIConstraints: *PageSize foolscap *Duplex DuplexTumble
```

---

### Post by ardouronerous on 2018-07-07
Printer is not printing now, even a test page. How do I fix?

---

